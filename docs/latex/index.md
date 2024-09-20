# LaTeX

## pLaTeX + pBibTeX + dvipdfmx

Under Construction.

```shell-session
$ platex main
$ pbibtex main
$ platex main
$ platex main
$ dvipdfmx main
```

```shell-session
$ latexmk
```

```mermaid
graph LR
  TEX --> PLATEX
  STY --> PLATEX
  BBL --> PLATEX
  PLATEX --> AUX
  PLATEX --> DVI
  PLATEX --> LOG
  AUX --> PBIBTEX
  BIB --> PBIBTEX
  BST --> PBIBTEX
  PBIBTEX --> BBL
  PBIBTEX --> BLG
  DVI --> DVIPDFMX
  DVIPDFMX --> PDF
  TEX[.tex]:::src
  BIB[.bib]:::src
  STY[.sty]:::fmt
  AUX[.aux]:::tmp
  DVI[.dvi]:::tmp
  LOG[.log]
  BLG[.blg]
  BST[.bst]:::fmt
  BBL[.bbl]:::tmp
  PDF[.pdf]:::dst
  PLATEX([platex])
  PBIBTEX([pbibtex])
  DVIPDFMX([dvipdfmx])
  classDef src stroke-width:4px
  classDef dst stroke-width:4px, stroke:#0f0
  classDef tmp stroke-width:1px, stroke-dasharray: 5 5
  classDef fmt stroke-width:4px, stroke:#f96
```

- source files
	- `.tex`
	- `.bib`
- template files
	- `.sty`
	- `.bst`
- log files
	- `.log`
	- `.blg`
- temporary files
	- `.aux`
	- `.bbl`
- final output files
	- (`.dvi`)
	- `.pdf`

## pdfTeX + BibTeX

Under Construction.
