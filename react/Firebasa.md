# firebase
https://firebase.google.com/?hl=ja

## アプリ作成
npx create-react-app my-app

##  firebaseサイト
- databaseの作成をする

- webアプリを追加する

## アプリ側
- プロジェクトにAPIをインストール
` npm install --save firebase`

 

## 並べ替えメソッド
- orderByKey
>キーによって並べ替える
- orderByValue
>値によって並べ替える
- orderByChild
>引数に指定したノードの順によって並べ替える

## フィルターメソッド
- equalTo
>引数の値と等しいものを取り出す
- limitToFirst
>最初から引数で指定した数だけ取り出す
- limitToLast
>最後から引数で指定した数だけ取り出す
- startAt
>引数で指定した値のデータを取り出す
- endAt
>引数で指定した値のデータまでを取り出す

## onイベント処理
`.on(イベント名, (snapshot) =>{~~~~終了後の処理~~~~});`

>onメソッドはlimitFirstでアクセスした結果の処理を行うためのもの
>データーベースのアクセスは非同期で行われる
>非同期はメインの処理の流れから切り離して勝手に行う処理のこと
>処理が終わったら実行することをセットする感じ

- 第一引数には処理を割り当てるイベント名(valueはDBにアクセスし値を受け取るイベント)
- 値の取得が完了したら第２引数の関数を実行
>snapshot関数はイベント時に受け取ったデータなどの情報をまとめたオブジェクト
### 終了後の処理
- 取り出したsnapshotオブジェクト(取得したデータ)のvalue属性を取得してdataステートに設定
```js
self.setState({
 data:snapshot.val()
  });
```
