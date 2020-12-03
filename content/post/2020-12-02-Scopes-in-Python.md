---
URL: /2020/12/02/Scopes/in/Python
author: Adrian Gabriel
categories:
- Python
date: "2020-12-01 09:00:00"
description: Understanding scopes in Python
excerpt: Understanding scopes in Python
image: "img/taghia.jpg"
published: true
subtitle: Learn about how scopes work in Python
tags:
- Python
- Software Engineering
title: Understanding scopes in Python
output:
  html_document:
    keep_md: true
    toc_float: true
    toc: true
    toc_depth: 3.0
    code_download: true
    theme: paper
    highlight: kate
---

# Scopes
The scoping rules define which names and variables are visible in a
given environment. There are different **namespaces** within in an application.
There is an enclosing environment which defines all the names that are available
outside of a function or class.

## Global variables
Variable is usable within the function but you can not change it's value.

```python
z = 100

def f():
  return z+1

f()
```

```
## 101
```

```python
print("Value of z: {}".format(z))
```

```
## Value of z: 100
```
If you redefine a variable within a function than this variable is separat from
the global variable. In this example we didn't use the global variable but
a separat one.

```python
z = 100

def f():
  z=200
  return z

f()
```

```
## 200
```

```python
print("Value of z: {}".format(z))
```

```
## Value of z: 100
```

The Python interpreter searches for variables in this sequence:
* Local
* Enclosing
* Global
* Predefined

What will this function return?


```python
a = 'Globale Variable a'
b = 'Globale Variable b'
def funktion():
    b = 'Enclosing Variable b'
    c = 'Enclosing Variable c'
    print(a) # 'Globale Variable a'
    print(b) # 'Enclosing Variable b'
    
    def funktion_inner():
        c = 'lokale Variable c'
        print(a) # Global Variable a
        print(b) # 'Enclosing Variable b'
        print(c) # 'Enclosing Variable c'
    funktion_inner()
    print(c)
funktion()
```

```
## Globale Variable a
## Enclosing Variable b
## Globale Variable a
## Enclosing Variable b
## lokale Variable c
## Enclosing Variable c
```
