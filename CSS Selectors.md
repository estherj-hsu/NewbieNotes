##Common Selectors

###Type Selector

HTML標籤

`h1, body, p, em`

###ID Selector

頁面單次使用之ID選擇器

    #wrap, #container

###Class Selector

可多次使用之類別選擇器

    .box, .btn--blue

###Universal Selector

通用選擇，套用所有p元素

    p *
      color: #000000

##Child Selectors

###Descendant Selector 後代選擇 

選擇父元素(.box)內的所有後代元素(p)

    .box p
      color: #E2E2E2
      font-weight: bold

###Direct Child Selector >

選擇父元素為.box的所有子元素p（子元素需直屬於父元素）

    .box > p
      color: #E2E2E2
      font-weight: bold

##Sibling Selectors 同層選擇

###General Sibling Selector 同層全體選擇 ~

選擇與h1**相同階層**的p元素

    h1 ~ p
      color: #b43d54
      

###Adjacent Sibling Selector 同層相鄰選擇器 +

選擇與h1 **相同階層且相鄰**的p元素

    h1 + p
      color: #b43d54

##Attribute Selectors 指標選擇

針對HTML內容作屬性選擇，省去定義class或ID之步驟

###Attribute Present Selector 特定屬性 [ ]

選擇所有連結中具有特定屬性target之元素

    a[target]
      color: #b43d54
    
    <a href="#" target="_self">HOME</a>

###Attribute Equals Selector 精確屬性 [ = ]

選擇所有連結屬性中target=_blank之元素

        a[target=_blank]
          color: #b43d54
          
        <a href="#" target="_blank">HOME</a>

###Attribute Contains Selector 包含屬性 [ *= ]
選擇所有連結中，href內容**包含** pdf 之元素

    a[href*="pdf"]
      color: #b43d54
      
    <a href="http://www.abc.com/file.pdf">PDF</a>


###Attribute Begins With Selector 起始屬性 [ ^= ]

選擇所有連結中，href內容**起始**為www之元素

    a[href^="www"]
      color: #b43d54
      
    <a href="www.abc.com">HOME</a>


###Attribute Ends With Selector 結尾屬性 [ $= ]

選擇所有連結中，href內容**結尾**為.html之元素

    a[href$=".html"]
      color: #b43d54
    
    <a href="http://www.abc.com/test.html">HOME</a>

###Attribute Spaced Selector 空格屬性[ ~= ]

選擇所有連結中，title內容**包含** page此**單字**之元素

    a[title~="page"]
      color: #b43d54
    
    <a href="http://www.abc.com/" title="Home page">HOME</a>

> 此選擇器與container selector的差異在於僅限於單字選擇，即前後需有空格區隔

###Attribute Hyphenated Selector [ |= ] 

選擇所有連結中，title內容中**含有** home **單字**且單字後方有 **-** 之元素

    a[title|=home]
      color#b43d54
    
    <a href="#" title="home-page">HOME</a> 

##Pseudo-classes 虛擬類選擇器

###Link Pseudo-classes 連結虛擬類別 :link, :visited

    :link 未訪問過連結元素
    :visited 訪問過之連結元素

###User Action Pseudo-classes 使用者動作虛擬類別 :hover, :active, :focus

    :hover 游標滑過
    :active 游標點擊時
    :focus 成為焦點之屬性

###UI State Pseudo-classes UI元素狀態虛擬類別 :enabled, :disabled, ...

    :enabled 啟用之元素
    :disabled 未啟用之元素
    :checked 已核選之元素
    :indeterminate 樹狀情況下，部分子項目被選取之父項目元素


###Structural & Position Pseudo-classes 結構&定位虛擬類別 :root, :nth-child(), ...

![enter image description here](https://css-tricks.com/wp-content/csstricks-uploads/relationalpseudos2.png)

####:first-child, :last-child, & :only-child

    :first-child 父元素下第一個子項目
    :last-child 父元素下最後一個子項目
    :only-child 父元素下唯一項目之子項目

####:first-of-type, :last-of-type, & :only-of-type

    :first-of-type 同階層下相同樣式的第一個
    :last-of-type 同階層下相同樣式的最後一個
    :only-of-type 同階層下唯一一個樣式

####:nth-child(n) & :nth-last-child(n)

    :nth-child(n) 父元素下的第N個子項目
    :nth-last-child(n) 父元素下的倒數第N個子項目

> N可為數字(1, 2, 3, ...)、關鍵詞(odd, even)或公式(4n, 4n+5, ...)。
> 4n: 每四個子元素
> 4n+5: 第5個元素後起每4個元素

####:nth-of-type(n) & :nth-last-of-type(n)

    :nth-of-type(n) 同階層下相同樣式的第N子項目
    :nth-last-of-type(n) 同階層下相同樣式的倒數第N個子項目

###Target Pseudo-class 目標虛擬類別 :target



###Empty Pseudo-class



###Negation Pseudo-class 否定虛擬類別 :not()

