# インストール＆起動
- npx create-react-app react-tutorial

- npm start

## フォルダとファイルの追加
- src/components
  - App.js
  - Board.js
  - Game.js
  - Square.js
- src/style
  - App.css
- index.js

App.js
```js
import React from 'react';
import '../style/App.css';
import Game from './Game';

function App() {
  return < Game />;
}

export default App;
```

index.js
```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './components/App';

ReactDOM.render(<App />, document.getElementById('root'));
```

Board.js
```js
import React from 'react';
import Square from './Square';
~~~~~以下略~~~~~~
export default Board;
```
Game.js
```js
import React from 'react';
import Board from './Board';
~~~~~以下略~~~~~~
export default Game;
```
Square.js
```js
import React from 'react';
~~~~~以下略~~~~~~
export default Square;

```
チュートリアル終了後のgithub
https://github.com/chomeko/react-tutorial
