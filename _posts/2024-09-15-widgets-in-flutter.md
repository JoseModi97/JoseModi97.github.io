---
title: Widgets In Flutter
description:  Widgets are the core components of any Flutter application
author: modi
date: 2024-09-15 06:31 +0800
categories: [Flutter, Widgsts]
tags: [flutter-widgets]
pin: true
math: true
mermaid: true
---

Widgets are the core components of any Flutter application. Everything in Flutter is a widget, from simple UI elements like text and buttons to complex layouts and entire screens. Widgets are designed to be highly customizable and reusable, allowing developers to create flexible and responsive user interfaces.

## Types of Widgets
1. Stateless Widgets:
- Definition: These widgets are immutable, meaning their properties do not change once they are built. They are ideal for displaying static content.
### Examples of Stateless Widgets
   - Text: Displays a string of text.
   - Icon: Displays an icon from the material design icons library.
   - Image: Displays an image from the internet or local assets.
   - Container: A versatile widget that can be used for styling, positioning, and sizing other widgets.
2. Stateful Widgets
- Definition: These widgets maintain a state that can change over time. They are useful for interactive elements that need to update based on user input or other events. 
### Examples of Stateful Widgets
   - Checkbox: Allows users to select or deselect an option.
   - Slider: A widget that lets users select a value from a range.
   - Form: A group of form fields like text fields, checkboxes, and buttons that can validate and submit user input.


## Building a Simple UI with Widgets:

By combining different widgets, you can build complex UIs. For example:

- Use a Column widget to arrange a group of widgets vertically.
- Wrap a Text widget inside a Padding widget to add space around the text.
- Place a Button widget within a Container to style it with background color, padding, and borders.

### Creating a Basic Flutter App

#### Step 1: Create a New Flutter Project

- Open Your IDE: Start by launching Visual Studio Code.
- Create a New Flutter Project:
- Open a terminal or command prompt.
- Create a new Flutter project using the flutter create command:

(flutter create your_project_name)

- Replace your_project_name with your desired project name.
- Alternatively, use Visual Studio Code's command palette:
- Open the command palette: Press Ctrl + Shift + P (Windows/Linux) or Cmd + Shift + P (macOS).
- Type Flutter: New Project: Start typing "Flutter: New Project" and select it when it appears in the list.
- Name your project and choose a location: Enter a name for your project and select a location on your file system to save it.
- Open the main.dart file:
- Navigate to the lib folder within your project.
- Open the main.dart file to start editing your Flutter application's entry point.

#### Step 2: Modify the main.dart File

Replace the Default Code: Delete the default code in main.dart and replace it with the following:

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Hello Flutter App'),
        ),
        body: MyHomePage(),
      ),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: <Widget>[
          Text(
            'Hello, Flutter!',
            style: TextStyle(fontSize: 24),
          ),
          SizedBox(height: 20),
          ElevatedButton(
            onPressed: () {
              print('Button Pressed!');
            },
            child: Text('Press Me Please'),
          ),
          SizedBox(height: 20),
          Image.network(
            'https://tinyurl.com/bdfd544u',
          ),
        ],
      ),
    );
  }
}
```

`Explanation of the Code`:

- import 'package:flutter/material.dart';: This line imports the Flutter material design library, which contains pre-designed widgets that adhere to the Material Design guidelines.
- runApp(MyApp());: This function is the entry point of the app. It loads the MyApp widget.
- StatelessWidget: The MyApp and MyHomePage classes extend StatelessWidget, meaning they are immutable and do not maintain any internal state.
- MaterialApp: This widget acts as the root of the app, setting up various properties like the home screen and themes.
- Scaffold: Provides the basic visual structure for the app, including an app bar and a body.
- AppBar: This widget displays a title at the top of the app.
- Center: Centers its child widgets within itself.
- Column: Arranges its children vertically.
- Text: Displays the "Hello, Flutter!" text.
- ElevatedButton: A button that triggers an action (printing to the console) when pressed.
- Image.network: Displays an image from a provided URL.

#### Step 3: Run the App

- Run the Flutter App:
- In Visual Studio Code: Open the terminal and type flutter run.
- Interact with the App:
      - You should see "Hello, Flutter!" text in the center of the screen, a button labeled "Press Me" that prints "Button Pressed!" to the console when clicked, and an image loaded from the internet below the button.
- View Console Output: Check the console in your IDE to see the "Button Pressed!" message when the button is clicked.