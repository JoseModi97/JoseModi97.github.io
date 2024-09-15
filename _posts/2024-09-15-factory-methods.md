---
title: Factory Methods
description: Factory constructors do use the return key word.
author: modi
date: 2024-09-15 04:07:00 +0800
categories: [Dart, OOP]
tags: [dart-oop]
pin: true
math: true
mermaid: true
---

In Dart, factory constructors or methods are used to provide alternative ways to create instances of a class. They are useful when you need to control the instantiation process or return an instance of a subclass.

Factory constructors do use the return key word.
You cannot refer to 'this' within the factory constructor.

```dart
import 'dart:math'; // Import math library to use pi

// Circle Class Definition
class Circle {
  double radius; // Instance variable to store the radius of the circle

  // Constructor to initialize the radius
  Circle(this.radius);

  // Factory constructor to control instance creation
  factory Circle.create(double radius) {
    // Ensure the radius is positive before creating the instance
    if (radius > 0) {
      return Circle(radius); // Return a new Circle instance
    } else {
      // Throw an error if the radius is not valid
      throw ArgumentError('Radius must be greater than zero');
    }
  }

  // Method to calculate the area of the circle
  double calculateArea() {
    return pi * radius * radius; // Area formula: pi * radius^2
  }
}

void main() {
  // Using the factory constructor to create circle instances
  Circle circle1 = Circle.create(5.0); // Create a circle with radius 5.0
  Circle circle2 = Circle.create(10.0); // Create a circle with radius 10.0

  // Print the area of the circles by calling the calculateArea method
  print('Circle 1 Area: ${circle1.calculateArea()}'); // Output: Circle 1 Area
  print('Circle 2 Area: ${circle2.calculateArea()}'); // Output: Circle 2 Area

  // Example of error handling for invalid radius
  try {
    Circle circle3 = Circle.create(-3.0); // Invalid radius, will throw an error
  } catch (e) {
    print(e); // Catch and print the error message
  }
}

```

`Explanation:`
1. Circle Class:
The Circle class represents a circle with a given radius.
It has an instance variable radius to store the radius of the circle.
The constructor Circle(this.radius) initializes the radius variable when an instance of Circle is created

2. Factory Method:
The Circle class contains a factory method create that takes a radius parameter.
It ensures that the radius is positive and then creates and returns a new instance of Circle with the given radius.
If the provided radius is not positive, it throws an ArgumentError.

3. Calculate Area Method:
The calculateArea() method calculates the area of the circle using the formula pi * radius * radius.

4. Main Function:
In the main() function:We create instances of Circle using the factory method Circle.create() with different radii.
We call the calculateArea() method on each circle instance to calculate and print its area.