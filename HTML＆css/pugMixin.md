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
