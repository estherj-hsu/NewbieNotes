##@mixin

=涵式名稱 (變數1: 預設值, 變數2, ...)

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
	  
--------------------------------

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

##@each+map

    /* SASS */
	
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

##@for

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

##list

Data structure is **flat** (different from **maps**)

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

##@function

Output = single value (different form mixin)

    @function calc-em($target-px, $context)
	  @return ($target-px / $context) * 1em
	h2
	  padding-left: calc-em(12px, 32px)

----

    h2 {
	  padding-left: 0.375em;
	}

##@extend + % 佔位符

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

##&
###&.--

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

###-- &

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
