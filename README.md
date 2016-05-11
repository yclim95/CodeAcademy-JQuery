#CodeAcademy-JQuery
## Intro to JQuery 

So far, we've built web pages using HTML and styled them using CSS. Our pages look great, but they're not interactive —we can't drag elements around the page, open and close sliding panels, animate HTML elements, or add new elements to our HTML pages simply by clicking a button.

All that's about to change, though. In this track, you're going to learn **jQuery**, which will allow you to do all these things and more.

**index.html**
```html
<!DOCTYPE html>
<html>
    <head>
        <link rel="stylesheet" type="text/css" href="stylesheet.css"/>
        <script type="text/javascript" src="script.js"></script>
    </head>
    <body>
        <div id="red"></div>
        <div id="blue"></div>
        <div id="yellow"></div>
        <div id="green"></div>
    </body>
</html>
```

**stylesheet.css**
```css
div {
    height:100px;
    width:100px;
    display: inline-block;
}

#red {
    background-color:#FF0000;
}

#blue {
    background-color:#0000FF;
}

#yellow {
    background-color:#E2BE22;
}

#green {
    background-color:#008800;
}
```

**script.js (JQuery)**
```javascript
$(document).ready(function() {
   $('div').mouseenter(function() {
       $(this).animate({
           height: '+=10px'
       });
   });
   $('div').mouseleave(function() {
       $(this).animate({
           height: '-=10px'
       }); 
   });
   $('div').click(function() {
       $(this).toggle(1000);
   }); 
});
```

## What is JQuery ? 

jQuery is a **library**, or set of helpful add-ons, to the **JavaScript** programming language. It may seem counterintuitive to learn how to use a library before learning the actual language, but there are a few good reasons for this.

1. It takes a while to become comfortable with JavaScript, and it's trickier to manipulate HTML elements directly with JavaScript than with jQuery. In order to help you build awesome websites faster, we're starting you off with jQuery.

2. jQuery provides a simple interface for the underlying JavaScript. It's easier for many users to learn jQuery first, then dive into the nitty-gritty JavaScript details later.

3. jQuery is much better at giving you immediate, visual results than regular JavaScript. By the end of this lesson, you'll have built your own interactive button!
