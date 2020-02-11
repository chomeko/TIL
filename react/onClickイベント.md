# ２つの処理 イベント　state

## クリックされた時に処理を実行する イベント

```
<button onClick={() => {処理}}>ちょめこ</button>
```

## state　
>ユーザーの動きに合わせて変わる値のことを、Reactではstateと呼ぶ
>stateは、constructorの中で、オブジェクトとして定義
>定義したオブジェクトがstateの初期値
>constructor(props)」と「super(props);」は定型文

```js
constructor(props) {
  super(props);
  // stateを定義
  this.state = {name: 'ちょめこんぶ'};
```

## 表示
>this.stateはオブジェクト.nameがプロパティ
```js
<h1>やあ、{this.state.name}様！</h1>
```

## stateの変更

```js
this.setState({プロパティ名: 変更する値})
```
>指定されたプロパティに対応するstateの値が変更される
## 注意点
- stateの値に直接代入することで値を変更してはいけない
- 値を変更したい場合は、setStateを使い

ダメな例
```js
this.state = {name: 'ちょめめ'};
```

いい例
```js
this.setState({name: 'ちょめめ})；
```

```js
import React from 'react';

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {name: 'ちょめこ'};
  }
  
  render() {
    return (
    	<div>
    	  <h1>やあ、{this.state.name}様！</h1>
    	  {/* onClickの処理に、stateを変更する処理 */}
        <button onClick={() => {this.setState({name: 'ちょめめ'})}}>ちょめこ</button>
        {/* onClickの処理に、stateを変更する処理 */}
        <button onClick={() => {this.setState({name: 'ちょめこ'})}}>ちょめめ</button>
      </div>
    );
  }
}

export default App;
```

## メソッド化
- メソッドに引数を渡す
```js
メソッド名(name) {
 this.setState({name: name})
  }
```

## onClickイベントでメソッドを呼び出す

```js
<button onClick={() => {this.メソッド名('ちょめめ')}}ちょめこ</button>
```


