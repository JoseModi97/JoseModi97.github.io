---
title: OOP Paragidm
description: OOP uses objects and their interactions to design and program
author: modi
date: 2024-09-12 09:47:00 +0800
categories: [Dart, OOP]
tags: [dart-oop]
pin: true
math: true
mermaid: true
---

## Learning Objectives

- To understand KEY WORDS in object-oriented programming.
- To understand paradigms of OOP.
- Introduce Factory Methods in OOP
- Introduce Singletons in OOP
- Explain what Mixins are in OOP



### OOP In Dart

Object-oriented programming (OOP) is a programming method that uses objects and their interactions to design and program applications. It is one of the most popular programming paradigms and is used in many programming languages, such as Dart, Java, C++, Python, etc.

In OOP, an object can be anything, such as a person, a bank account, a car, or a house. Each object has its attributes (or properties) and behavior (or methods). For example, a person object may have the attributes name, age and height, and the behavior walk and talk.



### Advantages
- It is easy to understand and use.
- It increases reusability and decreases complexity.
- The productivity of programmers increases.
- It makes the code easier to maintain, modify and debug.
- It promotes teamwork and collaboration.
- It reduces the repetition of code.



### Features Of OOP
- Class
- Object
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction



### Key Points
- Object Oriented Programming (OOP) is a programming paradigm that uses objects and their interactions to - design and program applications.
- OOP is based on objects, which are data structures containing data and methods.
- OOP is a way of thinking about programming that differs from traditional procedural programming.
- OOP can make code more modular, flexible, and extensible.
- OOP can help you to understand better and solve problems.



## Classes

In object-oriented programming, a class is a blueprint for creating objects. A class defines the properties and methods that an object will have. For example, a class called Dog might have properties like breed, color and methods like bark, run.



### Declaring A class in Dart

In Dart programming, you can declare a class using the class keyword followed by the class name. Here's a simple example:

```dart
// Declaring a class in Dart

class Person {

 // Properties of the class

 String name;

 int age;

 // Constructor

 Person(this.name, this.age);

 // Method to display person details

 void displayInfo() {

  print('Name: $name, Age: $age');

 }

}

```
Class Declaration
: The class keyword is used to declare a class, followed by the class name Person.



### Objects

An object is an instance of a class. It represents a real-world entity with attributes (properties) and behaviors (methods). Objects allow you to create multiple instances of a class, each with its own unique data.


```dart
// Declaring a simple class in Dart

class Car {

 String brand;

 String model;

 Car(this.brand, this.model);

 void showDetails() {

  print('Brand: $brand, Model: $model');

 }

}

void main() {

 // Creating an object of the Car class

 Car myCar = Car('Toyota', 'Corolla');


 // Calling the method using the object

 myCar.showDetails(); // Output: Brand: Toyota, Model: Corolla

}
```




Class Declaration
: The Car class has two properties: brand and model.
: The constructor Car(this.brand, this.model); initializes these properties.

Object Creation
: Car myCar = Car('Toyota', 'Corolla'); 
: creates an object myCar of the Car class with specific values for brand and model.



## Object Oriented Programming Paradigm

### Data Encapsulation

Data encapsulation is the process of keeping a class' implementation details hidden from the user through an object's functions.

### How To Achieve Encapsulation In Dart

Encapsulation can be achieved by:

- Declaring the class properties as private by using underscore(_).
- Providing public getter and setter methods to access and update the value of private property.



### Getter and Setter Methods

Getter and setter methods are used to access and update the value of private property. Getter methods are used to access the value of private property. Setter methods are used to update the value of private property.

### `Code sample`

```dart
class Circle {
  // Private property with underscore (_)
  double _radius;

  // Constructor to initialize the radius
  Circle(this._radius);

  // Getter method to access the private radius
  double get radius => _radius;

  // Setter method to update the radius with validation
  set radius(double value) {
    if (value > 0) {
      _radius = value;
    } else {
      print('Radius must be greater than 0');
    }
  }

  // Method to calculate area of the circle
  double calculateArea() {
    return 3.1416 * _radius * _radius; // Area = πr²
  }
}

void main() {
  // Creating an instance of Circle
  Circle circle = Circle(5.0);

  // Accessing the radius using getter
  print("Initial radius: ${circle.radius}");

  // Calculating and printing the area
  print("Initial area: ${circle.calculateArea()}");

  // Updating the radius using setter
  circle.radius = 7.0;

  // Accessing updated radius and area
  print("Updated radius: ${circle.radius}");
  print("Updated area: ${circle.calculateArea()}");

  // Trying to set an invalid radius
  circle.radius = -3.0; // This will trigger validation
}
```

### Explanation

- The Circle class has a private variable _radius, which is not directly accessible from outside the class.
- The constructor initializes the _radius variable.
- Getter (get radius) allows external code to access the value of _radius.
- Setter (set radius) provides controlled access to update the value of _radius with validation.

The calculateArea method demonstrates how methods can use the encapsulated data.



### Inheritance

Generally speaking, inheritance is the process of gaining properties. OOP allows for the inheritance of properties from one object to another.

### `Code sample`

```dart
// Base class (Superclass)
class Vehicle {
  String brand;
  int year;

  // Constructor for Vehicle
  Vehicle(this.brand, this.year);

  // Method to display vehicle info
  void displayInfo() {
    print("Brand: $brand");
    print("Year: $year");
  }
}

// Derived class (Subclass) inheriting from Vehicle
class Car extends Vehicle {
  String model;

  // Constructor for Car which uses super to call the base class constructor
  Car(String brand, int year, this.model) : super(brand, year);

  // Method to display car-specific info
  void displayCarInfo() {
    displayInfo(); // Call the base class method
    print("Model: $model");
  }
}

void main() {
  // Creating an instance of the Car class
  Car car = Car('Toyota', 2021, 'Corolla');

  // Accessing methods from both base and derived classes
  car.displayCarInfo();
}
```

### Explanation

- The Vehicle class is the base class with instance variables brand and year, and a method displayInfo.
- The Car class is the derived class that extends (inherits from) the Vehicle class. It adds an additional property model and a method displayCarInfo.
- The Car constructor uses super to call the constructor of the base class (Vehicle).
- The main function demonstrates creating an instance of the Car class and accessing methods from both the base and derived classes.


### Polymorphism

Polymorphism is the practice of having many classes use the same method name while redefining it for the derived classes.

![Animals](https://raw.githubusercontent.com/JoseModi97/images/main/inheritance.PNG){: width="972" height="589" }

