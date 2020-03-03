# next.jsにFirebaseを取り込む
## インストール

` npm install --save firebase`

- store.jsにてfirebaseの初期化をする

`import firebase from "firebase";`

詳細
https://github.com/chomeko/next_app/blob/857ba787c919908f0809bdae866c9ffff3f26168/store.js

## firebaseにアクセスするページの作成
- pages/fire.js

https://github.com/chomeko/next_app/blob/master/pages/fire.js

- components/Sampledata.js

https://github.com/chomeko/next_app/blob/master/components/Sampledata.js

## 特定のデータの取り出し方
- 1つ目

`let ref = db.ref('hoge/1/');`

- 2つ目
```js
let ref = db.ref('sample/');

ref.orderByKey()
  .equalTo(取り出す項目名)
  .on('value', (snapshot)={....});
```
詳細https://github.com/chomeko/next_app/blob/803ce25714eba1e3b38032d95ae1d6e86c0b51b9/components/Firefind.js


## データの追加
- 参照を取り出す
変数　= database.ref(設定する項目のパス);
- 値を設定する
参照.set({項目:値,　項目:値,.....})

詳細https://github.com/chomeko/next_app/blob/777225bc7f9b20cf249b5cb4c1550bbc0c04855b/components/Fireadd.js
