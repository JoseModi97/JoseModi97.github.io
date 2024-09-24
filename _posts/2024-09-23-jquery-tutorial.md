---
title: JQuery Bible
description:  A short tutorial on how to use Jquery
author: modi
date: 2024-09-23 10:14 +0800
categories: [JQuery, FullTutorial]
tags: [jquery-notes]
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
## Chapter 1 - Introduction
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

## Chapter 2: Selectors
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


### Class Selector


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

### oddeven selector

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


## Chapter 3: Attributes
### Get Attribute

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

### Set Attributes

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

### Set Attribute With Callback Function

`usecase 1`

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

<div title="Hello World">I am Awesome</div>


<button id="EpicButton">Click Me</button>

</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);


$("#EpicButton").click(function(){
    $("div").attr("title", function(i, originalValue){
        console.log(i)
        console.log(originalValue)
        return "New Title";
    })
})

});
```


`usecase 2`

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

```javascript
"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);


$("#EpicButton").click(function(){
    $("div").attr("title", function(i, originalValue){
        return  i + 100;
    })
})

});
```


### Set Multiple Attributes

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
    
<div title="Hello World" epicAttr="Epic Value">I am Awesome</div>


<button id="EpicButton">Click Me</button>

</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);


$("#EpicButton").click(function(){
    $("div").attr({
        "title" : "Goku",
        "epicAttr" : "Yoda"
    })
})

});
```


### Remove attributes from elements

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


```javascript
"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);


$("#EpicButton").click(function(){
$("div").removeAttr("title");
});

});
```


### Text Attribute
get and set text of an element
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

```javascript
"use strict"


$(document).ready(function(){


$("#EpicButton").click(function(){

// get a text value
console.log($("div").text());

//change text of html element

$("div").text("Awesome Stuff");
});

});
```

### Data Attribute
set and retrieve data values
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
    
<div id="AwesomeDiv" data-name="Frahaan" data-age="26">I am Awesome</div>

<button id="EpicButton">Click Me</button>

</body>
</html>
```


```javascript
"use strict"


$(document).ready(function(){


$("#EpicButton").click(function(){

var name = $("div").data("name");
var age = $("div").data("age");

//Fetch data values
console.log(name)
console.log(age)

//Set data values

$("div").data("name", "BATMAN");

var name = $("div").data("name");

console.log(name)
console.log(age)

});
});
```


`Get and Set Values on input html fields`

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
    
<input type="text" id="SimpleId" value="Awesome Input">

<button id="EpicButton">Click Me</button>

</body>
</html>
```


```javascript
"use strict"


$(document).ready(function(){


$("#EpicButton").click(function(){

var val = $("#SimpleId").val();

console.log(val);

$('#SimpleId').val('Batman is Coming');

});
});
```

### HTML Value

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
    <p>Hello World</p>
</div>

<button id="EpicButton">Click Me</button>

</body>
</html>
```


```javascript
"use strict"


$(document).ready(function(){


$("#EpicButton").click(function(){


// console.log($("div").text());
console.log($("div").html());

// $("div").text("Awesome stuff")
$("div").html("<b>You are a bold one.</b>")

});
});
```


### Class
hasClass, removeClass, toggleClass, addClass

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
    
    <p class="epicClass">Hello World</p>
    <p class="epicClass">Hello World</p>
    <p id="EpicID">Hello World</p>

<button id="RemoveClass">Remove Class</button>
<button id="ToggleClass">Toggle Class</button>
<button id="AddClass">Add Class</button>

</body>
</html>
```

```javascript
"use strict"


$(document).ready(function()
{$("p").click(function(){
    var result = $("p").hasClass("epicClass")
    console.log(result)
});


$("#EpicID").click(function(){
    var result = $("#EpicID").hasClass("epicClass")
    console.log(result)
});



$("#RemoveClass").click(function(){

$("p").removeClass();

});


$("#ToggleClass").click(function(){

$("p").toggleClass("epicClass");

});

$("#AddClass").click(function(){

$("p").addClass("addedClass");

});
});
```

## Chapter 4: Events
### Binding and Unbinding


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
    
    <p class="epicClass">Hello World</p>

    <button id="BindButton">Bind Button</button>

</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {
    // Initial bind to paragraphs

    function AfterBind(event){
        console.log("After Bind Function")
    }
    $("p").bind("click", function() {
        console.log("Before Bind");
    });

    // Bind button click event
    $("#BindButton").click(function() {
        // Unbind the previous click event from paragraphs
        $("p").unbind("click");

        // Bind a new click event to paragraphs
        // $("p").bind("click", function(event) {
        //     console.log("After Bind");
        // });


        $("p").bind("click", function(event) {
            AfterBind(event)
        });
    });
});

```

### Attributes


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
    
    <p class="epicClass">Hello World</p>
</body>
</html>

```
```javascript
"use strict";

$(document).ready(function() {

    $("p").bind("click", function(event) {
        console.log(event);
        console.log(event.pageX+ " : " + event.pageY);
    });
});

```



### Propagation 
Propagation is when a child element inherits the event of the parent element when it occurs. 
: In order to prevent propagation, you can use the following function
```javascript
event.preventPropagation()
```

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
    
    <div id="Red" style="background-color: red; height: 200px">
        Red Box
        <div id="Yellow" style="background-color: yellow; width: 100px">Yellow Box</div>
    </div>
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

    $("#Red").click(function(){
        console.log("Red Button Clicked")
    })

    $("#Yellow").click(function(event){
        console.log("Yellow Button Clicked")
        event.stopPropagation();
    })
});

```

### Prevent Default

This function is for preventing the default nature of html submit button that results in refreshing of the page and going to the web location of the action

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
    <form action="account.html">
        <input type="text" name="" id="" placeholder="Enter username">
        <br/>
        <input type="password" name="" id="" placeholder="Enter password">
        <br/>
        <input id="SubmitButton" type="submit" value="Submit">
    </form>
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

    $("#SubmitButton").click(function(event){
        event.preventDefault();
    })
});

```

### Mouse Single Click

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
    <div>1</div>
    <div>2</div>
    <div>3</div>

    <p id="EpicId">Epic Paragraph</p>
</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {

    $("div").click(function(event){
        console.log("A div is clicked")
    })


    $("#EpicId").click(function(event){
        alert("Epic Id Alert")
    })

});

```

### Mouse Double Click

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
    <div>1</div>
    <div>2</div>
    <div>3</div>

</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {
    
    $("div").dblclick(function(event){
        console.log("Double Click")
    })

});

```

### Mouse Enter Event

---
title: JQuery Bible
description:  A short tutorial on how to use Jquery
author: modi
date: 2024-09-23 10:14 +0800
categories: [JQuery, FullTutorial]
tags: [jquery-notes]
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
## Chapter 1 - Introduction
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

## Chapter 2: Selectors
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


### Class Selector


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

### oddeven selector

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


## Chapter 3: Attributes
### Get Attribute

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

### Set Attributes

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

### Set Attribute With Callback Function

`usecase 1`

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

<div title="Hello World">I am Awesome</div>


<button id="EpicButton">Click Me</button>

</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);


$("#EpicButton").click(function(){
    $("div").attr("title", function(i, originalValue){
        console.log(i)
        console.log(originalValue)
        return "New Title";
    })
})

});
```


`usecase 2`

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

```javascript
"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);


$("#EpicButton").click(function(){
    $("div").attr("title", function(i, originalValue){
        return  i + 100;
    })
})

});
```


### Set Multiple Attributes

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
    
<div title="Hello World" epicAttr="Epic Value">I am Awesome</div>


<button id="EpicButton">Click Me</button>

</body>
</html>
```

```javascript
"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);


$("#EpicButton").click(function(){
    $("div").attr({
        "title" : "Goku",
        "epicAttr" : "Yoda"
    })
})

});
```


### Remove attributes from elements

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


```javascript
"use strict"


$(document).ready(function(){
var titleVar = $("div").attr("title");

console.log(titleVar);


$("#EpicButton").click(function(){
$("div").removeAttr("title");
});

});
```


### Text Attribute
get and set text of an element
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

```javascript
"use strict"


$(document).ready(function(){


$("#EpicButton").click(function(){

// get a text value
console.log($("div").text());

//change text of html element

$("div").text("Awesome Stuff");
});

});
```

### Data Attribute
set and retrieve data values
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
    
<div id="AwesomeDiv" data-name="Frahaan" data-age="26">I am Awesome</div>

<button id="EpicButton">Click Me</button>

</body>
</html>
```


```javascript
"use strict"


$(document).ready(function(){


$("#EpicButton").click(function(){

var name = $("div").data("name");
var age = $("div").data("age");

//Fetch data values
console.log(name)
console.log(age)

//Set data values

$("div").data("name", "BATMAN");

var name = $("div").data("name");

console.log(name)
console.log(age)

});
});
```


`Get and Set Values on input html fields`

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
    
<input type="text" id="SimpleId" value="Awesome Input">

<button id="EpicButton">Click Me</button>

</body>
</html>
```


```javascript
"use strict"


$(document).ready(function(){


$("#EpicButton").click(function(){

var val = $("#SimpleId").val();

console.log(val);

$('#SimpleId').val('Batman is Coming');

});
});
```

### HTML Value

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
    <p>Hello World</p>
</div>

<button id="EpicButton">Click Me</button>

</body>
</html>
```


```javascript
"use strict"


$(document).ready(function(){


$("#EpicButton").click(function(){


// console.log($("div").text());
console.log($("div").html());

// $("div").text("Awesome stuff")
$("div").html("<b>You are a bold one.</b>")

});
});
```


### Class
hasClass, removeClass, toggleClass, addClass

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
    
    <p class="epicClass">Hello World</p>
    <p class="epicClass">Hello World</p>
    <p id="EpicID">Hello World</p>

<button id="RemoveClass">Remove Class</button>
<button id="ToggleClass">Toggle Class</button>
<button id="AddClass">Add Class</button>

</body>
</html>
```

```javascript
"use strict"


$(document).ready(function()
{$("p").click(function(){
    var result = $("p").hasClass("epicClass")
    console.log(result)
});


$("#EpicID").click(function(){
    var result = $("#EpicID").hasClass("epicClass")
    console.log(result)
});



$("#RemoveClass").click(function(){

$("p").removeClass();

});


$("#ToggleClass").click(function(){

$("p").toggleClass("epicClass");

});

$("#AddClass").click(function(){

$("p").addClass("addedClass");

});
});
```

## Chapter 4: Events
### Binding and Unbinding


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
    
    <p class="epicClass">Hello World</p>

    <button id="BindButton">Bind Button</button>

</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {
    // Initial bind to paragraphs

    function AfterBind(event){
        console.log("After Bind Function")
    }
    $("p").bind("click", function() {
        console.log("Before Bind");
    });

    // Bind button click event
    $("#BindButton").click(function() {
        // Unbind the previous click event from paragraphs
        $("p").unbind("click");

        // Bind a new click event to paragraphs
        // $("p").bind("click", function(event) {
        //     console.log("After Bind");
        // });


        $("p").bind("click", function(event) {
            AfterBind(event)
        });
    });
});

```

### Attributes


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
    
    <p class="epicClass">Hello World</p>
</body>
</html>

```
```javascript
"use strict";

$(document).ready(function() {

    $("p").bind("click", function(event) {
        console.log(event);
        console.log(event.pageX+ " : " + event.pageY);
    });
});

```



### Propagation 
Propagation is when a child element inherits the event of the parent element when it occurs. 
: In order to prevent propagation, you can use the following function
```javascript
event.preventPropagation()
```

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
    
    <div id="Red" style="background-color: red; height: 200px">
        Red Box
        <div id="Yellow" style="background-color: yellow; width: 100px">Yellow Box</div>
    </div>
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

    $("#Red").click(function(){
        console.log("Red Button Clicked")
    })

    $("#Yellow").click(function(event){
        console.log("Yellow Button Clicked")
        event.stopPropagation();
    })
});

```

### Prevent Default

This function is for preventing the default nature of html submit button that results in refreshing of the page and going to the web location of the action

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
    <form action="account.html">
        <input type="text" name="" id="" placeholder="Enter username">
        <br/>
        <input type="password" name="" id="" placeholder="Enter password">
        <br/>
        <input id="SubmitButton" type="submit" value="Submit">
    </form>
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

    $("#SubmitButton").click(function(event){
        event.preventDefault();
    })
});

```

### Mouse Single Click

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
    <div>1</div>
    <div>2</div>
    <div>3</div>

    <p id="EpicId">Epic Paragraph</p>
</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {

    $("div").click(function(event){
        console.log("A div is clicked")
    })


    $("#EpicId").click(function(event){
        alert("Epic Id Alert")
    })

});

```

### Mouse Double Click

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
    <div>1</div>
    <div>2</div>
    <div>3</div>

</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {
    
    $("div").dblclick(function(event){
        console.log("Double Click")
    })

});

```

### Mouse Enter Element


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
    <div>1</div>
    <div>2</div>
    <div>3</div>


    <span>Epic Span</span>
</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {

    $("div").mouseenter(function(event){
        console.log("Entered Mouse")
    })

    $("span").mouseenter(function(event){
        console.log("Entered Span")
    })

});

```

### Mouse Leave Element

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
    <div>1</div>
    <div>2</div>
    <div>3</div>


    <span>Epic Span</span>
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

    $("div").mouseenter(function(event){
        console.log("Entered Div")
        $(this).css("color", "red");
    })


    $("div").mouseleave(function(){
        console.log("Left Mouse")
        $(this).css("color", "black");
    })

    $("span").mouseenter(function(event){
        console.log("Entered Span")
    })

});

```

### Mouse Hover

This is a combination of Mouse Enter and Mouse Leave Event. It takes two functions

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
    <div>1</div>
    <div>2</div>
    <div>3</div>

</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {


    $("div").hover(function(){
    console.log("Entered Div")
        $(this).css("color", "yellow");
    },
    function(){
           $("div").mouseleave(function(){
        console.log("Left Mouse")
        $(this).css("color", "black");
    })
    });

    // $("div").mouseenter(function(event){
    //     console.log("Entered Div")
    //     $(this).css("color", "red");
    // })


    // $("div").mouseleave(function(){
    //     console.log("Left Mouse")
    //     $(this).css("color", "black");
    // })

});

```

### Mouse Down

To add a mouse down event, you can use the `mousedown` event in jQuery. Here's
an example:

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
    <div>1</div>
    <div>2</div>
    <div>3</div>

</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {
    
    $("div").mousedown(function(event){
        console.log("Mouse Down")
    })

});
```

### Mouse Up
To add a mouse up event, you can use the `mouseup` event in jQuery. Here's
an example:


```javascript
$(document).ready(function() {

    $("div").mouseup(function(event){
        console.log("Mouse Up")
    })

});

```

### Keyboard Down

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
    <input type="text" name="" id="">

</body>
</html>
```

```javascript

"use strict";

$(document).ready(function() {

    $("input").keydown(function(event){
        console.log(event.which + " Key is pressed")
    })

});

```

### Keyboard Press

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
    <input type="text" name="" id="">

</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

    $("input").keydown(function(event){
        console.log(event.which + " Key is pressed")
    })


    $("input").keypress(function(event){
        console.log(event.which + " single press")
    })

        $("input").keypress(function(event){
        console.log(event.which + " single press")
    })

});

```

### Keyboad Up

```javascript
"use strict";

$(document).ready(function() {

    $("input").keydown(function(event){
        console.log(event.which + " Key is pressed")
    })


    $("input").keypress(function(event){
        console.log(event.which + " single press")
    })

    
    $("input").keyup(function(event){
        console.log(event.which + " key was released")
    })

});

```

### Form Submit

Detect When a form has been submitted

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
<form action="">
    <input type="text" name="username" id="" placeholder="Enter username">

    <input type="submit" value="login">
</form>

</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {

    $("form").submit(function(event){
        alert("Form has been submitted")
    })


});

```

### Form Change

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

    <input type="text" name="username" id="" placeholder="Enter username" value="JosephModi1997">
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

    $("form").submit(function(event){
        alert("Form has been submitted")
    })
 $('input').change(function() {
                alert('The username has been changed to: ' + $(this).val());
    });

});

```

### Form. Input Change

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

    <input type="text" name="username" id="" placeholder="Enter username" value="JosephModi1997">
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

 $('input').change(function() {
                alert('The username has been changed to: ' + $(this).val());
    });

});

```

### Form Blur
Used for validation of input values

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
    <div>Hello World</div>
    <p>I love fishy fish</p>
    <input type="text" name="" id="batman">
    <a href="#">I am Batman</a>
</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {


$('*').blur(function() {
    console.log('Please don\'t leave me')
});

});

```

### Document Window Scroll


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
    <textarea name="" id="" cols="30" rows="10">
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Culpa, maiores ullam libero dolores iusto voluptatem. Illum saepe consequuntur enim asperiores doloremque, dolor eos voluptate perspiciatis! Reiciendis eligendi voluptatem molestiae quia!
        Voluptatum iste, asperiores veniam repellat ut alias voluptate, temporibus veritatis odit dolorum tempora at. Aspernatur cum, adipisci esse maiores ipsa quis iste, pariatur perferendis magni, enim dolores dolore soluta porro!
        Culpa dolores pariatur odio atque est reprehenderit porro at, cupiditate doloribus. Cupiditate nulla placeat quos laborum tempore optio sit natus! Excepturi molestiae eos sapiente cupiditate enim ex pariatur ea voluptatibus.
        Animi optio ipsum harum magnam consequatur porro a autem itaque, consectetur libero facere, perspiciatis molestiae totam repudiandae necessitatibus ea iusto. Beatae, deleniti tenetur. Optio minima eligendi sequi tempora. Voluptates, eos.
        Voluptatum libero, temporibus assumenda dolor, repudiandae officiis cumque alias voluptatem consequuntur ipsum consequatur deleniti eligendi vitae modi optio debitis? Totam non minus earum accusantium eveniet nihil modi adipisci labore ipsum.
    </textarea>
</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {

var num = 0;
$('*').scroll(function() {
    console.log('Scrolling yay')
       num ++

    console.log(num);
});

});

```

### Combining Multiple Events Using A Single Selector

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
    <textarea>Hello World</textarea>
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

$("textarea").on({
    click: function() {
    alert("Text area is clicked");
},
mouseenter: function() {
    $(this).css("background-color", "yellow");
},
mouseleave: function() {
    $(this).css("background-color", "white");
}
})
});

```