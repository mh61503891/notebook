---
tags:
  - Draft
---

# LaTeXのセットアップ

## インストール

=== "macOS :material-apple:"

	macOSでは[Homebrew](https://brew.sh/)を使って[TeX Live](https://www.tug.org/texlive/)をインストールするのが楽である。

	以下のコマンドでインストールする。

	```sh
	$ brew install texlive
	```

=== "Windows :material-microsoft-windows:"

	Under Construction.

## 動作確認

日本語文書を扱う場合で、かつpLaTeXを用いる場合は、次の3つのコマンドが動作することを確認する。

- `platex`
- `pbibtex`
- `dvipdfmx`

=== "macOS :material-apple:"

	`platex` コマンドのバージョンを確認する。ロングオプションの `-version` のハイフンは1つであることに気を付ける。

	```shell-session
	$ platex -version
	e-upTeX 3.141592653-p4.1.1-u1.30-230214-2.6 (utf8.euc) (TeX Live 2024/Homebrew)
	kpathsea version 6.4.0
	ptexenc version 1.4.6
	Copyright 2024 D.E. Knuth.
	There is NO warranty.  Redistribution of this software is
	covered by the terms of both the e-upTeX copyright and
	the Lesser GNU General Public License.
	For more information about these matters, see the file
	named COPYING and the e-upTeX source.
	Primary author of e-upTeX: Japanese TeX Development Community.
	```

	`pbibtex` のバージョンを確認する。ロングオプションの `-version` のハイフンは1つであることに気を付ける。

	```shell-session
	$ pbibtex -version
	upBibTeX 0.99d-j0.36-u1.30 (utf8.euc) (TeX Live 2024/Homebrew)
	kpathsea version 6.4.0
	ptexenc version 1.4.6
	Copyright 2024 Oren Patashnik.
	There is NO warranty.  Redistribution of this software is
	covered by the terms of both the upBibTeX copyright and
	the Lesser GNU General Public License.
	For more information about these matters, see the file
	named COPYING and the upBibTeX source.
	Primary author of upBibTeX: Oren Patashnik.
	```

	`dvipdfmx` コマンドのバージョンを確認する。ロングオプションの `--version` のハイフンは**2つ**であることに気を付ける。

	```shell-session
	$ dvipdfmx --version
	This is dvipdfmx Version 20240305 by the DVIPDFMx project team,
	modified for TeX Live,
	an extended version of dvipdfm-0.13.2c developed by Mark A. Wicks.

	Copyright (C) 2002-2024 the DVIPDFMx project team
	Copyright (C) 2006-2024 SIL International.

	This is free software; you can redistribute it and/or modify
	it under the terms of the GNU General Public License as published by
	the Free Software Foundation; either version 2 of the License, or
	(at your option) any later version.
	```

=== "Windows :material-microsoft-windows:"

	Under Construction.
