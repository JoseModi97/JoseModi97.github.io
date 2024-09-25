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

```shell
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

As per the syntax above, a class is defined using the `class` keyword followed by the class name and: operator after the class name, which allows you to continue in the next indented line to define class members.

The following are class members:

Class attributes
Constructor
Instance attributes
Properties
Class methods




A class can also be defined without any members. The following example defines an empty class using the `pass` keyword.



```bash
class Person:

    pass

```


We will discuss the class members in detail in the next lesson


## Class Attributes, Constructors, Instance Attricbutes and Class Methods Explained

### Class Attributes

Class attributes are the variables defined directly in the class that are shared by all objects of the class. Class attributes can be accessed using the class name as well as using the objects.



```bash
class Person:

    name = 'Skinny’ #Class attribute
```



Above, the name is a class attribute defined inside a class Person. The value of the name will remain the same for all the objects unless modified explicitly.



```bash
Accessing class attributes

>>> Person.name

'Skinny' 

>>> details = Person()

>>> details.name

'Skinny'
```


### Constructor

In Python, the constructor method is invoked automatically whenever a new object of a class is instantiated, same as constructors in C++ or Java.

The constructor must have a special name __init__() and a special parameter called self. 

All classes have a function called __init__(), which is always executed when the class is being initiated.

The constructor in Python is used to define the attributes of an instance and assign values to them.


NB: The first parameter of each method in a class must be the self, which refers to the calling object. However, you can give any name to the first parameter, not necessarily self.


Example of how to define a constructor:



```bash
class Person:

    def __init__(self): # constructor method

        print('Constructor invoked')

```

Now, whenever you create an object of the Person class, the __init__() constructor method will be called, as shown below.

```bash
>>>details1 = Person()

Constructor invoked

>>>details2 = Person()

Constructor invoked
```



### Instance Attributes

Instance attributes are attributes or properties attached to an instance of a class. Instance attributes are defined in the constructor.

The following example defines instance attributes name and age in the constructor.

```bash
class Person:

    nationality = 'Ethiopian' # class attribute

    def __init__(self): # constructor

        self.name = '' # instance attribute

        self.age = 0 # instance attribute

```

To access an instance variable, we use dot notation: 


[instance name].[attribute name], as shown below


```bash
>>> p1 = Person()

>>> p1.name

''

>>> p1.age

0
```

You can set the value of attributes using the dot notation, as shown below.

```bash
>>> p1 = Person()

>>> p1.name = "Mutemi" # assign value to instance attribute

>>> p1.age = 65    # assign value to instance attribute

>>> p1.name     # access instance attribute value

Mutemi

>>> std.age     # access value to instance attribute

65
```

The best practice is to always specify the values of instance attributes through the constructor. 


### Setting Attribute Values

The following constructor includes the name and age parameters, other than the self parameter.

class Person:

```bash
# name & age parameters passed in constructor

    def __init__(self, name, age): 

        self.name = name

        self.age = age
```

Passing Instance Attribute Values in Constructor

Now, you can specify the values while creating an instance, as shown below.

```bash
>>> p1 = Person('Mutemi', 65)

>>> p1.name

'Mutemi'

>>> p1.age

65
```


### Setting Default Values of Instance Attributes

Also, you can set default values to instance attributes. By doing this, if the values are not provided when creating an object, the default values will be assigned.

Lets assign name=”mkuu” and age=101
```bash
class Person:

    def __init__(self, name="mkuu", age=101)

        self.name=name

        self.age=age

```

Instance Attribute Default Value

Now, you can create an object with default values, as shown below

```bash
>>> p1 = Person()

>>> p1.name

'Guest'

>>> p1.age

65
```


### Class Methods

A python function in a class is called class method. Methods are defined using the def keyword. 
Each method must have a self as the first parameter, which refers to calling the instance.

Self is just a conventional name for the first argument of a method in the class.
A method defined as mymethod(self, a, b) should be called as x.mymethod(a, b) for the object x of the class.


Example: here we have a method named displayInfo

```bash
class Person:

    def displayInfo(self): # class method

        print('Personal Information')
```

The above class method can be called as a normal function, as shown below.

```bash
>>> p1 = Person()

>>> p1.displayInfo()


'Personal Information'
```

Let's combine our knowledge so far for class constructors and methods to access instance attributes using self parameter.

```bash
class Person:

    def __init__(self, name, age): # class constructor

        self.name = name 

        self.age = age 




    def displayInfo(self): # class method

        print('Person Name: ', self.name,', Age: ', self.age)

```


`Calling a Method`

Let's call/Invoke the displayInfo method as shown below:
```bash
>>> p1 = Person('Mutemi', 65)

>>> p1.displayInfo()

Person Name: Mutemi , Age: 65

```

## File Handling in Python
### Understanding how to read and write files

Input and Output in Python refer to the process of taking input from the user and displaying output to the user. The input function is used to take input from the user, and the print function is used to display output to the user.

`Here's a simple example to illustrate this: `

```python
name = input("Enter your name: ")
print("Hello, World")
```

In this example, the input function takes a string argument (prompt) which is displayed to the user, and it returns the user's input as a string. The input function is used to take input from the user and store it in a variable. The print function is used to display output to the user by printing its argument(s).

Another explanation is that




Input and Output in Python are two important concepts that are used to interact with the user.

Input refers to the process of taking data from the user and storing it in a program for further processing. This can be done using the input function in Python. The input function takes a string argument (prompt) which is displayed to the user, and it returns the user's input as a string.


```python
name = input("What is your name? ")
age = input("What is your age? ")
```

In the above code, the input function is used to prompt the user to enter their name and age. The input data is then stored in the variables' names and ages, respectively.




The print function, on the other hand, is used to display output to the user by printing its argument(s) to the screen. The argument(s) can be a string, variable, or expression. For example:


```python
print("Hello, "+name+ "! You are "+age+" years old")

```

Output refers to the process of displaying the result of a computation or a processing step to the user. This can be done using the print function in Python. The print function is used to display output to the user by printing its argument(s).


```python
result = 2 + 3
print("The result is:", result)
```


Output:

The result is: 5


In addition to the input and print functions, there are other ways to handle Input-Output in Python, such as reading and writing to files, using command line arguments, or using third-party libraries.




### `Why do we use Input and Output in Python:`

Input and Output are used in Python to allow the user to interact with the program. The use of Input and Output enables the program to receive data from the user and provide results to the user.

Here are some common use cases for Input and Output in Python:

1. Taking input from the user: The input function is used to take input from the user, such as a name, age, or any other type of data. The input received from the user can be stored in a variable for further processing.
2. Displaying output to the user: The print function is used to display output to the user. This can be used to display the result of a calculation, the contents of a list or dictionary, or any other type of data.
3. Reading data from a file: Input can also be taken from a file, such as a text file, CSV file, or any other type of file. This can be done using the open function in Python or using third-party libraries like Pandas.
4. Writing data to a file: Output can also be stored in a file, such as a text file, CSV file, or any other type of file. This can be done using the open function in Python or using third-party libraries like Pandas.

Input and Output are essential in making the program more interactive and user-friendly. They also allow the program to receive and provide data, which is crucial for many applications.




Python (Files I/O)

`Understanding how to read and write files:`

In Python, reading from and writing to files can be accomplished using the open function. The open function takes two arguments: the name of the file and the mode in which the file should be opened.

There are four modes in which a file can be opened in Python:

1. "r" (Read Only): This mode is used to only read the contents of a file. If the file does not exist, a FileNotFoundError will be raised.
2. "w" (Write Only): This mode is used to write to a file. If the file already exists, its contents will be truncated (i.e., deleted), and a new file with the same name will be created. If the file does not exist, a new file with the specified name will be created.
3. "a" (Append Only): This mode is used to append to an existing file. If the file does not exist, a new file with the specified name will be created.
4. "x" (Write Only, Exclusive Creation): This mode is used to write to a file only if the file does not already exist. If the file already exists, a FileExistsError will be raised.

Here's an example of how to read from a file in Python:

```python
# Open file for reading
file = open("example.txt", "r")

# Read the content of the file
content = file.read()

#print the content of the file
print(content)

# Close the file
file.close()
```

`And here's an example of how to write to a file in Python:`

```python
# Open file for writing
file = open("example.txt", "w")

#write some text to the file
file.write("Hello, world!\n")
file.write("This is a test.\n")

# Close the file
file.close()
```


It's recommended to use the with the statement when opening files in Python, as it automatically takes care of closing the file when the code block is exited, even if an exception is raised



### Reading Keyboard Input

Python provides two built-in functions to read a line of text from standard input, which by default comes from the keyboard. These functions are −
- raw_input
- input

### The raw_input Function

The raw_input([prompt]) function reads one line from standard input and returns it as a string (removing the trailing newline).


### Flat Files vs. Non-Flat Files

Flat files are data files that contain records with no structured relationships between the records, and there's also no structure for indexing like you typically find it in relational databases. These files can contain only basic formatting, have a small fixed number of fields, and can or can not have a file format.

![Desktop View](https://raw.githubusercontent.com/JoseModi97/images/refs/heads/main/Flat%20FIle.PNG){: width="972" height="589" .w-75 .normal}


### Python File Objects

Python has in-built functions to create, read, write, and manipulate accessible files. The io module is the default module for accessing files that can be used off the shelf without even importing it. Before you read, write, or manipulate the file, you need to make use of the module open(filename, access_mode) that returns a file object called "handle". After which you can simply use this handle to read from or write to a file. Like everything else, files in Python are also treated as an object, which has its own attributes and methods.

An IOError exception is raised if, while opening the file, the operation fails. It could be due to various reasons like trying to read a file that is opened in write mode or accessing a file that is already closed.

As you already read before, there are two types of flat files, text and binary files:

As you might have expected from reading the previous section, text files have an End-Of-Line (EOL) character to indicate each line's termination. In Python, the new line character (\n) is the default EOL terminator.
Since binary files store data after converting it into a binary language (0s and 1s), there is no EOL character. This file type returns bytes. This file is used when dealing with non-text files such as images, .exe, or .pyc.

Let's now understand the Python file objects in detail, along with necessary examples.


`Open()`

The built-in Python function open() has the following arguments: open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None) The open() function has almost 8 parameters along with their default values for each argument as shown above.

You would be focusing on the first and second parameters for now, which are essential for reading and writing files. And go through other parameters one by one as the tutorial progresses.

Let's understand the first argument, i.e., file.

`File`

file is a mandatory argument that you have to provide to the open function while the rest of the arguments are optional and use their default values.

To put it simply, the file argument represents the path where your file resides in your system.

If the path is in the current working directory, you can just provide the filename. If not then you have to provide the absolute path of the file, just like in the following examples: my_file_handle=open("mynewtextfile.txt") If the file resides in a directory other than the current directory, you have to provide the absolute path with the file name:

```python
my_file_handle = open("mynewtestfile.txt")
my_file_handle = open("/path/to/mynewtextfile.txt") #different folder
my_file_handle = open("c:\\path\\to\\mynewtextfile.txt") #Windows machine you can use backslashes
```


Let's understand the second argument of the open function, i.e., access modes.

`Access Modes`

Access modes define in which way you want to open a file, whether you want to open a file in:

   - read-only mode
   - write-only mode
   - append mode
   - both read and write mode

Though a lot of access modes exist as shown in the below table, the most commonly used ones are read and write modes. It specifies where you want to start reading or writing in the file.

You use 'r', the default mode, to read the file. In other cases where you want to write or append, you use 'w' or 'a', respectively.

There are, of course, more access modes! Take a look at the following table:

![Desktop View](https://raw.githubusercontent.com/JoseModi97/images/refs/heads/main/Character.PNG){: width="972" height="589" .w-75 .normal}