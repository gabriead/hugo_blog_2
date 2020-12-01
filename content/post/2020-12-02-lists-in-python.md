
---
URL: /2020/12/02/lists-in-python/
author: Adrian Gabriel
categories:
- Python
date: "2020-12-01 09:00:00"
description: Learn about list as a data structure
excerpt: Python
image: "img/taghia.jpg"
published: true
subtitle: The fundamentals of lists
tags:
- Python
- Data Science
title: "Lists in Python"
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

# `Lists`
In this post I assume that you are already familiar with the basics of the list as a data structure as such.
I will show you different possibilities of accessing elements within a list.

## Indexing a list
In order to retrieve an element from the list you can use an index. Let's see an example.


```python
a_list = [1,2,3,4,5]
index = 1
print("Element at {} is :".format(index),  a_list[index])
```

```
## Element at 1 is : 2
```
A `string` is also represented as a list of single characters. Therefore you can index it just as you would with
a list. Here is how.


```python
a_string = 'i am some random string'
index = 0
print("Element at {} is :".format(index),  a_string[index])
```

```
## Element at 0 is : i
```



```python
a_string = 'i am some random string'
index = 0
print("Element at {} is :".format(index),  a_string[index:5])
```

```
## Element at 0 is : i am
```

## Creating list of lists
In python a list is not typed that means it can contain all sorts of things.
It could be a mixture of strings, lists and other objects. Sounds confusing?
Don't worry they behave just as you would expect them to.
Here is an example.


```python
mixed_list = ['string', 5, ['a',2,3,], dir(str)]
index1 = 0
index2 = 2
index3 = 3

print("Element at {} is :".format(index1),  mixed_list[index1])
```

```
## Element at 0 is : string
```

```python
print("Element at {} is :".format(index2),  mixed_list[index2])
```

```
## Element at 2 is : ['a', 2, 3]
```

```python
print("Element at {} is :".format(index3),  mixed_list[index3])
```

```
## Element at 3 is : ['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'removeprefix', 'removesuffix', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```
And of course just as we indexed the "outer" list we can index further into each single list if we like.
Like so:


```python
mixed_list = ['string', 5, ['a',2,3,], dir(str)]
index1 = 0
index2 = 2

print("Element at {} is :".format(index1),  mixed_list[index1][index2])
```

```
## Element at 0 is : r
```

```python
print("Element at {} is :".format(index2),  mixed_list[index2][index2])
```

```
## Element at 2 is : 3
```
A very important feature of a `list` is that it is mutuable. What the hell does that mean?
See an example here:


```python
mixed_list = ['string', 5, ['a',2,3,], dir(str)]
index1 = 0
index2 = 2
```

## `List`-Operators
Similar to the class `str` the list class also provides special functionality.

### `+` and `*` Operators
The `+` operator results in a concatenation of the lists it is applied to.
Let's see an example.


```python
mixed_list = ['string', 5, ['a',2,3,]]
mixed_list = ['string', 5, ['a',2,3,]]

print("Concatenation with + operator", mixed_list+ mixed_list)
```

```
## Concatenation with + operator ['string', 5, ['a', 2, 3], 'string', 5, ['a', 2, 3]]
```

We can also use this to append an element to a list. Like so:


```python
print("Concatenation with + operator", 'Hello World here'.split() +"I am".split())
```

```
## Concatenation with + operator ['Hello', 'World', 'here', 'I', 'am']
```

What do we expect if we apply the `*` operator? Correct it concatenates the string
n times.

```python
some_list = 'Hello World here'.split()
print("Concatenation with * operator", some_list*2)
```

```
## Concatenation with * operator ['Hello', 'World', 'here', 'Hello', 'World', 'here']
```

```python
print("Concatenation with * operator", 'Hello World'*2)
```

```
## Concatenation with * operator Hello WorldHello World
```
There is another way of expressing addition in this case. We might as well use the following notation.

```python
some_list = 'Hello World here'.split()
some_list += ['am']
print("Concatenation with * operator", some_list)
```

```
## Concatenation with * operator ['Hello', 'World', 'here', 'am']
```


### `dir` commmand
Similar as to the `string` class you can get an exhaustive list of the available methods with the `dir` command.

```python
dir(list)
```

```
## ['__add__', '__class__', '__class_getitem__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__iadd__', '__imul__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__rmul__', '__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__', 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
```

### `append` method
With the `append` method you can add an element to a list. It's important to know that
`append` does not return a value but modifies the list it is applied to in sito.
Therefore if you store the value of `append` in a variable it will be of type `NoneType`.


```python
l = [1,2,3]
l.append(10)
l
```

```
## [1, 2, 3, 10]
```

```python
print("Return value of append-method" , type(l.append(10)))
```

```
## Return value of append-method <class 'NoneType'>
```

### Excercise 2
To deepen our understanding of the list operations let's find out what happens here.
What values do `t` and `l` have after we execute the two lines of code?


```python
l = [1,2,3]
l.append(10) # l=[1,2,3,10]
t = type(l.append(11))
l = l.append(1000)
```




## Solutions
### Solution - Excercise 1
So what is going on here? Well the expression takes the element at index 1 from the first (which is `type`)
and puts that in front of the the element at index 0 from the second list (which is "Hallo").
That results in `(type)(str)`. 

```python
([len, type, 1,2,3][1])(["Hallo", "Welt"][0])
```

```
## <class 'str'>
```

### Solution - Excercise 2
As explained before `append` returns a `NoneType`. Therfeore both `l` and `t` are assigned to that.

```python
l = [1,2,3]
l.append(10) # l=[1,2,3,10]
t = type(l.append(11))
l = l.append(1000)
print("Value of t is {} and value of l is {} ".format(t,l))
```

```
## Value of t is <class 'NoneType'> and value of l is None
```
