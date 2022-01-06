# Python Decorators

## Starter Knowledges

Decorators are to add addtional functionalities to existing implemented functions.

Use the simple math operation functions as examples below.

```python
def add(n1, n2):
    return n1 + n2

def subtract(n1, n2):
    return n1 - n2

def multiply(n1, n2):
    return n1 * n2

def divide(n1, n2):
    return n1 / n2

# Functions are first-class objects.
# It means the functions can be passed around as arguments,
# the same way like passing around int, string, or float variables.

# Now we can define a method to use one of the functions
# above to do calculations.
def calculate(calc_function, n1, n2):
    return calc_function(n1, n2)

# Test Code
result = calculate(add, 2, 3)
print(result)  # 5


# There is also the concept of "Nested Functions"
def outer_function():
    print("I'm outer")

    def nested_function():
        print("I'm inner")

# We cannot call the nested_function from outside.
# We can only call the nested_function inside the outer_function,
# like this:
def outer_function():
    print("I'm outer")

    def nested_function():
        print("I'm inner")

    nested_function()

# Additionally, functions can be returned from other functions
# The above code becomes:
def outer_function():
    print("I'm outer")

    def nested_function():
        print("I'm inner")

    return nested_function  # No parenthesis!

# Now we can call the nested_function from outside world.
inner_function = outer_function()
inner_function()
```

## Python Decorators

```python
# Python Decorator Function
def decorator_function(function):
    def wrapper_function():
        function()
    return wrapper_function
```

The problem we want to solve here is that - how do we add delay 2 seconds for all my functions?

```python
def say_hello():
    time.sleep(2)
    print("Hello")


def say_bye():
    print("Bye")

def say_greeting():
    print("How are you?")
```

Instead of adding a `time.sleep()` call in each new methods, we can use decorators.

```python
def delay_decorator(function):
    def wrapper_function():
        time.sleep(2)
        # Do something before
        function()
        # Do something after
    return wrapper_function

@delay_decorator
def say_hello():
    print("Hello")

@delay_decorator
def say_bye():
    print("Bye")

@delay_decorator
def say_greeting():
    print("How are you?")
```



## Advance Decorator Functions

* conditions, and,

* passing arguments to the inner function.
