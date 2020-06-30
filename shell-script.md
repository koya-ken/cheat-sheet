# 標準出力と標準エラーと両方を同時に出力する

```
command 2>&1 > >(tee stdout.log >&1) 2> >(tee stderr.log >&2) | tee all.log
```