---
title: Arrow Functions
description: The Arrow function is represented by => symbol. 
author: modi
date: 2024-09-12 09:34:00 +0800
categories: [Dart, Functions]
tags: [dart-functions]
pin: true
math: true
mermaid: true
---

If you want to declare a function in one line; In Dart we have a fat arrow function that can enable you. The function is represented by => symbol. 

## Syntax 
Below is the syntax for the arrow function

```bash
returnType functionName(parameters) => expression;
```

### Knowledge Panel 
Note: The arrow function is used to make your code short. => expr syntax is a shorthand for { return expr; }.


## Example 1: WITHOUT Arrow Function

This program finds simple interest without using the arrow function.
``` dart
  void main() {
    // Principal amount, rate of interest, and time period
    double principal = 1000.0;
    double rate = 5.0;
    double time = 3.0;

    // Function to calculate simple interest
    double calculateSimpleInterest(double p, double r, double t) {
      return (p * r * t) / 100;
    }

    // Calling the function and storing the result
    double interest = calculateSimpleInterest(principal, rate, time);

    // Printing the result
    print("The simple interest is: \$${interest}");
  }
```

## Example 2: WITH Arrow Function

This program finds simple interest using the arrow function.

```dart
  void main() {
    // Principal amount, rate of interest, and time period
    double principal = 1000.0;
    double rate = 5.0;
    double time = 3.0;

    // Arrow function to calculate simple interest
    double calculateSimpleInterest = (double p, double r, double t) => (p * r * t) / 100;

    // Calling the function and storing the result
    double interest = calculateSimpleInterest(principal, rate, time);

    // Printing the result
    print("The simple interest is: \$${interest}");
  }
```

