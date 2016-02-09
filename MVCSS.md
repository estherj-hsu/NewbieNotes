
##Manifest

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

##Style Sheets

 - 屬性按字母順序排列（有 vendor 前綴的屬性按無前綴來排序）
 - Extends 和 Mixins 應該被放在標準屬性之前
 - 使用兩個空格縮排
 - 在 : 之後添加一個空格
 - 在註解 // 之後添加一個空格
 - 在值中的逗號之後添加一個空格（如 rgba(#000, 0.5)）
 - 在數學運算符的結尾寫數字（如 $b-space * 0.5）
 - 堅持為類別而非 ID 上樣式 盡可能限制巢狀結構
 
-

    .component
      @extend .group
      +transition(opacity 0.2s ease-in-out)
      border-radius: 5px
      box-shadow: 0 2px 5px rgba(#000, 0.5)
      -webkit-flex: 1 1 50%
      -ms-flex: 1 1 50%
      flex: 1 1 50%
      font-style: italic
      padding-bottom: $b-space * 3

## Markup
 - 按字母順序排列類別，依序是 Component、Structure、Tool、狀態和情境
 - 在每個獨立模組之後應用修飾符類別（modifier classes）

-

    <div class="g collection collection--1of3 bch mtl tci is-active has-dropdown"></div>

##Comments

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

##naming
###Tools
大部分的 Tool 類別看起來是首字母略縮詞。在這個概念下，採用兩個或三個字母的類別。
.mbm = margin bottom medium
.mbl = bottom margin large

###Components/Structures
 - 單數命名 Ex. icon, button, g (grid), form, modal
 - 如果名稱包含兩個單詞，利用 駝峰式命名（camelCase）Ex. taskList

###Modifiers
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

###States
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

###Context
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

###Variables
定義在 Config 裡，並且帶有他們的角色或相應 Component/Structure 的前綴。

 - $b-* 用於基礎變數
 - $c-* 用於顏色
 - $g-* 用於斷點（breakpoints）
 - $componentName-* 用於Components
 - $structureName-* 用於 Structures

##Foundation - config.sass sample

    // -------------------------------------
	//   Colors
	// -------------------------------------
	
	// ----- Palette ----- //
	
	$cerulean: #017ba7
	$forest: #7ba05b
	$gainsboro: #ecf0f1
	$gold: #ffd700
	$jet: #343434
	$scarlet: #ff3f00
	$white: #fff
	
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

