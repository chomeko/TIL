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

## ストアの作成
`変数　= createStore(レデューサー);`
## レデューサーの作成　関数で作成
```js
function 関数名(state = ステート, アクション) {
---処理---
}
```

# 流れ

- App.js
各import
```js
import React, { Component } from 'react';
import { connect } from 'react-redux';
import './App.css';
import Memo from './memo/Memo';  コンポーネント
import AddForm from './memo/AddForm';　コンポーネント
import FindForm from './memo/FindForm';　コンポーネント
import DelForm from './memo/DelForm';　コンポーネント

//Appコンポーネント
class App extends Component {
  td = {
    width: "250px"
  }

  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
        <h1>Memo</h1>
        <AddForm />
        <hr />
        <table><tbody><tr>
          <td style={this.td}><FindForm /></td>
          <td style={this.td}><DelForm /></td>
        </tr></tbody></table>
        <Memo />
      </div>
    );
  }
}

export default App;
```
- index.js
各import
```js
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import './index.css';
import App from './App';
import MemoStore from './memo/Store' //作るStore名

//表示をレンダリング
//プロバイダーに作ったstoreを指定
ReactDOM.render(
  <Provider store={MemoStore}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```
- Store.js作成

