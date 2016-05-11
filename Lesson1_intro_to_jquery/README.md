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
