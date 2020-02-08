#基本
```pug
.swiper__container
  .swiper-wrapper
    a.swiper-slide(href="")
      img.swiper-slide--img(src="" alt="Swiper01")
      h3.swiper-slide--title テキスト
      p.swiper-slide--lead あああああああああああああああああああああああああああああああああああああ
    a.swiper-slide(href="")
      img.swiper-slide--img(src="" alt="Swiper02")
      h3.swiper-slide--title 
      p.swiper-slide--lead 
    a.swiper-slide(href="")
      img.swiper-slide--img(src="" alt="Swiper03")
      h3.swiper-slide--title 
      p.swiper-slide--lead 
    a.swiper-slide(href="")
      img.swiper-slide--img(src="" alt="Swiper04")
      h3.swiper-slide--title 
      p.swiper-slide--lead 
    a.swiper-slide(href="")
      img.swiper-slide--img(src="" alt="Swiper05")
      h3.swiper-slide--title 
      p.swiper-slide--lead 
    a.swiper-slide(href="")
      img.swiper-slide--img(src="" alt="Swiper06")
      h3.swiper-slide--title 
      p.swiper-slide--lead 
  .swiper-pagination
.results--button
  a(href="")
    .results--button--text ボタンです
```

```sass
.swiper__container
    width: 100%
    height: 100%
    overflow-x: hidden //はみ出しを非表示
    margin-left: 1.6rem　//モバイル側はleftに余白作った
    @include mq('+sp')
      margin-left: 0
  .swiper-wrapper
    width: 100%
  .swiper-slide
    height: auto
    color: $black
    @include mq('+sp')
      max-width: 42.2rem !important //最大カードの大きさ強制
    &--img
      max-width: 100%
      height: auto
    &--title
      padding: 1.2rem
      background: $whit
      font-size: 1.5rem
      line-height: 0.8
      letter-spacing: .01rem
      width: 100%
      @include mq('+sp')
        font-size: 2.0rem
        padding: 2rem
        line-height: 1.2
    &--lead
      background: $whit
      font-size: 1.2rem
      line-height: 1.6
      letter-spacing: .01rem
      padding: 0 1.2rem 1.2rem 1.2rem
      width: 100%
      @include mq('+sp')
        font-size: 1.6rem
        line-height: 1.5
        padding: 0 2.0rem 2.0rem 2.0rem
  .swiper-pagination
    position: static //位置調整
    margin-top: 4.8rem
    @include mq('+sp')
      text-align: left //初期値はセンターになっている
  /* ページネーション編集 */
  .swiper-container-horizontal > .swiper-pagination-bullets .swiper-pagination-bullet
    margin: 0 10px
    margin-bottom: 1px //ちょっと途切れるから余白開けた
    &:first-child
      margin-left: 1px　//ちょっと途切れるから余白開けた
  /* ページネーションの丸 */
  .swiper-pagination-bullet
    width: 1.2rem
    height: 1.2rem
    margin-left: 2rem
    background: $whit
    padding: .1rem
    /* ページネーションの二重丸*/
    &-active
      border: 3px solid $black
      width: 1.6rem
      height: 1.6rem
      box-shadow: 0 0 0 1px $whit
  &--button
    background: inherit
    color: $whit
    width: 100%
    height: 100%
    display: flex
    justify-content: center
    @include mq('+sp')
      justify-content: flex-start
    &:hover
      opacity: 1
    &--text
      color: $whit
      font-family: $font-en
      display: flex
      align-items: center
      justify-content: center
      font-weight: bold
      letter-spacing: 3.6px
      line-height: 1.2
      font-size: 1.8rem
      width: 34.3rem
      height: 5.4rem
      margin-top: 4rem
      margin-bottom: 4rem
      border: 1px solid #FFFFFF
      @include mq('+sp')
        font-size: 2rem
        width: 30.1rem
        height: 6.4rem
        margin-bottom: 4.6rem
        margin-top: 4.6rem
      &:hover
        opacity: 1
        background: $whit
        color: $black
```

## swiperのjs設定

```js
$( function() {
  var swiper = new Swiper('.swiper__container', {
      speed: 400,
      pagination: {
        el: '.swiper-pagination',
        clickable: true,
      },
      autoplay: true,
      //centeredSlides: true,　//activeのカードをセンターにする今回はoff
      slideToClickedSlide: true, //クリックで止め
      slidesPerView: 2.6,//何枚画面上に表示させるか、今回は２.６枚（くそハマった）
      loop: true,
      loopedSlides: 6,//loopとセットで画像数
      spaceBetween: 40,　//カードの間の余白
      breakpoints: {　//各ブレークポイント　（超鬼ハマった）
        1050: {
          slidesPerView: 2.2,
          spaceBetween: 40,
        },
        891: {
          slidesPerView: 2,
          spaceBetween: 40,
        },
        767: {
          slidesPerView: 1.27,
          spaceBetween: 24,
        },
        374: {
          slidesPerView: 1,
          spaceBetween: 24,
        },
      },
  });
});
```
