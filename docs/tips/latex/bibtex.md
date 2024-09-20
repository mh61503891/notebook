# BibTeX

## Tips

### Fields

#### author (著者)

- 複数の著者名は `and` で繋ぐ。 `, ` で繋ぐのは誤りなので注意する。
- 著者名はカンマを使って「名, 姓」の順番で書くこともできる。
- 英語の場合はイニシャルが用いられる場合もあるがあまり推奨しない。可能であればフルネームで書く方が良い。
- 著者が組織名の場合は `{` `}` で囲むことでセンテンスケース（Sentence case）への変換を抑制できる。

著者の記述例

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



## 記述例

### 学術雑誌論文

- DOIは積極的に記載する。

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

### 国際会議論文

=== "IPSJ"

- DOIは積極的に記載する。

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

### ウェブページ

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


