# インストール
## redux
- `npm install --save redux`
## react redux
- `npm install --save react-redux`
## redux devtools
- `npm install --save-dev redux-devtools`

## 仕組み
- ストア
>データを保管し管理するもの。保管される値はステートと呼ぶ
- プロバイダー
>ストアを他のコンポーネントに受け渡す仕組み
- レデューサー
>ストアに保管されるステートを変更する仕組み
### ストアは内部に値を保管するステート、値の操作処理であるレデューサを持っている。
### プロバイダーのタグの中にコンポーネントを記述すると、それら内部のコンポーネントでストアに保管されている値や処理が使える
