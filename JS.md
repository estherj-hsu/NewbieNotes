##Data Type

### 字串方法&屬性

#### **toLowerCase** (字串小寫) & **toUpperCase** (字串大寫)

    var uptxt = "UPPER CASE";
	var lowtxt = "lower case";
	
	// 字串小寫
	var val = uptxt.toLowerCase();
	
	// 字串大寫
	var val = lowtxt.toUpperCase();

#### **substring**(子字串) & **split** (字串分割)

    var data = "name|phone|address";
    
    // 取得位於5-10字元中的子字串
	var val = data.substring(5, 10);
	
	// 取得第五字元後子字串
	val = data.substring(5);
	
	// 以|作為分隔符，分割字串內容
	val = data.split("|");

#### **length** (取得長度) & **charAt** (取得特定字符)

    var input = "jenny@wickedlysmart.com";
    
    //取得字串長度
    for(var i = 0; i < input.length; i++) {
      // 取得特定字符 @
      if (input.charAt(i) === "@") {
        console.log("There's an @ sign at index " + i);
      }
    }
#### **indexOf** / **lastIndexOf** (取得字串初次/最後出現位置引數)

    var phrase = "the cat in the hat";
    
    // 取得字串中cat初次出現位置
	var index = phrase.indexOf("cat");
	
	// 由字串第五字元後開始，取得the位置
	index = phrase.indexOf("the", 5);
	
	// 若無法取得引數則顯示-1
	var index = phrase.indexOf("dog");
	
	// 取得字串中the最後出現位置
	index = phrase.indexOf("the");


##DOM

### HTML

	// set the element as var
	var planet = document.getElementById("greenplanet");
	
	// change HTML content
	planet.innerHTML = "Red Alert: hit by phaser fire!";
	
	// set html attribute
	planet.setAttribute("style", "font-size: 13px");
	
	// get html attribute by ID first, then get attribute value
	var getBlue = document.getElementById("blueplanet");
	var blueTitle = getBlue.getAttribute("title");
	console.log(blueTitle);

###window.onload
頁面完全載入後才執行JS

    function init() {
	    var planet = document.getElementById("greenplanet");
	    planet.innerHTML = "Red Alert: hit by phaser fire!";
	    planet.setAttribute("class", "redtext");
	}
	window.onload = init;