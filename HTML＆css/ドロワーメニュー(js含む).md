# ドロワーメニュー作成
```pug
header.header
  .header__inner
    h1.header__logo
      a(href="#")
        img.header__logo__img(src="../img/logo@2x.png", alt="ロゴ画像" href="#")
    .menu-trigger//ここはトグル
      span
      span
      span
    .header__wrapper//ここからナビゲーショングループ
      nav.header__nav//ナビゲーション
        ul.header__nav__list
          li.header__nav__list--item
            a(href="") News
          li.header__nav__list--item
            a(href="") Service
          li.header__nav__list--item
            a(href="") Results
          li.header__nav__list--item
            a(href="") FAQs
          li.header__nav__list--item
            a(href="") Price
          li.header__nav__list--item
            a(href="") Comments
          li.header__nav__list--item
            a(href="") Contact
```

## js

```js
//.menu-triggerのトグルをクリックしたら
$('.menu-trigger').on('click',function(){
  //.hasClassでactiveクラスを確認して、クラスがあれば
  if($(this).hasClass('active')){
    //.removeClassでactiveクラスを外す
    $(this).removeClass('active');
    //navの.removeClassでopenクラスを外す
    $('nav').removeClass('open');
    //.hasClassでactiveクラスを確認して、クラスがなかったら
  } else {
    //.addClassでactiveクラスをつける
    $(this).addClass('active');
    //.addClassでopenクラスをつける
    $('nav').addClass('open');
  }
});
```
