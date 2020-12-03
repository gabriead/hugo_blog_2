---
URL: 2020/12/02/Indexing/in/Python
author: Adrian Gabriel
categories:
- Python
date: "2020-12-01 09:00:00"
description: The art of indexing in Python
excerpt: The art of indexing in Python
image: "img/taghia.jpg"
published: true
subtitle: Learn about the different ways to use indexing in Python
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

# Indexing
In order to select an element from a sequence you can use different techniques
in order to achieve that. It can be done by one of the following:
* selecting a single element
* selecting a specific group of elements (slicing)
* selecting a group of elements within a range (extended slicing)

We will clarif each of the techniques by examples.

## Indexing a single element
```python
s = "i am a random string"
print("Selection by indexing: {}".format(s[1]))
```
You can also nest the indexing operator. Can you figure out what it will return?

```python
s = ["Hallo", 1, 2, "another string with words".split(), 10]
s[3][1][2]
```

```
## 'r'
```
## Indexing using slicing
In order to select a specific group of elements within a sequence we can define
a range of values. We can achieve that by using the `range` function. The range function
takes a starting and an end parameter that define the range. It **includes the starting point but excludes the end point**. If you ommit a parameter Python will use a default value.
For the starting position that will be zero and for the end position that will be the position of the last element of the sequence.
The pattern looks like this: **<Sequenz>[<Startindex>:<Endindex>]**
I will give you an example.


```python
s = ["Hallo", 1, 2, "another string with words".split(), 10]

print("Slicing of a range selects: {} ".format(s[0:3]))
```

```
## Slicing of a range selects: ['Hallo', 1, 2]
```

```python
print("Slicing of a range selects: {} ".format(s[3:22]))
```

```
## Slicing of a range selects: [['another', 'string', 'with', 'words'], 10]
```
There are also some shortcuts when you leave away the left or right boundary.


```python
s = ["Hallo", 1, 2, "another string with words".split(), 10]

print("Slicing of a range selects: {} ".format(s[0:]))
```

```
## Slicing of a range selects: ['Hallo', 1, 2, ['another', 'string', 'with', 'words'], 10]
```

```python
print("Slicing of a range selects: {} ".format(s[:]))
```

```
## Slicing of a range selects: ['Hallo', 1, 2, ['another', 'string', 'with', 'words'], 10]
```

```python
print("Slicing of a range selects: {} ".format(s[:3]))
```

```
## Slicing of a range selects: ['Hallo', 1, 2]
```
## Indexing using extended slicing
The pattern looks like this: **<Sequenz>[<Startindex>:<Endindex>:<Schrittweite>]**


```python
s = list(range(20))
print("extended slicing: {} ".format(s[0:5:1]))
```

```
## extended slicing: [0, 1, 2, 3, 4]
```

```python
print("extended slicing: {} ".format(s[0:6:3]))
```

```
## extended slicing: [0, 3]
```
## Indexing using negative indices
You can iterate in reverse by using a **negative** index. Let's look at an example.


```python
s = [1,2,3,4,5]
print("Slicing of extended slicing: {} ".format(s[-1]))
```

```
## Slicing of extended slicing: 5
```

```python
print("Slicing of extended slicing: {} ".format(s[:-1]))
```

```
## Slicing of extended slicing: [1, 2, 3, 4]
```

```python
print("Slicing of extended slicing: {} ".format(s[::-1]))
```

```
## Slicing of extended slicing: [5, 4, 3, 2, 1]
```

```python
print("Slicing of extended slicing: {} ".format(s[4::-1]))
```

```
## Slicing of extended slicing: [5, 4, 3, 2, 1]
```

```python
print("Slicing of extended slicing: {} ".format(s[3:1:-1]))
```

```
## Slicing of extended slicing: [4, 3]
```

```python
print("Slicing of extended slicing: {} ".format(s[3:1:-2]))
```

```
## Slicing of extended slicing: [4]
```

```python
print("Slicing of extended slicing: {} ".format(s[::-2]))
```

```
## Slicing of extended slicing: [5, 3, 1]
```
## Excercises
Let's solve some exercises.


```python
s = "Das enthaelt kein icks"
print(len(s))
```

```
## 22
```

```python
print("Last four letters in reverse: {} ".format(s[:17:-1]))
```

```
## Last four letters in reverse: skci
```

```python
print("Last four letters: {} ".format(s[18::1]))
```

```
## Last four letters: icks
```

```python
print("Last four letters: {} ".format(s[-4:]))
```

```
## Last four letters: icks
```

```python
print("First ten letters: {} ".format(s[:11:1]))
```

```
## First ten letters: Das enthael
```



```python

satz = "Hallo Welt ich lebe hier auf der Erde und bin glücklich"

print("First three letters: {} ".format(satz.split()[0][0:3]))
```

```
## First three letters: Hal
```

```python
print("First three words: {} ".format(satz.split()[0:3]))
```

```
## First three words: ['Hallo', 'Welt', 'ich']
```

```python
print("Last two words: {} ".format(satz.split()[-2:]))
```

```
## Last two words: ['bin', 'glücklich']
```

```python
print("Last two words: {} ".format(satz.split()[-2][-2:]))
```

```
## Last two words: in
```

