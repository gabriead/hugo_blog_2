
---
URL: /2020/12/02/references-in-python/
author: Adrian Gabriel
categories:
- Python
date: "2020-12-01 09:00:00"
description: Learn about references in Python
excerpt: Python
image: "img/taghia.jpg"
published: true
subtitle: The fundamentals of references
tags:
- Python
- Software Engineering
title: "References in Python"
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

# References
## References in Python
In contrast to languages like C++ oder C Python does not allow tow write directly to memory.
Python uses references to objects that are bound to variables.

### Surprising Behavior
In this example nothing interesting happens until we print the two lists.

```python
l = ['Hello', 'World', 'here', 'I', 'am']
r=l
r[0] = 1000
print("list l {}".format(l))
```

```
## list l [1000, 'World', 'here', 'I', 'am']
```

```python
print("list r {}".format(l))
```

```
## list r [1000, 'World', 'here', 'I', 'am']
```

```python
print("Address of l {}".format(id(l)))
```

```
## Address of l 140675616502400
```

```python
print("Address of r {}".format(id(r)))
```

```
## Address of r 140675616502400
```
By adding an element to r we also mutated l. This comes as kind of a surprise.
In order to understand what is going on behind the curtain let's take a look at
what happens in memory. This can be done by using `id`.


```python
y = 0
x = 2
print("current address of x: {}".format(id(x)))
```

```
## current address of x: 140675615299920
```

```python
print("current address of y: {}".format(id(y)))
```

```
## current address of y: 140675615299856
```

```python
y = x
print("current address of y  after referencing x: {}".format(id(y)))
```

```
## current address of y  after referencing x: 140675615299920
```

```python
y = 4

print("current address of x after y has changed: {}".format(id(x)))
```

```
## current address of x after y has changed: 140675615299920
```

```python
print("current address of y after new value was assigned: {}".format(id(y)))
```

```
## current address of y after new value was assigned: 140675615299984
```

```python
print("current value of x: {}".format(x))
```

```
## current value of x: 2
```

```python
print("current value of y: {}".format(y))
```

```
## current value of y: 4
```
We observe that the `id` of y changes after referencing to x and changes again when a
new value is assigned. The address of x does not change even if the value of y is altered again.
Let's checkout another example.

```python
y=x
x=y
print("current address of x: {}".format(id(x)))
```

```
## current address of x: 140675615299920
```

```python
print("current address of y: {}".format(id(y)))
```

```
## current address of y: 140675615299920
```

```python
x=x+2
print("current address of x: {}".format(id(x)))
```

```
## current address of x: 140675615299984
```

```python
print("current address of y: {}".format(id(y)))
```

```
## current address of y: 140675615299920
```
It is noteworthy that after incrementing the value of x, the variable is assigned a new id in memory.
Operators such as `-`, `*` and `/` or `**` **always create a new reference**.

The behavior that we have observed for variables of type `int` is also true for `strings`.
Watch this.


```python
s='Hello'
print("current address of s: {}".format(id(s)))
```

```
## current address of s: 140675657864304
```

```python
s=s+str(1)
print("Value of s: {}".format(s))
```

```
## Value of s: Hello1
```

```python
print("current address of s after addition: {}".format(id(s)))
```

```
## current address of s after addition: 140675657863984
```
It is good to know that Python automatically takes care of the 'old' and unused reference and removes it from memory.

## Excercise
Given two lists `l1` and `l2`. Explain the behavior for each of the possibilities of adding an element.

```python
l1 = [1,2,3]
l2 = l1

print("current address of x: {}".format(id(l1)))
```

```
## current address of x: 140675656696832
```

```python
print("current address of y: {}".format(id(l2)))

# Appending an element with the '+' operator
```

```
## current address of y: 140675656696832
```

```python
l2 = l2 + [100]
l1
```

```
## [1, 2, 3]
```

```python
l2
```

```
## [1, 2, 3, 100]
```


```python
l1 = [1,2,3]
l2 = l1

print("current address of x: {}".format(id(l1)))
```

```
## current address of x: 140675616542400
```

```python
print("current address of y: {}".format(id(l2)))

# Appending an element by indexing
```

```
## current address of y: 140675616542400
```

```python
l2[2]= 100
l2
```

```
## [1, 2, 100]
```

```python
l1
```

```
## [1, 2, 100]
```


```python
l1 = [1,2,3]
l2 = l1

print("current address of x: {}".format(id(l1)))
```

```
## current address of x: 140675616437760
```

```python
print("current address of y: {}".format(id(l2)))

# Appending an element with 'append'
```

```
## current address of y: 140675616437760
```

```python
return_value = l2.append(100)
l2
```

```
## [1, 2, 3, 100]
```

```python
l1
```

```
## [1, 2, 3, 100]
```

```python
print("Return value of append {}".format(return_value))
```

```
## Return value of append None
```


## Solutions
### Excrecise 1
The `+` operator always creates a new reference. Therfore l2 is assigned with a new reference
that is different than the one before. `Append` does add an element in situ and does **not**
create a new reference. Therefore l1 and l2 are still referencing the same `id` in memory.
