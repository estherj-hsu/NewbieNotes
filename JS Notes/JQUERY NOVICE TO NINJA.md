## Ch2 Selecting, Decorating, Enhancing

### Selecting
    // by tag
    $('tr')
    
    // by id
    $('#id')
    
    // by class name
    $('.className')
    
    $('td')
    $('#greeting')
	$('.textContent')
	$('#table tr .tdStyle')

### Decorating

    $('h1').css('font-size', '22px');
    
    // multi selector
    $('p, table, li').css('font-size', '13px');
    $('td').css('padding', '4px 12px');
    
    // with multi styles
    $('#celebs tr').css({
      'background-color': '#fff',
      'color': '#212121',
      'line-height': '3'
    });
    
    // with selector even/odd
    $('#celebs tr:even').css('background-color', '#fafafa');
    
    // Add/Remove Class
    $('th').addClass('thStyle');
    $('p.info').removeClass('info');

### Enhancing

#### Hiding/Revealing Elements

	$('#hideButton').click(function() {
	  $('#disclaimer').hide();
	});
	$('#showButton').click(function() {
	  $('#disclaimer').show();
	});
	
	// this
	$('td').click(function() {
	  $(this).css('background-color', '#333');
	});
	$('p').click(function() {
	  $(this).css('background-color', 'rgba(255,229,0,.3)');
	
	// toggle
	$('#toggleButton').click(function() {
	  if ($('#disclaimer').is(':visible')) {
	    $('#disclaimer').hide();
	  } else {
	    $('#disclaimer').show();
	  }
	});
	
	// toggle and change button text
	$('#toggleButton').click(function() {
	  $('#disclaimer').toggle();
	  if ($('#disclaimer').is(':visible')) {
	    $(this).val('Hide');
	  } else {
	    $(this).val('Show');
	  }
	});

#### Add New Elements (inserAfter / insertBefore)

    $('<input type="button" id="toggleButton" value="toggle">').insertBefore('#disclaimer');
    $('#toggleButton').click(function() {
      $('#disclaimer').toggle();
    });
    
    // Add new advanced element
    $('<div>', {
      id: 'newDiv',
      text: 'Click Me!',
      click: function () {
        alert("Advanced jq")
      }
    }).insertBefore('#disclaimer');
    
    // prepenTo/appendTo
    $('<strong>START!</strong>').prepenTo('#disclaimer');
    $('<strong>END!</strong>').appendTo('#disclaimer');

#### Removing Existing Elements

    $('#news').remove();
    $('#celebs tr').remove(':contains("Singer")');

#### Basic Animation

    // fade out
	$('#hideButton').click(function () {
	  $('#news').fadeOut();
	});
	
	// fade in
	$('#showButton').click(function () {
	  $('#news').fadeIn();
	
	// toggle: slow
	$('#toggleButton').click(function() {
	  $('#disclaimer').toggle('slow');
	});

#### Callback function

    $('#toggleButton').click(function() {
      $('#disclaimer').slideToggle('slow', function () {
        alert('The slide has finished sliding!')
      });
    });

#### Mouseover / Mouseout

    $('td').mouseover(function () {
      $(this).css('background-color', 'rgba(255,229,0,.3)')
    });
    
    $('td').mouseout(function () {
      $(this).css('background-color', 'inherit')
    });

#### Spoiler Button

    $('.spoiler').hide();
    $('<input type="button" id="spoilerButton" value="toggle">').insertBefore('.spoiler');
    $('#spoilerButton').click(function () {
      $('.spoiler').toggle('slow');
    });