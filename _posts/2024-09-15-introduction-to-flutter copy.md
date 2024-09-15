---
title: Installing Flutter SDK
description:  A comprehensive description on how to install flutter sdk
author: modi
date: 2024-09-15 05:31 +0800
categories: [Flutter, Introduction]
tags: [flutter-Intro]
pin: true
math: true
mermaid: true
---

1. Download and Install Flutter SDK

Before you begin developing with Flutter, you need to set up the Flutter SDK. This involves downloading the SDK from the official Flutter website and extracting it to a location on your computer. The Flutter SDK contains all the tools and libraries you'll need to build and run Flutter applications.

Steps:

  - Visit the Flutter website: [Click Me](https://docs.flutter.dev/get-started/install) to download flutter sdk based on your operating system : Windows, macOS, or Linux.
  - Download the Flutter SDK archive: Follow the instructions on the website to download the correct archive for your system.
  - Extract the archive: Extract the downloaded archive to your desired location. This will create a flutter directory with all necessary files.

2. Add Flutter to the System Path

To use Flutter from the command line, you need to add it to your system’s PATH. This makes it easier to run Flutter commands from anywhere in your terminal or command prompt. Each operating system has its own method for updating the PATH variable.

Steps:

Windows:
  - Open System Properties: Press Win + Pause, then click on "Advanced system settings".
  - Environment Variables: Click on the "Environment Variables" button.
  - Edit Path: Find the "Path" variable in the system variables section and click "Edit".
  - Add Flutter bin directory: Add the path to the bin directory inside your Flutter installation to the Path    variable. For example, if you extracted Flutter to C:\src\flutter, you would add C:\src\flutter\bin to the   Path.
  - Save changes: Click "OK" to save the changes.
macOS:
   - Open Terminal: Open the Terminal application.
   - Edit .bash_profile or .zshrc: Open your shell configuration file (usually .bash_profile or .zshrc) in a  text editor.
   - Add Flutter to PATH: Add the following line to the file, replacing /path/to/flutter with the actual path  to your Flutter installation:
   bashCopy codeexport PATH="/path/to/flutter/bin:$PATH"
   - Save and source the file: Save the file and run source ~/.bash_profile or source ~/.zshrc to apply the   changes.
Linux:
   - Open Terminal: Open the Terminal application.
   - Edit .bashrc: Open the .bashrc file in your home directory with a text editor.
   - Add Flutter to PATH: Add the following line to the file, replacing /path/to/flutter with the actual path to your Flutter installation:
   bashCopy codeexport PATH="/path/to/flutter/bin:$PATH"
   - Save and source the file: Save the file and run source ~/.bashrc to apply the changes.

3. Verify Flutter Installation

Once you have installed Flutter and added it to your PATH, it's essential to verify that the installation was successful. Running the flutter doctor command will check your environment for missing dependencies and provide instructions for resolving any issues.

`Steps`:

Open a terminal or command prompt.
Run `flutter doctor`: This command will check your environment and show a report on any missing dependencies or issues.

4. Install Visual Studio Code

Visual Studio Code (VS Code) is a popular code editor that supports Flutter development. Installing VS Code will provide you with a powerful environment for writing and debugging your Flutter code.

`Steps`:

   - Download Visual Studio Code: [Click Me](https://code.visualstudio.com/download) to download the appropriate version for your operating system.
   - Install Visual Studio Code: Follow the installation instructions for your operating system.

5. Install Flutter and Dart Extensions

To enhance your development experience in VS Code, you need to install the Flutter and Dart extensions. These extensions provide tools and features for developing Flutter applications efficiently.

`Steps`:
   - Open Visual Studio Code.
   - Open Extensions view: Press Ctrl+Shift+X (or Cmd+Shift+X on macOS).
   - Search for Flutter: Search for "Flutter" in the Extensions view and install the Flutter extension. The Dart extension is usually installed automatically with the Flutter extension.