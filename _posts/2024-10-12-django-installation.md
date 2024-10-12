---
title: Django Installation
description:  An brief description of the architecture of django framework
author: modi
date: 2024-10-12 09:11 +0800
categories: [Django, Installation]
tags: [python, django, framework]
pin: true
math: true
mermaid: true
---

## Django Installation

Python recommends using a virtual environment to build Python applications.


`Note: A virtual environment` is an isolated environment having its copy of the interpreter and libraries so that there’s no clash with the global installation of Python.


Python’s virtual environment is set-up with the help of a built-in module named venv. For example:




### To create a Virtual Environment

`python -m venv myenv` - Here `myenv` is the name of the Environment


To activate the Virtual Environment, Run this command:

`For windows:` .\myenv\Scripts\activate

`For Linux:` source myenv/bin/activate



After the virtual environment is activated, install the Django framework with the following command:

(myenv) c:\django> pip3 install django


Django comes with some other 3 libraries, to view the libraries in terminal, use the command below:

   - pip freeze

To append the libraries in a requirements.txt file use:

   - pip freeze > requirements.txt

To install available libraries listed in the requirements.txt file, make sure your target virtual environment is active and run the following command:



pip install -r requirements.txt


The VS Code software can be launched from within this folder as follows:  

(myenv) C:\django>code .




## Working with virtual environments on your local machine

While working with Django, you must first go to the local directory where you want to 

create your project and set up a virtual environment.

Ensure pip is installed on your device. The latest version can be installed and upgraded by using the command:



For Windows:

py -m pip install --upgrade pip


For macOS:

python3 -m pip install --user --upgrade pip

venv (for Python 3) and virtualenv (for Python 2) allow you to manage separate package installations for different projects. 




You can create a virtual environment in the specific project directory by running a command:

Windows

python -m venv myenv


macOS/Linux

python3 -m venv myenv


Note:

myenv is the name assigned to the virtual environment and this will create a virtual Python installation in the myenv folder.


## Activate the virtual environment

Next you need to activate the virtual environment. will put the virtual environment-specific python and pip executables into your shell’s PATH.

You can do this by running a command such as:

Windows:

.\myenv\Scripts\activate

MacOS:

source myenv/bin/activate




## Exit the virtual environment

You can exit the virtual environment by running the command:

MacOS and Windows use the command:

deactivate


Note: 

venv is not the only option available for creating virtual environments other options exist such as pipenv which is another variation.

However, in this module, the use of venv is recommended.



## Check Django Version

You can check if Django is installed by asking for its version number like this:


(myenv) >python -m django --version


If Django is installed, you will get a result with the version number:

4.0.3