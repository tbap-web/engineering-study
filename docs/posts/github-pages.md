# GitHub Pages で技術ブログを公開する手順

2026年11月10日 · 公開

PC に保存していたこのブログを、GitHub Pages で誰でも読めるようにした。HTML と CSS だけで作ったサイトを、既存の公開リポジトリから配信する手順をまとめる。

この記事は初回公開時の記録。現在のブログでは、Markdown の記事を MkDocs で HTML に変換し、GitHub Actions で公開している。

## 1. ブログのファイルを GitHub に送る

リポジトリの一番上に `index.html` と `style.css` を置き、各記事は `posts` フォルダーに入れた。空の `.nojekyll` も置くと、GitHub Pages は Jekyll で変換せずにファイルを配信する。

クローンしたフォルダーで PowerShell を開き、公開するファイルを指定してコミットする。次はこのブログの初回の例。

```powershell
git add -- index.html style.css posts/git-path.html .nojekyll
git commit -m "Create engineering study blog"
git push -u origin main
```

コミット時に名前とメールアドレスの設定を求められたら、Git の作成者情報を設定してからやり直す。プッシュ時に GitHub のサインイン画面が出たら、そのリポジトリに書き込めるアカウントでサインインする。

## 2. 公開元に main ブランチを指定する

1. GitHub でリポジトリを開き、**Settings** → **Pages** に進む。
2. **Source** で **Deploy from a branch** を選ぶ。
3. ブランチに `main`、フォルダーに `/(root)` を選び、**Save** を押す。

`/(root)` はリポジトリの一番上を指す。ここにある `index.html` がトップページになる。

## 3. 公開ページを開いて確認する

公開処理が終わったら、Pages の **Visit site** でトップページを開く。記事一覧から記事を開き、一覧へ戻れることも確認する。このブログのように URL にリポジトリ名が入る場合は、`posts/git-path.html` のような相対リンクを使うと、リポジトリ名の下にある記事へ移動できる。

変更がすぐに表示されない場合は、リポジトリの **Actions** タブで公開処理が進行中か、エラーが出ているかを確認する。

## 記事を追加するとき

初回の構成では `posts` に HTML を置き、`index.html` にリンクを追加していた。現在は `docs/posts` に Markdown を置き、`docs/index.md` と `mkdocs.yml` に追加する。変更をコミットして `main` にプッシュすると、同じ URL に更新が反映される。

[GitHub Docs の公開元の設定手順](https://docs.github.com/ja/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

[記事一覧に戻る](../index.md)
