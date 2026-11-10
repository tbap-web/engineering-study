# Windows の PowerShell で Git を使えるようにする

2026年11月10日 · 環境構築

PowerShell で `git --version` を実行すると、`CommandNotFoundException` が出た。

## Git がインストールされているか確認する

```powershell
Test-Path 'C:\Program Files\Git\cmd\git.exe'
```

`True` が返った。実行ファイルをフルパスで呼び出すと Git のバージョンも表示された。

## ユーザー環境変数 Path に追加する

1. Windows の検索で「環境変数」を探し、「アカウントの環境変数を編集」を開く。
2. ユーザー環境変数の `Path` を選び、「編集」を押す。
3. 一覧に `C:\Program Files\Git\cmd` がなければ「新規」で追加し、「OK」で保存する。

## 新しい PowerShell で確かめる

開いている PowerShell を閉じて起動し直し、次のコマンドを実行する。

```powershell
git --version
```

この PC では `git version 2.56.0.windows.4` と表示された。`Path` は、コマンド名だけを指定したときに Windows が実行ファイルを探すフォルダーの一覧だ。

[記事一覧に戻る](../index.md)
