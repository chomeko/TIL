# netlifyにデプロイ

https://chomeko-test.netlify.com/

# インストール
- npm install --global gatsby-cli
## バージョン確認
- gatsby --version
```
gatsby --version
Gatsby CLI version: 2.8.29

```
## シンプルな構成のgatsby-starter-hello-worldを使い、開発環境を構築

- ディレクトリを作成
```
 $ mkdir gatsby-test
```
- 移動
```
 $ cd gatsby-test
```
- gatsby new {プロジェクト名} {Githubのパス}でgatsby-starter-hello-worldをダウンロード

```
gatsby new gatsby-test https://github.com/gatsbyjs/gatsby-starter-hello-world
```
- yarnかnpmを選べる。今回はnpm

- インストール完了
- ファイル構成



- ターミナルでnpm run develop
(http://localhost:8000/)
で表示完了

## headerの作成

- /src/commonents/header.jsの作成
```js
import React from 'react'
//link作成
import { Link } from 'gatsby'

export default () => (
  <header>
    <h1>headerだよ</h1>
    <ul>
      <li><Link to="/">Home </Link></li>
      <li><Link to="/about/">About</Link></li>
    </ul>
  </header>
)
```

## index.js
```js
import React from "react"
import Header from '../commonents/header'
import Footer from '../commonents/footer'

export default () => (
  <div>
    <Header />
    <h2>ここからindexになるよ</h2>
    <p>トップページ</p>
    <Footer />
  </div>
)
```

## aboutページの追加

- /src/pages/about.jsの作成
```js
import React from "react"
import Header from '../commonents/header'
import Footer from '../commonents/footer'

export default () => (
  <div>
    <Header />
    <h2>ここはaboutページだよ</h2>
    <p>トップページ</p>
    <Footer />
  </div>
)
```

## スタイルをつける
- sassを使えるようにする
 ```
 npm install --save node-sass gatsby-plugin-sass
 ```
 
全体のスタイルを設定
リセットスタイル
- /src/styles/reset.scssの作成

- /gatsby-browser.jsの作成

```js
import "./src/styles/reset.scss"
```

### スコープされたスタイルを設定する

>CSS Modulesを使用し、CSS（SCSS）をスコープさせることができる


- gatsbytest/src/styles/main.module.sass作成

```js
import Styles from "../styles/main.module.sass"
```
```js
<main className={Styles.test}>
  <h2>トップページだよ</h2>
</main>
```



