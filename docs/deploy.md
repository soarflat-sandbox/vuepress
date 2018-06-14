# デプロイ

記事の内容は以下を前提に基づいているため注意。

- プロジェクトの`docs`ディレクトリにドキュメントを置いている
- ビルド出力ディレクトリは`.vuepress/dist`である
- VuePress はローカルにインストール（`npm install vuepress`など）され、以下の npm scripts がある

```json
{
  "scripts": {
    "docs:build": "vuepress build docs"
  }
}
```

## GitHub Pages

1.  `/.vuepress/config.js`に`base`を設定する。

- `https://<USERNAME>.github.io/`にデプロイする場合は、デフォルトである`"/"`を指定する
- `https://<USERNAME>.github.io/<REPO>/`にデプロイする場合（つまり、リポジトリが`https://github.com/<USERNAME>/<REPO>`の場合）、`"/<REPO>/"`を指定する

例えば、`https://hira777.github.io/qiita-articles-by-soarflat`にデプロイする場合、`"/qiita-articles-by-soarflat/"`を指定する。

2.  プロジェクト内で、以下の内容の`deploy.sh` を作成して実行すればデプロイできる。

```bash
#!/usr/bin/env sh

# abort on errors
set -e

# build
npm run docs:build

# navigate into the build output directory
cd docs/.vuepress/dist

# if you are deploying to a custom domain
# echo 'www.example.com' > CNAME

git init
git add -A
git commit -m 'deploy'

# if you are deploying to https://<USERNAME>.github.io
# git push -f git@github.com:<USERNAME>/<USERNAME>.github.io.git master

# if you are deploying to https://<USERNAME>.github.io/<REPO>
# git push -f git@github.com:<USERNAME>/<REPO>.git master:gh-pages

cd -
```
