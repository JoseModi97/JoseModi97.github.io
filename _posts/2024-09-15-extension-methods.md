---
title: Extension Methods
description:  A class has only one instance and also provides a global point of access to it. 
author: modi
date: 2024-09-15 04:48:00 +0800
categories: [Dart, OOP]
tags: [dart-oop]
pin: true
math: true
mermaid: true
---

An extension method is a feature in Dart that allows developers to add new methods to existing classes or interfaces without changing their original implementation. These methods can be used as if they were part of the original class. In other words, extensions enable developers to add functionality to a class or interface that they did not write and don’t control.




```dart
// Extending the String class with an extension method

extension StringExtensions on String {

 // Method to capitalize the first letter of a string

 String capitalizeFirstLetter() {

  if (this.isEmpty) {

   return this;

  }

  return this[0].toUpperCase() + this.substring(1);

 }

}


void main() {

 // Create a String object

 String message = "hello, world!";

  

 // Use the extension method to capitalize the first letter

 String capitalizedMessage = message.capitalizeFirstLetter();

  

 // Print the result

 print(capitalizedMessage); // Output: Hello, world!

}
```


`Explanation:`
1. Extension Declaration:
- extension StringExtensions on String { ... } defines an extension named StringExtensions that adds 2.functionality to the String class.
2. Adding a Method:
- String capitalizeFirstLetter() { ... } is a method added to the String class. It checks if the string is empty, and if not, it returns the string with the first letter capitalized.
3. Using the Extension Method:
- In the main() function, message.capitalizeFirstLetter() calls the new method on a String object, demonstrating how the extension method can be used just like a regular method of the class.

