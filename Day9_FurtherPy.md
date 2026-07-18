# Further on Python 

 
## 1. Functions

- A function is a block of code that performs a **specific task**.
- Example idea: if you need to draw a blue circle, you could split the work into:
  - a function that creates a circle
  - a function that applies color
- Dividing a complex problem into smaller chunks makes a program easier to understand and reuse.

### Types of Functions
1. **Standard library functions** – built-in functions Python already provides.
   - Almost all keywords are functions.
   - Examples: `print()`, `len()`, `input()`
2. **User-defined functions** – functions I create myself based on what I need.

### Creating Functions
Syntax:
```python
def function_name(arguments):
    # function body
```

Example:
```python
def greet():
    print('Hello World!')

# call the function
greet()
```

- Functions must be **called** to run — just like calling a plumber to fix a pipe, you have to "call" the function to make it do its task.

### Function Arguments
- Arguments are used to pass values into a function when calling it.

```python
# function with two arguments
def add_numbers(num1, num2):
    sum = num1 + num2
    print('Sum: ', sum)

# function call with two values
add_numbers(5, 4)
# Output: Sum: 9
```

- You can give **default values** to arguments:
```python
def add_numbers(num1=1, num2=1):
    ...
```

```python
def users(fname, lname):
    print(f"Hello {fname}!, your father name is: {lname}")

users('Meklit', 'Example')
# Output: Hello Meklit!, your father name is: Example
```

```python
def display(number1):
    print(f'the value u entered is: {number1}')

user_Input = input("Enter number: ")
display(user_Input)
# Output: Enter number: 23
#         the value u entered is: 23
```

### Return Statement
- A function **may or may not** return a value.
- To send a value back to the caller, use the `return` statement.

```python
def add(number1, number2):
    return number1 + number2

add(2, 3)
# Output: NOTHING (not printed, just returned silently)

print(add(2, 3))
# Output: 5

sum = add(2, 3)
print(sum)
# Output: 5
```

- Everything in Python is essentially a function — `print()`, `input()`, `len()`, etc.
- Default values example:
```python
def display(number1=100):
    print(f'the value u entered is: {number1}')

display()
# Output: 100
```

---

## 2. Recursion

- Recursion = the process of **defining something in terms of itself**.
- In Python, a function can call other functions — and it can even call **itself**. This is called a recursive function.

```python
def factorial(x):
    """Recursive function to find factorial of an integer"""
    if x == 1:
        return 1
    else:
        return x * factorial(x - 1)

num = 3
print("The factorial of", num, "is", factorial(num))
# Output: The factorial of 3 is 6
```

Trace:
```
factorial(3)                  # 1st call with 3
3 * factorial(2)              # 2nd call with 2
3 * 2 * factorial(1)          # 3rd call with 1
3 * 2 * 1                     # return from 3rd call (base case)
3 * 2                         # return from 2nd call
6                             # return from 1st call
```

### Advantages of Recursion
1. Makes code look clean and elegant.
2. Breaks a complex task into simpler sub-problems.
3. Easier to generate sequences than using nested iteration.

### Disadvantages of Recursion
1. The logic can be hard to follow.
2. Recursive calls are expensive (memory & time).
3. Harder to debug.

---

## 3. Anonymous / Lambda Function

- A function without a name is called a **lambda function / anonymous function**.
- Used when you only need **one line** of code to return a value — no need to `def` a full function.
- Syntax:
```python
lambda argument(s): expression
```
- We use the `lambda` keyword instead of `def`.

```python
def greet():
    return "Hello World"
print(greet())

greet = lambda: print('Hello World')
greet()
```

```python
def numbers(a, b):
    return a + b
print(numbers(2, 3))

numbers = lambda a, b: a + b
print(numbers(2, 3))
```

---

## 4. Functions That Take Functions (filter, map)

- `filter`, `map`, and `reduce` take a **function as an argument**.

### Filter Function
- Used to filter/search items from a sequence based on a condition.

```python
def is_even(n):
    return n % 2 == 0

nums = [3, 2, 6, 8, 4, 6, 2, 91]

evens = list(filter(is_even, nums))
print(evens)
# Output: [2, 6, 8, 4, 6, 2]
```

With lambda:
```python
nums = [3, 2, 6, 8, 4, 6, 2, 91]
evens = list(filter(lambda n: n % 2 == 0, nums))
print(evens)
# Output: [2, 6, 8, 4, 6, 2]
```

### Map Function
- Used to perform some operation on every item in a sequence.
- `map(func, *iterables)` → makes an iterator that applies the function to each item, stopping at the shortest iterable.

```python
nums = [3, 2, 6, 8, 4, 6, 2, 91]

def doub(n):
    return n * 2

doubles = list(map(doub, nums))
print(doubles)
# Output: [6, 4, 12, 16, 8, 12, 4, 182]
```

With lambda:
```python
nums = [3, 2, 6, 8, 4, 6, 2, 91]
doubles = list(map(lambda n: n * 2, nums))
print(doubles)
# Output: [6, 4, 12, 16, 8, 12, 4, 182]
```

Combining filter + map:
```python
nums = [3, 2, 6, 8, 4, 6, 2, 91]
evens = list(filter(lambda n: n % 2 == 0, nums))
doubles = list(map(lambda n: n * 2, evens))
print(doubles)
# Output: [4, 12, 16, 8, 12, 4]
```

### The `.append()` Keyword
- Used to add a new element to an existing list.
- Syntax:
```python
mylist.append("New Element")
```

```python
languages = ["Swift", "Java", "Python"]
print(languages)

languages.append("Amharic")
print(languages)
# Output: ["Swift", "Java", "Python"]
# Output: ["Swift", "Java", "Python", "Amharic"]
```

---

## 5. Object-Oriented Programming (OOP)

- Python is an object-oriented programming language — most things in Python are **objects**.
- An **object** is anything that can have an action (behavior) and a name.
- Objects have:
  - **Attributes** (properties)
  - **Methods** (actions/functions)
- Example: My Computer is an object because it has:
  - Attributes: name, size, cpu, ram...
  - Behaviour: running games, playing music, displaying text...

### Python Class
- A **class** is a place where we define an object's attributes and behaviour.
- It's like a **template / blueprint** for creating objects.
- Syntax:
```python
class Computer:
    # Creating Attributes
    name = ""
    cpu = ""
```
- Conventionally, class names start with a **capital letter**.
- Once a class (blueprint) is created, we can create actual objects from it.

### Creating Objects
- You can create many objects from **one** class.
- Syntax:
```python
var = ClassName()
var.attribute = "value"
```

```python
# Creating an object based on the blueprint
Meklit_Computer = Computer()
Meklit_Computer.name = "Hp laptop"
Meklit_Computer.cpu = "Intel Core i5"

# Creating another object
Friend_Computer = Computer()
Friend_Computer.name = "Dell Desktop"
Friend_Computer.cpu = "Intel Core i3"

print(f"Meklit's Computer Name is called {Meklit_Computer.name}.\n It is {Meklit_Computer.cpu}")
# Output: Meklit's Computer Name is called Hp laptop.
#         It is Intel Core i5
```

- Analogy: One **Flower** class → many objects like Daisy, Sunflower, Lily (different flowers based on the same blueprint).

### Checking type() of an Object
```python
Meklit_Computer = Computer()
print(type(Meklit_Computer))
# Output: <class '__main__.Computer'>

a = 4
print(type(a))
# Output: <class 'int'>
```
- `a` and `Meklit_Computer` are **objects**; `int` and `Computer` are **classes**.

### Giving Behaviours == Creating Methods
- Functions inside a class are called **methods**.
- Calling syntax: `ClassName.method(object)`
- Every method needs a `self` parameter — `self` refers to the object itself.

```python
class Computer:
    # Attributes
    name = ""
    cpu = ""

    # Behavior
    def run(self):
        return "BIOS is Good!"

Meklit_Computer = Computer()
Meklit_Computer.name = "Hp laptop"
Meklit_Computer.cpu = "Intel Core i5"

print(f"Running: {Computer.run(Meklit_Computer)}")
```

### Python Constructors (`__init__`)
- Earlier, attributes were set manually one by one.
- We can instead use a **constructor** to set values automatically when the object is created.
- `__init__()` is the constructor method — called automatically whenever a new object is instantiated.
- `self.name` refers to the attribute **inside** the class; `name` (the parameter) is the value coming from **outside**.
- If a constructor requires values, we must pass them when creating the object.

```python
class Bike:
    # constructor function
    def __init__(self, name=""):
        self.name = name

bike1 = Bike()
bike1 = Bike("Mountain Bike")
```

```python
class Computer:
    # Creating Attributes
    def __init__(self, name, cpu):
        self.name = name
        self.cpu = cpu

    # Creating Behavior
    def run(self):
        return "BIOS is Good!"

# Creating objects based on the blueprint
Meklit_Computer = Computer('Hp Laptop', 'Intel i5')
Friend_Computer = Computer("Dell Desktop", "Intel Core i3")

print(f"Meklit's Computer Name is called {Meklit_Computer.name}.\n It is {Meklit_Computer.cpu}")
```

### Python Inheritance
- A way of creating a **new class** that reuses properties of an **existing class**.
- Syntax:
```python
class NewClass(OldClass):
    ...
```

```python
# base class
class Animal:
    def eat(self):
        print("I can eat!")

    def sleep(self):
        print("I can sleep!")

# derived class
class Dog(Animal):
    def bark(self):
        print("I can bark! Woof woof!!")

# Create object of the Dog class
dog1 = Dog()

# Calling members of the base class
dog1.eat()
dog1.sleep()

# Calling member of the derived class
dog1.bark()

# Output:
# I can eat!
# I can sleep!
# I can bark! Woof woof!!
```

### Python Encapsulation
- Encapsulation = bundling attributes and methods together inside a **single class**.
- It allows better control and protection of data — data should be accessed/modified only through specified methods (e.g., a `setprice()` method rather than changing the attribute directly).

```python
class Computer:
    def __init__(self, name, cpu):
        self.name = name
        self.cpu = cpu
        self.price = 1000

    def run(self):
        return "BIOS is Good!"

    def setprice(self, birr):
        self.price = birr

Meklit_Computer = Computer('Hp Laptop', 'Intel i5')
Friend_Computer = Computer("Dell Desktop", "Intel Core i3")

print(f"Meklit Computer price is: {Meklit_Computer.price} birr.")
# Ye PC waga chemere! (changing the price)
Meklit_Computer.setprice(2000)
print(f"Meklit Computer price is: {Meklit_Computer.price} birr.")

# Output: Meklit Computer price is: 1000
#         Meklit Computer price is: 2000
```

---

## 6. Packages / Modules

### Package Installing
- Same as package installing seen in Linux tutorial.
- On terminal:
```
pip install packagename
```

### Package Using
- To use a package in Python:
```python
import packagename
```
- Each package has its own classes and methods, so we need to study each package individually.

```python
import sys

a = sys.argv[2]
```
- Here, we imported the `sys` package and used its `argv` method to create object `a`.

- Going forward, learning "web development with Python" is really just learning specific packages:
  - Django, Flask, Pandas, NumPy, etc.
- Will go deeper into packages later when building hacking tools.
- **Don't forget to practice!**

---

## Summary
- Functions let us break tasks into reusable blocks; recursion lets a function call itself.
- Lambda functions are quick, unnamed, one-line functions — often used with `filter()` and `map()`.
- OOP organizes code around **classes** (blueprints) and **objects** (instances), with **attributes**, **methods**, **constructors (`__init__`)**, **inheritance**, and **encapsulation**.
- Packages/modules extend Python's functionality via `pip install` and `import`.
