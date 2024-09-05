# echo

## Tips

### echoコマンドでタブなどの制御文字を出力する。

`-e` オプション（an escape character）を指定する必要がある。

例:

```console
$ echo -e "a\tb\tc"
```