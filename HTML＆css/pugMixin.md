# pugでのmixinのサンプル
```
mixin skill_item(name, icon, level)
  li.skill__item
    .skill__item__icon
      .skill__item__name= name
      img.skill__item__img(src="img/" + icon, alt="Html")
    .skill__item__desc
      .skill__item__lebel レベル #{level}
      .skill__item__meter
+skill_item(1,2,3)
+skill_item(1,2,3)
+skill_item(1,2,3)
+skill_item(1,2,3)
+skill_item(1,2,3)
```
imgタグは親にできない
その場合はdivタグを作ってその中にimg入れる
```
//divタグの中にimgとspanまたはdiv(今回はdisplay: blockを使う為divにした)
.skill__item__icon
  .skill__item__name= name
   img.skill__item__img(src="img/" + icon, alt="Html")
//divタグをこれで２個作り最終的にdivとdivをdisplay: flexで２個横に並べた
.skill__item__desc
   .skill__item__lebel レベル #{level}
   .skill__item__meter
```
