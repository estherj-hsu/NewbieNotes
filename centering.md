#Centering

**Reference**
* https://css-tricks.com/centering-css-complete-guide/
* http://howtocenterincss.com/

##Horizontal

    // Text
    text-align: center
    
    // Div
    margin: 0 auto
    display: inline-block (多行)

##Vertical

    // Text
    vertical-align: middle
    
    // Div
    top: 50% (不論child高度是否固定情況下皆可用)
    position: absolute (並設定parent容器position: relative)

##Flexbox

**Reference**
* https://medium.com/@samserif/flexbox-s-best-kept-secret-bd3d892826b6#.3bd4xfkt8

Refer to [flexbox](https://github.com/estherj-hsu/NewbieNotes/blob/master/flexbox.md) note. :")

----
##display

* display: none 不可見、不佔空間
* visibility: hidden 不可見、佔空間
* display: inline 不換行 (不可包任何display: block之元素，且不可設定任何top/bottom之padding/margin)
* display: block 換行
* display : inline-block 、內block外inline (可設定top/bottom之padding/margin)

> inline-block可取代float，省略使用float後須clear之動作