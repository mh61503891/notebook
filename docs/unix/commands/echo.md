---
tags:
  - echo
  - CLI
  - 制御文字
description: echoコマンドに関するメモです。
---

# echo

## Tips

### echoコマンドでタブなどの制御文字を出力する。

`-e` オプション（an escape character）を指定する必要がある。

例:

```sh
$ echo -e "a\tb\tc"
```