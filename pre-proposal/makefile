PREFIX = proposal
PREFIX2 = supplement
TEXFILE = $(PREFIX).tex
TEXFILE2 = $(PREFIX2).tex
BIBFILE = $(PREFIX).aux
LATEX = pdflatex
BIBTEX = biber
TRASH = *.aux *.log *.dvi *.ps *.nav *.out *.snm *.backup *.bak *.toc *~ *.bbl *.blg *.toc *.run.xml *-blx.bib *.bcf


sciencetext:
	$(LATEX) -halt-on-error '\def\haveScience{} \input '$(TEXFILE)

impacttext:
	$(LATEX) -halt-on-error '\def\haveImpact{} \input '$(TEXFILE)

profiletext:
	$(LATEX) -halt-on-error '\def\haveProfile{} \input '$(TEXFILE)

abstracttext:
	$(LATEX) -halt-on-error '\def\haveAbstract{} \input '$(TEXFILE)

outputtext:
	$(LATEX) -halt-on-error '\def\haveOutput{} \input '$(TEXFILE)
	$(BIBTEX) $(PREFIX)
	$(LATEX) -halt-on-error '\def\haveOutput{} \input '$(TEXFILE)
	$(LATEX) -halt-on-error '\def\haveOutput{} \input '$(TEXFILE)


wordCountProfile:
	make profiletext 
	pdftotext proposal.pdf
	cat proposal.txt | wc -w > wordProfile.tex
	cat wordProfile.tex

wordCountOutput:
	make outputtext 
	pdftotext proposal.pdf
	cat proposal.txt | wc -w > wordOutput.tex
	cat wordOutput.tex

wordCountAbstract:
	make abstracttext 
	pdftotext proposal.pdf
	cat proposal.txt | wc -w > wordAbstract.tex
	cat wordAbstract.tex

wordCount: wordCountAbstract wordCountOutput wordCountProfile


single:
	cat summary.tex | wc -w > wordSummary.tex
	cat public-summary-en | wc -w > wordPublicEN.tex
	$(LATEX) -halt-on-error '\def\haveAbstract{} \def\haveScience{} \def\haveImpact{} \def\haveFirstLit{} \def\haveProfile{} \def\haveOutput{} \input '$(TEXFILE)

singlepdf:
	cat summary.tex | wc -w > wordSummary.tex
	cat public-summary-en | wc -w > wordPublicEN.tex
	$(LATEX) -halt-on-error '\def\haveAbstract{} \def\haveScience{} \def\haveImpact{} \def\haveFirstLit{} \def\haveProfile{} \def\haveOutput{} \input '$(TEXFILE)
	$(BIBTEX) $(PREFIX)
	$(LATEX) -halt-on-error '\def\haveAbstract{} \def\haveScience{} \def\haveImpact{} \def\haveFirstLit{} \def\haveProfile{} \def\haveOutput{} \input '$(TEXFILE)
	$(LATEX) -halt-on-error '\def\haveAbstract{} \def\haveScience{} \def\haveImpact{} \def\haveFirstLit{} \def\haveProfile{} \def\haveOutput{} \input '$(TEXFILE)

pdf: wordCount
	cat summary.tex | wc -w > wordSummary.tex
	cat public-summary-en | wc -w > wordPublicEN.tex
	$(LATEX) -halt-on-error '\def\haveAbstract{} \def\haveScience{} \def\haveImpact{} \def\haveFirstLit{} \def\haveProfile{} \def\haveOutput{} \input '$(TEXFILE)
	$(BIBTEX) $(PREFIX)
	$(LATEX) -halt-on-error '\def\haveAbstract{} \def\haveScience{} \def\haveImpact{} \def\haveFirstLit{} \def\haveProfile{} \def\haveOutput{} \input '$(TEXFILE)
	$(LATEX) -halt-on-error '\def\haveAbstract{} \def\haveScience{} \def\haveImpact{} \def\haveFirstLit{} \def\haveProfile{} \def\haveOutput{} \input '$(TEXFILE)
	#rm -rf $(TRASH)
	#zip supplement.zip $(PREFIX2).pdf ../../../AAAI/totsat/paper/Behnke2018totSAT.pdf 

.PHONY: bib
bib:
	#cat /home/gregor/Dokumente/svn/private/bibtex/main.bib | awk -f /home/gregor/Dokumente/svn/private/bibtex/filter.awk -- -shortproc -nopublisher -nopages  > paper.bib
	cat /home/gregor/Dokumente/svn/private/bibtex/main.bib | awk -f /home/gregor/Dokumente/svn/private/bibtex/filter.awk -- > application.bib
	#cat /home/gregor/Dokumente/svn/private/bibtex/main.bib | awk -f /home/gregor/Dokumente/svn/private/bibtex/filter.awk --  > paper.bib
	#cat /home/gregor/Dokumente/svn/private/bibtex/main.bib | awk -f /home/gregor/Dokumente/svn/private/bibtex/filter.awk -- -onlyconf -nopublisher | sed 's/Proc. of //g'> paper.bib


.PHONY: clear
clear:
	rm -rf $(TRASH)
