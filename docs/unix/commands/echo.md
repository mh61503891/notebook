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

実行例:

```shell title="shell"
echo -e "a\tb\tc"
```