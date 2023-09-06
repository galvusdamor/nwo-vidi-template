# nwo-vidi-template
This is a LaTeX template for proposals of the 2023 Vidi proposals of the NWO.

## Pre-Proposal
The template for the pre-proposal is located in the directory pre-proposal.
The makefile contains several targets.
`make single` simply compiles the proposal once.
`make singlepdf` compiles the proposal including bibtex (note: we use biber for compilation).
`make pdf` compiles the proposal including bibtex and *determines the wordcounts of the individual sections*.

Note that you need to run `make pdf` *first* as it creates files that include the word counts that are included in the overall proposal.
