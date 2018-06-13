# コンフィグ

## コンフィグファイル

コンフィグがなければ、ユーザーはサイトを回遊できない。

サイトをカスタマイズするには、`docs`ディレクトリに、全ての VuePress 固有のファイルが配置される`.vuepress`ディレクトリを作成する。

VuePress サイトを設定するための必須ファイルは`.vuepress/config.js`であり、以下のように JS オブジェクトを export する。

```js
module.exports = {
  title: 'Hello VuePress',
  description: 'Just playing around',
};
```

上記の状態で、dev サーバを稼働させれば、そのページにタイトル（Hello VuePress）と検索ボックスのあるヘッダが表示される。

コンフィグの詳細は[Config Reference](https://vuepress.vuejs.org/config/)を参照。

## テーマの設定

VuePress には、技術ドキュメント用に設計されたデフォルトのテーマが付属している（VuePress のドキュメントがそのテーマ）。

このテーマでは、ナビゲーションバー、サイドバー、ホームページなどをカスタマイズするためのいくつかのオプションを設定できる。詳細は、[Default Theme Config](https://vuepress.vuejs.org/default-theme-config/) を参照。

カスタムテーマを作成する場合は、[Custom Themes](https://vuepress.vuejs.org/guide/custom-themes.html)を参照。
