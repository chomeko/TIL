# 基本

## 形
```js
{/*Reactをインポート*/}
import React from 'react';

{/*React.Componentを継承する定義*/}
class App extends React.Component {
  {/*JSXを戻り値とするrenderメソッドを定義*/}
  render() {
    {/*return内にHTMLを書く*/}
    return (
      <h1>Hello React</h1>
    );
  }
}
{*/Appクラスをエクスポートしてください*/}
export default App;
```

## render内で定義してretrun内に{}で使える

```js
import React from 'react';

class App extends React.Component {
  render() {
    // 定数nameを定義
    const name = "ちょめこ";
    
    // 定数imgUrlを定義
    const imgUrl = "https://.png";
    
    return (
      <div>
        {/* 定数nameを用いて表示 */}
        <h1>{name}</h1>
        
        {/* 定数imgUrlを用いて画像が表示 */}
        <img src={imgUrl} />
        
      </div>
    );
  }
}

export default App;
```
