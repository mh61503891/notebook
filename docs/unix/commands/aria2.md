---
tags:
  - aria2
  - CLI
description: aria2コマンドに関するメモです。
---

# aria2

[aria2](https://aria2.github.io/)は複数サーバから分割ダウンロードを行うのに便利なコマンドです。OSのイメージファイルなど巨大なファイルをダウンロードする場合にダウンロード時間を短縮できます。

主要なオプション:

- `--max-connection-per-server`: サーバ1台あたりの接続数を指定します。
    - あまり大きな値は指定しないようにしましょう。サーバ側でBANされるかも知れません。2か3程度が良い気がします。
- `--continue`: ダウンロードを中断した場合に続きからダウンロードできるようにします。

実行例:

```sh
$ aria2c --max-connection-per-server=3 --continue=true https://example.net/
```
