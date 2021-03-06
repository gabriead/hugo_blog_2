
---
URL: 020-12-02-Command-vs-expression-in-python
author: Adrian Gabriel
categories:
- Python
date: "2020-12-01 09:00:00"
description: Command vs. expression in Python
excerpt: Command vs. expression in Python
image: "img/taghia.jpg"
published: true
subtitle: Learn about the difference between a command an expression in Python
tags:
- Python
- Software Engineering
title: Command vs expression in Python
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

# Command vs. Expression

An **expression is a value** that does not change the state of the program. What do I mean by that?
A change in state can be achieved by referencing to a different value for instance. 
A value can be anything of the following:
* string
* list, tuple or a function
* `sorted(list)`

A **command** on the contrary **changes the state of a program**. The `print()` statement
changes the state of the monitor for instance.
Examples are:
* `list.append()`
* `print()`
* `list.sort()`

Let's summarize what we just learned about expressions and commands in a code snippet.


```python

# Adding to a list using +-Operator is an expression =>  returns a value
l=[1,2,3]
l+=[4]

# Adding to a list using append is a command => does not return a value
l=[1,2,3]
return_value_append = l.append(4)
print("Append() has a return value of: {} ".format(return_value_append))

# Sorting using sorted(aList) is an expression => returns a value
```

```
## Append() has a return value of: None
```

```python
l=[3,2,1]
return_value_sorted=sorted(l)
print("Append() has a return value of: {} ".format(return_value_sorted))

# Sorting using aList.sorted() is a command => does not return a value
```

```
## Append() has a return value of: [1, 2, 3]
```

```python
l=[3,2,1]
return_value_sort = l.sort()
print("Append() has a return value of: {} ".format(return_value_sort))
```

```
## Append() has a return value of: None
```

## `if` expression
You can use the `if` statement as an expression as well.

```python
x = 10 if len("hello") < 20 else 100
```
