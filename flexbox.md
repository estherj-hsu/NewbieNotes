# Flexbox

**實作**
* [Pinterest Grid with Flexbox](http://codepen.io/estherj-hsu/pen/bVXOMY)

**Reference**

 - [CSS-Tricks: Flexbox](https://css-tricks.com/using-flexbox/)
 - [W3 - Flexbox](http://www.w3.org/html/ig/zh/wiki/Css3-flexbox)
 - [CSS參考手冊 - Flexbox](http://css.doyoe.com/properties/flex/index.htm)
 - [CSS-Tricks: A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
 - [Flexbox Fundamentals (video)](https://egghead.io/lessons/misc-flexbox-fundamentals)
 - [Flexbox版面配置](http://zh-tw.learnlayout.com/flexbox.html)
 - [Flexbox Froggy (learning tool)](http://flexboxfroggy.com/)
 - [CSS Reference - Flexbox](http://tympanus.net/codrops/css_reference/flexbox)
 - [Flexbox Grid Finesse](https://medium.com/@Heydon/flexbox-grid-finesse-4d22b80bfee1#.txc4ylkrf)
 - [Flexbox’s Best-Kept Secret](https://medium.com/@samserif/flexbox-s-best-kept-secret-bd3d892826b6#.3bd4xfkt8)
 - [Vertical Centering (flexbox)](https://philipwalton.github.io/solved-by-flexbox/demos/vertical-centering/)
 - [What is Flexbox](https://medium.com/@spaceninja/what-is-flexbox-6aed968555ef#.4wvachxkk)
 - [Floats, Inline Block or Display Table? Or Flexbox?](http://blog.karenmenezes.com/2014/apr/13/floats-inline-block-or-display-table-or-flexbox/)
 - [Responsive Multi-Column Lists with Flexbox](http://fourword.fourkitchens.com/article/responsive-multi-column-lists-flexbox)
 - [Flexbox Grid](http://callmenick.com/post/flexbox-examples)
 - [Flexbox.help](http://flexbox.help/)

## Parent (wrap/container)

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/flex-container.svg)

    display: flex

### flex-direction

容器內部child排列方向


    flex-direction: row(default) 橫向 | ltr 左到右 | rtl 右到左
    flex-direction: row-reverse 逆橫向
    flex-direction: column 縱向
    flex-direction: column-reverse 逆縱向


### flex-wrap
容器內部child換行

    flex-wrap: nowrap 單行
    flex-wrap: wrap 多行
    flex-wrap: wrap-reverse 逆向多行

> 當採**橫向**(row/row-reverse)排列時，需藉由控制容器**寬度**來呈現多行排列模式
> 當採**縱向**(column/column-reverse)排列時，需藉由控制容器**高度**來呈現多行排列模式

### flex-flow
合併`flex-direction`與`flex-wrap`，共有4(方向)x3(換行)總組合方式

```
    flex-flow: row wrap
    flex-flow: column wrap
```

### justify-content
容器內部 **單行** 主軸(X軸)對齊

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2013/04/justify-content.svg)

    justify-content: flex-start 對齊主軸起始點
    justify-content: flex-end 對齊主軸終點
    justify-content: center 對齊主軸中間點
    justify-content: space-between 對齊主軸左右
    justify-content: space-around 對齊主軸左右且每個item左右保有相同空間

### align-items
容器內部**單行**側軸(Y軸)對齊

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/align-items.svg)

    align-items: flex-start 對齊側軸起始點
    align-items: flex-end 對齊側軸終點
    align-items: center 對齊側軸中間點
    align-items: stretch 延展至側軸雙邊、對齊側軸雙邊
    align-items: baseline 對齊文字基準線

### align-content
容器內部**多行**對齊

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2013/04/align-content.svg)

    align-content: flex-start 對齊主軸起始點
    align-content: flex-end 對齊主軸終點
    align-content: center 對齊主軸中間點
    align-content: stretch 延展至側軸雙邊、對齊側軸雙邊
    align-content: space-between 對齊主軸左右
    align-content: space-around 對齊主軸左右且每個item左右保有相同空間

## Child (item)

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/flex-items.svg)

### order
控制子項目順序，數字越小越接近起始點

    order: # (1, 2, 3, ...)

### flex-basis
取代 item之 `width`，預約空間

    flex-basis: auto(default) 不指定 | <width> (100px, 50%, ...) 指定 | content 以內容計算

> [注意]  flex-shrink屬性**優先**於width，但若兩者之一值為auto，則非auto之屬性優先

### flex-grow

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/flex-grow.svg)

主容器剩餘空間索取之擴大比例，default為0(代表皆不索取)，代表若主容器寬/高度大於各item寬/高度總和時，如何分配於各item，數字代表索取之份量。

假設容器寬度為500px，且flex-grow為預設值0時，每個item寬度為500/3px；
但若設定三個item寬度為100px，再針對其中一個itemA設定flex-grow為1，
則itemA之寬度為100px(預設寬度) **+200px** (總剩餘寬度)。

承上，若再設定itemB之flex-grow為3，
則itemB寬度為100px **+ 150px**(總剩餘寬度200px中的3/4)，
而A之寬度為100px **+ 50px**(總剩餘寬度200px中的1/4)。

```
    flex-grow: 0(default) | #(1, 2, 3, ...)
```

### flex-shrink
主容器剩餘空間吸收之縮小比例，default為1，代表若主容器寬/高度**不足時**，各item吸收比例皆相同，數字代表吸收之份量。

假設容器寬度為700px，預設4個item的寬度皆為200px，
此時主容器寬度不足100px(200px × 4 = 800px)，
預設情況(flex-shrink: 1)下，不足的100px平均由4個item吸收，
因此每個item的寬度為200px **- 25px**(不足寬度100px的1/4)。

承上，若再指定itemA之flex-shrink為2，則itemA之寬度為200px(預設寬度) **- 40px**(不足寬度100px的2/5)。

```
    flex-shrink: 1(default) | #(1, 2, 3, ...)
```

### flex
整合`flex-grow`、`flex-shrink`、`flex-basis`之屬性，依序以空格區隔

```
    flex: 0 1 auto(default) | none 不指定
```

### align-self
針對item之側軸對齊設定， **可取代主容器之align-item屬性**

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/align-items.svg)


```
    align-self: auto 跟從align-item設定
    align-self: flex-start 對齊側軸起始邊
    align-self: flex-end 對齊側軸終邊
    align-self: center 對齊側軸中間
    align-self: baseline 以文字為基準
    align-self: stretch 延展至側軸雙邊、對齊側軸雙邊
```


----------

## Compatibility

### Parant

```
    display: -webkit-box
    display: -moz-box
    display: -ms-flexbox
    display: -webkit-flex
    display: flex
```

### Child

```
    -webkit-box-flex: 0 1 auto
  -moz-box-flex: 0 1 auto
  flex: 0 1 auto

  -webkit-box-ordinal-group: 1
  -moz-box-ordinal-group: 1
  -ms-flex-order: 1
  order: 1
```

### Bugs in IE10, IE11

**Reference**
 - [Flexbugs](https://github.com/philipwalton/flexbugs)
 - [Normalizing Cross-browser Flexbox Bugs](http://philipwalton.com/articles/normalizing-cross-browser-flexbox-bugs/)

**Bugs**

 - 子項目設定min-height情況下，容器的高度設定將會被忽略 [[solution](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items)](fixed in Edge)
 - 子項目不允許無單位的flex-basis [[solution](https://github.com/philipwalton/flexbugs#4-flex-shorthand-declarations-with-unitless-flex-basis-values-are-ignored)](fixed in Edge)
 - 子項目圖片自動調整比例問題[[solution](https://github.com/philipwalton/flexbugs#5-column-flex-items-dont-always-preserve-intrinsic-aspect-ratios)](fixed in Edge)
 - flex-basis: auto超出容器大小（包含::before/after）[[solution](https://github.com/philipwalton/flexbugs#7-flex-basis-doesnt-account-for-box-sizingborder-box)](fixed in Edge)
 - inline元件無法成為子項目[[solution](https://github.com/philipwalton/flexbugs#12-inline-elements-are-not-treated-as-flex-items)](fixed in Edge)

**Extra**

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2010/09/widthbox.png)

    box-sizing: content-box(default) | border-box | initial | inherit

> **content-box:** element size =  width/height + padding + border
>
> **border-box:** element size =  width/height
