---
layout: post
title:  "Fileop module in Python"
date:   2018-10-22
desc: "A filehandling module for python written to reduce writting efforts"
keywords: "python,pypi,pip,website,blog"
categories: [Project,Python]
tags: [open source,python,PIP]
icon: icon-python
---
[![PyPi Version][pypiversion-button]][pypi]
![Python Versions][pyversion-button]

[pypiversion-button]: https://img.shields.io/badge/pypi-v0.0.3-green.svg
[pypi]: https://pypi.org/project/fileop/
[pyversion-button]: https://img.shields.io/badge/python-3.4%20%7C%203.5%20%7C%203.6%20%7C%203.7-blue.svg

Fileop is a python module written for handling files without maintaining file pointers. It helps to Read, Write, Create, Delete, Append data of file as well as to get permissions, owner and group of files. It also helps to load remote file data to local file or to a variable.

## Installation
This package is deployed on Python Package Index i.e. PyPi so you can download it by simple command

```sh
$ pip3 install fileop 
```

## Usage example

This modules is not available with python itself need to download by ```pip3 install``` and works for only _python3+_ version. 

Fileop(file Operation) having 3 classes;
```
Fileop____
          \---->(file)
           \--->(fstat)
            \-->(net)

file---|--- append()
       |--- copy()
       |--- count()
       |--- create()
       |--- delete()
       |--- read()
       |--- write()

fstat--|--- owner()
       |--- group()
       |--- size()
       |--- perm()

net----|--- load_data()
```
## Functions
-   import fileop
    ```python
    >>> import fileop
    ```
-   import file from fileop
    ```python
    >>> from fileop import file
    ```

    -   file.**create("abc.txt")**
        
        return a boolen value, If file is generated then _True_ else _False_. You can pass name of file as a argument or assign name to _file.name_ and call _file.create()_

        ```python
        >>> file.create("abc.txt")

                or

        >>> file.name="abc.txt"
        >>> file.create()
        ```

## Development setup

if you want to contribute:

```sh
$ git clone https://github.com/saurabhlondhe/fileop.git
$ cd fileop
$ python3
    >>> import fileop as f
```

## Release History

* 0.0.3
    * FIX: bugs fixed and stable release
* 0.0.2
    * Not released
    * ADD: fstat,net
* 0.0.1
    * The first proper release
    * ADD: File class with few methods
* 0.0.0
    * Work in progress

## Meta

Saurabh Londhe – [About](https://saurabhlondhe.github.io) – saurabhlondhe1111@gmail.com.com



## Contributing

1. Fork it (<https://github.com/saurabhlondhe/fileop/fork>)
2. Commit your changes (`git commit -am 'Add some'`)
3. Push to the branch (`git push origin`)
4. Create a new Pull Request