# QRコード

## QRコードのベクタ形式画像を生成する。

QRコードの画像はベクター形式の方が良い。[segno](https://pypi.org/project/segno/)を使うのが便利のようだ。

インストール:

```sh
$ pip install segno
```

使い方:

```sh
$ segno --output="example.net.pdf" "https://example.net"
```

```sh
$ segno --help
```
