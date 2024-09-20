---
tags:
  - BibTeX
  - bibtex-tidy
  - IPSJ
---

# BibTeX

## 参考文献の参照

- `~` （チルダ）を `\cite{}` の前に書くことで参照記号の直前で改行されてしまうことを防ぐ。
- 文に対して参考文献を示す場合、句点の後ではなく句点の前に参照記号を書くことに注意する。


1つの文献を参照する場合:

```tex
これは参考文献を参照する場合の記述例である~\cite{Sample}．
```

```tex
文献~\cite{Sample}では，〜が提案されている．
```

複数の文献を参照する場合:

```tex
これは参考文献を参照する場合の記述例である~\cite{Sample1,Sample2}．
```

```tex
文献~\cite{Sample1,Sample2}では，〜が提案されている．
```

## 参考文献リスト

### Fields (フィールド)

#### author (著者)

- 複数の著者名は `and` で繋ぐこと。複数の著者名を `, ` で繋ぐのは誤りなので注意する。
- 著者名はカンマを使って「名, 姓」の順番で書くこともできる。
- 英語の場合はイニシャルが用いられる場合もあるが推奨しない。フルネームで書く方が良い。
- 著者名が組織名の場合は `{` `}` で囲むことでセンテンスケース（Sentence case）への変換を抑制できる。
- 著者名を間違うと大変失礼なので絶対に間違わないこと。

##### 著者の記述例

```
author = {著者 太郎 and 著者 花子},
```

```
author = {太郎, 著者 and 花子, 著者},
```

```
author = {Taro Chosya and Hanako Chosya},
```

```
author = {Chosya, Taro and Chosya, Hanako},
```

```
author = {T. Chosya and H. Chosya},
```

```
author = {Chosya, T. and Chosya, H.},
```

```
author = {{Company LLC}},
```

##### 著者の一部省略

原則として著者は全てフルスペルで書き出す。ただし、特定の条件では、著者数が多い場合に、全ての著者を記述せずに後半の著者を省略しても良い場合がある。例えば[情報処理学会の場合は、4名以上の場合に省略可能](https://www.ipsj.or.jp/journal/submit/ronbun_j_prms.html)としている。繰り返しになるが、原則として著者は全てフルスペルで書き出すこと。原稿のページ数に制限がある場合で、ページ制限内に収まらない場合に限って省略するようにすると良い。

BibTeXでは次のように `others` を使うことで残りの著者を省略できる。

```
author = {Taro Tottori and Hanako Kuratyosi and Torimi Yonago and others},
```

### 記述例

#### 学術雑誌論文

- DOIは積極的に記載する。
- DOIが無い場合、 `url` を記載することもできる。

=== "IPSJ"

    ```bibtex
    @article{Example,
      author = {著者 太郎 and 著者 花子},
      title = {論文のタイトル},
      journal = {サンプル学会論文誌},
      year = 2024,
      volume = 1,
      number = 1,
      pages = {1--10},
	  doi =	{prefix/suffix},
    }
    ```

#### 国際会議論文

=== "IPSJ"

- DOIは積極的に記載する。
- DOIが無い場合、 `url` を記載することもできる。

    ```bibtex
    @inproceedings{Example,
      author = {Taro Chosya and Hanako Chosya},
      title = {Example Title},
      year = 2024,
      booktitle = {In Proceedings of The 1st International Conference on Example},
      pages = {1--8},
	  doi =	{prefix/suffix},
    }
    ```

#### ウェブページ

- ウェブページは内容が変更される場合があるので、参照した年月日を記載する。
- 論文執筆時のウェブページの内容が失われないように、PDF形式やMHTML形式でハードコピーを保存しておく。

=== "IPSJ"

   ```bibtex
   @webpage{Example,
     title = {Example},
     author = {Taro Chosya and Hanako Chosya},
     organization = {Example University},
     url = {https://example.net},
     refdate = {2024-04-01},
   }
   ```

### フォーマッタの利用

`.bib` ファイルを自動整形するには、[bibtex-tidy](https://github.com/FlamingTempura/bibtex-tidy) が非常に便利である。

- CLIで使う場合: [https://github.com/FlamingTempura/bibtex-tidy](https://github.com/FlamingTempura/bibtex-tidy) をインストールして使う。
- GUIで試す場合: [こちらのリンク](https://flamingtempura.github.io/bibtex-tidy/index.html?opt=%7B%22modify%22%3Atrue%2C%22curly%22%3Atrue%2C%22numeric%22%3Atrue%2C%22months%22%3Afalse%2C%22space%22%3A2%2C%22tab%22%3Afalse%2C%22align%22%3A1%2C%22blankLines%22%3Atrue%2C%22duplicates%22%3A%5B%22key%22%2C%22doi%22%5D%2C%22stripEnclosingBraces%22%3Afalse%2C%22dropAllCaps%22%3Afalse%2C%22escape%22%3Afalse%2C%22sortFields%22%3A%5B%22title%22%2C%22shorttitle%22%2C%22author%22%2C%22year%22%2C%22month%22%2C%22day%22%2C%22journal%22%2C%22booktitle%22%2C%22location%22%2C%22on%22%2C%22publisher%22%2C%22address%22%2C%22series%22%2C%22volume%22%2C%22number%22%2C%22pages%22%2C%22doi%22%2C%22isbn%22%2C%22issn%22%2C%22url%22%2C%22urldate%22%2C%22copyright%22%2C%22category%22%2C%22note%22%2C%22metadata%22%5D%2C%22stripComments%22%3Afalse%2C%22trailingCommas%22%3Atrue%2C%22encodeUrls%22%3Afalse%2C%22tidyComments%22%3Atrue%2C%22removeEmptyFields%22%3Afalse%2C%22removeDuplicateFields%22%3Afalse%2C%22lowercase%22%3Atrue%2C%22backup%22%3Atrue%7D)から試せる。

CLIでの使用方法:

```sh
$ npx bibtex-tidy --help
```

```sh
$ npx bibtex-tidy --no-align --blank-lines --duplicates=key,doi --no-escape --sort-fields --trailing-commas --no-remove-dupe-fields main.bib
```
