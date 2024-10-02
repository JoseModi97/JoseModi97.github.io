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

## Chapter 4: HTML CSS

### Get and Set CSS Property

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
    <div style="color: blue">Hello World</div>
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {

$("div").click(function(){
    console.log($(this).css("color"));
    $(this).css("color", "#567FFA")
})
});

```

### Set Multiple CSS Properties

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
    <div style="color: blue">Hello World</div>
</body>
</html>
```



```javascript
"use strict";

$(document).ready(function() {

$("div").click(function(){
    console.log($(this).css("color"));
    $(this).css({
        "color": "white",
        "background-color": "red"
    })
})
});

```

### Add, Remove and Toggle CSS Classes

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
    <div style="color: blue">Hello World</div>
</body>
</html>

```


```javascript

"use strict";

$(document).ready(function() {

$("div").click(function(){
    console.log($(this).css("color"));
    $(this).css({
        "color": "white",
        "background-color": "red"
    })
})
});

```

### Get and Set Element Dimensions

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
<style>
    #RedBox{
        width: 200px;
        height: 350px;
        background-color: red;
        padding: 10px;
        border: 2px solid black;
        margin: 90px;
    }
</style>
<body>
    <div id="RedBox"></div>

    <button id="ClickMe">Change Width & Height</button>

    <button id="ClickAnotherMe">Change Width & Height</button>
</body>
</html>
```


```javascript
"use strict";

$(document).ready(function() {

var width = $("#RedBox").width();
var height = $("#RedBox").height();


var innerWidth = $("#RedBox").innerWidth();
var innerHeight = $("#RedBox").innerHeight();



var outerWidth = $("#RedBox").outerWidth();
var outerHeight = $("#RedBox").outerHeight();


var outerWidthWithMargin = $("#RedBox").outerWidth(true);
var outerHeightWithMargin = $("#RedBox").outerHeight(true);
console.log("Width: "+width);
console.log("Height: "+ height);
console.log("Inner Width: "+ innerWidth);
console.log("Inner Height: "+innerHeight);
console.log("Outer Width: "+ outerWidth);
console.log("Outer Height: "+outerHeight);

console.log("Outer Width With Margin: "+ outerWidthWithMargin);
console.log("Outer Height With Margin: "+outerHeightWithMargin);


$("#ClickMe").click(function(){
   $("#RedBox").width(400); 
})

$("#ClickAnotherMe").click(function(){
   $("#RedBox").height(400); 
})
});

```

### Adding Elements Using Append, Prepend, After and Before

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
<style>
    #EpicDiv{
        color: red;
    }
</style>
<body>
    <div id="EpicDiv">Hello World</div>
    <button id="AppendButton">Append</button>
    <button id="PrependButton">Prepend</button>
    <button id="AfterButton">After</button>
    <button id="BeforeButton">Before</button>
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {
$("#AppendButton").click(function(){
   $('#EpicDiv').append("<b>Append</b>")
})


$("#PrependButton").click(function(){
   $('#EpicDiv').prepend("<b>Prepend</b>")
})


$("#AfterButton").click(function(){
   $('#EpicDiv').after("<b>After</b>")
})

$("#BeforeButton").click(function(){
   $('#EpicDiv').before("<b>Before</b>")
})
});

```


###  Removing Elements Using Remove and Empty

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
<style>
#parentDiv{
background-color: red;
        color: white;
        min-width: 200px;
        min-height: 400px;
    }
</style>
<body>
    <div id="parentDiv" class="epicDiv">
        Hello World
        <div>Pizza</div>
        <div>Fish Fingers</div>
        <div>Mash Potato</div>
    </div>

    <div>Pizza is awesome</div>

    <button id="RemoveButton">Remove</button>
    <button id="EmptyButton">Empty</button>

    <button id="RemoveFilterButton">FIlterRemove</button>
</body>
</html>
```

```javascript
"use strict";

$(document).ready(function() {
$("#RemoveButton").click(function(){
   $("div").remove();
})

$("#EmptyButton").click(function(){
   $("div").remove();
})

$("#RemoveFilterButton").click(function(){
   $("div").remove(".epicDiv");
})
});

```

## Traversing
### Elements By Index

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
<style>
.red{
    color: red;
    }
</style>
<body>
    <div>Div 1</div>
    <div>Div 2</div>
    <div>Div 3</div>
    <div>Div 4</div>
    <div>Div 5</div>
</body>
</html>

```

```javascript
"use strict";

$(document).ready(function() {
$("div").eq(3).addClass("red");
});

```

### Child Elements

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
<style>
    .red
    {
    color: red;
    }
</style>
<body>
    <div>
        Hello World
    </div>
    <div>
        <div>Div 1</div>
        <div class="hello">Div 2</div>
        <div>Div 3</div>
        <div class="hello">Div 4</div>
        <div>Div 5</div>
    </div>
</body>
</html>

```


```javascript
"use strict";

$(document).ready(function() {
// $("div").children().addClass("red")
$("div").children(".hello").addClass("red")
});

```


### Parent Element

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
<style>
    .red
    {
    color: red;
    }
</style>
<body>
<div>
    Root Div
    <div>
        Hello World
        <div id="Hello">Div 1</div>
    </div>
</div>
</body>
</html>

```

`parant()`
```javascript
"use strict";

$(document).ready(function() {
$("#Hello").parent().addClass("red")
});

```

`parents()`
This traverses all parents above the selected element

```javascript
"use strict";

$(document).ready(function() {
$("#Hello").parents().addClass("red")
});

```

`parents() select a particular class in parents`
This traverses all parents above the selected element

```javascript
"use strict";

$(document).ready(function() {
$("#Hello").parents(".red").addClass("red")
});

```

### Siblings

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
<style>
    .red
    {
    color: red;
    }
</style>
<body>
<div>
    <div class="epicClass">Pizza</div>
    <div>Fried Chicken</div>
    <div id="mash">Mash Potatoes</div>
    <div class="epicClass">Fish Fingers</div>
    <div>Cookie Dough</div>
</div>
</body>
</html>

```

`All Siblings`

```javascript
"use strict";

$(document).ready(function() {
$("#mash").siblings().addClass("red")
});

```

`Particular Siblings`
```javascript
"use strict";

$(document).ready(function() {
$("#mash").siblings(".epicClass").addClass("red")
});

```

### Filtering Elements

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
<style>
    .red
    {
    color: red;
    }
</style>
<body>
<div>Pizza</div>
<div class="Hello">Fried Chicken</div>
<div>Waffles and Ice Cream</div>
<div class="Hello">Fish Fingers</div>
<div>Mash Potatoes</div>
</body>
</html>

```

```javascript
"use strict";

$(document).ready(function() {
//select everything
// $("div").addClass("red")

//select the first item
// $("div").first().addClass("red")

//select the last item
// $("div").last().addClass("red")

//select by index
// $("div").eq(1).addClass("red")

//filter based on condition
// $("div").filter(".Hello").addClass("red")

//filter not based on condition
$("div").not(".Hello").addClass("red")
});

```



## Effects
### Show, Hide and Toggle

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
<style>
    .red
    {
    color: red;
    }
</style>
<body>
<div>I love Tuna Pizza</div>

<button id="HideButton">Hide</button>
<button id="ShowButton">Show</button>
<button id="ToggleButton">Toggle</button>

<br />

<button id="SlowButton">Slow</button>
<button id="FastButton">Fast</button>

<br>

<input id="Time" type="text" value="0">

<button id="CustomSpeed">Custom Speed</button>
</body>
</html>

```

```javascript
"use strict";

$(document).ready(function() {
    $("#HideButton").click(function(){
        $("div").hide();
    })

    $("#ShowButton").click(function(){
        $("div").show();
    })

    $("#ToggleButton").click(function(){
        $("div").toggle();
    })

        $("#SlowButton").click(function(){
        $("div").toggle("slow");
    })

    $("#FastButton").click(function(){
        $("div").toggle("fast");
    })

    $("#CustomSpeed").click(function(){
        var time = parseInt($("#Time").val());
        $("div").toggle(time, function(){
            console.log("Effect finished");
        });
    })
});

```

### Sliding Using slideDown, slideUp and slideToggle

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
<style>
    #Panel, #SlideDownButton, #SlideUpButton, #SlideToggleButton {
        padding: 5px;
        text-align: center;
        background-color: #cccccc;
        border: solid 1px #c3c3c3;
    }
    #Panel
    {
        padding: 50px;
        display: none;
    }
</style>
<body>
<div id="SlideDownButton">Click to Slide Down</div>
<div id="Panel">Hello world</div>
<div id="SlideUpButton">Click to Slide Up</div>

<div id="SlideToggleButton">Slide Toggle</div>
</body>
</html>

```

```javascript

"use strict";

$(document).ready(function() {
 $("#SlideDownButton").click(function(){
    $("#Panel").slideDown();
 })

  $("#SlideUpButton").click(function(){
    $("#Panel").slideUp();
 })

 $("#SlideToggleButton").click(function(){
    $("#Panel").slideToggle();
 })

});


```

## Chapter 8: AJAX
### Load

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
<span id="AJAXDiv">Darth Vader</span>

<button id="EpicButton">Click ME!!!</button>
</body>
</html>

```

In this case, the txt file is within the same directory as the javascript file. You can also load files from other locations through relative path or url (incase it has been hosted in a local host).
```javascript
"use strict";

$(document).ready(function() {
 $("#EpicButton").click(function(){
    $("#AJAXDiv").load("textfile.txt")
 })


});


```


### GETJSON

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
<button id="EpicButton">Click ME!!!</button>
</body>
</html>

```

```json
{
    "game": "Half-life 2",
    "food": "Pizza",
    "planet": "Earth is ok"
}
```

```javascript
"use strict";

$(document).ready(function() {
 $("#EpicButton").click(function(){
    $.getJSON("favourites.json", function(result){
        console.log(result);

        $.each(result, function(index, value){
            console.log(`${index} - ${value}`)
        })
    })
 })


});

```

### GET Data

index.html
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
        
    </div>
<button id="EpicButton">Click ME!!!</button>
</body>
</html>

```
favourites.php
```php
<?php


echo '<b>Pizza is the best</b>';

```

```javascript
"use strict";

$(document).ready(function() {
 $("#EpicButton").click(function(){
   $.get("favourites.php", function(data, status){
    console.log(data);
    $("div").html(data);
    console.log(status);
   })
 })


});

```

### POST Data

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

<button id="EpicButton">Click ME!!!</button>
</body>
</html>

```

favourites.php (Server)
```php
<?php


$food = $_POST['food'];
$game = $_POST['game'];

echo $food . " and " . $game;

```

```javascript
"use strict";

$(document).ready(function() {
 $("#EpicButton").click(function(){
   $.post("favourites.php",{
    "food" : "pizza",
    "game": "Half-Life 3"
   }   ,function(data, status){
    console.log(data);
   })

 })


});

```

## Chapter 9: Utility Functions 
### Trim String
Gets rid of spaces before and after a word. It is used mostly in input form fields.

```javascript
"use strict";

$(document).ready(function() {

   var food = " Pizza is the best ";

   console.log(food);
   console.log(food.trim());


});

```

### Extend

This is a way to merge or combine the values of two different objects into one
In the parameters, the object that is called first will have all the records merged into it.

```javascript
"use strict";

$(document).ready(function() {

   var object1 = 
   {
    apple: 0,
    banana: {weight: 52, price: 100},
    cherry: 97
   };

   var object2 = {
    banana: { price: 200},
    taste: 100
   };
   console.log(object1);
   console.log(object2);
   $.extend( object1, object2)

   console.log(object1);
   console.log(object2);

});

```

### $.inArray()

```javascript
"use strict";

$(document).ready(function() {

   var epicArray = [34, 27, "Batman","Pizza"];
//result is 0
   console.log($.inArray(34, epicArray));
   //result is 2
   console.log($.inArray("Batman", epicArray));

   //Check whether Add exists in the array. In this case it doesn't so the result will be -1
   console.log($.inArray("Add", epicArray));

   //check whether a specific value appears after a particular array element
   console.log($.inArray("Pizza", epicArray, 2));

});

```

### $.each()
Iterate over a javascript array

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
<div></div>
<button id="EpicButton">Click ME!!!</button>
</body>
</html>

```

```javascript
"use strict";

$(document).ready(function() {

   var array = ["Batman", "Pizza", "Yoda"];
   var html = '';
   html += '<ul>'
   $.each(array, function(index, value){
    console.log(`${index}: ${value}`);
    html += '<li>' + value + '</li>';
   });
   html += '</ul>'
   
   $("#EpicButton").click(function(){
        $("div").html(html);
   });
});

```

### Data Function / Method
Used to give information about data

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
    My Name is <span></span> 
    I am <span></span> years old</div>

    <button id="EpicButton">Click Me</button>
</body>
</html>

```


```javascript
"use strict";

$(document).ready(function() {
   $("#EpicButton").click(function(){
var div = $("div")[0];

   $.data(div, "epic", 
    {
        "name": "Frahan",
        "age": 27
    }
   )
   $("span:first").text($.data(div, "epic"). name)
   $("span:last").text($.data(div, "epic"). age)
   })
});

```


### Proxy function
This is a function that represents certain objects when a particular function is called. this keyword is placed within the function and the content of the object can be accessed

```javascript
    "use strict";

    $(document).ready(function() {
    var func = function(){
        console.log(this);
    }
    var object = 
    {
        food: "Pizza",
    }

    var proxyFunction  = $.proxy(func, object);

    proxyFunction();
    });

```
### Is Window Function

```javascript
"use strict";

$(document).ready(function() {
console.log($.isWindow(window))
});

```

### Now Epoch Method

```javascript
    "use strict";

    $(document).ready(function() {
    var time = $.now();
    //epoch time, number of seconds since 1st January 1970
    console.log(time);
    });

```

### Number Check isNumeric()

checks is provided number is numeric

```javascript
"use strict";

$(document).ready(function() {
console.log($.isNumeric(6)) // true
console.log($.isNumeric("Hello")) // false
console.log($.isNumeric(-56.835)) // true
console.log($.isNumeric("67")) // true
console.log($.isNumeric("67u")) // false
});

```

### Queue and Dequeue methods

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
   <div style="background: blue; height: 100px; width: 100px;">
   </div>
    <button id="DequeueButton">Click Me</button>
</body>
</html>

```

```javascript
"use strict";

$(document).ready(function() {
$("#DequeueButton").click(function(){
    var div = $("div");
    div.animate({height: 300}, "slow");
    div.animate({width: 300}, "slow");

    div.queue(function(){
        div.css("background-color","red")
        div.dequeue();
    })
    div.animate({height: 100}, "slow");
    div.animate({width: 300}, "slow");
})
});

```

### Global Evaluation `$.globalEval()`

This is a function that enables you to access a value defined within a function's scope from anywhere within the code 

```javascript
"use strict";

$(document).ready(function() {
    function EpicFunc(){
        $.globalEval(" var epicVar = 27;");

    }

    EpicFunc()
    console.log(epicVar);
});

```