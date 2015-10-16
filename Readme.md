
#Notes

##Git

Useful links:
* [Backlogtoll(TW)](http://backlogtool.com/git-guide/tw/)
* [Command list(EN)](https://confluence.atlassian.com/stash/basic-git-commands-278071958.html)
* [Command list(TW)](http://shyuanliang.blogspot.tw/2010/12/git-command-list.html)

##CSS3 / HTML5

* Round Corners*
* Multiple Backgrounds (layers)
* Color Opacity (1.0-0.0)
* Gradient *
* Text-shadow / Box-shadow
* Text-overflow
* Web-font
* Transforms (2D/3D)*
* Transitions*
* Animations*
* Multi-Column*
* Flex Concept*
* Media Queries (RWD)

*Browsers

| Safari / Chrome | Opera | Firefox | IE9 |
|:---:|:---:|:---:|:---:|
| -webkit | -o | -moz | -ms |

Useful site: [Can I Use](http://caniuse.com/)

**Reset style**: a style to reset all settings, especially for margin, padding, height, etc.

**Wrapper** = container

##Sass / SCSS

| . | Sass | SCSS | 
|:---:|:---:|:---:|
| ; / {} | NO | YES |
|mixin|=|@mixin|
|maps|X|O|

* $ = Variables
* Nesting {}
* Mixin (@mixin / @include)
* Inheritance (@extend)

!default


###@mixin

    /* SASS */
    
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

------

    /* Resulting CSS */
    
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


###@mixin ($args...) 不定量引數

    /* SASS */
    
    @mixin box-shadow($args...)
      -webkit-box-shadow: $args
      -moz-box-shadow: $args
      box-shadow: $args
    .box
      @include box-shadow(5px 5px 3px lightgray, inset 5px 5px 5px yellow)

###@each+map (loop)

    /* SCSS */
    
    $menus: (
      menu1: #94a437,
      menu2: #cb0a3a,
      menu3: #5d5d5d
    );
    .menu a {
      color: #fff;
      padding: 8px 8px;
      margin: 3px 3px;
      font-family: Arial;
      font-size: 0.8em;
    }
    @each $menu-item, $menu-color in $menus {
      .#{$menu-item} {
        background: $menu-color;
      }
      .#{$menu-item}:hover {
        background: lighten($menu-color, 5%);
      }
    }
    
----------
    /* Resulting CSS */
    
    .menu a {
      color: #fff;
      padding: 8px 8px;
      margin: 3px 3px;
      font-family: Arial;
      font-size: 0.8em;
    }
    .menu1 {
      background: #94a437;
    }
    .menu1:hover {
      background: #a5b73d;
    }
    .menu2 {
      background: #cb0a3a;
    }
    .menu2:hover {
      background: #e30b41;
    }
    .menu3 {
      background: #5d5d5d;
    }
    .menu3:hover {
      background: #6a6a6a;
    }
    
###@for (loop)

    /* SCSS */
    
    @for $i from 1 through 3 {
      .menu-#{$i} { font-size: 1em + $i; }
    }
    
--------------------

    */ Resulting CSS */
    
    .menu-1 {
      font-size: 2em;
    }
    .menu-2 {
      font-size: 3em;
    }
    .menu-3 {
      font-size: 4em;
    }


###list

Data structure is **flat** (different from **maps**)

    /* SCSS */
    
    $pages: ('home', 'about', 'products', 'contact');
    $selector: ();
    @each $item in $pages {
      $selector: append($selector, unquote('.#{$item} .nav-#{$item}'), 'comma');
    }
    #{$selector} {
      style: awesome;
    }
    
-------------

    /* Resulting CSS */
    
    .home .nav-home, .about .nav-about, .products .nav-products, .contact .nav-contact {
      style: awesome;
    }


###@function

Output = **single value**  (different form **mixin**)

    /* SCSS */
    
    @function calc-em($target-px, $context) {
      @return ($target-px / $context) * 1em;
    }
    h2 {
      padding-left: calc-em(12px, 32px);

-----

    /* Resulting CSS */
    
    h2 {
      padding-left: 0.375em;
    }

###&

####&.--

    /*  SASS */
    
    h3
      font-size: 20px
      margin-bottom: 10px
      &.some-selector
        font-size: 24px
        margin-bottom: 20px

----

    /* Resulting CSS */
    
    h3 {
      font-size: 20px;
      margin-bottom: 10px;
    }
    h3.some-selector {
      font-size: 24px;
      margin-bottom: 20px;
    }

####-- &

    /* Sass */
    
    h3
      font-size: 20px
      margin-bottom: 10px
      .some-parent-selector &
        font-size: 24px
        margin-bottom: 20px


----------

    /* Resulting CSS */ 
    
    h3 {
      font-size: 20px;
      margin-bottom: 10px;
    }
    .some-parent-selector h3 {
      font-size: 24px;
      margin-bottom: 20px;
    }

##@extend + %


    /* Sass */
    
    %txt
      font-size: 0.8em
      font-weight: 300
      color: steelblue
    .highlight
      @extend %txt
      line-height: 200%
    .bold
      @extend %txt

-----

    /* Resulting CSS */
    
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
