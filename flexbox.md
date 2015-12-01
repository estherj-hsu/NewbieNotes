# Flexbox

[pinterest grid with Flexbox](http://codepen.io/estherj-hsu/pen/bVXOMY)

## Parent (wrap/container)

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/flex-container.svg)

    display: flex

###flex-direction

容器內部child排列方向


    flex-direction: row(default) 橫向 | ltr 左到右 | rtl 右到左 
    flex-direction: row-reverse 逆橫向
    flex-direction: column 縱向
    flex-direction: column-reverse 逆縱向

> 當採**縱向**(column/column-reverse)排列時，需藉由控制**容器高度**來呈現多行排列模式

###flex-wrap
容器內部child換行，多行時藉由控制parent **寬度** / **高度** 實現

    flex-wrap: nowrap 單行
    flex-wrap: wrap 多行
    flex-wrap: wrap-reverse 逆向多行

###flex-flow
合併flex-direction與flex-wrap，共有4(方向)*3(換行)總組合方式

    flex-flow: row wrap
    flex-flow: column wrap

###justify-content
容器內部**單行**主軸(X軸)對齊

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2013/04/justify-content.svg)

    justify-content: flex-start 對齊主軸起始點
    justify-content: flex-end 對齊主軸終點
    justify-content: center 對齊主軸中間點
    justify-content: space-between 對齊主軸左右
    justify-content: space-around 對齊主軸左右且每個item左右保有相同空間
 
###align-items
容器內部**單行**側軸(Y軸)對齊

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/align-items.svg)

    align-items: flex-start 對齊側軸起始點
    align-items: flex-end 對齊側軸終點
    align-items: center 對齊側軸中間點
    align-items: stretch 延展至側軸雙邊、對齊側軸雙邊
    align-items: baseline 對齊文字基準線

###align-content
容器內部**多行**對齊

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2013/04/align-content.svg)

    align-content: flex-start 對齊主軸起始點
    align-content: flex-end 對齊主軸終點
    align-content: center 對齊主軸中間點
    align-content: stretch 延展至側軸雙邊、對齊側軸雙邊
    align-content: space-between 對齊主軸左右
    align-content: space-around 對齊主軸左右且每個item左右保有相同空間

##Child (item)

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/flex-items.svg)

###order
控制子項目順序，數字越小越接近起始點

    order: # (1, 2, 3, ...)

###flex-basis
取代item之width，預約空間

*[注意]  flex-shrink屬性優先於width，但若兩者之一為auto，非auto之屬性優先*

    flex-basis: auto(default) 不指定 | <width> (100px, 50%, ...) 指定 | content 以內容計算


###flex-grow

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/flex-grow.svg)

主容器剩餘空間索取之擴大比例，default為0，代表皆不索取，數字代表索取之份量。
假設容器寬度為500px，若flex-grow為0時，每個item寬度為500/3px；
但若設定三個item寬度為100px，再針對其中一個itemA設定flex-grow為1，則itemA之寬度為100px(預設寬度)+200px(總剩餘寬度)。
承上，若再設定itemB之flex-grow為3，則itemB寬度為100px+150px(總剩餘寬度200px中的3/4)，而A之寬度為100px+50px(總剩餘寬度200px中的1/4)

    flex-grow: 0(default) | #(1, 2, 3, ...)
 
###flex-shrink
主容器剩餘空間索取之縮小比例，default為1，代表若主容器寬度不足時，各item收縮比例皆相同，數字代表索取之份量。
假設容器寬度為700px，若flex-shrink為1，且4個item預設寬度皆為200px，此時主容器寬度不足100px，預設情況(flex-shrink: 1)下，不足的100px平均由4個item吸收，因此每個item的寬度為200px-25px(100px/4)；
承上，若再設定itemA之flex-shrink為2，則itemA之寬度為200px(預設寬度)+40px(不足寬度100px的2/5)。

    flex-shrink: 1(default) | #(1, 2, 3, ...)

###flex
整合flex-grow、flex-shrink、flex-basis之屬性

    flex: 0 1 auto(default) | none 不指定

###align-self
針對item之側軸對齊設定，可取代主容器之align-item屬性

![enter image description here](https://cdn.css-tricks.com/wp-content/uploads/2014/05/align-items.svg)


    align-self: auto 跟從align-item設定
    align-self: flex-start 對齊側軸起始邊
    align-self: flex-end 對齊側軸終邊
    align-self: center 對齊側軸中間
    align-self: baseline 以文字為基準
    align-self: stretch 延展至側軸雙邊、對齊側軸雙邊


----------

##Compatibility

###Parant

    display: -webkit-box
    display: -moz-box
    display: -ms-flexbox
    display: -webkit-flex
    display: flex

###Child

    -webkit-box-flex: 0 1 auto
	-moz-box-flex: 0 1 auto
	flex: 0 1 auto

	-webkit-box-ordinal-group: 1
	-moz-box-ordinal-group: 1 
	-ms-flex-order: 1
	order: 1



##Reference
* https://css-tricks.com/using-flexbox/
* http://www.w3.org/html/ig/zh/wiki/Css3-flexbox
* http://css.doyoe.com/properties/flex/index.htm
* https://css-tricks.com/snippets/css/a-guide-to-flexbox/
* https://egghead.io/lessons/misc-flexbox-fundamentals
* http://zh-tw.learnlayout.com/flexbox.html