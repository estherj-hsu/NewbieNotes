## OOCSS
Object Oriented CSS (OOCSS) 的核心概念：

 - Seperate *structure*（結構） and *skin*（樣式）
 - Seperate *container*（容器） and *content*（內容）

在遵循上述兩點情況下，達到重複使用樣式的最高原則。

> Reference
> [http://andyyou.logdown.com/posts/290513-understanding-oocss](http://andyyou.logdown.com/posts/290513-understanding-oocss)
> [http://oocss.org/](http://oocss.org/)
> [https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)


### Rules
 - 避免以 html tag 作為選擇器
 - 以*邏輯與語意*命名元素，非外觀語意
 - 避免樣式相依於結構（低耦合概念）

=

    <div class="page">
        <div class="head"></div>
        <div class="body">
            <div class="leftCol"></div>
            <div class="rightCol"></div>
            <div class="main"></div>
        </div>
        <div class="foot"></div>
    </div>


## SMACSS
Scalable and Modular Architecture for CSS (SMACSS) 的主要概念：
 - 提升網頁語意
 - 減少對 html tag 的依賴

> Reference
> [http://ithelp.ithome.com.tw/articles/10161555](http://ithelp.ithome.com.tw/articles/10161555)
> [http://www.w3cplus.com/blog/tags/383.html](http://www.w3cplus.com/blog/tags/383.html)
> [https://smacss.com/](https://smacss.com/)
> [https://www.sitepoint.com/bem-smacss-advice-from-developers/](https://www.sitepoint.com/bem-smacss-advice-from-developers/)

### Manifest
    @import
        "site-settings",
        "mixins",
        "base",
        "states",
        "layout/grid",
        "module/btn",
        "module/bookmarks",
        "module/callout";
      
### Categories
 - Base 基本設定：reset, normalize, etc... 初始設定
 - Layout 框架/容器：以 `.l-` 作為前綴，如 `.l-header`
 - Module 元件：可單獨存在且重複使用，如 `.pullquote`
 - State 狀態：和 layout/module搭配，以 `.is-` 為前綴，如 `.is-active`
 - Theme 視覺：網站整體樣式、佈景，以 `.theme-` / `.t-` 為前綴，如 `.t-light`

較特別的是，SMACSS 建議在 state 中使用 `!important`，且 module 下可細拆 sub module

### Sample
    <div class="media is-box-shadow">
        <div class="media-img></div>
        <div class="media-body"></div>
    </div>


## BEM
Block Element Modifier (BEM) 是目前最常被使用的 CSS 設計模式，由區塊（Block）、元素（Element）、修飾符（Modifier）構成，可輕鬆地藉由樣式名稱了解元素間彼此關係，也廣泛被其他的 CSS 方法論（OOCSS, SMACSS, SUITCSS, Atomic, etc...）作為命名依據。

 > Reference 
 > [https://en.bem.info/](https://en.bem.info/)
 > [http://getbem.com/](http://getbem.com/)

### Blocks, Elements and Modifiers
 - Blocks 區塊：獨立且可以單獨存在於頁面中的區塊，如 `.menu` `.header`
 - Elements 元素：可重複使用，需被包含於 block 內，命名方式會以 block__ 名稱作為前綴，如`.menu__item`
 - Modifiers 修飾符：定義 blocks 和 elements 的狀態或屬性，命名以 block-- 或 block__element-- 為前綴，如 `.menu__item--active` `.menu--hidden`

### Sample
    <!-- HTML -->
    <form class="form form--theme-xmas form--simple">
      <input class="form__input" type="text" />
      <input
        class="form__submit form__submit--disabled"
        type="submit" />
    </form>
    
    <!-- CSS -->
    .form { }
    .form--theme-xmas { }
    .form--simple { }
    .form__input { }
    .form__submit { }
    .form__submit--disabled { }

## SUIT CSS
Style UI Tool for CSS (SUIT CSS) 類似 BEM 的 CSS 命名規範，此命名規範區分出了頁面中的幾個主要元素：
 - 通用樣式
 - 獨立/模組化 UI 元件
 - 單獨元素
 - 修飾符

 SUIT CSS 以帕斯卡命名（PascalCase）為主，搭配駝峰命名（camelCase），減少 BEM 中的 -- / __ 使用量，並增加樣式名稱識別度。

 > Reference
 > [https://github.com/estherj-hsu/suit/blob/master/doc/naming-conventions.md](https://github.com/estherj-hsu/suit/blob/master/doc/naming-conventions.md)
 > [http://www.w3cplus.com/PostCSS/using-postcss-with-bem-and-suit-methodologies.html](http://www.w3cplus.com/PostCSS/using-postcss-with-bem-and-suit-methodologies.html)
 
### Architectural Division
 - Utilities 結構：控制位置、頁面結構
 - Components 組建：類似 BEM 中的 blocks
    - Descents 後代：子元素，類似 BEM 中的 elements
    - Modifiers 修飾符：限用於 components
    - States 狀態：可用於 components 與 descents，用於改變狀態

### Naming
#### Utilities
以 `.u-` 為前綴，RWD 時可加上尺寸修飾，如 `u-[sm-|md-|lg-]<utilityName>`

    <div class="u-cf">
      <a class="u-floatLeft" href="{{url}}">
        <img class="u-block" src="{{src}}" alt="">
      </a>
      <p class="u-sizeFill u-textBreak">
        …
      </p>
    </div>

#### Components
通常為元件名稱，並延伸後代、修飾符與狀態，如 `[<namespace>-]<ComponentName>[-descendentName][--modifierName]`

##### ComponentName
一般為防止命名衝突，建議在 CompnentName 前加上前綴，如 `.sp-MyComponent`，增加命名空間。

    <article class="MyComponent">
      …
    </article>

##### ComponentName--modifierName
限用於 components，不能用於狀態表示，以雙破折號 `--` 和 ComponentName 連接。

    <button class="Button Button--default" type="button">…</button>

##### ComponentName-descendentName
以破折號 `-` 和 ComponentName 連接，類似子元素概念。

    <article class="Tweet">
      <header class="Tweet-header">
        <img class="Tweet-avatar" src="{{src}}" alt="{{alt}}">
        …
      </header>
      <div class="Tweet-bodyText">
        …
      </div>
    </article>

##### ComponentName.is-stateOfComponent
可用於 components 和 ComponentName-descendentName，通常用於反應狀態改變，多以 `.is-` 作為前綴。

    <article class="Tweet is-expanded">
      …
    </article>

## ITCSS
Inverted Triangle CSS (ITCSS) 以倒三角的形狀為主要概念，由上到下特異性逐增，ITCSS是一種CSS的概念，可以與其他方法論（OOCSS, SMACSS）共用，主要特性為：

 - 頁面內的元素被拆分後可以提高重複使用性
 - 可與其他方法論融合使用
 - 無特定的資料夾結構，活用度高

 > Reference
 > [https://read01.com/ndExyQ.html](https://read01.com/ndExyQ.html)
 > [https://medium.okgrow.com/building-a-maintainable-and-scalable-css-codebase-with-itcss-ceda5b2f495b#.pf75off6e](https://medium.okgrow.com/building-a-maintainable-and-scalable-css-codebase-with-itcss-ceda5b2f495b#.pf75off6e)
 > [https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/)
 > [http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/](http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)
 
### Layers
 - Settings 設置：變數、基本設定，無實際樣式
 - Tools 工具：mixins、函數，無實際樣式
 - Generic 通用：reset/normalize、通用樣式
 - Elements 元素：基本 html tag 定義
 - Objects 物件：非裝飾性質的元素，如 layout
 - Components 特定的 UI 元件，通常由 objects 和 elements 構成
 - Trumps 王牌：utilities/helpers，用於覆蓋上述所有樣式

### BEMIT
ITCSS 設計者將 ITCSS 與 BEM 做完美融合為 BEMIT，是設計者本身推薦的融合方法論

    <div class="o-media  c-user  c-user--premium">
      <img src="" alt="" class="o-media__img  c-user__photo  c-avatar" />
      <p class="o-media__body  c-user__bio">...</p>
    </div>

### Structure
    main.scss
    
    settings
    -- _typography.scss
    -- _palette.scss
    
    tools
    -- _box-model.scss
    -- _position.scss
    
    generic
    -- _normalize.scss
    -- _box-sizing.scss
    
    elements
    -- _body.scss
    -- _a.scss
    
    objects
    -- _media.scss
    
    components
    -- _button.scss
    -- _loading.scss
    
    trumps
    -- _clear-fix.scss

## MVCSS

MVCSS 是針對 sass 延伸出的 CSS 方法論，融合了SMACSS、OOCSS、BEM的設計模式，是少數**規範完整**的方法論。

 > Reference
 > [https://mvcss.ycnets.com/](https://mvcss.ycnets.com/)
 > [http://mvcss.io/](http://mvcss.io/)
 > [https://github.com/mvcss/mvcss](https://github.com/mvcss/mvcss)

### Manifest

    application.sass 資源配置&收件匣(inbox)
	foundation/
	  _reset.sass
	  _helpers.sass  function, mixin, extend, ...
	  _config.sass   font-face, colors, ...
	  _base.sass     HTML tag level, html, ...
	  _tools.sass    Specific style
	components/      可用於不同專案，EX. card, box, ...
	structures/      加強components，大範圍用，EX. RWD
	vendor/          3rd party css

### Style Sheets

 - 屬性按字母順序排列（有 vendor 前綴的屬性按無前綴來排序）
 - Extends 和 Mixins 應該被放在標準屬性之前
 - 使用兩個空格縮排
 - 在 : 之後添加一個空格
 - 在註解 // 之後添加一個空格
 - 在值中的逗號之後添加一個空格（如 rgba(##000, 0.5)）
 - 在數學運算符的結尾寫數字（如 $b-space * 0.5）
 - 堅持為類別而非 ID 上樣式 盡可能限制巢狀結構
 
=

    .component
      @extend .group
      +transition(opacity 0.2s ease-in-out)
      border-radius: 5px
      box-shadow: 0 2px 5px rgba(##000, 0.5)
      -webkit-flex: 1 1 50%
      -ms-flex: 1 1 50%
      flex: 1 1 50%
      font-style: italic
      padding-bottom: $b-space * 3

### Markup
 - 按字母順序排列類別，依序是 Component、Structure、Tool、狀態和情境
 - 在每個獨立模組之後應用修飾符類別（modifier classes）

=

    <div class="g collection collection--1of3 bch mtl tci is-active has-dropdown"></div>

### Comments

    // *************************************
	//
	//   First Level
	//   -> Description
	//
	// *************************************
	
	// -------------------------------------
	//   Second Level
	// -------------------------------------
	
	// ----- Third Level ----- //
	
	// Fourth Level

### Naming
##### Tools
大部分的 Tool 類別看起來是首字母略縮詞。在這個概念下，採用兩個或三個字母的類別。
.mbm = margin bottom medium
.mbl = bottom margin large

##### Components/Structures
 - 單數命名 Ex. icon, button, g (grid), form, modal
 - 如果名稱包含兩個單詞，利用 駝峰式命名（camelCase）Ex. taskList

##### Modifiers
修飾符的存在允許建立在初始定義上的風格調整。這些調整以兩個連字符 -- 表示。例如，一個按鈕可能有一些不同的顏色和大小。

> 註： 修飾符通常在分層序列（a、b）定義或透過功能（cancel、submit）時發揮最好，而不是使用外觀（red、blue）。

    // *************************************
	//
	//   Button
	//   -> Action points
	//
	// *************************************
	
	.btn
	  border: 0
	  display: inline-block
	  line-height: 2.5
	  padding: 0 $b-space
	  font-weight: bold
	
	// -------------------------------------
	//   Modifiers
	// -------------------------------------
	
	// ----- Sizes ----- //
	
	.btn--s
	  font-size: 75%
	
	.btn--l
	  font-size: 150%
	
	// ----- Theme ----- //
	
	// Hierarchy
	
	.btn--a
	  background: $c-base
	
	.btn--b
	  background: $c-highlight

##### States
通常是透過 JavaScript 添加，狀態類似於修飾符但具有條件的情境。is- 表示是一個狀態，例如 is-active

    // *************************************
	//
	//   Button
	//   -> Action points
	//
	// *************************************
	
	.btn
	  // Styles
	
	// Modifiers
	
	// -------------------------------------
	//   States
	// -------------------------------------
	
	.btn.is-active
	  background: $c-highlight

##### Context
情境選擇器以 has- 開頭表示。

    // *************************************
	//
	//   Dropdown
	//   -> Revealed information
	//
	// *************************************
	
	.dropdown
	  // Styles
	
	// Modifiers, States
	
	// -------------------------------------
	//   Context
	// -------------------------------------
	
	.has-dropdown
	  position: relative

##### Variables
定義在 Config 裡，並且帶有他們的角色或相應 Component/Structure 的前綴。

 - $b-* 用於基礎變數
 - $c-* 用於顏色
 - $g-* 用於斷點（breakpoints）
 - $componentName-* 用於Components
 - $structureName-* 用於 Structures

### Foundation - config.sass sample

    // -------------------------------------
	//   Colors
	// -------------------------------------
	
	// ----- Palette ----- //
	
	$cerulean: ##017ba7
	$forest: ##7ba05b
	$gainsboro: ##ecf0f1
	$gold: ##ffd700
	$jet: ##343434
	$scarlet: ##ff3f00
	$white: ##fff
	
	// ----- Base ----- //
	
	$c-background-invert: $white
	$c-background: $gainsboro
	$c-border: lighten($jet, 30%)
	$c-error: $scarlet
	$c-highlight: $cerulean
	$c-text-invert: $white
	$c-text: $jet
	$c-subdue: lighten($cerulean, 40%)
	$c-success: $forest
	$c-warning: $gold
	
	// ----- Components ----- //
	
	// 範例：$row--a-background: $c-highlight
	
	// ----- Structures ----- //
	
	// 範例：$dropdown-link-color: $c-subdue
	
	// -------------------------------------
	//   Base
	// -------------------------------------
	
	// ----- Borders & Box Shadow ----- //
	
	$b-borderRadius: 3px
	$b-borderStyle: solid
	$b-borderWidth: 2px
	$b-border: $b-borderWidth $b-borderStyle $c-border
	$b-boxShadow: 0 2px 0 rgba($jet, 0.25)
	
	// ----- Typography ----- //
	
	$b-fontFamily-heading: 'OpenSans', sans-serif
	$b-fontFamily: 'OpenSans', sans-serif
	$b-fontSize: 16px
	$b-fontSize-s: 75%
	$b-fontSize-m: 90%
	$b-fontSize-l: 115%
	$b-lineHeight: 1.5
	
	// ----- Sizing ----- //
	
	$b-space: em(20px)
	$b-space-s: 0.5 * $b-space
	$b-space-l: 2 * $b-space
	$b-space-xl: 4 * $b-space
	
	// -------------------------------------
	//   Components
	// -------------------------------------
	
	// ----- Grid ----- //
	
	$g-s: em(480px)
	$g-m: em(800px)
	$g-l: em(1024px)
	
	// -------------------------------------
	//   Structures
	// -------------------------------------
	
	// ----- Dropdown ----- //
	
	// 範例：$dropdown-width: em(200px)

