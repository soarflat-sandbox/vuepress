# アセットのハンドリング

## 相対 URL

マークダウンファイルは Vue コンポーネントにコンパイルされ、webpack によって処理されるため、相対 URL を使用してアセットを参照することもできる。

```md
![An image](./image.png)
```

画像は `url-loader` と `file-loader` で処理され、生成された静的ビルドは適切な場所にコピーされる。

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

## Public Files

状況によってはファビコンや PWA アイコンなど、マークダウンやテーマのコンポーネントで直接参照されていない静的アセットが必要な場合がある。

そのような場合、それらを`.vuepress/public`の中に置くことができる。それらは生成されたディレクトリのルートにコピーされる。

## Base URL

サイトがルート以外の URL にデプロイされている場合は、`.vuepress/config.js`で`base`オプションを設定する必要がある。

例えば、https://foo.github.io/bar/にサイトを展開する場合は、`base`を `"/bar/"`に設定する必要がある（常に開始と終了がスラッシュである必要があるため、`"/bar"`などは NG）。

Base URL で`.vuepress/public` の画像を参照する場合は、`/bar/image.png` のような URL を使用する必要がある。

しかし、後に`base`を変更した場合、URL を再度変更する必要があり非常に面倒。

この手間を省くために、VuePress は正しいパスを生成する `$withBase`ヘルパーを提供している。

```vue
<img :src="$withBase('/foo.png')" alt="foo">
```

テーマのコンポーネントだけでなく、マークダウンファイルにも上記の構文を利用できる。

また、`base`が設定されている場合、`.vuepress/config.js`オプションのすべてのアセット URL の前に自動的に追加される。
