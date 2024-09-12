---
title: Anonymous Functions
description: An anonymous function behaves the same as a regular function, but it does not have a name with it.
author: modi
date: 2024-09-11 08:37:00 +0800
categories: [Dart, Functions]
tags: [dart-functions]
pin: true
math: true
mermaid: true
---

In the previous lesson we introduced you to functions that are defined by using a function name like main(), fullName(). In this lesson we will talk about nameless functions or functions without a name. This type of function is known as an anonymous function, lambda, or closure. An anonymous function behaves the same as a regular function, but it does not have a name with it. It can have zero or any number of arguments / parameters with an option type annotation.

## Syntax 
Below is the syntax of the anonymous function

```dart
(parameters){
  // body of an anonymous function
}
```

### Knowledge Panel:
- You can assign an anonymous function to a variable
- You can pass an anonymous function as a parameter / argument


## Example 1:

In this example, you will learn to use an anonymous function to print all list items. This function invokes each fruit without having a function name.

```dart
void main() {
  // List of fruits
  var fruits = ['Apple', 'Banana', 'Cherry', 'Date'];

  // Using an anonymous function with forEach to print each fruit
  fruits.forEach((fruit) {
    print(fruit);
  });
}
```

### Explanation:
- var fruits = ['Apple', 'Banana', 'Cherry', 'Date'];: Defines a list of fruits.
- fruits.forEach((fruit) { ... });: The forEach method is used to iterate over each item in the list. It takes an anonymous function as its argument.
   - (fruit) { print(fruit); }: This is an anonymous function (a function without a name) that takes one parameter fruit and prints it.
