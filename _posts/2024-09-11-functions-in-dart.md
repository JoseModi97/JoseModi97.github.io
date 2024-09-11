---
title: Functions in Dart
description: Dart is an open-source programming language developed by Google
author: modi
date: 2024-09-11 08:37:00 +0800
categories: [Dart, Functions]
tags: [dart-functions]
pin: true
math: true
mermaid: true
---

### Learning Objectives

1. To understand what Functions are
2. To understand the composition of functions
3. Be able to understand types of functions in Dart

### What are Functions?

In this tutorial, you will learn about functions in dart. Functions are the block of code that performs a specific task. They are created when some statements are repeatedly occurring in the program. The function helps reusability of the code in the program.

### Function Advantages
- Avoid Code Repetition
- Easy to divide the complex program into smaller parts
- Helps to write a clean code

### Syntax of a function
``` bash
returntype functionName(parameter1,parameter2, ...){

// function body

}
```

`Return type`: It tells you the function output type. It can be void, String, int, double, etc. If the function doesn’t return anything, you can use void as the return type.

`Function Name`: You can name functions by almost any name. Always follow a lowerCamelCase naming convention like void printName().

`Parameters`: Parameters are the input to the function, which you can write inside the bracket (). Always follow a lowerCamelCase naming convention for your function parameter.