# liの6番目の画像にcssを当てたい時
- nth-of-type()
>原因は&img:nth-of-type(6)にしていたため
```
li
  &:nth-of-type(6)
    img
      transform: scaleY(0.4) translateY(1.5rem)
```
