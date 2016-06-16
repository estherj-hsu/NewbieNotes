From "Head First JavaScript"



## Ch6. DOM

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

### window.onload
頁面完全載入後才執行JS

    function init() {
	    var planet = document.getElementById("greenplanet");
	    planet.innerHTML = "Red Alert: hit by phaser fire!";
	    planet.setAttribute("class", "redtext");
	}
	window.onload = init;
 

## Ch7. Data Type

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


 
## Ch9. Event Object

 - load / unload
 - click
 - resize
 - play / pause
 - dragstart / drop
 - touchstart / touchend
 - mouseover / mouseout / mousemove
 - keypress

-

    // load 瀏覽器載入
    window.onload = init;
    
    // click 滑鼠點擊
    function init () {
      var images = document.getElementsByTagName("img");
      for (var i = 0; i < images.length; i++) {
        images[i].onclick = showAnswer;
      }
    }
    function showAnswer (eventObj) {
      var image = eventObj.target;
    
      var name = image.id;
      name = "src/img/" + name + ".jpg";
      image.src = name;
    }
    
    // mousemove 滑鼠移動
    function init() {
      var map = document.getElementById("map");
      map.onmousemove = showCoords;
    }
    function showCoords (eventObj) {
      var map = document.getElementById("coords");
      var x = eventObj.pageX;
      var y = eventObj.pageY;
      map.innerHTML = "Map coordinates: " + x + ", " + y;
    }
    
   

### Random numbers

    // 0 -> 10
    Math.floor(Math.random() * 11);
    
    // 1 -> 10
    Math.floor(Math.random() * 10) + 1;
    
    // 5 -> 20
    Math.floor(Math.random() * 16) + 5;
    
    // -10 -> (-2)
    Math.floor(Math.random() * 9) - 10;


## Ch12. Object Constructor

新增物件建構程序
	
	function Car(make, model, year, color, passengers, converitble, mileage) {
	  this.make = make;
	  this.model = model;
	  this.year = year;
	  this.color = color;
	  this.passengers = passengers;
	  this.convertible = convertible;
	  this.mileage = mileage;
	  this.started = false;
	  this.start = function() {
	    this.started = true;
	  };
	  this.stop = function() {
	    this.started = false;
	  };
	  this.drive = function() {
	    if (this.started) {
	      alert("Zoom zoom!");
	    } else {
	      alert("Start the engine first!");
	    }
	  };
	}

新增物件

    var chevy = new Car("Chevy", "Bel Air", 1957, "red", 2, false, 1021);

改寫為物件字面


	var chevyParams = {make:"Chevy",
	                   model: "Bel Air",
	                   year: 1957,
	                   color: "red",
	                   passengers: 2,
	                   convertible: false,
	                   mileage: 1021};
	
	var chevy = new Car(chevyParams)
	
	function Car(params) {
	  this.make = params.make;
	  this.model = params.model;
	  this.year = params.year;
	  this.color = params.color;
	  this.passengers = params.passengers;
	  this.convertible = params.convertible;
	  this.mileage = params.mileage;
	  this.started = false;
	  this.start = function() {
	    this.started = true;
	  };
	  this.stop = function() {
	    this.started = false;
	  };
	  this.drive = function() {
	    if (this.started) {
	      alert("Zoom zoom!");
	    } else {
	      alert("Start the engine first!");
	    }
	  };
	}


## Ch13. Prototype

新增prototype Dog

    function Dog(name, breed, weight) {
      this.name = name;
      this.breed = breed;
      this.weight = weight;
    }

新增屬性給Dog，預設值為Canine

    Dog.prototype.species = "Canine";

新增function屬性

    Dog.prototype.bark = function () {
      if (this.weight > 25) {
        console.log(this.name + " says WOOF!");
      } else {
        console.log(this.name + " says YIP!");
      }
    };

以prototype建立新物件

    var fido = new Dog("Fido", "Mixed", "38");
    var spot = new Dog("Spot", "Poodle", "10");

自訂屬性

    spot.bark = function (){
	    console.log(this.name + " says WOOF!");
	};

新增prototype(ShowDog)並繼承原有prototype(Dog)

    function ShowDog(name, breed, weight, handler) {
	  Dog.call(this, name, breed, weight);
	  this.handler = handler;
	}
	ShowDog.prototype = new Dog();

