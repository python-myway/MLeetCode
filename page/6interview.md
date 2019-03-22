---
layout: page
title: Interview
permalink: /interview/
icon: bookmark
type: page
---

* content
{:toc}

这是国外网友整理的Python面试问题，[阅读原文](https://luminousmen.com/post/python-interview-questions-junior)

Q: What is Python? What are the key features of Python?

Q: What Python libs did you use?

Q: What is pass in Python?

Q: What is lambda in Python?

Q: What is docstring in Python?

Q: What is the ternary operator in Python? Example?

Q: What are *args, **kwargs?

Q: What is the difference between list and tuple in Python?

Q: What are the built-in types that Python provides? Which are mutable which are immutable?

Q: In Python what is slicing?

Q: What keywords can be used in conjunction with the keyword `for`?

Q: How to list object methods in Python?

Q: How to get documentation of object in Python?

Q: What can be the key in the dictionary?

Q: What is `yield` in Python?

Q: How can I swap the values of two variables in Python?

Q: What is duck typing?

Q: What the difference between packages and modules?

Q: What is PEP 8?

Q: What is self?

Q: What is __init__.py module? What it's for?

Q: How to translate a string containing a binary code (1 and 0) into a number (integer)? Write a program for this.

Q: How to check that tuple A contains all elements of tuple B. Both tuples contain unique values? Write a program for this.

Q: What will be the output of the following code?

```
def f():
     x = 15
     print(x)
x = 12
f()
```
Q: How to convert a string to a number which consists of letters ASCII code. Example: 'abcd' -> 979899100. Write a program for this.

Q: How to remove empty lines from a sheet of lines (with a length of 0). Write a program for this.

Q: Write a program that counts all distinct pairs with difference equal to k

Q: Build a string with the numbers from 0 to 100, "0123456789101112..."

Q: Making a list with the unique element from a list with duplicate elements

Q: Make a prime number list from (1,100)


Q: What is the output: -12 // 10?

Q: What is the sequence of call operators in the expression a ** b ** c?

Q: What are the steps required to make a script executable on Unix?

Q: What is an iterator? What is a generator? What is the difference between them?

Q: Why shouldn't the default argument be to make an empty list?

Q: Let A and B be objects of class Foo. What functions and in what order is called when print(A() + B()) is executed?

Q: Is there an assignment operation in python?

Q: How are arguments passed by value or by reference?

Q: How are Dict and Set implemented internally?

Q: How memory is managed in Python?

Q: How garbage collector works in Python?

Q: How can you copy an object in Python? / What is the difference between deep and shallow copy?

Q: Can we write a multithreaded application in Python?

Q: What is GIL? Why GIL is still existing?

Q: Difference between multithreading and multiprocessing libraries in Python?

Q: What is a decorator? How to create custom decorator?

Q: What is map, filter, and reduce operations in Python?

Q: What is globals(), locals() and vars()?

Q: What is context managers in Python? How are they different from try ... finally?

Q: What functions need to be redefined in class so that its instances implement the context manager protocol?

Q: Does Python fully support OOP? How to create a private attribute in Python object?

Q: What are dunder methods in Python?

Q: What are __init__ functions?

Q: How to call a constructor method in Python?

Q: What is __dict__ attribute of Python object? Make an example.

Q: How can you share global variables across modules?

Q: You have a function that takes other functions as an argument. How to validate the value of an argument?

Q: You need to implement a function that should use a static variable (for example, a call counter). You cannot write any code outside the function and you do not have information about external variables (outside your function). How to do it?

Q: What is a descriptor? What is a decorator? Is there a difference between a descriptor and a decorator?

Q: What will be the output of the following code?

```
>>> a = [[]]*3
>>> a[1].append(1)
>>> print(a)
Q: What's wrong with this code?

def foo():
     from .module import *
     print(f'{bar()}')
```

Q: The file is located in /usr/lib/python/person.py. The program starts as python /usr/lib/python/person.py. What is the output?

```
class Person:
    def __init__(self, name):
        __name__ = name

    def getAge(self):
        print(__name__)

p = Person('John')
p.getAge()
```

Q: Write timeit decorator for measure time of function execution.

Q: Write repeater decorator that will catch errors several times(customizable).

Q: Output?

```
class parent:
     def __init__(self, param):
         self.v1 = param

class child:
     def __init__(self, param):
         self.v2 = param

obj = child(11)
print(obj.v1 + " " + obj.v2)
```

Q: Add some code to make it work
```
class Repeater:
    ...
class RepeaterIterator:
    ...

repeater =Repeater('Hello')
for I in repeater:
    print (i)  # hello
```

Q: Write the code for getting unique values from list complex types.

Q: We have the following code with the unknown function f(). In f(), we do not want to use return, instead, we may want to use generator.

```
for x in f(5):
    print x,
The output looks like this:

0 1 8 27 64
Write a function f() so that we can have the output above.

Q: Output?

x = [[0], [1]]
print(len(' '.join(list(map(str, x)))))
```

Q: Write a program that prints the numbers from 1 to 20. But for multiples of three print “Fizz” instead of the number and for the multiples of five print “Buzz”. For numbers which are multiples of both three and five print “FizzBuzz”.

Q: Output? What is wrong? How to fix?

```
class Developer(object):
    coffee_cups = 0

    def __init__(self, name):
        self.name = name
        self.coffee_cups += 1

    def speak(self):

        print("I'm %s and I've had %d cups of coffee today" % (self.name, self.coffee_cups))

rover = Developer("Steve")
spot = Developer("Bob")
```

Q: When will the else part of try-except-else be executed?

Q: What are metaclasses in Python?

Q: What is monkey patching? How to use in Python? Example?

Q: What are the tools that help to find bugs or perform static analysis? What static code analyzers do you know/used?

Q: Whenever Python exits, why isn’t all the memory de-allocated?

Q: Explain how can you access a module written in Python from C? Vise versa?

Q: What do these mean to you: @classmethod, @staticmethod, @property?

Q: Is Python a functional language?

Q: What is the attribute __slots__?

Q: Is it possible to use the construction True = False?

Q: How to create a class without the class statement?

Q: Give an example of filter and reduce over an iterable object

Q: Is it possible to have a producer thread reading from the network and a consumer thread writing to a file, really work in parallel? What about GIL?

Q: How do you create a dictionary which can preserve the order of pairs?

Q: What does the PYTHONOPTIMIZE flag do?

Q: What are descriptors? Code example?

Q: What is MRO in Python? How does it work?

Q: Mention what is the difference between Django, Pyramid, and Flask?

Q: Specify the requirements for code written in a functional style.

Q: Identify the pitfalls/limitations in the function code.

Q: How to package code in Python?

Q:What is wheels and eggs? What is the difference?

Q: How to package binary dependencies in Python?

Q: How can I reload a previously imported `module` module? (we assume that the module is a file with module.py)

Q: What advantages do NumPy arrays offer over (nested) Python lists?

Q: What is the process of compilation and linking in python?

Q: What id() function in Python is for?

Q: Is Python call-by-value or call-by-reference?

Q: Explain how you reverse a generator?

Q: Let A and B be objects of class Foo. What methods and in what order are called when "print (A + B)" is executed?

Q: Place the following functions below in order of their efficiency. How would you test your answer?

```
def f1(lIn):
    l1 = sorted(lIn)
    l2 = [i for i in l1 if i<0.5]
    return [i*i for i in l2]
 

def f2(lIn):
    l1 = [i for i in lIn if i<0.5]
    l2 = sorted(l1)
    return [i*i for i in l2]
 

def f3(lIn):
    l1 = [i*i for i in lIn]
    l2 = sorted(l1)
    return [i for i in l1 if i<(0.5*0.5)]
```

Q: Write a one-liner that will count the number of capital letters in a file. Your code should work even if the file is too big to fit in memory.

Q: Output? Why? Is this inheritance?

```
class C:
    pass
type (C ())
type (C)
```

Q: What's the output we get from running the following?

```
big_num_1   = 1000
big_num_2   = 1000
small_num_1 = 1
small_num_2 = 1
big_num_1 is big_num_2
small_num_1 is small_num_2
```

Q: How is this possible?

```
_MangledGlobal__mangled = 23
class MangledGlobal:
     def test(self):
         return __mangled

>>> MangledGlobal().test()
23
```
## Comments

{% include comments.html %}