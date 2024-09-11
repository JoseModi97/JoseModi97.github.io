---
title: Control Flow in Dart
description: The control statements or flow of control statements are used to control the flow of Dart program.
author: modi
date: 2024-09-11 06:11:00 +0800
categories: [Dart, ControlFlow]
tags: [dart]
pin: true
math: true
mermaid: true
---

## Control Flow In Dart

## Control Flow

The control statements or flow of control statements are used to control the flow of Dart program. These statements are very important in any programming languages to decide whether other statement will be executed or not. The code statement generally runs in the sequential manner. We may require executing or skipping some group of statements based on the given condition, jumps to another statement, or repeat the execution of the statements.



## Categories of Flow Statement

In Dart, Control flow statement can be categorized mainly in three following ways.

- Decision-making statements
- Looping statements
- Jump statements



### Decision-making Statements

Dart provides following types of Decision-making statement.

- If Statement

  Executes a block of code if a specified condition is true.

```dart
// if statement outputs depending on a certain conditional expression
void main() {
  var age = 10;
  if (age > 18) {
    print("Mariam is a voter in Kenya");
  }
  print("Mariam is still young to vote");
}
```


- If-else Statements

  In Dart, the if-else statement is used to execute a block of code based on whether a condition is true or false. Here's the syntax:

```dart
void main() {
  var age = 10;

  if (age > 18) {
    print("Mariam is a voter in Kenya");
  } else {
    print("Mariam is still too young to vote");
  }
}
```
- If else if Statement

  In Dart, the if-else if-else statement allows you to evaluate multiple conditions and execute different blocks of code based on these conditions. Here's the syntax:

```dart
void main() {
  var age = 10;

  if (age > 18) {
    print("Mariam is a voter in Kenya");
  } else if (age == 18) {
    print("Mariam is just old enough to vote in Kenya");
  } else {
    print("Mariam is still too young to vote");
  }
}

```






- Switch Case Statement

  In Dart, the switch statement is used to evaluate an expression and execute different blocks of code based on matching cases. The syntax of the switch statement is as follows:
```dart
void main() {
  int i = 3;
  switch (i) {
    case 1:
      print("The value is 1");
      break;
    case 2:
      print("The value is 2 ");
      break;
    case 3:
      print("the value is 3");
      break;
    default:
      print("The value is out of range ");
      break;
  }
}
```


## Looping Statements

  Dart Loop is used to run a block of code repetitively for a given number of times or until matches the specified condition. Loops are essential tools for any programming language. It is used to iterate the Dart iterable such as list, map, etc. and perform operations for multiple times. A loop can have two parts - a body of the loop and control statements. The main objective of the loop is to run the code multiple times. Dart supports the following type of loops.

- Dart for loop

  The for loop is used when we know how many times a block of code will execute.
  ```dart
  //The for loop is used when we know how many times a block of code will execute
  void main()  
  {  
      int num = 1;  
      for(num; num<=10; num++)           //for loop to print 1-10 numbers  
      {  
          print(num);     //to print the number  
      }  
  }  
  ```

- Dart for…in loop

  The for..in loop is similar to for loop but different in its syntax. It iterates through an object's properties. The Dart for..in loop accepts an expression as iterator and iterates through the elements one at a time in sequence. The variable var holds the values of the iteration. The for…in will execute until elements remain in iterators.

  ```dart
    //The for…in loop is slightly different from the for loop
    //It only takes dart object or expression as an iterator and iterates the element one at a time.

    void main()  
    {  
        var list1 = [10,20,30,40,50];  
        for(var i in list1)           //for..in loop to print list element  
        {  
            print(i);       //to print the number  
        }  
    }  
  ```


- Dart while loop

  The while loop is used when the number of execution of a block of code is not known. It will execute as long as the condition is true. It initially checks the given condition then executes the statements that are inside the while loop. The while loop is mostly used to create an infinite loop.

  ```dart
  void main() {
  var list1 = [10, 20, 30, 40, 50];
  int i = 0;            // Initialize index

  while (i < list1.length) {  // Loop until i is less than the length of the list
    print(list1[i]);          // Print the current element at index i
    i++;                      // Increment the index
  }
  }
  ```


- Dart do-while loop

  Dart do while loop executes a block of the statement first and then checks the condition. If the condition returns true, then the loop continues its iteration. It is similar to Dart while loop but the only difference is, in the do-while loop a block of statements inside the body of loop will execute at least once.

  ```dart
    //do…while loop is similar to the while loop but only 
  //difference is that, it executes the loop statement and then check the given condition. 

  void main()  
  {  
  var a = 1;  
  var maxnum = 10;  
  do  
      {                
        print("The value is: ${a}");  
        a = a+1;                                    
        }while(a<maxnum);  
  } 
  ```

## Jump Statements
Jump statements are used to alter the flow of control in a program by transferring the execution to a different part of the code. The main jump statements in Dart are:

1. `break Statement`: Used to exit a loop (for, while, do-while) or switch statement prematurely.
2. `continue Statement`: Used to skip the current iteration of a loop and continue with the next iteration.
3. `return Statement`: Used to exit a function and optionally return a value.

<!-- `break Statement`
---------------- -->

### `break statement`
  ```dart
  void main() {
    for (int i = 0; i < 5; i++) {
      if (i == 3) {
        break; // Exit the loop when i equals 3
      }
      print(i); // Output: 0, 1, 2
    }
  }

  ```