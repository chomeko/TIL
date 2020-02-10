# 基本

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
