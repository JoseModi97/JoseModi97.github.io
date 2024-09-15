---
title: String Manipulation and Collections
description:  Essential for processing and formatting text data in programming,
author: modi
date: 2024-09-15 04:55:00 +0300
categories: [Dart, Utilities]
tags: [dart-utilities]
pin: true
math: true
mermaid: true
---

### Importance
  String manipulation is essential for processing and formatting text data in programming, such as generating messages, formatting user input, or performing text-based calculations.

### Common Operations
  - Concatenation: Concatenation combines two or more strings into one. Dart uses the + operator for this.
```dart
  void main() {
    String firstName = 'John';
    String lastName = 'Doe';

    // Concatenate two strings
    String fullName = firstName + ' ' + lastName;

    print('Full Name: $fullName'); // Output: Full Name: John Doe
  }
```



  - Interpolation String interpolation allows embedding variables directly within a string. Dart uses $ for simple variables and ${} for expressions.

```dart
  void main() {
  String name = 'Alice';
  int age = 30;

  // String interpolation with a variable
  String greeting = 'Hello, $name!';

  // String interpolation with an expression
  String message = 'In 5 years, you will be ${age + 5} years old.';

  print(greeting); // Output: Hello, Alice!
  print(message);  // Output: In 5 years, you will be 35 years old.
  }
```




  - Substring: The substring() method extracts a portion of a string by specifying start and end indices.

```dart
  void main() {
    String text = 'Hello, Dart programming!';

    // Extract a substring from index 7 to 11
    String subText = text.substring(7, 11);

    print('Substring: $subText'); // Output: Substring: Dart
  }
```