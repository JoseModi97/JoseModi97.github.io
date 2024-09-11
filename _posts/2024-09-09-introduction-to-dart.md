---
title: Introduction To Dart
description: Dart is an open-source programming language developed by Google
author: modi
date: 2024-09-09 16:21:00 +0800
categories: [Dart, Introduction]
tags: [chapter1]
pin: true
math: true
mermaid: true
---


## Learning Objectives

- To introduce Dart as a modern, object-oriented, and statically typed programming language.
- To install the Dart SDK and set up Visual Studio Code for Dart development.
- To understand basic Dart syntax, including variables, data types, and operators.
- To learn about control flow statements (if, else, switch, loops) in Dart.


## Introduction to Dart

Dart is an open-source programming language developed by Google. It is used to create mobile, web and desktop applications. It is also used to develop server-side applications. Dart is a strongly typed language, which means that the compiler will detect any errors in the code before the code is compiled.


Currently, Dart is one of the most preferred languages to learn. A solid understanding of Dart is necessary to develop high-quality apps with flutter. According to Github, Dart is one of the most loved programming languages in the world.

If you know languages like C, Java, C#, Javascript, etc. Dart will be easy for you. This course covers Dart and flutter from basic to advanced.

Dart is a powerful and versatile language that can be used for a wide range of applications. Whether you're a beginner or an experienced programmer, it's worth taking the time to learn this language. It's sure to become an important part of your development toolkit.

### Dart Features 

  Dart also has several features that make it easier to learn and use compared to other languages. For example, it has a simple syntax and a flexible type system. It also has built-in support for asynchronous programming, which makes it easier to write code that runs concurrently. Below are interesting things about Dart:

- Free and open-source.
- Object-oriented programming language.
- Used to develop android, iOS, web, and desktop apps fast.
- Can compile to either native code or javascript.
- Offers modern programming features like null safety and asynchronous programming.
- You can even use Dart for servers and backend.

### Why Learn Dart?

There are several reasons why learning Dart can be beneficial:

- Easy to Learn: Dart has a clean and intuitive syntax, making it easy for beginners to grasp the basics of programming.
- Fast Development: Dart offers a range of features and tools that enable rapid development, allowing developers to build applications more efficiently.
- Platform-Independent: Dart can be used to develop applications for various platforms, including web, mobile, and desktop, making it a versatile language.
- Strong Type System: Dart has a strong type system that helps catch errors at compile-time, resulting in more reliable and bug-free code.


## Installing Dart

There are multiple ways to install a dart sdk on your system. You can install Dart on Windows, Mac, and Linux or run it from the browser.

### System requirements

- Windows
  - Supported versions: Windows 10 and 11.
  - Supported architectures: x64, IA32, ARM64
  - Support for ARM64 is experimental, and is available only in the dev channel.


- macOS
  - Supported versions: Latest three major versions. Dart supports the following macOS versions as of November 2022:
  - macOS 11 (Big Sur)
  - macOS 12 (Monterey)
  - macOS 13 (Ventura)
  - Supported architectures: x64, ARM64.
- Linux
  - Supported versions: [Debian](https://www.debian.org/releases/) stable and [Ubuntu](https://wiki.ubuntu.com/Releases) LTS under standard support.
  - Supported architectures: x64, IA32, ARM64, ARM, RISC-V (RV64GC).
  - Support for RISC-V is experimental, and is available only in the dev channel.


## Installing Dart SDK on windows

Installing the Dart SDK on Windows is a simple process that can be completed in just a few steps.

1. Download the Dart SDK from the official website
: Visit the official Dart website <https://dart.dev> or click here <https://dart.dev/get-dart/archive> to go directly to the download page and download the Dart SDK that is appropriate for your version of Windows.

2. Install the Dart SDK
: Once the download is complete, unzip the file and store it in drive C

3. Set the PATH environment variable
: Once the installation is complete, you need to set the PATH environment variable so that the Dart SDK can be used from the command line. To do this, open the Control Panel and select "System and Security" then "System". Click the "Advanced system settings" link and then the "Environment Variables" button. In the "System Variables" section, find the "Path" variable and edit it. Add the path to the Dart SDK bin directory (e.g. "C:\dart-sdk-2.4.1\bin") to the end of the existing value.

4. Verify the installation
: Open a command prompt and type "dart --version". This should print the version of the dart sdk you have installed.


## Creating a basic Dart program
Creating a basic program in Dart that prints "Hello World" is a great way to get familiar with the Dart programming language. In this lesson, we will be walking through the steps to create a basic Dart program that prints "Hello World". 

Step 1: Create a New Dart Project
: Once you have installed the Dart SDK, you can create a new Dart project. This can be done using an IDE (Integrated Development Environment) such as Visual Studio Code or IntelliJ, throughout this course we will be using VS Code. Once you have opened VS Code, you can create a new Dart project by selecting the “Open folder” option and select the folder where you want to store your dart program. 

Step 2: Write the Program
: This is a simple dart program that prints Hello World on screen. Most programmers write the Hello World program as their first program.Lets do it!



```dart
void main() {
  print('Hello, World!');
}
```

This code will print the words “Hello World” to the console when the program is run. 

Step 3: Congratulations! 
: If all went well, you should now have a basic Dart program that prints “Hello World” to the console. Congratulations! You have now created a basic Dart program!

### Variables in Dart

## Understanding Variables in Dart:

Variables are used to store data that can be used and manipulated throughout your program. In Dart, you can declare variables using var, final, or const. The choice depends on whether the variable's value is intended to be mutable or immutable.

```dart
void main() {
  // Declaring and initializing variables
  String name = 'Alice';     // String variable
  int age = 25;              // Integer variable
  double height = 5.6;       // Double (floating-point number) variable
  bool isStudent = true;     // Boolean variable

  // Printing the values of the variables
  print('Name: $name');
  print('Age: $age');
  print('Height: $height');
  print('Is Student: $isStudent');

  // Modifying a variable
  age = 26;
  print('Updated Age: $age');
}
```