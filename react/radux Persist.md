# Redux Persistはストレージで管理(ローカルストレージ)

- インストール

`npm install --save redux-persist`

- パーシストレデューサーを用意

`const 変数 = persistReducer(設定,レデューサー)`

- パーシスターを用意

`ストア = createStore(パーシストレデューサー)`
を作って

`変数 = persistStore(ストア)`を作る

## パーシストゲートの利用
```js
<Provider store={ストア}>
  <PersistGate loading={値} persistor={パーシスター}>
   〜〜〜表示するコンポーネント〜〜〜〜
  </PersistGate>
</Provider>
```

## インポート
- import {persistStore, persistReducer} from 'redux-persist'
>パーシストレデューサーとパーシスター
- import storage from 'redux-persist/lib/storage'
>ストレージ
- import {PersistGate} from 'redux-persist/integration/react'
>パーシストゲート


##　永続化の注意
- オブジェクトの読み込みには問題がある
>ストレージに保存するときにストアに保管されている値がオブジェクトだと正しく保管できない、保管する際にテキストに変換されたりすると、元のオブジェクトに戻せずにエラーになる？？
>保存するときにはテキストの値として保存して、取り出したときに値をそのまま表示することで回避

## 保管されるデータを整理できる
- blacklist
>ストレージに保存したくない値を配列の中にテキスト値で指定['message', 'mede', 'fdata'];
- whitelist
その逆

## 永続化の停止や再開
- purge
>保存されているデータ削除
- flush
>保留になってる変更を反映し最新の状態にする
- pause
>永続化の処理を一時的に停止する
- persist
>停止していた永続処理を再開する
