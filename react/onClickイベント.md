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
ダメな例
```js
this.state = {name: 'ちょめめ'};
```
いい例
```js
this.setState({name: 'ちょめめ})；
