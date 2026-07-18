# Core of Python Programming  
 
 

## 1. Indexing

- We already know lists have **index numbers**, starting at `0`.

```python
languages = ["Python", "Swift", "C++"]
```
| "Python" | "Swift" | "C++" |
|---|---|---|
| index 0 | 1 | 2 |

- **Negative indexing** counts backward from the end, starting at `-1`.

| "Python" | "Swift" | "C++" |
|---|---|---|
| index 0 | 1 | 2 |
| negative index -3 | -2 | -1 |

```python
languages = ["Python", "Swift", "C++"]

# access item at index 0 (last item using negative)
print(languages[-1])   # C++

# access item at index 2 using negative
print(languages[-3])   # Python
```

> ⚠️ **Note:** list index always starts at `0`, not `1`.

### Indexing also works on Strings & Tuples
```python
name = ('hello', 23, 22)
print(name[2])
# Output: 22

name = 'Meklit'
print(name[2])
# Output: k

name = 'Meklit'
print(name[-2])
# Output: i
```

---

## 2. Slicing

- Slicing lets you grab a **section** of items, not just one — using the `:` operator.
- Syntax:
```
Mylist[ start : stop : step ]
```
- `a[m:n]` returns the portion:
  - Starting at position **m**
  - Up to but **not including n**
  - Negative indexing can be used too
- Applies especially well to strings.
- Default `step` = 1 (no need to write it)
- Default stop = end of the sequence (no need to write it)

```python
name = 'No 1 is Meklit'
print(name[8:14:1])
# Output: Meklit
```

### More slicing examples
```python
name = 'No 1 is Meklit'
print(name[8:14])
# Output: Meklit

print(name[8:])
# Output: Meklit

print(name[8:-1])
# Output: Meklit (minus last char depending on string length)
```

```python
name = ['ethiopia', 'banana', 'china', 'apple']
print(name[::])
# Output: ['ethiopia', 'banana', 'china', 'apple']
```

**Indexing/step reference:**
| item | ethiopia | banana | china | apple |
|---|---|---|---|---|
| normal index | 0 | 1 | 2 | 3 |
| negative index | -4 | -3 | -2 | -1 |

```python
name = ['ethiopia', 'banana', 'china', 'apple']
print(name[-1:0:-2])
# Output: ['apple', 'banana']
```

### Quiz-style examples I noted down
```python
name = ['ethiopia', 'banana', 'china', 'apple']
print(name[::-1])
# Output: ['apple', 'china', 'banana', 'ethiopia']  (reverses the list)

print(name[::-2])
# Output: ['apple', 'banana']  (reverse, skip every other)

print(f"countries are: {name[-2::-2]}")
# Output: countries are: ['china', 'ethiopia']
```

---

## 3. User Input Handling

Python has **2 types of input**:
1. By `input()` function
2. By Arguments (command line)

### A) `input()` function
- Syntax: `var = input("Text you like to display: ")`
- Accepts input and **stores it in a variable**.

```python
name = input("What is your name?\n name: ")
print(f"Hello {name}!")

# Output: What is your name?
#         name: 'Meklit'
#         Hello Meklit!
```

- `input()` always returns a **string** by default. We can convert type using `int()`, `float()`, `eval()`, `str()`...

```python
number = input("Enter number: ")
print(type(number))
# Output: <class 'str'>

number = int(input("Enter number: "))
print(type(number))
# Output: <class 'int'>

number = eval(input("Enter number: "))
print(type(number))
# Output: <class 'int'>

number = float(input("Enter number: "))
print(type(number))
# Output: <class 'float'>
```

### B) By Arguments (`sys.argv`)
- Helps get input directly from the command line.
- Shell example: `python gtst.py arg1 arg2 arg3`

```python
import sys
name = sys.argv[1]
print(f"Hello {name}!")
```
```
PS> python test.py Meklit
Hello Meklit!
```

- ⚠️ If a name has multiple words (e.g. "Meklit Tesfaye"), it gets split into **separate arguments** unless wrapped in quotes:
```
python test.py Meklit Tesfaye
Hello Meklit!     # only takes the first word

python test.py "Meklit Tesfaye"
Hello Meklit Tesfaye!    # quotes keep it as one argument
```

### More on arguments
```python
import sys
firstname = sys.argv[1]
lastname = sys.argv[2]
print(f"Hello {firstname}!, Your Father name is: {lastname}.")
```
```
PS> python test.py Meklit Tesfaye
Hello Meklit!, Your Father name is: Tesfaye.
```
- Can create variables up to `n` arguments: `var = sys.argv[100]`

---

## 4. Operators

- Operators are symbols that perform operations on variables/values.
```python
print(5 + 6)   # 11
```
- Types of operators in Python:
  - Arithmetic operators
  - Assignment operators
  - Comparison operators
  - Logical operators
  - Bitwise operators
  - Special operators

### A) Arithmetic Operators
- Simple math operations. Inputs must be `int`, `float`, or via `eval`.

| Operator | Operation | Example |
|---|---|---|
| `+` | Addition | 5 + 2 = 7 |
| `-` | Subtraction | 4 - 2 = 2 |
| `*` | Multiplication | 2 * 3 = 6 |
| `/` | Division | 4 / 2 = 2 |
| `%` | Modulo | 5 % 2 = 1 |
| `**` | Power | 4 ** 2 = 16 |

```python
a = 7
b = 2
print('Sum: ', a + b)
print('Subtraction: ', a - b)
print('Multiplication: ', a * b)
print('Division: ', a / b)
print('Modulo: ', a % b)
print('Power: ', a ** b)
```

### B) Assignment Operators
- Used to assign values to variables — arithmetic operation happens **first**, then the assignment.

| Operator | Name | Example |
|---|---|---|
| `=` | Assignment | a = 7 |
| `+=` | Addition Assignment | a += 1 → a = a + 1 |
| `-=` | Subtraction Assignment | a -= 3 → a = a - 3 |
| `*=` | Multiplication Assignment | a *= 4 → a = a * 4 |
| `/=` | Division Assignment | a /= 3 → a = a / 3 |
| `%=` | Remainder Assignment | a %= 10 → a = a % 10 |
| `**=` | Exponent Assignment | a **= 10 → a = a ** 10 |

```python
a = 10
b = 5
a += b   # a = a + b
print(a)
# Output: 15
```

### C) Comparison Operators
- Compare two variables → return **boolean** (`True`/`False`)

| Operator | Meaning | Example |
|---|---|---|
| `==` | Is Equal To | 3 == 5 → False |
| `!=` | Not Equal To | 3 != 5 → True |
| `>` | Greater Than | 3 > 5 → False |
| `<` | Less Than | 3 < 5 → True |
| `>=` | Greater Than or Equal | 3 >= 5 → False |
| `<=` | Less Than or Equal | 3 <= 5 → True |

### D) Logical Operators
- Check if an expression is TRUE or FALSE, using **truth tables**: `and`, `or`, `not`

**AND (`and` )** → only True **and** True = True

| A | B | A and B |
|---|---|---|
| True | True | True |
| True | False | False |
| False | True | False |
| False | False | False |

**OR (`or` )** → only False **or** False = False

| A | B | A or B |
|---|---|---|
| True | True | True |
| True | False | True |
| False | True | True |
| False | False | False |

**NOT (`not` )** → simply the opposite

| A | not A |
|---|---|
| True | False |
| False | True |

```python
print(True and True)    # True
print(True and False)   # False
print(True or False)    # True
print(not True)         # False
```

### E) Bitwise Operators
- Computers work with **binary** (bits). `True` = 1, `False` = 0.
- `bin(YourDecimal)` shows the binary value of a decimal.
- Used to do math (logical operations) on the **binary value** of an expression.
- Very important for **cryptography / hacking**!

Types:
- Complement / NOT `~`
- AND `&`
- OR `|`
- XOR `^`
- Left Shift `<<`
- Right Shift `>>`

```python
print("3 in binary is: ", bin(3))
print("11 in decimal is: ", int('11', 2))
# Output: 3 in binary is: 0b11
#         11 in decimal is: 3
```

**Complement (`~`)**
- Converts value to binary, reverses each bit, converts back to decimal.
- In simple math: adds 1 to the number, then makes it negative.
```
~12  =>  -(12+1)  =  -13
~4   =>  -5
```
```python
print(~12)
# Output: -13
```

**AND (`&`)**
- You can pad binary with leading 0s if it's not the same digit length (`bin(7) → 111`, but can write `0111`)
```
10 -> 1010
      &&&&
7  -> 0111
------------
AND   0010  == 2
```
```python
print(10 & 7)
# Output: 2
```

**OR (`|`)**
- Same idea as AND, but different logic operator
```
10 -> 1010
      ||||
7  -> 0111
------------
OR    1111  == 15
```
```python
print(10 | 7)
# Output: 15
```

**XOR (`^`)**
- If bits are same → 0. If different → 1.
```
1^1 = 0 , 0^0 = 0   (same → 0)
1^0 = 1 , 0^1 = 1   (different → 1)
```
```
10 -> 1010
      ^^^^
7  -> 0111
------------
XOR   1101 == 13
```
```python
print(10 ^ 7)
# Output: 13
```

**Left Shift (`<<`)** — shifts bits to the left
```
10<<2 - shifting 2 bits to the left
10 -> 1010.0000
      101000.00
------------
<<    101000 == 40
```
```python
print(10 << 2)
# Output: 40
```

**Right Shift (`>>`)** — shifts bits to the right
```
10>>2 - shifting 2 bits to the Right
10 -> 1010.0000
      10.100000
------------
>>    10 == 2
```
```python
print(10 >> 2)
# Output: 2
```

---

## 5. Indentation

- Indentation = whitespace that Python uses to define code blocks/structure.
- ⚠️ If indentation is wrong → **IndentationError**, program breaks.
- Similar concept to nested tags in XML (children/inner elements get extra indent).

---

## 6. If...else Conditions

- We use `if` to run a block of code **only when a condition is True**.
- Example use case: assigning grades based on marks:
  1. if percentage > 90 → grade A
  2. if percentage > 75 → grade B
  3. if percentage > 65 → grade C

Python has **3 forms**:
1. `if` statement
2. `if...else` statement
3. `if...elif...else` statement

### A) `if` statement
- Evaluates a condition.
  - If **True** → code inside `if` body runs.
  - If **False** → code inside `if` body is **skipped**.

Syntax:
```python
if condition:
    # body of if statement
```

```python
number = 10
# check if number is greater than 0
if number > 0:
    print('Number is positive.')
print('The if statement is easy')

# Output: Number is positive.
#         The if statement is easy
```

### B) `if...else` statement
- `if` can have an optional `else` clause for when the condition is False.

```python
if condition:
    # block of code if condition is True
else:
    # block of code if condition is False
```

```python
number = 10
if number > 0:
    print('Positive number')
else:
    print('Negative number')

print('This statement is always executed')

# Output: Positive number
#         This statement is always executed
```

### C) `if...elif...else` statement
- If condition1 True → code block 1 runs
- If condition1 False → condition2 is checked
- If condition2 True → code block 2 runs
- If condition2 False → code block 3 (`else`) runs

```python
number = 0
if number > 0:
    print("Positive number")
elif number == 0:
    print('Zero')
else:
    print('Negative number')

print('This statement is always executed')
```

### Nested if statements
- An `if` statement placed **inside another `if`** statement.
- Both conditions must be True to reach the inner body.

```python
number = 5

# outer if statement
if (number >= 0):
    # inner if statement
    if number == 0:
        print('Number is 0')
    # inner else statement
    else:
        print('Number is positive')

# outer else statement
else:
    print('Number is negative')

# Output: Number is positive
```

---

## 7. Logical Errors (Exceptions)

- Errors that occur **at runtime** (after passing the syntax check) are called **exceptions** or **logical errors**.
- Examples:
  - Calling an index greater than the list size → `IndexError`
  - Dividing a number by zero → `ZeroDivisionError`
  - Syntax/naming mistake at runtime → `NameError`
  - ...and more
- These runtime errors can cause serious damage to the program, so we need to **handle** them.

---

## 8. Error Handling

- We handle errors using **`try...except`** blocks.

```python
try:
    # code that may cause exception
except:
    # code to run when exception occurs
```

### Example 1 — ZeroDivisionError
```python
try:
    numerator = 10
    denominator = 0
    result = numerator/denominator
    print(result)
except:
    print("Error: Denominator cannot be 0.")

# Output: Error: Denominator cannot be 0.
```

### Example 2 — Handling specific exceptions
```python
try:
    even_numbers = [2, 4, 6, 8]
    print(even_numbers[5])
except ZeroDivisionError:
    print("Denominator cannot be 0.")
except IndexError:
    print("Index Out of Bound.")

# Output: Index Out of Bound
```
- We can catch **specific exception types** separately (`ZeroDivisionError`, `IndexError`, etc.), so we can give a more accurate error message depending on what actually went wrong.

---

## 9. Python Loops

- Loops are used to **repeat a block of code**.
- Example: showing a message 100 times without writing `print()` 100 times.
- 2 types of loops in Python:
  - **For Loop**
  - **While Loop**

### A) For Loop
- Runs a block of code for a certain number of times.
- Used to **iterate over any sequence** — list, tuple, string, etc.

Syntax:
```python
for val in sequence:
    # statement(s)
```
- `sequence` = a list, tuple, string, or range
- `val` = variable holding the current item during iteration

```python
languages = ['Swift', 'Python', 'Go', 'JavaScript']

# access items of a list using for loop
for language in languages:
    print(language)

# Output:
# Swift
# Python
# Go
# JavaScript
```

### `range()` keyword
- A series of values between two numeric intervals.
- Syntax: `range(size)`

```python
number = range(5)
print(number)
# Output: range(0, 5)

for i in range(5):
    print(i)
# Output: 0 1 2 3 4
```

### `len()` keyword
- Shows the **length** of a sequence (list, tuple, or string).

```python
a = [1, 2, 3, 4, 5, 'hello']
print(len(a))
# Output: 6

for i in range(len(a)):
    print(i)
# Output: 0 1 2 3 4 5
```

### B) While Loop
- Runs code repeatedly **until a certain condition is met**.

Syntax:
```python
while condition:
    # body of while loop
```

```python
# program to display numbers from 1 to 5

# initialize the variable
i = 1
n = 5

# while loop from i = 1 to 5
while i <= n:
    print(i)
    i = i + 1
```

**How it evaluates:**
| Variable | Condition (i <= n) | Action |
|---|---|---|
| i=1, n=5 | True | 1 is printed, i → 2 |
| i=2, n=5 | True | 2 is printed, i → 3 |
| i=3, n=5 | True | 3 is printed, i → 4 |
| i=4, n=5 | True | 4 is printed, i → 5 |
| i=5, n=5 | True | 5 is printed, i → 6 |
| i=6, n=5 | False | loop terminates |

### Infinite loops
```python
# infinite while loop
while True:
    # body of the loop
```

### For vs While — the difference
- **For loop**: used when the number of iterations is **known**.
- **While loop**: used when the number of iterations is **unknown** — depends on a condition.

Example use case: checking a user's level and printing "you have passed level {n}" until the user's level equals the class's final level.
```python
current_level = 0
final_level = 5
while current_level <= final_level:
    print('You have passed level', current_level)
    current_level += 1
print('Level Ends')
```

- **For loops** end when the iterable is finished.
- **While loops** end when the condition becomes False.

### `break`
- Used to **exit an infinite loop** (or any loop) early.

```python
code = [2313, 2314, 4325, 6546]
errors = 0

while True:
    if errors <= 5:
        user = int(input(f"Enter The captcha correctly {code[0]}:\n>>"))
        if user != int(code[0]):
            print(f"trail{errors}: incorrect!, try again")
            errors += 1
        elif user == int(code[0]):
            print("wellDone!")
            break
    else:
        print("try again,next time.")
        break
```
- This example: keeps asking the user to enter a correct captcha code.
  - If wrong → error count goes up, keeps asking again (up to 5 tries)
  - If correct → prints "wellDone!" and breaks out of the loop
  - If errors exceed the limit → prints "try again, next time" and breaks

---

## Key Takeaways
- Indexing/slicing works the same way for lists, strings, and tuples.
- `input()` always returns a string — convert type as needed (`int`, `float`, `eval`).
- `sys.argv` reads input straight from the command line; wrap multi-word input in quotes.
- Bitwise operators matter a lot for cryptography/security work.
- Proper indentation is mandatory in Python — no exceptions.
- Use `try...except` to prevent runtime errors from crashing the program.
- Use `for` when the number of repetitions is known, `while` when it depends on a condition.
- `break` lets you exit a loop early once a goal condition is met.
