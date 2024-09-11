---
title: Data Types in Dart
description: Dart is an open-source programming language developed by Google
author: modi
date: 2024-09-11 05:49:00 +0800
categories: [Dart, DataTypes]
tags: [dart]
pin: true
math: true
mermaid: true
---

## Data Types In Dart

A data type is an attribute of data which tells the compiler or interpreter how the programmer intends to use the data.

Dart supports the following data types:

1. Number
2. Strings
3. Boolean
4. Lists
5. Maps
6. Runes
7. Null


## Numbers

When you need to store numeric value on dart, you can use either int or double. Both int and double are subtypes of num. Int stores whole numbers while double stores decimal numbers.

```dart
void main() {
  // Integer variable
  int age = 30;
  int year = 2024;

  // Double variable
  double pi = 3.14159;
  double temperature = 36.6;

  // Operations on numbers
  int sum = age + year;
  double area = pi * 5 * 5; // Area of a circle with radius 5
  double difference = temperature - 1.5;

  // Printing the values
  print('Age: $age');
  print('Year: $year');
  print('Pi: $pi');
  print('Temperature: $temperature');
  print('Sum of age and year: $sum');
  print('Area of circle: $area');
  print('Difference in temperature: $difference');
}
```

## String

String helps you to store text data in your program. You can use single or double quotes to store string in dart.

```dart
void main() {
  //lets work with string data type and variables
  String name = "john Doe";
  String city = "Nairobi";
  String favfood = "Rice";
  //lets print this
  print("My name is $name  and my city is $city. I love eating $favfood ");
  print("My favorite food is ${favfood}");
  //length of strings(property of the string)
  print(city.length);
  //refer to specific character in the string using its index
  print(city[6]);
  // print(city[5]);
  //string functions
  //to uppercase
  print(city.toUpperCase());
  print(city.toLowerCase());
  //see if a character is inside the string

  print(city.indexOf("b"));
  //print(name.indexOf("o"));
  print(name.contains("p"));

  //string concatenation- adding two or more string variables
  String greeting = "Hello";
  String greeting2 = " World";
  print(greeting + greeting2);
  print(greeting + " " + greeting2);

  //string interpolation -adding string variables to a string/sentence
  // print("The greeting of each language is ${greeting + greeting2}");
  var myname = "John";
  print("My name is $myname");
}
```

## Booleans

In Dart, boolean holds either true or false value. You can write the bool keyword to define the boolean data type. You can use boolean if the answer is true or false. Consider the answer to the following questions:

- Are you asleep?
- Is the door open?
- Does a cat fly?
- Are you older than your father?