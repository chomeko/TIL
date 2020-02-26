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
