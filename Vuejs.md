# ディレクティブ

## v-if="クラス"
- 分岐とループ
## v-bind:class="クラス_class" v-bind:src="img_src"
- 属性の変更
## v-on:click="メソッド名"
- jsイベント
## v-for="変数名　in 配列名"
- 配列繰り返し

# アニメーション
## button v-on:click="メソッド名"
- イベント
- scriptはlodashとか使える

https://www.jsdelivr.com/package/npm/lodash


```
methods: {
  shuffle: function(){
    this.prefs = _.shuffle(this.prefs);
  }
}
```
## transition-grop name="名前" tag="ul"
- タグはul表示させてグループで囲む感じ

## li v-for="pref in prefs" v-bind:key="pref.name"
- liタグにkeyを持たせる

```
<div id="app">
  <button v-on:click="shuffle">シャッフル</button>
  <transition-group name="flip-list" tag="ul">
    <!-- 変数名　in 配列名-->
    <li v-for="pref in prefs" v-bind:key="pref.name">
      {{ pref.name }}
    </li>
  </transition-group>
```

## スタイルをつける
```
<!-- transition-groupで指定したnameの所 moveは動く時ってこと-->
  <style>
    .flip-list-move {
      transition: transform .5s;
    }
  </style>
```
