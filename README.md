# 工学の勉強ノート

試したことと、そこからわかったことを残す技術ブログです。

## PC でプレビューする

リポジトリのフォルダーを VS Code で開き、ターミナルで次を実行します。最初の2行は初回だけ実行します。

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m mkdocs serve
```

ターミナルに表示されたアドレスをブラウザーで開きます。終了するときはターミナルで Ctrl+C を押します。

## 記事を追加する

1. `docs/posts` に Markdown ファイルを作ります。
2. `docs/index.md` の記事一覧と `mkdocs.yml` の `nav` に記事を追加します。
3. プレビューで表示を確認します。変更をコミットして `main` にプッシュすると、GitHub Actions がサイトを生成して公開します。
