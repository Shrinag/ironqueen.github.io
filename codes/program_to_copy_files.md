[Home](./../index.html) [About](./../about.html) [Codes](./../codes.html) 

# Program to copy files

6th July, 2019

by Nagashri Krishnamurthy and [Arun Prasaad Gunasekaran](http://fluidiccolours.in)

[TOC]

## What is this?

Suppose you have multiple ``DCIM`` folders in your Iphone or Android devices and each folder has many subfolders inside them with photos in them.

It can get tedious to move all the files from all the subfolders to one main folder.

This program helps to automate the file transfer.

## Prerequisites

* Basics of Python
* Basic understanding of directory and folder structures in an OS
* Knowledge of ``os`` library

## Walk through

First, let's import the ``os`` library from python and feed the working directory to it.

```python
import os
root = os.getcwd()
# work = 'E:/test'
work = input("Give the working directory:")
```

List down all the folders in the ``work`` directory.

```python
Folders = os.listdir(work)
```

Now, from this list, let's keep only the ``DCIM`` folders.

```python
DCIM_Folders = []
for folder in Folders:
    # print(folder[0:4])
    if folder[0:4] == 'DCIM':
        DCIM_Folders.append(folder)
```

Next, we go into each ``DCIM`` folder and list down all the subfolders. And in each subfolder, we list down all the files. Using a for loop, and ``os.rename`` method to move the individual files to the first subdirectory in each ``DCIM`` folder.

```python
for DCIM in DCIM_Folders:
    new_path = work + "/" + DCIM
    # print(os.listdir(new_path))
    subfolders = os.listdir(new_path)
    # print(new_path, subfolders)
    
    for subfolder in subfolders[1:]:
        m_path = new_path + "/" + subfolders[0]
        print(subfolder)
        subpath = new_path + "/" + subfolder
        
        files = os.listdir(subpath)
        print(files)
        for file in files:
            source = subpath + '/' + file
            destination = m_path + '/' + file
            os.rename(source, destination)

```



## Full Program



```python
# -*- coding: utf-8 -*-
"""
Created on Sat Jul  6 20:09:24 2019

@author: Lenovo
"""

import os

root = os.getcwd()

# work = 'E:/test'

work = input("Give the working directory:")

# print(os.path.isdir(work))

# go to main folder
# os.chdir(work)
# print(os.getcwd())

# print(os.listdir(work))

Folders = os.listdir(work)
# print(Folders)

DCIM_Folders = []
for folder in Folders:
    # print(folder[0:4])
    if folder[0:4] == 'DCIM':
        DCIM_Folders.append(folder)

# print(DCIM_Folders)

for DCIM in DCIM_Folders:
    new_path = work + "/" + DCIM
    # print(os.listdir(new_path))
    subfolders = os.listdir(new_path)
    # print(new_path, subfolders)
    
    for subfolder in subfolders[1:]:
        m_path = new_path + "/" + subfolders[0]
        print(subfolder)
        subpath = new_path + "/" + subfolder
        
        files = os.listdir(subpath)
        print(files)
        for file in files:
            source = subpath + '/' + file
            destination = m_path + '/' + file
            os.rename(source, destination)

```

