---
title: JQuery Bible
description:  A short tutorial on how to use Jquery
author: modi
date: 2024-09-23 10:14 +0800
categories: [JQuery, Setup]
tags: [jquery-setup]
pin: true
math: true
mermaid: true
---

### index.html

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    
</body>
</html>

```

### `custom.js`

```javascript
"use strict"
```

### document ready function
This function is used to check if the document is done loading. The following is longhand and shorthand version of the implementation

`custom.js`
```javascript
"use strict"

//Longhand Version
$(document).ready(function(){
console.log('I am Ready')
});

//Shorthand Version
$(function(){

});
```

### Element Selector

A guide on how to select a html element from jquery which is an easier approach than javascript

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <div>
        Hello World
    </div>    
    <p>Paragraph</p>
</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
$("div").click(function(){
    console.log("Div is Clicked");
});

$("p").click(function(){
    console.log("P is Clicked");
});
});
```


### All Element Selector

```javascript
$(document).ready(function(){
$("*").click(function(){
    console.log("All element Selector");
})
});
```

### this keyword

this is only applied to the element that caused the trigger. Lets say we have set a selector for all divtags and we want to modify one divtag at a time like hide each divtag we click, we can usethis keyword to do so

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <div>
        Hello World
    </div>    
    <p>Paragraph</p>
<div> Second Div</div>   
</body>
</html>
```


```javascript
"use strict"


$(document).ready(function(){
$("div").click(function(){
    console.log("Div is Clicked");

    console.log($(this));

    $(this).hide()
});
});
```


## Class Selector


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <div class="epicClass">
        Hello World
    </div>    
    <p id="HW" class="epicClass">Paragraph</p>
<div> Second Div</div>   
</body>
</html>
```

if you click on Paragraph, you will get two console messages as it has id HW and class epicClass. Second Div will not react. Hello World will trigger only one message as it has id HW
```javascript
"use strict"


$(document).ready(function(){
$("#HW").click(function(){
    console.log("HW is Clicked");
});

$(".epicClass").click(function(){
    console.log("Epic Class is Clicked");
});

});
```

### multipleitems selector

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <div class="epicClass">Hello World</div>    
    <p id="HW">Paragraph</p>
    <div class="epicClass"> Second Div</div>   
</body>
</html>
```

```javascript
"use strict"

$(document).ready(function(){
$("#HW, .epicClass").click(function(){
    console.log("Awesome click 2.0");
});
});
```

### select first element with same property e.g class

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <div class="epicClass">Hello World</div>    
    <p id="HW">Paragraph</p>
    <div class="epicClass"> Second Div</div>   
</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
$("#HW, .epicClass:first").click(function(){
    console.log("Awesome click first element");
});
});
```

### oddeven

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>

    <table border = "1">
        <tr>
            <th>Superhero</th>
            <th>Franchise</th>
        </tr>
        <tr>
            <td>Batman</td>
            <td>DC</td>
        </tr>
        <tr>
            <td>Yoda</td>
            <td>Start Wars</td>
        </tr>
        <tr>

            <td>Thanos</td>
            <td>Marvel Comics</td>
        </tr>

<tr>

            <td>Little Ani</td>
            <td>Start Wars</td>
        </tr>
    </table>
</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
$("tr:odd").css( "background-color", "red");

$("tr:even").css( "background-color", "yellow");

});

```


### Element and Class Selector

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <div class="epicClass">Element 1</div>    
    <p>Paragraph 1</p>
    <p class="epicClass">Paragraph 2</p>
    <div class="epicClass"> Element 2 </div>   
    <div class="epicClass"> Element 3</div>   
    <div class="epicClass"> Element 4</div>   
    <div class="epicClass"> Element 5</div>   
    
</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
$("p.epicClass").click(function(){
    console.log(" Element and Class Selector");
});
});
```

### Children selector

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <div>
        <span>Span 1</span>
        <span>Span 2</span>
        <span>Span 3</span>
        <p>
            <span>Span Uber</span>
        </p>
    </div>

    <div>
        <span>Span 4</span>
    </div>
</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
$("div > span").css("color", "red")

$("div").css("font-size", "20px")
});
```

### target Selector

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <div target="_blank">Element 1</div>
    <div target="_blank">Element 2</div>
    <div target="hello">Element 3</div>
    <div>Element 4</div>
    <div>Element 5</div>
</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
$("div[target='_blank']").click(function(){
    console.log("Target is blank");
})

});
```


### Type (Input) Selector

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <input type="text" name="" id="" >
    <input type="text" name="" id="" >
    <input type="button" value="Button 1">
    <input type="button"  value="Button 2">
    <input type="button"  value="Button 3">
</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
$(":button").click(function(){
    console.log("Button is clicked");
});

$(":input").click(function(){
    console.log("input is clicked");
});

});
```

### contains selector

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    <p>Hello world</p>
    <p>My name is Frahaan</p>
    <p>I live on planet Earth</p>
    <p>I am 26 years old</p>
    <p>My alter ego is batman</p>
</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
$("p:contains(i)").css("background-color", "yellow")

$("p:contains(My)").css("background-color", "red")

});
```

### fetch html attribute

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    
<div title="Hello World">I am Awesome</div>

</body>
</html>
```

```javascript

"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);

});

```

### Set html attribute

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script type="text/javascript" src="custom.js"></script>
</head>
<body>
    
<div title="Hello World">I am Awesome</div>


<button id="EpicButton">Click Me</button>

</body>
</html>

```

```javascipt
"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);


$("#EpicButton").click(function(){
    $("div").attr("title", "Epic Div")
    console.log(titleVar);
})

});
```

