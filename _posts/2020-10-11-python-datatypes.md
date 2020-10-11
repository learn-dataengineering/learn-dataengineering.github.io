---
title: Python Built-In Datatypes
date: 2020-10-11
---
In Python most common buit-in types are numeric, sequences & mappings(key-pair). 

![Data Types](https://raw.githubusercontent.com/only-python/only-python.github.io/gh-pages/images/python-datatypes.png "Datatypes")

Here are the list of Python buit-in types:

Numeric Types
+ int
+ float
+ complex

Sequence Types
+ list
+ tuple
+ range
+ str

Binary Sequence Types
+ bytes
+ bytearray

Mapping (HashMap Key-Pair)
+ dict

Set Types
+ set

Other Built-In Types
+ bool
+ None
+ ellipsis
+ type

Using Python's built-in function type() you can check what type of object is assigned to a variable.

```python
#Example: Variable declaration python

my_str = "John"                         # String
my_bytstr = b"John"                     # Bytes
my_int = 50                             # Integer
my_float = 150.50                       # Float
my_list = [1,2,3]                       # List
my_dict = {1:'One', 2:'Two', 3:'Three'} # Dictionary
my_tuple = (1,2,3)                      # Tuple
my_set = {1,2,3}                        # Set
my_bool = True                          # Boolean
my_none = None                          # NoneType


print(type(my_str))
print(type(my_bytstr))
print(type(my_int))
print(type(my_float))
print(type(my_list))
print(type(my_dict))
print(type(my_tuple))
print(type(my_set))
print(type(my_bool))
print(type(my_none))

<class 'str'>
<class 'bytes'>
<class 'int'>
<class 'float'>
<class 'list'>
<class 'dict'>
<class 'tuple'>
<class 'set'>
<class 'bool'>
<class 'NoneType'>
```
---
Happy Learning! Your feedback would be appreciated!<br>
[onlypython.py](https://only-python.github.io/)
