## 3 Array
### Nested Array

    var reality = ["yusuf", ["arthur", ["eames", ["cobb", "ariadne", "saito, "fischer"]]]];
    
    reality[0];            // returns "yusuf"
    reality[1][0];         // returns "arthur"
    reality[1][1][0];      // returns "eames"
    reality[1][1][1][0];   // returns "cobb"
    reality[1][1][1][1];   // returns "ariadne"
    reality[1][1][1][2];   // returns "saito"
    reality[1][1][1][3];   // returns "fischer"

### Mutator Methods

    var tasks = [
                 "Pay phone bill",
                 "Write best-selling novel",
                 "Walk the dog"
                ];

#### pop
Removes the last element from array and returns it

    tasks.pop();   //returns "Walk the dog"
    
    // tasks array is now
    var tasks = [
                 "Pay phone bill",
                 "Write best-selling novel"
                ];

#### push
Adds new item to the end of array and returns the new length

    tasks.push("Feed the cat");   // returns 4
    
    // tasks array is now
    var tasks = [
                 "Pay phone bill",
                 "Write best-selling novel",
                 "Walk the dog",
                 "Feed the cat"
                ];

#### shift
Removes the first item from array and returns it

    tasks.shift();   // returns 4
    
    // tasks array is now
    var tasks = [
                 "Write best-selling novel",
                 "Walk the dog"
                ];

#### sort
Sorts the array items and list them in ascending order

    array.sort([tasks]);
    
    // tasks array is now
    var tasks = [
                 "Pay phone bill",
                 "Walk the dog",
                 "Write best-selling novel"
                ];

#### splice
Adds and remove items from the array with the same command

    tasks.splice(1, 1, "World domination")   // remove [index] [howMany], [add items]
    
    // tasks array is now
    var tasks = [
                 "Pay phone bill",
                 "World domination",
                 "Write best-selling novel"
                ];

#### unshift
Adds one or more items to the beginning of the array and returns the new length

    tasks.unshift("Defeat nemesis", "Pick up dry cleaning");   // returns 5
    
    // tasks array is now
    var tasks = [
                 "Defeat nemesis",
                 "Pick up dry cleaning",
                 "Pay phone bill",
                 "World domination",
                 "Write best-selling novel"
                ];

### Accessor Methods

#### contact
Combines two or more arrays into one

    var arr1, arr2, arr3, arr4;
    arr1 = ["Pay mobile bill"];
    arr2 = ["Write best-selling novel"];
    arr3 = ["Walk the dog"];
    arr4 = arr1.concat(arr2, arr3);
    
    // arr4 is now
    arr4 = [
		    "Pay mobile bill",
		    "Write best-selling novel",
		    "Walk the dog"
		   ]

#### join
Takes the values from one array and joins them into a string

    var num = [4, 8, 15, 16, 23, 42];
    alert.join("The winning lottery numbers are: " + nums.join(", ");
    
    // alert content
    The winning lottery numbers are: 4, 8, 15, 16, 23, 42

#### slice
Copies a part of an array and returns it
slice(#1, #2) = from index[1] to index[2]

    var tasks, todo, cleanUp, noCleaning;
    tasks = [
		     "Fly a kite",
		     "Save the world",
		     [
			  "Clean bathroom",
			  "Clean garage",
			  "Clean up act"
			 ]
			];
	todo = tasks.slice(0);         // copies tasks
	cleanUp = tasks.slice(-1);     // copies only the nested array
	noCleaning= tasks.slice(0, 2)  // copies from index[0] to index[2]

#### toString
returns a string with the array items

    var arr = ["These", "words", "are", "separeted", "by", "commas"];
    arr.toString();    // returns "These,words,are,separeted,by,commas"

#### indexOf / lastIndexOf
Finds the first/last instance of an item and returns its index
array.indexOf(searchElement, [fromIndex])
array.lastIndexOf(searchElement, [fromIndex])

    var alphabet = ["a", "b", "c", "d", "e", "f", "g", "a", "b", "c", "d"];
    alphabet.indexOf("b");     // returns 1
    alphabet.indexOf("b", 6);  // returns 8
    alphabet.lastIndexOf("b");     // returns 8
    alphabet.lastIndexOf("b", 6);  // returns 1



## Ch6 DOM

[DOM Obj](http://www.w3schools.com/jsref/dom_obj_document.asp)

    getElementById('id')
    getElementsByClassName('className')
    getElementsByTagName('tagName')
    getElementsByName('name')
    createElement('div')
    createAttribute('style')
    createTextNode('Link text')
  
[DOM Elements](http://www.w3schools.com/jsref/dom_obj_all.asp)
[DOM Attribute](http://www.w3schools.com/jsref/dom_obj_attributes.asp)

    // create new element
	var myDiv = document.createElement("div");
	// add the new element into specify place
	document.contact.appendChild(myDiv);
	// add value and content [attribute], [attributeContent]
	myDiv.setAttribute("name", "foo");
	
	var myLink = document.createElement("a");
	// create new attribute
	href = document.createAttribute("href");
	// add node value
	href.nodeValue = "http://sitepoint.com";
	// set node attribute
	myLink.setAttributeNode(href);
	// create node text
	linkText = document.createTextNode("Sitepoint(JS)");
	// add and set attribute
	myLink.setAttribute("target", "_blank");
	// set node into element
	myLink.appendChild(linkText);
	document.contact.appendChild(myLink);
	
	// create list
	var list = document.createElement("ul");
	for (var i = 1; i <= 5; i++ ) {
	  var itemNum = "item" + i;
	  itemNum = document.createElement("li");
	  itemNum.appendChild(document.createTextNode(i));
	  list.appendChild(itemNum);
	}
	document.contact.appendChild(list);

[DOM Style](http://www.w3schools.com/jsref/dom_obj_style.asp)

    // get HTML element
	var hello = document.getElementById("greeting");
	// change text content
	hello.textContent = "Good morning!";
	// change style
    hello.style.color = "#6c6c6c";
	hello.style.padding = "15px";
	hello.style.background = "#f5f5f5";
	hello.style.width = "200px";
	hello.style.margin = "0 auto";
	hello.style.border = "solid 3px #CCC";

## Ch7 Events

### Event Handler
#### addEventListener (multi)

    var myButton = document.getElementById("btnClickMe");
    function handleClick() {
      alert("addEventListerner clicked!");
    }
    function handleClick2() {
      alert("addEventListerner2 clicked!");
    }
    myButton.addEventListener("click", handleClick, false);
    myButton.addEventListener("click", handleClick2, false);

#### DOM Element Properties (unique)

    var myButton = document.getElementById("btnClickMe");
	myButton.onclick = function(e) {
	  alert("onClick clicked!");
	};

### Custom Events

    // custom events
	// var event = new CustomEvent(type, eventInitDict);
	var taskEvent = new CustomEvent("TaskAdded", {
	  detail: {
	    message: "A task has been added",
	  },
	  bubbles: true,
	  calcelable: true
	});
	var btnAdd = document.getElementById("btnAdd");
	
	btnAdd.onclick = function (e) {
	  document.dispatchEvent(taskEvent);
	}
	
	function handleTaskAdded (e) {
	  alert(e.detail.message);
	}
	document.addEventListener("TaskAdded", handleTaskAdded, false);