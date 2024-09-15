---
title: Data Types in Dart
description: A data type is an attribute of data which tells the compiler or interpreter how the programmer intends to use the data.
author: modi
date: 2024-09-11 05:49:00 +0300
categories: [Dart, DataTypes]
tags: [dart-intro]
pin: true
math: true
mermaid: true
---

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

These all are yes/no questions. Its a good idea to store them in boolean.

```dart
void main() {
  // this is a true or false statement

  bool isOver18 = true;
  print(isOver18);

  print(7 < 8);
}
```

## Lists

Dart List is similar to an array, which is the ordered collection of the objects. If you want to store multiple values without creating multiple variables, you can use a list.


```dart
void main() {
  // use square brackets for listing
  List myList = [1, 2, 4, "Jackson"];
  // adding value to the list

  myList.add(67);
  myList.remove("Jackson");
  // remove value
  // myList.remove(4);
  print(myList);
}
```

## Maps

A map is a dynamic collection that represents a set of values ​as key-value pairs. Keys and values ​in the

map can be of any type.

```dart
void main() {
  // Creating a Map with String keys and int values
  Map<String, int> ages = {
    'Alice': 30,
    'Bob': 25,
    'Charlie': 35,
  };
  print("Ages of students: $ages");
}
```



## Runes

A rune can be defined as an integer used to represent any Unicode code point. As a Dart string is a simple sequence of UTF-16 code units, 32-bit Unicode values in a string are represented using a special syntax.


```dart
void main( )
{
 var heart_symbol = '\u2665'; 
var laugh_symbol = '\u{1f800}';
 print(heart_symbol);
 print(laugh_symbol);
 }
```


## Arithmetic Operations using Numbers

Arithmetic operators are the most common types of operators. They perform operations like addition, subtraction, multiplication, division.

```dart
void main() {
  // Declaring integer and double variables
  int a = 10;
  int b = 3;
  double x = 5.5;
  double y = 2.5;

  // Performing arithmetic operations
  int addition = a + b;            // Addition
  int subtraction = a - b;         // Subtraction
  int multiplication = a * b;      // Multiplication
  double division = a / b;         // Division (returns a double)
  int integerDivision = a ~/ b;    // Integer Division (returns an int)
  int modulus = a % b;             // Modulus (remainder of division)

  // Using double variables
  double doubleAddition = x + y;
  double doubleMultiplication = x * y;

  // Printing results
  print('Addition (int): $a + $b = $addition');
  print('Subtraction (int): $a - $b = $subtraction');
  print('Multiplication (int): $a * $b = $multiplication');
  print('Division (double): $a / $b = $division');
  print('Integer Division: $a ~/ $b = $integerDivision');
  print('Modulus: $a % $b = $modulus');

  print('Addition (double): $x + $y = $doubleAddition');
  print('Multiplication (double): $x * $y = $doubleMultiplication');
}
```