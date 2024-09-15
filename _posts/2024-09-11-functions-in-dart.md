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

`Key Points`
- In dart function are also objects.
- You should follow the lowerCamelCase naming convention while naming function.
- You should follow the lowerCamelCase naming convention while naming function parameters.

### Types Of Functions

Functions are the block of code that performs a specific task. Here are different types of functions:

- No Parameter And No Return Type
- Parameter And No Return Type
- No Parameter And Return Type
- Parameter And Return Type

`Function With No Parameter And No Return Type`
: In this function, you do not pass any parameter and expect no return type. Here is an example of it:

printName() is a function which prints name on your screen.


```dart
  // No parameter and no return type
  void main() {
    printName();
  }

  //no parameters and no return type (nothing in parameter list and no return type)
  void printName() {
    print("Aron Jackson is a student ");
  }
```

`Function With Parameter And No Return Type`

In this function, you do pass the parameter and expect no return type. Here is an example of it:

```dart
  //Here printFullName is a function  With a parameter and no return type function that takes the name of the parameter
  void main() {
    printName("Aron Jackson");
  }

  // parameters and no return type
  void printName( String name ) {
    print("My name is $name ");
  }
```
In this program, printName(String name) is the function which has keyword void. It means it has no return type, and the pair of parentheses is not empty but this time that suggests it to accept a parameter.

`Function With No Parameter And Return Type`

In this function, you do not pass any parameter but expect return type. Here is an example of it:

Here InstructorName() is a function which returns Instructor's name. In the entire program, anyone can use this function to find the name of the Instructor

```dart
// Function to return Instructor's name
String InstructorName() {
  return "Allan";
}

void main() {
  // Calling the function and storing the result
  String instructor = InstructorName();

  // Printing the instructor's name
  print("The Instructor's name is: $instructor");
}
```
In this program, InstructorsName() is the function which has String keyword before function name, means it return String value, and the empty pair of parentheses suggests that there is no parameter that is passed to the function.

`Function With Parameter And Return Type`

In this function, you do pass the parameter and also expect return type. Here is an example of it:

```dart
// Function to add two integers and return the result
int add(int a, int b) {
  return a + b;
}

void main() {
  // Calling the function with two integers
  int result = add(10, 20);
  
  // Printing the result
  print("The sum of 10 and 20 is: $result");
}
```
In this program, int add(int a, int b) is the function with int as the return type, and the pair of parenthesis has two parameters, i.e., a and b.

## THE TYPES OF FUNCTIONS DISCUSSED

The code snippets below indicate all the functions. Use the comments as your guidelines.

```dart
  void main() {
    // Calling the functions and displaying their outputs

    // Function with no parameters and no return type
    printWelcomeMessage();

    // Function with parameters and no return type
    greetUser("Alice");

    // Function with parameters and return type
    int sumResult = add(10, 20);
    print("The sum of 10 and 20 is: $sumResult");

    // Function with no parameters but expects a return type
    String instructorName = InstructorName();
    print("The instructor's name is $instructorName");

    // Function with parameters and return type
    int productResult = multiply(5, 6);
    print("The product of 5 and 6 is: $productResult");
  }

  // Function with no parameters and no return type
  void printWelcomeMessage() {
    print("Welcome to the Dart programming tutorial!");
  }

  // Function with parameters and no return type
  void greetUser(String name) {
    print("Hello, $name! Welcome to Dart.");
  }

  // Function with parameters and return type
  int add(int a, int b) {
    return a + b;
  }

  // Function with no parameters but expects a return type
  String InstructorName() {
    return "Allan";
  }

  // Function with parameters and return type
  int multiply(int a, int b) {
    return a * b;
  }
 
```


### Explanation:
- printWelcomeMessage(): Prints a welcome message. No parameters and no return type.
greetUser(String name): Prints a greeting message using the provided name. Takes one parameter and has no return type.
- add(int a, int b): Returns the sum of two integers. Takes two parameters and returns an int.
- InstructorName(): Returns a fixed string, the instructor's name. No parameters and returns a String.
- multiply(int a, int b): Returns the product of two integers. Takes two parameters and returns an int.