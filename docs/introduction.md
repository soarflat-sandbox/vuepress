# イントロダクション

VuePress は、以下の二つで構成されている

- Vue-powered theming システムを備えた最小限の静的サイトジェネレータ
- 技術ドキュメントを書くために最適化されたデフォルトテーマ

VuePress によって生成された各ページには、事前にレンダリングされた静的な HTML が用意され、読み込みパフォーマンスが高く SEO にも優れている。

ただし、ページがロードされると Vue は静的コンテンツを引き継ぎ、SPA に変換する。ユーザーがサイトをナビゲートすると、追加のページがオンデマンドで取得される。

## 特徴

- Vue、Vue Router、webpack を搭載した SPA
- Vue DevTools を利用してデバッグできる
- ビルド中に、サーバーでレンダリングされたバージョンのアプリケーションを作成し、仮想的に各ルートにアクセスして対応する HTML をレンダリングする
- Vue をマークダウンファイル内で利用できる

## 機能

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
