---
title: Django Project Structure
description:  Python's standard library contains the venv module. 
author: modi
date: 2024-10-12 09:29 +0800
categories: [Django, Structure]
tags: [python, django, framework]
pin: true
math: true
mermaid: true
---



## Setting Up Django Project

When installing Django globally or in a virtual environment, Python recommends using isolated environment libraries and other dependencies required for a particular application.

`Python's standard library contains the venv module. `

It installs a command-line utility called Django-admin in the system path and is located in the scripts folder of your current Python environment.

As the name suggests, you use the  `django-admin` utility to perform various administrative tasks.

These tasks include creating the project and app, performing `migrations` to generate database tables, whose structure matches data models, and running a development server.

## What is a project?

When you set out to build a modular, extensible and scalable web application, you need an arrangement that controls the standard features of its various sub-modules.

A Django project is a Python package containing the database configuration used by various sub-modules (Django calls them apps) and other Django-specific settings.


Use the startproject command of Django-admin to create a project named dproject as follows: 

django-admin startproject dproject


The startproject is Django’s default project template. It creates the following file structure in the Python environment: 

```bash
dproject

│ manage.py

│

└───demoproject

asgi.py

settings.py

urls.py

wsgi.py

__init__.py
```

![](https://raw.githubusercontent.com/JoseModi97/images/refs/heads/main/2ee95324-04c3-42cf-82fa-11f7f233fc0c.png){: width="972" height="589" }

You can see a folder named dproject is created in the Python environment folder. 

It contains a script manage.py and another folder of the same name.

You will learn more about the files in the inner folder later.

The manage.py script inside the outer dproject folder has the same role as the django-admin utility.

You can use it to perform various administrative tasks. In that sense, it is a local copy of the django-admin utility.


### manage.py

The manage.py script can perform everything that the django-admin utility does. However, using manage.py is more straightforward, especially if you are required to work on a single project.

If you have multiple projects, use django-adminand specify the settings, we will deal with this shortly.

The general usage of manage.py is as follows: 

python manage.py <command>

Some of the commands include:

startapp command: - a Django project folder can contain one or more apps. An app is also represented by a folder of a specific file system. The command to create an app is: 

   - python manage.py startapp <name of app>
   - eg python manage.py startapp myapp

### makemigrations

Django manages the database operations with the ORM(Object Relational Mapping) technique. Migration refers to generating a database table whose structure matches the data model declared in the app.

The following command should be run whenever a new model is declared. 

python manage.py makemigrations


### migrate

This command option of manage.py synchronizes the database state with the currently declared models and migrations. 

python manage.py migrate

### runserver

This command starts Django’s built-in development server on the local machine with IP address 127.0.0.1 and port 8000.  It helps if you don't use this development server in the production environment.



```bash
python manage.py runserver
```

### settings.py

Django configures specific parameters with their default values and puts them in this file.

The django-admin utility and manage.py script use these settings while performing various administrative tasks.

### urls.py

This script contains a list of object urlpatterns. Every time the client browser requests a URL, the Django server looks to match its pattern and routes the application to the mapped view.

The default structure of urls.py contains a view mapped to the project’s Admin site.

### asgi.py

This file is used by the application servers following the ASGI (Asynchronous Server Gateway Interface) standard to serve asynchronous web applications.

### wsgi.py

Many web application servers implement the WSGI (Web Server Gateway Interface) standard. This script is the entry point for such WSGI-compatible servers to serve your classical web application. 

### INSTALLED_APPS

This is a list of strings. Each string represents the path of an app inside the parent project folder. The startproject template installs some apps by default. They appear in the INSTALLED_APPS list. It is located in the settings.py file.

This list must be updated by adding its name whenever a new app is installed.


For example, to create a django app called demoapp, we use this following command:

python manage.py startapp demoapp


Then, add the 'demoapp' string inside the INSTALLED_APP list.



### Databases

This attribute is a dictionary that specifies the configuration of one or more databases to be used by the current Django application. By default, Django uses the SQLite database. Hence, this setting has a pre-defined configuration for it.



```python
DATABASES = {

'default': {

'ENGINE': 'django.db.backends.sqlite3',

'NAME': BASE_DIR / 'db.sqlite3',

}

}

```

The default name of the SQLite database is db.sqlite3, which is created in the parent project folder.

In place of SQLite, you may choose to use any other. For example, for MySQL, the database settings could be as follows:



```python
DATABASES = {

'default': {

'ENGINE': 'django.db.backends.mysql',

'NAME': 'djangotest',

'USER': 'root',

'PASSWORD': 'password',

'HOST': '127.0.0.1',

'PORT': '3306',

}

}
```



### DEBUG = True

By default, the development server runs in debug mode. This helps develop the application as the server picks up changes in the code and the output can be refreshed without restarting. However, it must be disabled in the production environment.




### ALLOWED HOSTS

This attribute is a list of strings. By default, it is empty. Each string represents the fully qualified host/domain where this Django site can be served. For example, to make the site running on localhost externally visible, you may add 0.0.0.0:8000 to this list.


### ROOT_URLCONF

This setting is a string pointing toward the urls.py module in which the project’s URL patterns are found. In this case, it would be:

ROOT_URLCONF = 'dproject.urls'

### STATIC_URL

This setting points to the folder where the static files, such as JavaScript code, CSS files and images, are placed. Usually, it is set to 'static/' corresponding to the folder of this name in the parent project folder.


### Test the installation

After creating the project, to verify that it is built correctly, start the development server with the following command while remaining in the project’s parent folder:


```bash
python manage.py runserver
```


On the terminal, you will see IP address: http://127.0.0.1:8000/, hold CTRL and click on it. You should see.....