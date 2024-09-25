---
title: OOP Asynchronous Functions
description:  Object-Oriented Programming (OOP) is a programming paradigm in computer science that relies on the concept of classes and objects.
author: modi
date: 2024-09-25 09:05 +0800
categories: [Python, OOP]
tags: [python, oop, asynchronous-functions]
pin: true
math: true
mermaid: true
---

## Introduction To Object Oriented Programming

### Object Oriented Programming
Object-Oriented Programming (OOP) is a programming paradigm in computer science that relies on the concept of classes and objects. It is used to structure a software program into simple, reusable pieces of code blueprints (usually called classes), which are used to create individual instances of objects.

### Building blocks of OOP
1. Classes - a blueprint of an object
2. Objects - an instance of a class
3. Methods - methods represent behaviors
4. Attributes - information to be stored in a class about an object

### Four Principles of OOP
The four pillars of object-oriented programming are:
1. Inheritance: child classes inherit data and behaviors from the parent class
2. Encapsulation: containing information in an object, exposing only selected information
3. Abstraction: only exposing high-level public methods for accessing an object
4. Polymorphism: many methods can do the same task


### What are the benefits of OOP?

Modularity

: Encapsulation enables objects to be self-contained, making troubleshooting and collaborative development easier.

Reusability

: Code can be reused through inheritance, meaning a team does not have to write the same code multiple times.

Productivity 

: Programmers can construct new programs quickly through the use of multiple libraries and reusable code.

Easily upgradable and scalable 

: Programmers can implement system functionalities independently.
Interface descriptions

: Descriptions of external systems are simple, due to message-passing techniques that are used for object communication.

Security 
: Using encapsulation and abstraction, complex code is hidden, software maintenance is easier and internet protocols are protected.

Flexibility
: Polymorphism enables a single function to adapt to the class it is placed in. Different objects can also pass through the same interface.

## Python Classes/Objects

Python is a completely object-oriented language. You have been working with classes and objects right from the beginning of this course. 

Every element in a Python program is an object of a class, with its properties and methods. A Class is like an object constructor or a "blueprint" for creating objects.

A number, string, list, dictionary, etc., used in a program is an object of a corresponding built-in class. You can retrieve the class name of variables or objects using the type() method, 

```python
>>> num=20

>>> type(num)

<class 'int'>            

>>> s="Python"

>>> type(s) 

<class 'str'>
```


### Create a Class

A class in Python can be defined using the class keyword.




`Syntax`:



```bash
class <ClassName>:

    <statement1>

    <statement2>

    .

    .

    <statementN>

```