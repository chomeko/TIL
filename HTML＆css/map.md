# googlemap埋め込み
## レスポンシブ化
```pug
.access__map
  iframe(src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d13046.113217757547!2d136.87604189925855!3d35.16838288661326!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x600376de737d9a29%3A0x95fb085c8053a6d2!2z44OK44OK44Gh44KD44KT5Lq65b2i!5e0!3m2!1sja!2sjp!4v1580645992792!5m2!1sja!2sjp" width="100%" height="auto" frameborder="0" style="border:0;" allowfullscreen="")
```

```sass
.access__map
  height: 0
  overflow: hidden
  padding-bottom: 56.25% //アスペクト比16:9になる　　７５％だと4:3
  position: relative //親指定
  margin-bottom: 4rem
  @include mq('+sp') 
    //pcでは高さ固定してるからレスポンシブにならない
    max-width: 72rem　//ここで横幅サイズ指定
    width: 100%      //ここはセットと覚えとく
    padding-bottom: 51.5rem　//ここでpaddingで高さを指定してる
    margin-bottom: 0
  @include mq('tab')
    //tabでは％指定してアスペクト比１６：９のレスポンシブ化になる
    padding-bottom: 56.25%
  iframe //子要素
    position: absolute
    top: 0
    left: 0
    width: 100%
    height: 100%
```
