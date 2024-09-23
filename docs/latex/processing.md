---
tags:
  - Draft
---

# LaTeXの処理系

Under Construction.

日本語文書を処理する場合の例

## pLaTeX + pBibTeX + dvipdfmx

`platex` コマンドは次のように複数回実行する必要がある。

```shell-session
$ platex main
$ pbibtex main
$ platex main
$ platex main
$ dvipdfmx main
```

`latexmk` を使えば複数のコマンドの実行を自動化できる。

次のように `latexmkrc` ファイルを用意しておく。

```.pl title="latexmkrc"
$latex = 'platex';
$bibtex = 'pbibtex';
$dvipdf = 'dvipdfmx %O -o %D %S';
$makeindex = 'mendex %O -o %D %S';
$pdf_mode = 3;
```

次のように `latexmk` コマンドを実行する。

```shell-session
$ latexmk -f main
```

各コマンドと入出力ファイルの関係は次のとおり。


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
  classDef src stroke-width:4px, stroke:#E69F00
  classDef dst stroke-width:4px, stroke:#009E73
  classDef tmp stroke-width:1px, stroke-dasharray: 5 5
  classDef fmt stroke-width:4px, stroke:#0072B2
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

英語文書を処理する場合の例



