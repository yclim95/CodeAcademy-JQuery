#Lesson3 Dynamic HTML
## Adding & Removing HTML Elements 

### 1. Creating HTML elements

Dynamically adding elements to our HTML page is a powerful tool—it lets us modify not only the formatting, but the actual structure of our websites in response to a user's actions. For example, when you get a Gchat, each message is actually a new `<div>` being dynamically added to the page. Cool, right?

If you think about it, we've sort of done this already: all we're doing is setting a variable equal to a jQuery object. In this case, however, instead of just having something like:

```javascript
$p = $('p');
```

We'll want to pass in an entire HTML element in quotes:

```javascript
$p = $("<p>I'm a new paragraph!</p>");
```

When we put text in quotes like this, we call it a **string** (as in a "string of characters"). From now on, when we say "string," you can think "text" or "phrase." Strings are always in single or double quotes.

### 2. Inserting elements

We can insert our newly created elements using a few jQuery actions.

1. `.append()` inserts the specified element as the **last child** of the target element. 

2. `.prepend()` inserts the specified element as the **first child** of the target element. 

If we have a div of class `.info`,

```javascript
$(".info").append("<p>Stuff!</p>"); //lastChild
$(".info").prepend("<p>Stuff!</p>"); //firstChild
```

will add a paragraph containing the text "Stuff!" inside all divs of class .info. 

1. `.append()` will make the paragraph the last child of each div;

2. `.prepend()` will make the paragraph the first child of each div.

`.appendTo()` does the same as `.append()`, but it just **reverses** the order of "what to add" and "where to add it." The code

```javascript
$('<p>Stuff!</p>').appendTo('.info');
```

has the same effect as the `.append()` code above. `.prependTo()` has a similar relationship to `.prepend()`.


### 3. Before & After

```javascript
$('target').after('<tag>To add</tag>');
```

Where `'target'` is the element after which you want to add something and the bit between `<tag>`s is the HTML element you want to add. You can add `<h1`>s, `<div`>s, or any other valid HTML you like.

EG:

**index.html**
```html
<!DOCTYPE html>
<html>
	<head>
		<title>Result</title>
        <script type='text/javascript' src='script.js'></script>
	</head>
	<body>
        <div class="container">
            <h2>Greetings</h2>
            <div id="one">Div #1</div>
            <div id="two">Div #2</div>
        </div>   
	</body>
</html>
```

**script.js (JQuery)**
```javascript
$(document).ready(function(){    
    $('#one').after('<p>lala</p>');    
});
//Output
//Div #1
//lala
//Div #2
```

### 4. Moving elements around 


```javascript
var $paragraph = $("p"); // existing element
$("div").after($paragraph); // Move it!
// Same as:
$("div").after($("p"));
```

EG:

**index.html**
```html
<!DOCTYPE html>
<html>
	<head>
		<title>Result</title>
        <script type='text/javascript' src='script.js'></script>
	</head>
	<body>
        <div class="container">
            <h2>Greetings</h2>
            <div id="one">Div #1</div>
            <div id="two">Div #2</div>
        </div>   
	</body>
</html>
```

**script.js**
```javascript
$(document).ready(function(){ 
    $('#one').after('<p>lala</p>');
    $('#one').after($('p'));
    $('#two').after($('p'));
    
    //Output
    //Div #1
    //Div #2
    
    //lala
});
```

### 5. Remove Elements 
Adding elements to our HTML documents is great, but without the ability to remove them, our pages can quickly become cluttered. Thankfully, we have two jQuery functions, `.empty()` and `.remove()`, that help us delete content from our pages.

`.empty()` deletes an element's content and all its descendants. For instance, if you .`empty()` an 'ol', you'll also remove all its 'li's and their text.

`.remove()`, not only deletes an element's content, but deletes the element itself.


EG:

**index.html**
```html
<!DOCTYPE html>
<html>
	<head>
		<title>Result</title>
        <script type='text/javascript' src='script.js'></script>
	</head>
	<body>
        <div class="container">
            <h2>Greetings</h2>
            <div id="one">Div #1</div>
            <div id="two">Div #2</div>
        </div>   
	</body>
</html>
```

**script.js**
```javascript
$(document).ready(function(){
    $('#one').after('<p>lala</p>');
     $('#one').after($('p'));
     $('#two').after($('p'));
     $('p').remove();
     
     //Output
     //Div #1
     //Div #2
});
```

## Modifying Classes & Contents

### 1. Adding & Removing Classes 
Let's start with classes. jQuery includes two functions :
1. `.addClass()`
2. `.removeClass()`

that can be used to add or remove a class from an element. This is great if, for example, you have a `highlighted` class that you want to apply to an element when clicked.

The syntax looks like this:

```javascript
$('selector').addClass('className');
$('selector').removeClass('className');
```

where `'selector'` is the HTML element you want and `'className'` is the class name you want to add or remove.

**Remember:** *You aren't selecting anything, you are modifying your element. This means that you do not need `#` or `.` before your class.*

EG:

**index.html**
```html
<!DOCTYPE html>
<html>
    <head>
		<title>Highlights</title>
        <link rel='stylesheet' type='text/css' href='stylesheet.css'/>
        <script type='text/javascript' src='script.js'></script>
	</head>
	<body>
        <div id="title" class="highlighted">I'm highlighted!</div>
        <div id="text">Highlight me, too!</div>
	</body>
</html>
```

**stylesheet.css**
```css
#title {
    background-color: #C02942;
    border-radius: 5px;
    text-align: center;
    font-family: Verdana, Arial, Sans-Serif;
    color: #FFFFFF;
    width: 200px;
    height: 25px;
}

#text {
    background-color: #0B486B;
    border-radius: 5px;
    text-align: center;
    font-family: Vivaldi, Cursive;
    color: #FFFFFF;
    width: 200px;
    height: 25px;
}

.highlighted {
    -webkit-box-shadow: 0 0 8px #FFD700;
    -moz-box-shadow: 0 0 8px #FFD700;
    box-shadow: 0 0 8px #FFD700;
    cursor:pointer;
}
```

**script.js (JQuery)**
```javascript
$(document).ready(function(){    
    $('#text').click(function() {
       $(this).addClass('highlighted'); 
    });    
});
```

### 2. Toggling Classes 
`.toogleClass()` will add class and remove class & add class again if the target elements doesn't have that class & Vice-versa.

**index.html**
```html
<!DOCTYPE html>
<html>
    <head>
		<title>Highlights</title>
        <link rel='stylesheet' type='text/css' href='stylesheet.css'/>
        <script type='text/javascript' src='script.js'></script>
	</head>
	<body>
        <div id="title" class="highlighted">I'm highlighted!</div>
        <div id="text">Highlight me, too!</div>
	</body>
</html>
```

**stylesheet.css**
```css
#title {
    background-color: #C02942;
    border-radius: 5px;
    text-align: center;
    font-family: Verdana, Arial, Sans-Serif;
    color: #FFFFFF;
    width: 200px;
    height: 25px;
}

#text {
    background-color: #0B486B;
    border-radius: 5px;
    text-align: center;
    font-family: Vivaldi, Cursive;
    color: #FFFFFF;
    width: 200px;
    height: 25px;
}

.highlighted {
    -webkit-box-shadow: 0 0 8px #FFD700;
    -moz-box-shadow: 0 0 8px #FFD700;
    box-shadow: 0 0 8px #FFD700;
    cursor:pointer;
}
```

**script.js (JQuery)**
```javascript
$(document).ready(function(){    
    $('#text').click(function() {
       $(this).toggleClass('highlighted'); 
    });   
});
```

### 3. Changing your Styles
Remember `style="height:300px;` `width:300px;`"? jQuery makes it a snap!

Because resizing elements is so common, jQuery has specific `.height()` and `.width()` functions that can be used to change the heights and widths of HTML elements. For instance:

```javascript
$("div").height("100px");
$("div").width("50px");
```

would give all `<div>`s on the page a height of 100 pixels and a width of 50 pixels.

jQuery also includes a general-purpose `.css()` function that takes two inputs: the first is the CSS element to alter, and the second is the value to set it to. For example:

```javascript
$("div").css("background-color","#008800");
```
would give all `<div>`s on the page a green background color. You can modify any element's CSS attributes this way.

EG: 

```javascript
$(document).ready(function(){
    $('div').height("200px");
    $('div').width("200px");
    $('div').css('border-radius','10px');
});
```

### 4. Modifying content 
Update the contents of our HTML elements using 2 ways : -

**`1 .html()`**

```
be used to set the contents of the first element match it finds, which is the content inside `.html()`. For instance,
```

```javascript
$('div').html();
```

will get the HTML contents of the first div it finds, and

```javascript
$('div').html("I love jQuery!");
```

will set the contents of the first div it finds to "I love jQuery!"


**`2 .val()`**

```
used to get the value of form elements.
```

Example:
```javascript
$('input:checkbox:checked').val();
```

would get the value of the first checked checkbox that jQuery finds.

**index.html**
```html
<!DOCTYPE html>
<html>
	<head>
		<title>Result</title>
        <script type='text/javascript' src='script.js'></script>
	</head>
	<body>
        <p>I'm about to change!</p>   
	</body>
</html>
```

**script.js (JQuery)**
```javascript
$(document).ready(function(){
   $('p').html("jQuery magic in action!"); 
   //$('p').val("jQuery magic in action!"); 
   // I'm about to change!
});
```


## Mastering Manipulations 
### Code for To-Do List

**index.html**
```html
<!DOCTYPE html>
<html>
    <head>
    	<title>To Do</title>
        <link rel="stylesheet" type="text/css" href="stylesheet.css"/>
        <script type="text/javascript" src="script.js"></script>
	</head>
	<body>
		<h2>To Do</h2>
		<form name="checkListForm">
			<input type="text" name="checkListItem"/>
		</form>
		<div id="button">Add!</div>
		<br/>
		<div class="list"></div>
	</body>
</html>
```

**stylesheet.css**
```css
h2 {
    font-family:arial;
}

form {
    display: inline-block;
}

#button{
    display: inline-block;
    height:20px;
	width:70px;
	background-color:#cc0000;
	font-family:arial;
	font-weight:bold;
	color:#ffffff;
	border-radius: 5px;
	text-align:center;
	margin-top:2px;
}

.list {
	font-family:garamond;
	color:#cc0000;
}
```

**script.js (JQuery)**
```javscript
$(document).ready(function(){
    $('#button').click(function(){
        var toAdd = $('input[name=checkListItem]').val();
        $('.list').append('<div class="item">' + toAdd + '</div>');
    });
    
    $(document).on('click', '.item', function() {
        $(this).remove();
   });
   
   /*
   $(document).on('event', 'selector', function() {
        Do something!
    });
   */
});
```