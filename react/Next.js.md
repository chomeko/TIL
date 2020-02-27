- Reactのようなページの生成方法をクライアントサイド・レンダリングと言う
>クライアント側で(webブラウザ)スクリプトを使ってWEBぺージを作って表示する方式

- 普通のWEBサイトはサーバーサイド・レンダリングと言う
>表示する内容をサーバー側で作成してそれを送っている

# Next.jsとは？
>reactをサーバーサイドでレンダリングし表示するプログラム
>静的WEBページとして作成し表示することもできる
>Reactは様々な表示を１枚のページで行うそれをSPAと呼ぶ
>next.jsでSPAのWEBページを複数のページによるWEBサイトとして作り変えることもできる

フォルダ作成
cd 移動
package.jsonファイル作成
```json
{
  "scripts": {
    "dev": "next",
    "build": "next build",
    "start": "next start",
    "export": "next export"
  }
}
```
## インストール
`npm install --save next react react-dom`

## コマンド
`npm run dev`
`npm run build`
`npm run export`

## HTMLファイルとして保存
next.config.jsファイル作成
```js
module.exports = {
  exportPathMap: function () {
    return {
      '/': {page: '/' }
    }
  }
}
```


