### if条件分岐
```js
const age = 31;
if (age >= 31) {
  console.log("31より大きいです");
}
```

### true と false
>この場合等しい時にtrueなのでパスワードが一致しているから
>ログイン成功と出力される
```js
const password = "kun";

if (password === "kun") {
  console.log("ログインに成功しました");
}
```
>この場合異なる時にtrueなのでパスワードが一致してるから
>何も出力されない
```js
const password = "kun";

if (password !== "kun") {
  console.log("パスワードが間違っています");
}
```

### else条件分岐
```js
const age = 17;

if (age >= 20) {
  console.log("私は20歳以上です");
} else {
  console.log("私は20歳未満です");
}
```

### else if条件分岐

```js
const age = 17;

if (age >= 20) {
  console.log("私は20歳以上です");
} else if (age >= 10) {
  console.log("私は20歳未満ですが、10歳以上です");
} else {
  console.log("私は10歳未満です");
}
```
### &&かつ　|| または
```js
const age = 24;

//「定数ageの値が20以上かつ30未満」
if (age >= 20 && age < 30) {
  console.log("私は20代です");
}
```

### switct文
変数の値によって条件を分けたい時
caseで条件１ 条件２ 条件３って分けれる
その時に条件毎にbreak;を忘れないこと
また全ての条件に当てはまらない場合は
defult:を使う。elseみたいなもの。
```js
const rank = 2;

switch (rank) {
  case 1:
    console.log("金メダルです！");
    break;

  // rankの値が2のcase
  case 2:
    console.log("銀メダルです！");
    break;
  
  // rankの値が3のcase
    console.log("銅メダルです！");
  break;
  // 全ての条件に当てはまらない時
  default:
    console.log("メダルはありません");
    break;
}

```
