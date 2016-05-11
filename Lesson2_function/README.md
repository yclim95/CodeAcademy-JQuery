#Lesson2 Function & Selector
**Functions** are the basic unit of action in jQuery. The main entry point of most jQuery applications is a block of code that looks like this:

```javascript
$(document).ready(function() {
    Do something
});
```

1. `$(document)` is a jQuery object. The $() is actually a function in disguise; it turns the document into a jQuery object.

2. `.ready()` is a type of function; you can think of it as sort of a helper that runs the code inside its parentheses as soon as the HTML document is ready.

3. `function(){}` is the action that .ready() will perform as soon as the HTML document is loaded. (In the above example, the Do something placeholder is where those actions would go.)


## 1. Explaination 
A `function` is made up of three parts: the function keyword, any inputs that function takes (they go between the `()`s and are separated by commas if there are more than one), and whatever actions the function should perform (these go between the `{}`s). The general form is:

```javascript
function(input1, input2, etc) {
    Do a thing
    Do another thing
    Do yet another thing!
}
```

One of the nice things about jQuery is that you can give a function just about anything as an input—even another function! That's why .ready() can take function between its parentheses; it's taking a function as input.

## 2. Variable

Variables are a place for us to store information for use at a later time. Variables can hold any type of information you work with, so just think of them as containers.

The single `=` sign is used to **assign** values. For instance, in jQuery, you can write

```javascript
var lucky = 7;
var name = "Codecademy";
var $p = $('p');
```

Our first variable contains a number, 7, while the second variable contains some text, "Codecademy". Our 3rd **variable** stores the result of a jQuery selector `$('p')` in the variable `$p` . As you can see, this is just a handy way to save this information for later.

Why would we do this? Well, up until now we haven't had to modify anything more than once. If we wanted to change the webpage based on new information, we would need to store that information in variables. Maybe you want to create a loading page and have it vanish as you receive that information. It'd be a good idea to use variables.

## 3. $p VS $('p')

```javascript
var $p = $('p');
```

There's a subtle difference between the two.

`$p` is just a variable name. There is no magic associated with the `$` in `$p`; it's just a convention for saying, "hey, this variable contains a jQuery object." We could call $p anything we want: $paragraph, paragraph, space_cows, whatever! It's just helpful for people reading our code to see `$p`, since this is a concise way of saying "hey, there's a `'p'` jQuery object in here."

`$()`, on the other hand, is magic. This is the function in disguise that creates jQuery objects. If you're making a jQuery object, you gotta use it!

## Using Selector 
### 1. Using Functions o select HTML Elements

Now that you know more about how functions work, you understand that when we have something like

```javascript
$(document).ready(function() {
    $('div').hide();
});
```
we're passing `.ready()` a function (which itself takes no inputs; that's why its `()` are empty) and that function's job is to `.hide()` the div jQuery object.

### 2. Selecting by Class
In CSS, we have class and ID. We can put any CSS selector in quotes and pass it into $(). This means we can select classes, too!

Recall that we can select classes in CSS by using a dot (`.`). If we have class="red" in our HTML, we can target it in CSS with .red. In jQuery, all we need to do is put `'.red'` in quotes, and we can pass it to $() to make a jQuery object.

```javascript
$(document).ready(function() {
    $('.red').click(function(){
        //Do something
    });
});
```

### 2. Selecting by ID
Instead of using . for classes, we need the # for IDs. We could target id="header" like so:

```javascript
$('#header');

```

### 3. Flexible selection 
Anything you can target with CSS, you can modify with jQuery. For example, we can apply a `fadeTo()` to a `p` selector like this:

```javascript
$('p').fadeTo('slow', 0);
```

We can apply a `fadeTo()` to an `li` selector like this:

```javascript
$('li').fadeTo('slow', 0);
```

We can apply a `fadeTo()` to both the `p` and `li` selectors like this:

```javascript
$('p, li').fadeTo('slow', 0);
```

### 4. This keyword

```javascript
$(document).ready(function() {
    $('div').click(function() {
        $(this).fadeOut('slow');
    });
});
```

The `this` keyword refers to the jQuery object you're currently doing something with. Its complete rules are a little tricky, but the important thing to understand is if you use an **event handler** on an element—that's the fancy name for actions like `.click()` and `.mouseenter()`, since they handle jQuery events—you can call the actual event that occurs (such as `fadeOut()`) on `$(this)`, and the event will only affect the element you're currently doing something with (for example, clicking on or mousing over).


### 5. Toggling Our Panel 
Use `.click()` & `.slideToggle()` .

**index.html**
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Slide Panel</title>
        <script type="text/javascript" src="script.js"></script>
        <link rel="stylesheet" type="text/css" href="stylesheet.css"></link>
    </head>
    <body>
        <div class="panel">
        <br />
        <br />
        <p>Now you see me!</p>
        </div>
        <p class="slide"><div class="pull-me">Slide Up/Down</div></p>
    </body>
</html>
```

**stylesheet.css**
```css
body {
    margin:0 auto;
    padding:0;
	width:200px;
    text-align:center;
}
.pull-me{
    -webkit-box-shadow: 0 0 8px #FFD700;
    -moz-box-shadow: 0 0 8px #FFD700;
    box-shadow: 0 0 8px #FFD700;
    cursor:pointer;
}
.panel {
	background: #ffffbd;
    background-size:90% 90%;
    height:300px;
	display:none;
    font-family:garamond,times-new-roman,serif;
}
.panel p{
    text-align:center;
}
.slide {
	margin:0;
	padding:0;
	border-top:solid 2px #cc0000;
}
.pull-me {
	display:block;
    position:relative;
    right:-25px;
    width:150px;
    height:20px;
	font-family:arial,sans-serif;
    font-size:14px;
	color:#ffffff;
    background:#cc0000;
	text-decoration:none;
    -moz-border-bottom-left-radius:5px;
    -moz-border-bottom-right-radius:5px;
    border-bottom-left-radius:5px;
    border-bottom-right-radius:5px;
}
.pull-me p {
    text-align:center;
}
```

**script.js** (JQuery)
```javascript
$(document).ready(function(){
    
 $('.pull-me').click(function(){
   $('.panel').slideToggle('slow');    
 });   
 
});
```