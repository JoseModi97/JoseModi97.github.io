---
title: Singletons
description:  A class has only one instance and also provides a global point of access to it. 
author: modi
date: 2024-09-15 04:30:00 +0800
categories: [Dart, OOP]
tags: [dart-oop]
pin: true
math: true
mermaid: true
---

The singleton pattern is a pattern used in object-oriented programming which ensures that a class has only one instance and also provides a global point of access to it. Sometimes it's important for a class to have exactly one instance, or you might force your app into a weird state. For example, you only want one instance of a class that represents your local storage, or you may end up with two different sources of data, which are out of sync. For the same reason, an operating system should have exactly one file system.



The idea is that anywhere in your code that you call MyClass(), it will return the same instance of that class, with the same state, etc. Thanks to factory constructors, implementing the singleton pattern in Dart is not only possible, but simple and flexible.


```dart
// Singleton class to manage file system operations
class FileSystemManager {
  // Static and final instance variable to hold the single instance of the class
  static final FileSystemManager _instance = FileSystemManager._internal();

  // Private constructor to restrict external instantiation
  FileSystemManager._internal();

  // Factory constructor to control the creation of the singleton instance
  factory FileSystemManager() {
    return _instance; // Always returns the same instance
  }

  // Method to simulate opening a file
  void openFile(String fileName) {
    print('Opening file: $fileName');
  }

  // Method to simulate writing to a file
  void writeFile(String fileName, String content) {
    print('Writing to file: $fileName with content: "$content"');
  }
}

void main() {
  // Create two references to the FileSystemManager singleton instance
  FileSystemManager manager1 = FileSystemManager(); // Uses factory constructor
  FileSystemManager manager2 = FileSystemManager(); // Returns the same instance

  // Verify that both references point to the same singleton instance
  print('Are manager1 and manager2 the same instance? ${identical(manager1, manager2)}');
  print('HashCode of manager1: ${manager1.hashCode}');
  print('HashCode of manager2: ${manager2.hashCode}');

  // Calling methods on both references
  manager1.openFile("data.txt");    // Opens the file using manager1
  manager2.writeFile("data.txt", "Hello, Dart!"); // Writes to the file using manager2
}

```

1. Singleton Design Pattern:

- The FileSystemManager class is implemented using the Singleton design pattern, which ensures that there is only one instance of the class throughout the application's lifecycle.

2. Static Instance Variable:

- The _instance variable is declared as static and final, meaning it is associated with the class itself rather than with instances of the class. This variable holds the single instance of the FileSystemManager class.

3. Private Constructor:

- The _internal constructor is private, indicated by the underscore _, meaning it can only be accessed from within the FileSystemManager class. This constructor is used for initialization logic and is called only once to create the singleton instance of the class.

4. Factory Constructor:

- The FileSystemManager class provides a factory constructor that ensures only one instance of the class is returned. This factory constructor checks if _instance is null, and if so, it creates a new instance using the private _internal constructor. Otherwise, it returns the existing instance.

5. Usage:

- In the main() function, two instances of FileSystemManager named manager1 and manager2 are created.
The hashCode comparison confirms that both manager1 and manager2 reference the same singleton instance, as expected in a Singleton pattern.
- The openFile() and writeFile() methods of FileSystemManager are called on manager1 and manager2, respectively, demonstrating that both instances share the same behavior implemented by the singleton instance.