#Lesson1 Intro to JQuery
## Manipulating HTML 

### 1. Document Object Model (DOM)

An HTML document is structured according to the **Document Object Model**, or **DOM**. It's by interacting with the DOM that jQuery is able to access and modify HTML.

The DOM consists of every element on the page, laid out in a hierarchical way that reflects the way the HTML document is ordered. Remember how we could think of the HTML document as a tree? You can think of the DOM the same way. Just as with an HTML document, elements in the DOM can have parents, children, and siblings.

E.g : 

```javascript
$(document).ready(function() {
    $('div').fadeOut(1000);
});
```

### 2. Changing Targets

Don't be intimidated by the amount of code you're seeing—we'll go through it piece by piece to make sure you understand it thoroughly.

Just like the CSS `div` refers to the HTML element `<div>`, the jQuery 'div' refers to the same HTML element `<div>`. You can think of the element name passed to jQuery as identical to the CSS element, only wrapped in quotes. So, for instance, you could target anything of class `button` with

```javascript
$('.button').someAction
```

As you'll remember, `.button` in your CSS file is how you'd target anything of `class="button"`in your HTML file.


## Mastery JQuery Syntax
### 1. Linking HTML & Javascript Files
Just like we need a `<link>` tag to connect our HTML and CSS, we need a `<script>` tag to connect our HTML and jQuery. The tag looks like this:

```html
<script type="text/javascript" src="script.js"></script>
```
**Note :** the `<script>` tag is not self-closing; it requires a closing `</script>` tag. **

### 2. Getting Started 

Next, we'll need to start up our jQuery magic using the `$(document).ready();` syntax you've seen. It works like this:

1. `$()` says, "hey, jQuery things are about to happen!"

2. Putting `document` between the parentheses tells us that we're about to work our magic on the HTML document itself.

3. `.ready()`; is a function, or basic action, in jQuery. It says "hey, I'm going to do stuff as soon as the HTML document is ready!"

4. Whatever goes in `.ready()`'s parentheses is the jQuery event that occurs as soon as the HTML document is ready.
So,

```javascript
$(document).ready(something);
```

says: "when the HTML document is ready, do `something`!" (We'll show you how to replace `something` with an action in the next exercise.)

**Note :** that `.ready();` ends with a semicolon. This tells jQuery that you're done giving it a command.


### 3. Functional Approach 

Perfect! Now we need to put something inside our `ready()` function.

Remember, when we say "function," you can think "action." Functions are the basic unit of doing work in jQuery.

For this reason, jQuery includes a `function` keyword. The syntax looks like this:

```javascript
function(){
    jQuery magic;
}
```

If we add our function inside our `.ready()`, jQuery will run the code in our function as soon as the HTML document loads. The syntax would then look like this:

```javascript
$(document).ready(function() {
    jQuery magic;
});
```

### 3. Slide down effect

Between the {}s of our function(), we'll want to turn our div into a jQuery object so jQuery can manipulate it. Much like we use .ready() on $(document), we'll use the .slideDown() action on our div jQuery object.

Inside .slideDown's parentheses, we'll want to tell it how quickly to slide down. Let's enter 'slow' (include the quotes). 

EG :
```javascript
$(document).ready(function(){
  $('div').slideDown('slow');
});
```


## Review 
1. What jQuery is and how it can manipulate HTML elements

2. jQuery syntax

## More Practice 
### More Effects 

Great! Next, let's include our function keyword and two new actions together, mouseenter() and fadeTo().

### 1. Go In 
mouseenter() does what you might expect: it produces a change when your mouse enters a given HTML element. For example,

```javascript
$(document).ready(function() {
    $('div').mouseenter(function() {
        $('div').hide();
    });
});
```

would hide every `<div>` on the page as soon as you mouse over one. (We'll find out how to affect just one `<div>` among many in the next lesson.) For now, we only have one `<div>`, so this setup is okay.

Instead of `hide()`, however, we'll place `fadeTo()` inside `mouseenter()`. `fadeTo()` takes two **arguments**, or **inputs**, between its parentheses, separated by a comma: the speed at which to fade, and the **opacity** (or transparency) to fade to. For example,

```javascript
fadeTo('fast', 0.25);

```

would quickly fade the target element to 25% of its original opacity, making it very light-colored.

### 2. Exit (mouseLeave) 


```javascript
$(document).ready(function() {
    $('div').mouseenter(function() {
        $('div').fadeTo('fast', 1);
    });
    
     $('div').mouseleave(function() {
        $('div').fadeTo('fast', 0.5);
    });
});
```