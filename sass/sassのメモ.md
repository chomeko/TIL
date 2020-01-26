# sassのメモ

## 変数
```sass
$color-black: #00000
```
呼び出しは
```sass
color: $color-black
```

## mixin
```sass
@mixin hoge 
  display: inline-block
  border-radius: 50%
  margin-left: 10px
  text-align: center
  background-color: #000000
```
呼び出しは
```sass
.hoge
  @include hoge
```

## mixinと引数
引数に$colorを指定
```sass
@mixin circle($color)
  display: inline-block
  border-radius: 50%
  margin-left: 10px
  text-align: center
  background-color: $color
```
使い方は
引数にカラーを指定してあげる
```sass
@include circle(#20efae)
```

## 関数
- darken(色,数値%)
- lighten(色,数値%)
- rgba(色,数値%)

## import
ファイルの読み込み
```sass
@import 'hogehoge.sass'
```

