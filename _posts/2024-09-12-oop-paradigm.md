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