# ユーザー設定を設定する

```
ii $PROFILE
# 開いたファイルに設定を書く
# bashrcみたいなやつ

# ファイルがない場合は下記で作成
New-Item $PROFILE
```

# キーバインドを変更する

```
Set-PSReadLineKeyHandler -Chord <shortcut> -Function <function name>
# 例 ctrl+a を先頭行に戻るに割り当てる
Set-PSReadLineKeyHandler -Chord Ctrl+a -Function BeginningOfLine
```

# 設定可能なキーバインド一覧を表示する

```
Get-PSReadLineKeyHandler
```

# 独自関数をエイリアスに割り当てる

```
function _test()
{
    echo test
}

Set-Alias say_test _test
```

# gitコマンドの補完を有効化する

```
Install-Module -Name posh-git -AllowPrerelease -Scope CurrentUser
"Import-Module posh-git" | Add-Content $PROFILE
# powershellを再起動する
```

# psコマンド
https://mathieubuisson.github.io/powershell-linux-bash/
```
Get-process
Get-Process | Where-Object WorkingSet -gt 104857600
```

# ping

```
Test-Connection 8.8.8.8
Test-Connection 8.8.8.8 | Format-Table -AutoSize
```

# tail

```
Get-Content -Tail 7 .\MyFile1
# tail -f
Get-Content -Tail 7 .\MyFile1 -Wait
```

# ビルドツール

```
Install-Module InvokeBuild
```

# yaml 

https://github.com/cloudbase/powershell-yaml
```
Install-Module -Name powershell-yaml -Scope CurrentUser
"Import-Module powershell-yaml" | Add-Content $PROFILE

# サンプル
 Get-Content .\test.yml| ConvertFrom-Yaml | ConvertTo-Yaml -JsonCompatible
```