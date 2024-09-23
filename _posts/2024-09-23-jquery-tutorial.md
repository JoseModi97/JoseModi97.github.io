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