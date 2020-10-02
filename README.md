# python-decorators

## Functions
In python, functions are first-class objects, which means that:
- functions are objects (they can be referenced, passed to a variable, and returned)
- functions can be *defined* inside another function
- functions can also be passed as an argument to another function

## Decorators
A decorator takes in a function, adds some functionality, and returns it. Functions that take other functions are arguments are also called higher-order functions.

Functions and methods are called **callable** as they can be called. What makes an object callable, exactly? Well, if they have the dunder method __call__() implemented.

Example:
```
def make_pretty(func):
    def inner():
        print("I'm decorating~~")
        func()
    return inner

@make_pretty
def normal():
    print("normal")
```

## Decorator with arguments
We can make decorators that work with any number of parameters using function(*args, **kwargs) where *args are a tuple of positional arguments and **kwargs are a dictionary of keyword arguments. 
```
def works_for_all(func):
    def inner(*args, **kwargs):
        print("I'm decorating anything!")
        return func(*args, **kwargs)
    return inner
```
## Chaining decorators
Decorators are evaluated from the bottom to the top, so if you were to decorate the following

```
@dec2
@dec1
def printer(msg):
    print(msg)
```
Then it would evaluate it as printer = dec2(dec1(printer))