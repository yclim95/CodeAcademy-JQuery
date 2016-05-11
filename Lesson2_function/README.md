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


## Explaination 
A `function` is made up of three parts: the function keyword, any inputs that function takes (they go between the `()`s and are separated by commas if there are more than one), and whatever actions the function should perform (these go between the `{}`s). The general form is:

```javascript
function(input1, input2, etc) {
    Do a thing
    Do another thing
    Do yet another thing!
}
```

One of the nice things about jQuery is that you can give a function just about anything as an input—even another function! That's why .ready() can take function between its parentheses; it's taking a function as input.