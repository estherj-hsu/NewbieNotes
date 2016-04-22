##DOM

### HTML

	// set the element as var
	var planet = document.getElementById("greenplanet");
	
	// change HTML content
	planet.innerenter code hereHTML = "Red Alert: hit by phaser fire!";
	
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