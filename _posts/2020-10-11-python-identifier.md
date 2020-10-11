---
title: Python Identifiers ASCII & Non-ASCII
date: 2020-10-11
---

In other programming languages like C,C++, Java, PL/SQL - we have to declare the variable with its type in advance see below some examples.
```java
int x, y;  // C variable declaration<br>
float interest;   // C variable declaration<br>
person_id number(10); -- PL/SQL variable declaration<br>
person_name varchar2(25); -- PL/SQL variable declaration<br>
```
In Python there is no advance declaration, so type of variable is not fixed. A variable is created when we assign value to it. It does not required any explicit declaration. Use the assignment operator = to assign the value to a variable.

Variable-Name = Value
Variables basically inherit type from current value. Type determine what operations are allowed.
```python
>>> x = 1
>>> interest = 1000.25
>>> x = 'Python'
```
+ We have assigned value 1 to variable x. Variable x is created
+ Now variable x has its type i.e. Int. Variables basically inherit type from current value.
+ Later string 'Python' is assigned to x, so now x has its type i.e. string (this is dynamic typing)

### Identifier Names Rules ASCII

Identifiers i.e. names used to identify a variables, function, class, methods etc.

+ Must start with a letter or the underscore character. Cannot start with a number.
+ Can only contain alpha-numeric characters and underscores (A-z, 0-9, & _ ). Within the range of 0-127 i.e. ASCII 
+ Variable names are case-sensitive.
+ Reserved words i.e.keyword cannot be used as regular identifier. 

To get the list of these reserved words i.e. keywords. We can use keyword module.

```python
>>> import keyword
>>> keyword.kwlist #list of all keywords
>>> keyword.iskeyword('def')  #check if given string is reserved word
```
To check if string is valid identifier or not, we can use isidentifier method of str class.
```python
>>> 'lv_status'.isidentifier()
True
>>> '5_status'.isidentifier()
False
```
To check if the string is valid ascii or not: user method 'isascii' of 'str' - return Boolean. Or use built-in function ascii - which returns a string containing a printable representation of an object. It escapes the non-ASCII characters in the string using \x, \u or \U escapes.

### Identifier Names Rules Non-ASCII

Python 3 introduces the characters for identifiers outside ASCII range. For these non-ascii characters, the classification uses the version of the UCD (Unicode Character Database) as present in the unicodedata Python module.
```python
>>> import unicodedata
>>> unicodedata.unidata_version
'12.1.0'
```
Characters having Unicode categories allowed for Python identifier: The identifier syntax is <XID_Start> <XID_Continue>*
+ ID_Start: Lu - uppercase letters, Ll - lowercase letters, Lt - titlecase letters, Lm - modifier letters, Lo - other letters, Nl - letter numbers, Pc - connector punctuations & Other_ID_Start property.
+ ID_Continue: [ID_Start Characters] + Mn - nonspacing marks, Mc - spacing combining marks, Nd - decimal numbers, Pc - connector punctuations & Other_ID_Continue property.

XID_Start characters are derived from ID_Start & XID_Continue characters are derived from ID_Continue as per NFKC normalization. Check Python documentation pep-3131 for more details.

To check the category of the Unicode character use: unicodedata module
```python
>>> unicodedata.category('Š')
'Lu'
>>> unicodedata.category('š')
'Ll'
>>> unicodedata.category('ॐ')
'Lo'
>>> unicodedata.category('_')
'Pc'
>>> unicodedata.category('9')
'Nd'
```
Code snippet to get the list of Unicode character based on category.
```python
import unicodedata
import sys

ucd_data =[]
for i in range(sys.maxunicode + 1):
    if unicodedata.category(chr(i)) in ('Pc','Lo'):
        ucd_data.append(chr(i))
print(ucd_data[:11])
```
I have picked up the Devanagari (U+0900–U+097F) Unicode block to create some non-ASCII characters identifiers.
```python
import unicodedata
import sys

# Devanagari code points: U+0900..U+0954

devanagari_data =[]
for i in range(int("0x904", 16), int("0x954", 16)+1):
  devanagari_data.append([unicodedata.category(chr(i)),chr(i)])
print(devanagari_data[:5])

[['Lo', 'ऄ'], ['Lo', 'अ'], ['Lo', 'आ'], ['Lo', 'इ'], ['Lo', 'ई']]
```
See below screenshot of some non-ASCII identifiers used to create a simple class:
```python
class ॐ():
    मंत्र = "ॐ नमः शिवाय" # Om Namaḥ Śivāya
    def अक्षर(self):
        # 'Na' 'Ma' 'Śi' 'Vā' and 'Ya'
        return ["न", "मः", "शि", "वा", "य"]
    def अर्थ(self):
        # I bow down to Lord Shiva
        return "भगवान शिव को नमस्कार"

print(ॐ.मंत्र)
उपयोग = ॐ()
print(उपयोग.अक्षर())
print(उपयोग.अर्थ())

ॐ नमः शिवाय
['न', 'मः', 'शि', 'वा', 'य']
भगवान शिव को नमस्कार
```
---
Happy Learning! Your feedback would be appreciated!<br>
[onlypython.py](https://only-python.github.io/)


