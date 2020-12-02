---
URL: /2020/12/02/2020-12-02-compound-data-types
author: Adrian Gabriel
categories:
- Python
date: "2020-12-01 09:00:00"
description: Learn about compound data types in Python
excerpt: Compound data types in Python
image: "img/taghia.jpg"
published: true
subtitle: Introduction to compound data types in Python
tags:
- Python
- Software Engineering
title: Compound data types in Python
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

# Compound data types

You can compare numerical types by using `<` and ´>´ for instance. The same is possible
for types like `str`, `list` or `tuple`. Sequences and lists are compared **lexicographically**.
That means that Python uses the ASCII values for comparison. Let's see an example.


```python
a = 'abcd'
b = 'efgh'

print("ASCII values in a {}".format([ord(c) for c in a]))
```

```
## ASCII values in a [97, 98, 99, 100]
```

```python
print("ASCII values in b {}".format([ord(c) for c in b]))
```

```
## ASCII values in b [101, 102, 103, 104]
```

```python
print(a < b)
```

```
## True
```

```python
a = '9999'
b = '1111'

print("ASCII values in a {}".format([ord(c) for c in a]))
```

```
## ASCII values in a [57, 57, 57, 57]
```

```python
print("ASCII values in b {}".format([ord(c) for c in b]))
```

```
## ASCII values in b [49, 49, 49, 49]
```

```python
print(a > b)
```

```
## True
```
If the first digits are equal Python considers the next pair of digits to evaluate the comparison.


```python
a = 'a911'
b = 'a199'

print("ASCII values in a {}".format([ord(c) for c in a]))
```

```
## ASCII values in a [97, 57, 49, 49]
```

```python
print("ASCII values in b {}".format([ord(c) for c in b]))
```

```
## ASCII values in b [97, 49, 57, 57]
```

```python
print(a < b)
```

```
## False
```
Same is true for the case when the first two digits are equal it will consider the next pair and so on.
If one sequence is shorter than the other then it is automatically considered to be less
Here is some code you fill you in.


```python
a = 'a111'
b = 'a199'

print("ASCII values in a {}".format([ord(c) for c in a]))
```

```
## ASCII values in a [97, 49, 49, 49]
```

```python
print("ASCII values in b {}".format([ord(c) for c in b]))
```

```
## ASCII values in b [97, 49, 57, 57]
```

```python
print(a < b)
```

```
## True
```

```python
a = 'aalen'
b = 'albstadt'

print(a < b)
```

```
## True
```



