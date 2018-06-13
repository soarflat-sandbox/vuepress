# VuePress

Vue 製の静的サイトジェネレータ

## イントロダクション

VuePress は、以下の二つで構成されている

- Vue-powered theming システムを備えた最小限の静的サイトジェネレータ
- 技術ドキュメントを書くために最適化されたデフォルトテーマ

VuePress によって生成された各ページには、事前にレンダリングされた静的な HTML が用意され、読み込みパフォーマンスが高く SEO にも優れている。

ただし、ページがロードされると Vue は静的コンテンツを引き継ぎ、SPA に変換する。ユーザーがサイトをナビゲートすると、追加のページがオンデマンドで取得される。

### 特徴

- Vue、Vue Router、webpack を搭載した SPA
- Vue DevTools を利用してデバッグできる
- ビルド中に、サーバーでレンダリングされたバージョンのアプリケーションを作成し、仮想的に各ルートにアクセスして対応する HTML をレンダリングする
- Vue をマークダウンファイル内で利用できる

### 機能

- 技術文書に最適化された組み込みの[マークダウン拡張機能](https://vuepress.vuejs.org/guide/markdown.html)
- [Markdown ファイル内の Vue を利用できる](https://vuepress.vuejs.org/guide/using-vue.html)
- [Vue 製のカスタムテーマシステム](https://vuepress.vuejs.org/guide/custom-themes.html)
- PWA のサポート
- Google アナリティクスの統合
- デフォルトテーマ：

  - レスポンシブレイアウト
  - オプションのホームページ
  - シンプルですぐに利用できるヘッダーベースの検索
  - カスタマイズ可能なナビゲーションバーとサイドバー
  - 自動生成された GitHub リンクとページ編集リンク

## コンフィグ

### コンフィグファイル

コンフィグがなければ、ユーザーはサイトをナビゲートできない。

サイトをカスタマイズするには、`docs`ディレクトリに、全ての VuePress 固有のファイルが配置される`.vuepress`ディレクトリを作成する。

VuePress サイトを設定するための必須ファイルは`.vuepress/config.js`。

以下のように JS オブジェクトを export する。

```js
module.exports = {
  title: 'Hello VuePress',
  description: 'Just playing around',
};
```

上記の状態で、dev サーバを稼働させれば、そのページにタイトル（Hello VuePress）と検索ボックスのあるヘッダが表示される。

コンフィグの詳細は[Config Reference](https://vuepress.vuejs.org/config/)を参照。

### テーマの設定

VuePress には、技術ドキュメント用に設計されたデフォルトのテーマが付属している（VuePress のドキュメントがそのテーマ）。

これは、ナビゲーションバー、サイドバー、ホームページなどをカスタマイズするためのいくつかのオプションを公開している。詳細は、[Default Theme Config](https://vuepress.vuejs.org/default-theme-config/) を参照。

カスタムテーマを作成する場合は、[Custom Themes](https://vuepress.vuejs.org/guide/custom-themes.html)を参照。

## アセットのハンドリング

### 相対 URL

マークダウンファイルは Vue コンポーネントにコンパイルされ、webpack によって処理されるため、相対 URL を使用してアセットを参照することもできる。

```md
![An image](./image.png)
```

画像は `url-loader` と `file-loader` で処理され、生成された静的ビルドの適切な場所にコピーされます。

また、`~`プレフィックスを利用して、これが webpack モジュールリクエストであることを明示的に示すことができる。明示的に示すことにより、webpack エイリアス、または npm 依存関係からファイルを参照できる。

```md
![Image from alias](~@alias/image.png)
![Image from dependency](~some-dependency/image.png)
```

webpack エイリアスは、以下のように`.vuepress/config.js` の `configureWebpack` に設定できる。

```js
module.exports = {
  configurewebpack: {
    resolve: {
      alias: {
        '@alias': 'path/to/some/dir',
      },
    },
  },
};
```

### Public Files

状況によってはファビコンや PWA アイコンなど、マークダウンやテーマのコンポーネントで直接参照されていない静的アセットが必要な場合がある。

そのような場合、それらを`.vuepress/public`の中に置くことができる。それらは生成されたディレクトリのルートにコピーされる。

### Base URL

サイトがルート以外の URL にデプロイされている場合は、.vuepress / config.js で基本オプションを設定する必要があります。 たとえば、https://foo.github.io/bar/にサイトを展開する場合は、baseを "/ bar /"に設定する必要があります（常に開始と終了がスラッシュである必要があります）。

ベース URL で.vuepress / public の画像を参照する場合は、/bar/image.png のような URL を使用する必要があります。 しかし、後でベースを変更することに決心した場合、これは脆弱です。 これを助けるために、VuePress は正しいパスを生成するビルトインヘルパー$ withBase（Vue のプロトタイプに注入）を提供します：

```vue
<img :src="$withBase('/foo.png')" alt="foo">
```

テーマのコンポーネントだけでなく、マークダウンファイルにも上記の構文を利用できる。

また、`base`が設定されている場合、`.vuepress/config.js`オプションのすべてのアセット URL の前に自動的に追加される。
