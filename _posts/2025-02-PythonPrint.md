---
layout: post
title: A sophisticated way of Printing in Python
date: 16-02-2025
categories: [documentations]
tag: [like,comment,subscribe]
---
# Python F-Strings: A sophisticated way of Printing

Python 3.6 introduced the f-strings ( f’ string/ F’ string / f” string / F” string ) for formatting and printing text strings ( including variable / expression result / function output) in a fancy way.

We can replace old style and syntax by f-string for format specifying and finally printing in a more elegant and efficient way  .

Example – traditionally we have been doing 

``` python
name='Supratim'
age=47
print("Name :",name,", Age :", age)
```

The output will look like.

Name : Supratim , Age : 47

Now, Let' try with the use of f-string

```python
name='Supratim'
age=47
print(f"Hi {name} , your age is {age}")
```

The output will look like.

Hi Supratim , your age is 47

## Let us see some more examples

Example:
``` python
# even we can print without using print keyword 
name=input("Your Name ? :")
age=int(input("Your age ? :"))
f'Hi {name} , your age is {age}'
```
The output will look like
Your Name ? : Supratim

Your age ? : 47

'Hi Supratim , your age is 47'

Example:
```python
name='Supratim'
age=47
height='190 cm'
print(f' Your details are as follows {name=} {age=} {height=}')
```
The output will look like

Your details are as follows name='Supratim' age=47 height='190 cm'

Example:
```python
# Multiline -- use of """

details = f"""
Name: Supratim Chakraborty
Age: 47
City: Kolkata
"""
print(details)
```
Output will look like

Name: Supratim Chakraborty
Age: 47
City: Kolkata

Example:
```python
# old style printing(formatting)
import math
print('The value of pi is approximately %4.3f' % math.pi)
```
Output will look like

The value of pi is approximately 3.142


```python
# newstyle printing(formatting)
import math
print(f'The value of pi is approximately {math.pi:.3f}')
```
Output will look like

The value of pi is approximately 3.142

Example:

```python
number = 200
s = f'{number:06}'
print(s) 
```
Output will look like

000200

Example:

```python
number = 200
s = f'{number:6}'
print(s)
```
Output will look like

   200

Example:

```python
number = 200
s = f'{number: 012}'
print(s)
```
Output will look like

 00000000200


 ## We have seen several examples ; there are more examples which will be discussed later