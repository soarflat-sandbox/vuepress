# VuePress
Vue製の静的サイトジェネレータ

## 特徴
- Vue、Vue Router、webpackを搭載したSPA
- Vue DevToolsを利用してデバッグできる
- ビルド中に、サーバーでレンダリングされたバージョンのアプリケーションを作成し、仮想的に各ルートにアクセスして対応するHTMLをレンダリングする
- Vueをマークダウンファイル内で利用できる

## 機能
- 技術文書に最適化された組み込みの[マークダウン拡張機能](https://vuepress.vuejs.org/guide/markdown.html)
- [Markdownファイル内のVueを利用できる](https://vuepress.vuejs.org/guide/using-vue.html)
- [Vue製のカスタムテーマシステム](https://vuepress.vuejs.org/guide/custom-themes.html)
- PWAのサポート
- Googleアナリティクスの統合
- デフォルトテーマ：
  - レスポンシブレイアウト
  - オプションのホームページ
  - シンプルですぐに利用できるヘッダーベースの検索
  - カスタマイズ可能なナビゲーションバーとサイドバー
  - 自動生成されたGitHubリンクとページ編集リンク
  
 ## コンフィグ
コンフィグがなければ、ページは非常に小さくユーザーはサイトをナビゲートする手段がない。

サイトをカスタマイズするには、`docs`ディレクトリに、全てのVuePress固有のファイルが配置される`.vuepress`ディレクトリを作成する。

VuePressサイトを設定するための必須ファイルは`.vuepress/config.js`。これはJavaScriptオブジェクトをエクスポートする必要がある。

```js
module.exports = {
  title: 'Hello VuePress',
  description: 'Just playing around'
}
```

上記の状態で、devサーバを稼働させれば、そのページにタイトルと検索ボックスのあるヘッダが表示される。