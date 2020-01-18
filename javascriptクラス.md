# クラス
```js
class User {
}
```
# インスタンスの生成
- クラスからオブジェクトを生成するにはnew クラス名()
- クラスから生成したオブジェクトはインスタンスと呼ぶ
```js
class User {
  
}
// ここでクラスのインスタンスを生成
const user = new User();
```
# コンストラクタ
- コンストラクタはインスタンスを生成するときに実行したい処理や設定を追加
- 処理はインスタンスが生成された直後に実行
- クラスの中括弧 { } 内にconstructor() { }
```js
class User {
  constructor() {
  
  }
}
// ここでクラスのインスタンスを生成
const user = new User();
```

# プロパティと値
- 生成されたインスタンスにプロパティと値を追加
- コンストラクタの中で`this.プロパティ = 値`

# メソッド
- メソッドはクラスの中で定義
- メソッドは関数と似たようなもの
- 中括弧「{ }」の中にそのメソッドで行いたい処理を記述
- クラスから生成したインスタンスに対して呼び出す
- メソッド名() { }
```js
class User {
  
}
// ここでクラスのインスタンスを生成
const user = new User();
```

class Animal {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  // greetメソッドを追加してください
  greet() {
    console.log("こんにちは");
  }
}
