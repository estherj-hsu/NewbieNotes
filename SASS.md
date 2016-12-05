# sass 快速入門

自己整理的sass快速入門重點，對於已有CSS經驗、不想花時間研讀sass手冊的懶人們應該會節省不少時間。

 > Reference  
 > [http://sass-lang.com/guide](http://sass-lang.com/guide)  
 > [Sass Guidelines](https://sass-guidelin.es/)

## 重點

 - 以雙空格取代 tab
 - 理想情況下每行的寬度在 80 字元內
 - 以多行方式呈現（善用 nesting）
 - 統一空格使用方式（冒號/分號後統一空格）
 - 以  `'單引號'`  呈現字串&路徑，若字串內包含單引號則使用雙引號 `"字串'引用'"`


## &

### & --

    h3
    font-size: 20px
    margin-bottom: 10px
    &.some-selector
      font-size: 24px
      margin-bottom: 20px

-------

    h3 {
      font-size: 20px;
      margin-bottom: 10px;
    }
    h3.some-selector {
      font-size: 24px;
      margin-bottom: 20px;
    }

### -- &

    h3
    font-size: 20px
    margin-bottom: 10px
    .some-parent-selector &
      font-size: 24px
      margin-bottom: 20px

-------

    h3 {
      font-size: 20px;
      margin-bottom: 10px;
    }
    .some-parent-selector h3 {
      font-size: 24px;
      margin-bottom: 20px;
    }

## Variables

基本的變數

    $c-warningRed: #d50000

    .btn-warning
      background-color: $c-warningRed

------

    .btn-warning {
      background-color: #d50000;
    }


## List

變數的進階版，需注意清單與map不同，簡單來說清單為列的話map為表格，儲存資料方式不同，取出方式當然也有差異

    $pages: ('home', 'about', 'products', 'contact')

    $selector: ()

    @each $item in $pages
      $selector: append($selector, unquote('.#{$item} .nav-#{$item}'), 'comma')
      #{$selector}
        style: awsome;

------

    .home .nav-home,
    .about .nav-about,
    .products .nav-products,
    .contact .nav-contact {
    style: awsome;


## @mixin

=mixinName (v1: default, v2: default, ...)

    =stf ($font:Arial, $color:#000000, $size:0.8em, $fwt:normal, $lh:100%)
      font-family: $font
      color: $color
      font-size: $size
      font-weight: $fwt
      line-height: $lh
    .p1
      +stf(Arial, #555555, 1.0em, bold, 200%)
    .p2
      +stf(Times New Roman, #888888, 1.5em, 700)
    .p3
      +stf(Arial, #888888, 2.5em)
    .p4
      +stf
    .p5
      +stf(Verdana)
      padding: 15px 5px

--------------------------------

    .p1 {
      font-family: Arial;
      color: #555555;
      font-size: 1em;
      font-weight: bold;
      line-height: 200%;
    }
    .p2 {
      font-family: Times New Roman;
      color: #888888;
      font-size: 1.5em;
      font-weight: 700;
      line-height: 100%;
    }
    .p3 {
      font-family: Arial;
      color: #888888;
      font-size: 2.5em;
      font-weight: normal;
      line-height: 100%;
    }
    .p4 {
      font-family: Arial;
      color: #000000;
      font-size: 0.8em;
      font-weight: normal;
      line-height: 100%;
    }
    .p5 {
      font-family: Verdana;
      color: #000000;
      font-size: 0.8em;
      font-weight: normal;
      line-height: 100%;
      padding: 15px 5px;
    }


簡單用：用於常成組出現的屬性可節省時間，如width/height、font-size/font-weight/font-family/color/line-height/text-align...

    =size($w, $h)
      width: $w
      height: $h

## @each+map

通常需要一組map/list去做特定的each迴圈

    $btns: (normal: #94a437, warning: #cb0a3a, closed: #5d5d5d)

    .btn a
      font-family: Arial
      font-size: 12px

    @each $btn-item, $btn-color in $btns
      .btn-#{$btn-item}
        background: $btn-color
      &:hover
          background: lighten($btn-color, 5%)

-------------

    .btn a {
      font-family: Arial;
      font-size: 12px;
    }
    .btn-normal {
      background: #94a437;
    }
    .btn-normal:hover {
      background: #a5b73d;
    }
    .btn-warning {
      background: #cb0a3a;
    }
    .btn-warning:hover {
      background: #e30b41;
    }
    .btn-closed {
      background: #5d5d5d;
    }
    .btn-closed:hover {
      background: #6a6a6a;
    }

## @for

基本數字迴圈

    @for $i from 1 through 3
    .heading#{$i}
      font-size: 1em + $i

------

    .heading1 {
      font-size: 2em;
    }
    .heading2 {
      font-size: 3em;
    }
    .heading3 {
      font-size: 4em;
    }

## @function

Output = single value (different form mixin)

    @function calc-em($target-px, $context)
    @return ($target-px / $context) * 1em

    h2
      padding-left: calc-em(12px, 32px)

----

    h2 {
      padding-left: 0.375em;
    }

## @extend + % 佔位符

    %txt
    font-size: 0.8em
    font-weight: 300
    color: steelblue
    .highlight
      @extend %txt
      line-height: 200%
    .bold
      @extend %txt

---------

    .highlight, .bold {
      font-size: 0.8em;
      font-weight: 300;
      color: steelblue;
    }

    .highlight {
      line-height: 200%;
    }

    .bold {
      font-weight: bold;
    }
