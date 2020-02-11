# コンポーネントとは

- コンポーネントは「部品」や「パーツ」という意味
>見た目を機能ごとにコンポーネント化して、コンポーネントを組み合わせることでWebサイトの見た目を作る

Test.jsファイル
- まずエクスポートする
```js
export default Test;
```

App.jsファイルにて
- インポートする
```js
import Test from './Test';
```
- return内でTestコンポーネントを呼び出す
```js
 <Test/>
```

## 何度でも呼び出すことができる

### props
- 変えたい部分の表示を変更できる

>App.jsからデータをTestコンポーネントに渡して表示を変えることができる。App.jsから渡すこのデータをprops（プロップス）という。

- propsは、「props名=値」で、コンポーネントを呼び出す箇所で渡す

(App.js)
```js
<Test
  //props名　= "値"
  name = "ちょめこ"
/>
```

- 渡されたpropsは、this.propsで取得でき,{ props名: 値}というオブジェクトになる
(Test.js)
```js
<div className='Test-name'>
  {this.props.name}
</div>
```

## コンポーネントを何度も呼び出す

### mapメソッドを使う
(App.js)
```js
//render内で定義 [ { , , , ,} ]
render() {
  const TestList = [
      {
        name: 'ちょめこ',
        image: 'https://.svg'
      },
      {
        name: 'ちょめめ',
        image: 'https://svg'
      },
      {
        name: 'うんこ',
        image: 'https://.svg'
      }
];
```

- そしてreturn()　内でmapメソッドで表示

```js
//retrun内
return (
  <div>
    <h1>人物一覧</h1>
    <div className='test'>
      {/* mapメソッドを用いて、Testコンポーネントを表示 */}
      {testList.map((testItem) => {
        return (
          // Testコンポーネントを呼び出し、その中でpropsを渡す
          <Test
            name = testItem.name
            image = testItem.image
          />
        )
      })}
    </div>
  </div>
);
```

- 渡されたpropsは、this.propsで取得でき,{ props名: 値}というオブジェクトになる
(Test.js)
```js
<div className='Test-name'>
  {this.props.name}
</div>
<div className='Test-image'>
  {this.props.image}
</div>
```
