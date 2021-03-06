---
URL: /2020/12/02/2020-12-02-advanced-data-structures-in-python
author: Adrian Gabriel
categories:
- Python
date: "2020-12-01 09:00:00"
description: Advanced data structures in Python
excerpt: Tuples in Python
image: "img/taghia.jpg"
published: true
subtitle: Introduction to advacned data structures in Python
tags:
- Python
- Software Engineering
- Advanced data structures
title: Tupes in Python
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

# Advanced data structures

## Tuple
A `tuple` is similar to a list in that it is a sequence of elements.
Let's see what I mean by that. It can consist of pairs of varying length 
and different types. A major difference in comparison to lists is it's **immutability**.
Let's see an example.


```python
a = ((1,"some_value"),2,3)
print(a)
```

```
## ((1, 'some_value'), 2, 3)
```

```python
b = (1,"some_value",3)
print(b)
```

```
## (1, 'some_value', 3)
```
Now when I try to change someting in the tuples I will get an error because **immutability**
prohibits us from manipulating the elements.


```python
a = ((1,"some_value"),2,3)
#a[0] = 'new_value'
#a[3] = 4
#TypeError: 'tuple' object does not support item assignment

#Detailed traceback: 
#  File "<string>", line 1, in <module>
```

If we want to get an element from the tuple we can do this by indexing or looping through the entire thing.


```python
a = ((1,"some_value"),2,3)

print("Current value by indexing {}: ".format(a[1]))
```

```
## Current value by indexing 2:
```

```python
[print("Current value {}: ".format(c)) for c in a]
```

```
## Current value (1, 'some_value'): 
## Current value 2: 
## Current value 3: 
## [None, None, None]
```

## Set
Just like `list`, `str` and `tuple` a `set` is a compound data type. A common use case
for using a `set` is when you need a list-type structure that stores values without
allowing duplicates. If we create a set by using a list it will automatically remove 
duplicates. You can apply the `in` operator to check if a certain value is contained.
It's good to know that the underlying structure behind a set is a so called **hashtable**.
Checking if an element is in the set is therfore very efficient.

```python
s = set([1,2,2])
s
```

```
## {1, 2}
```

```python
print("Is contained? ", 1 in s)
```

```
## Is contained?  True
```

Another important property is that there is no fixed order in which
the elements if a `set` are iterated. Let me show you what I mean.


```python
import random

s = set([40,20,1])

for elem in s:
  print(elem)
```

```
## 40
## 1
## 20
```
### Implementing methods on a set
This chapter includes some sample code of two operations that could be done using sets.
The first one is updating a value in a set the second function is joining two sets.

#### Updating a set

```python
def myUpdate(aSet, value_to_update, update):
  tmp_list = []
  for idx, val in enumerate(aSet):
    if(val==value_to_update):
      tmp_list.append(update)
      continue;
    
    tmp_list.append(val)

  return set(tmp_list)

aSet = set([4,2,10,13])
updated_set = myUpdate(aSet, 10, 100)
print(updated_set)
```

```
## {2, 13, 100, 4}
```

#### Joining two sets

```python
def myIntersect(set1, set2):
    intersect = set()
    [intersect.add(val) for val in set1 if val in set2 ]
    
    return intersect

set1 = set([3,2,10,5])
set2 = set([11,10,3,1])

updated_set = myIntersect(set1,set2)
print(updated_set)
```

```
## {10, 3}
```

### Excrecise-Set
It's time for an excercise. Create a set with 10 Mio. entries of random variables
and create a list with 10 Mio. entries. Measure the time it takes to retrieve
an element from either structure.

## `dict`
The data structure `dict` not only stores a sequence of values but provides the functionality
of storing a **key** and a **value** as a pair. In other programming languages this is referred to 
as a **hashmap**. With that said a `dict` has the algorithmic complexities of a hashmap.
Let's see a quick example:

```python
aDict = { "Alan Turing": "0042 123456", "Angela Merkel": "0049 030-123456", "Joe Biden": "+1 123456"}
print(aDict)
```

```
## {'Alan Turing': '0042 123456', 'Angela Merkel': '0049 030-123456', 'Joe Biden': '+1 123456'}
```

You can index a value by using the key. Like so.


```python
aDict = { "Alan Turing": "0042 123456", "Angela Merkel": "0049 030-123456", "Joe Biden": "+1 123456"}
print(aDict["Alan Turing"])
```

```
## 0042 123456
```
In order to retrieve all keys and values stored in a `dict` you can use the two following operations

```python
aDict = { "Alan Turing": "0042 123456", "Angela Merkel": "0049 030-123456", "Joe Biden": "+1 123456"}
print("All keys in the dict: {}".format(aDict.keys()))
```

```
## All keys in the dict: dict_keys(['Alan Turing', 'Angela Merkel', 'Joe Biden'])
```

```python
print("All values in the dict: {}".format(aDict.values()))
```

```
## All values in the dict: dict_values(['0042 123456', '0049 030-123456', '+1 123456'])
```
By indexing into a `dict` you can add new items or alter existing ones.

```python
aDict = { "Alan Turing": "0042 123456", "Angela Merkel": "0049 030-123456", "Joe Biden": "+1 123456"}
aDict["Alan Turing"] = "987654321"
print("Update value for a key in the dict: {}".format(aDict))
```

```
## Update value for a key in the dict: {'Alan Turing': '987654321', 'Angela Merkel': '0049 030-123456', 'Joe Biden': '+1 123456'}
```
If you need to iterate over an entire `dcit` you can use a loop for instance.

```python
aDict = { "Alan Turing": "0042 123456", "Angela Merkel": "0049 030-123456", "Joe Biden": "+1 123456"}

for key,value in enumerate(aDict):
  print("Key :", key)
  print("Value :", value)
```

```
## Key : 0
## Value : Alan Turing
## Key : 1
## Value : Angela Merkel
## Key : 2
## Value : Joe Biden
```


## Solutions

```python
import random 
import timeit

randomlist = set(random.sample(range(0, 10000), 10000))
print("done")
```

```
## done
```


