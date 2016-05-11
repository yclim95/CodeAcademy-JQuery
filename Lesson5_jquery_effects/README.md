#Lesson5 JQuery Effects
## More on JQuery Effects

### 1. .animate()
If we wanted to move a div 10 pixels down, we'd type something like

```javascript
$('div').animate({top:'+=10px'},500);
```

Where the bit between curly braces says "hey, jQuery! Add 10 pixels to the current top margin," and the second input says "do it in 500 milliseconds!" (1,000 milliseconds = one second.)

### 2. Intro to JQuery UI 
jQuery UI includes a number of ultra-fancy animations you can use to make your websites do incredible things.

For instance, remember when we lamented that jQuery didn't include a `.blowUp()` effect for our planet Krypton? Well, that's still true. But jQuery UI has an `.effect()` effect, and we are totally going to give it the input `'explode'`.

Note that we've included an extra `<script>` tag in our HTML documents; this is used to include jQuery UI in our webpages. We don't have to do this with regular jQuery, since Codecademy automatically includes it for us.


```javascript
$(document).ready(function(){
   $('div').click(function(){
       $(this).effect('explode');
    }); 
});
```

[Check Out JQuery UI Documentation Here](https://jqueryui.com/)

**Note:** *To use JQuery UI effect, include jquery-ui script*. 


### 3. .bounce()
We give this as an input to `.effect()` just like `'explode'`, but we add an extra input to tell it how many times to bounce. This code will make our target `'div'`s bounce twice in 200 milliseconds:

```javascript
$('div').effect('bounce', {times:2}, 200);
```

### 4. .slide()

**index.html**
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Krypton Redux</title>
		<link rel='stylesheet' type='text/css' href='stylesheet.css'/>
        <script type='text/javascript' src='script.js'></script>
        <script src="//ajax.googleapis.com/ajax/libs/jqueryui/1.9.1/jquery-ui.min.js"></script>
	</head>
	<body>
		<div></div>
	</body>
</html>
```

**stylesheet.css**
```css
body {
    background-image: url('http://bit.ly/UpQgJ6');
    repeat: no-repeat;
}

div {
    height: 100px;
    width: 100px;
    border-radius: 100%;
    background-color: #008800;
    background-image: -webkit-gradient(linear, 0% 0%, 0% 100%, from(#003500), to(#008800));
    background-image: -webkit-linear-gradient(left, #003500, #008800); 
    background-image:    -moz-linear-gradient(left, #003500, #008800);
    background-image:     -ms-linear-gradient(left, #003500, #008800);
    background-image:      -o-linear-gradient(left, #003500, #008800);
}
```

**script.js**
```javascript
$(document).ready(function(){
   $('div').click(function(){
       $(this).effect('slide');
    }); 
});
```

## JQuery UI Interactions 
### 1. .accordion (menu)

**index.html**
```html
<!DOCTYPE html>
<html>
    <head>
    	<title>Behold!</title>
        <link rel='stylesheet' type='text/css' href='http://code.jquery.com/ui/1.9.1/themes/base/jquery-ui.css'/>
        <script type='text/javascript' src='script.js'></script>
        <script src="//ajax.googleapis.com/ajax/libs/jqueryui/1.9.1/jquery-ui.min.js"></script>
	</head>
	<body>
        <div id="menu">
            <h3>jQuery</h3>
            <div>
                <p>jQuery is a JavaScript library that makes your websites look absolutely stunning.</p>
            </div>
            <h3>jQuery UI</h3>
            <div>
                <p>jQuery UI includes even more jQuery goodness!</p>
            </div>
            <h3>JavaScript</h3>
            <div>
                <p>JavaScript is a programming language used in web browsers, and it's what powers jQuery and jQuery UI. You can learn about JavaScript in the <a href="http://www.codecademy.com/tracks/javascript" target="blank" style="text-decoration:none; color:#F39814">JavaScript track</a> here on Codecademy.</p>
            </div>
        </div>
	</body>
</html>
```

**script.js**
```javascript
$(document).ready(function() {
    $("#menu").accordion({collapsible: true, active: false
	});
});
```

### 2. .draggable()

**index.html**
```html
<!DOCTYPE html>
<html>
	<head>
		<title></title>
        <link rel='stylesheet' type='text/css' href='stylesheet.css'/>
        <script type='text/javascript' src='script.js'></script>
        <script src="//ajax.googleapis.com/ajax/libs/jqueryui/1.9.1/jquery-ui.min.js"></script>
	</head>
	<body>
        <div id="car">
            <div id="top"></div>
            <div id="bottom"></div>
            <div id="fwheel"></div>
            <div id="bwheel"></div>
        </div>   
	</body>
</html>
```

**stylesheet.css**
```css
#top {
    position: relative;
    height: 50px;
    width: 50px;
    border-radius: 5px;
    background-color: #cc0000;
    left: 25px;
}
#bottom {
	position: relative;
	height:25px;
	width: 100px;
	background-color: #cc0000;
	border-top-left-radius: 5px;
	border-top-right-radius: 5px;
	top: -25px;
}
#fwheel {
	position: relative;
	height:20px;
	width:20px;
	border-radius: 100%;
	background-color: black;
	top: -35px;
	left: 5px;
}
#bwheel {
	position: relative;
	height:20px;
	width:20px;
	border-radius: 100%;
	background-color: black;
	top: -55px;
	left: 75px;
}
```

**script.js**
```javascript
$(document).ready(function(){
  $('#car').draggable();
});
```

### 3. .resizeable()
Resize to fit ALL

**script.js**
```javascript
$(document).ready(function(){
  $('div').resizable();    
});
```

### 4. .selectable()
A Greater selection 

**index.html**
```html
<!DOCTYPE html>
<html>
	<head>
		<title>Select Ye Favorite</title>
        <link rel='stylesheet' type='text/css' href='stylesheet.css'/>
        <script type='text/javascript' src='script.js'></script>
        <script src="//ajax.googleapis.com/ajax/libs/jqueryui/1.9.1/jquery-ui.min.js"></script>
	</head>
	<body>
        <ol>
            <li>Super Mario Bros.</li>
            <li>Tetris</li>
            <li>Legend of Zelda: Link's Awakening</li>
            <li>Kirby's Dream World</li>
            <li>Burger Time</li>
            <li>Pokémon Red</li>
            <li>Pokémon Blue</li>
        </ol>   
	</body>
</html>
```

**stylesheet.css**
```css
ol {
    list-style-type: none;
	position: relative;
	left: -20px;
}

ol li {
	background: #eeeeee;
	border-radius: 5px;
	border: 1px solid black;
	margin: 3px;
	padding: 0.4em;
	font-size: 1em;
	height: 16px;
	font-family: Verdana, Arial, Sans-Serif;
}

ol .ui-selected {
	background: #F39814; color: white;
}
```

**script.js**
```javascript
$(document).ready(function(){
    $('ol').selectable();
});
```

### 5. .sortable()
Reorder the elements in our list

In the script.js tab, replace your `.selectable()` with a `.sortable()`. 

**script.js**
```javascript
$(document).ready(function(){
    $('ol').sortable();
});
```