---
title: Functions in Dart
description: Functions are the block of code that performs a specific task.
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

### Example 1: Prints Name

This is a simple program that prints name using function. The name of function is printName().


```dart
  // Function to print name
  void printName() {
    print("My name is Mariam");
  }

  void main() {
    // Calling the function
    printName();
  }
```

### Example 2: Sum of Two Numbers

This function finds the sum of two numbers. Here, the function accepts two parameters. i.e., num1 and num2, and the return type is void.

```dart
  // Function to find the sum of two numbers
  void findSum(int num1, int num2) {
    int sum = num1 + num2;
    print("The sum of $num1 and $num2 is: $sum");
  }

  void main() {
    // Calling the function with two numbers
    findSum(10, 20);
  }
```

### Key Points
- In dart function are also objects.
- You should follow the lowerCamelCase naming convention while naming function.
- You should follow the lowerCamelCase naming convention while naming function parameters.

### Types Of Functions

Functions are the block of code that performs a specific task. Here are different types of functions:

- No Parameter And No Return Type footnote[^noparam]
- Parameter And No Return Type
- No Parameter And Return Type
- Parameter And Return Type

footnote[^noparam] `No Parameter And No Return Type `