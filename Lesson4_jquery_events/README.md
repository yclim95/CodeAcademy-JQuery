#Lesson4 JQuery Events
## Review

### Combining .click() && .hover()
```javascript
$('div').hover(function(){
  $('div').addClass('green');
});
```

1. Following the pattern we have been learning, we target Krypton, our `$('div')`

2. We then apply our hover event to our target.
Finally, we execute the code inside the `function(){}` which adds a class of `green` to our target.


## Mouse & Keyboard Events

### 1. .dblclick() Event
This happend when user double click. 

```javascript
$(document).ready(function(){
  $('div').dblclick(function(){
      $(this).fadeOut('fast');
  });    
});
```

### 2. Hover
What if you wanted to create an effect when your mouse is on top of an object, then have that effect vanish when your mouse moved away? You might notice this effect in use on many site's navigation bars!

```javascript
$('div').hover(
    function(){
      $(this).addClass('highlight');
   },
   function(){
      $(this).removeClass('highlight');
   }
);
```

1. We first select the element we want to modify `$('div')`

2. Secondly notice that our `hover` effect is able to take two `functions(){}` separated by a comma. The comma is very important!

3. The first `function(){}` we pass will be run when we first mouse over our target. Here we apply a class of `highlight`

4. The second `function(){}` will be called when our mouse leaves the object. This is where we remove the class `highlight`

Your second `function(){}` doesn't have to be the opposite of the first `function(){}`, but it would be very common!


### 3. .focus

`focus` when we click on it or tab over to it. If you've ever filled out a form on a web page and seen how each text box lights up when you tab to it or click on it, you've seen focus in action!

The `.focus()` event handler only works on elements that can receive focus—the list of these elements is a bit vague, but HTML elements like `<textarea>`s and `<input>`s are the usual suspects.

**index.html**
```html
<!DOCTYPE html>
<html>
    <head>
		<title>Time to Focus!</title>
		<link rel='stylesheet' type='text/css' href='stylesheet.css'/>
		<script type='text/javascript' src='script.js'></script>
	</head>
	<body>
		<form>
			Name: <input type='text' name='name'></input>
		</form>
	</body>
</html>
```

**stylesheet.css**
```css
input {
    font-family: Verdana, Arial, Sans-Serif;
}
```

**script.js**
```javascript
$(document).ready(function(){ 
    $('input').focus(function(){
        $(this).css('outline-color', '#FF0000');
    });
});
```

### .keydown() Event

The `.keydown()` event is triggered whenever a key on the keyboard is pressed. It only works on whatever page element has focus, so you'll need to click on the window containing your div before pressing a key in order for you to see its effects.

The `.animate()` effect takes two inputs: the animation to perform, and the time in which to perform the animation. Here's an example:

**script.js**
```javascript
$(document).ready(function() {
   $('div').animate({left:'+=10px'},500);
});
```

This will take the first div it finds and move it ten pixels to the right. Remember, increasing the distance from the left margin moves something to the right; the `+=` bit is just a shorthand for "take the existing number and add ten to it." In this case, it add ten pixels to the current distance from the left margin.

**script.js**
```javascript
$(document).ready(function(){
    $(document).keydown(function(){
        $('div').animate({left:'+=10px'},500);
    });
});
```

## Main Event 
### Mario Up, Left, Right & Down 

**index.html**
```html
<!DOCTYPE html>
<html>
    <head>
    	<title>Super Mario!</title>
        <link rel='stylesheet' type='text/css' href='stylesheet.css'/>
		<script type='text/javascript' src='script.js'></script>
	</head>
	<body>
        <img src="http://i1061.photobucket.com/albums/t480/ericqweinstein/mario.jpg"/>
	</body>
</html>
```

**stylesheet.css**
```css
img {
    position: relative;
    left: 0;
    top: 0;
}
```

**script.js**
```javascript
$(document).ready(function() {
    $(document).keydown(function(key) {
        switch(parseInt(key.which,10)) {
			// Left arrow key pressed
			case 37:
				$('img').animate({left: "-=10px"}, 'fast');
				break;
			// Up Arrow Pressed
			case 38:
			    $('img').animate({top: "-=10px"}, 'fast');
				// Put our code here
				break;
			// Right Arrow Pressed
			case 39:
			    $('img').animate({left: "+=10px"}, 'fast');
				// Put our code here
				break;
			// Down Arrow Pressed
			case 40:
			    $('img').animate({top: "+=10px"}, 'fast');
				// Put our code here
				break;
		}
	});
});
```