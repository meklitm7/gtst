# Introduction to Python Programming  
 

---

## 1. What is a Programming Language?
- A language that lets humans communicate with computers (computers can't understand human languages like English, French, Amharic, Arabic, etc.).
- Computers have their own languages too: **Assembly, C, C++, Java, JavaScript, Python, Ruby, Perl, Go...**
- A programming language lets us write **programs** using those languages.

## 2. What is a Program?
- A program = an **algorithm** expressed in a programming language.
- **Algorithm** = a detailed sequence of actions to accomplish a task (named after Iranian mathematician **Al-Khwarizmi**).
- Technically, an algorithm must reach a result after a **finite number of steps**.

### Algorithm Example
To ask someone their name:
1. Walk to the person
2. Greet them
3. Wait for a response
4. Ask "What is your name?"

> There can be many different algorithms for the same task.

## 3. Pseudocode
- A simplified, structured way to write program logic in plain language — no need to worry about actual syntax.
- Uses short, clear statements to describe each step.
- Helps beginners understand logic and helps programmers plan before writing real code.

**Example (login process):**
```
BEGIN
    PROMPT user for username
    PROMPT user for password
    IF username and password match
        DISPLAY "Login Successful"
    ELSE
        DISPLAY "Login Failed"
END
```

**Example (simple calculator):**
```
BEGIN
    DISPLAY "Enter the first number:"
    INPUT number1
    DISPLAY "Enter the second number:"
    INPUT number2
    result = number1 + number2
    DISPLAY "The result is: ", result
END
```

**Advanced version** adds operation choice (+, -, *, /) with an `IF/ELSE IF` chain, including a check for division by zero.

## 4. Evolution of Input/Output (I/O)
- **Early computing:** programs submitted on **punch cards** with all required data, executed with other programs sharing libraries. Output went to a **line printer**.
- **Later:** **interactive processing** was introduced, letting users provide data *while the program runs* (Question & Answer format).

## 5. Generations of Computers
1. **First Generation** – Vacuum Tubes → punch cards
2. **Second Generation** – Transistors → programming began here, using Assembly
3. **Third Generation** – Integrated Circuits → BASIC, COBOL, Pascal, Fortran, C, C++, Perl, Ada
4. **Fourth Generation** – Microprocessors → Python, SQL, Matlab
5. **Fifth Generation** – Artificial Intelligence

> First-generation computers could only solve one problem at a time — setting up a new program could take days or weeks.

## 6. Types of Programming Languages
Computers only understand **binary (0/1)**; humans don't. Languages are classified by closeness to machine vs. human language:

- **Closer to machine → faster execution**
- **Closer to human language → slower execution**

### A) Low-Level Programming Language
- Close to machine/hardware; harder for humans to read but very fast.
- Examples: **Assembly, C**

### B) High-Level Programming Language
- Close to human language; easier to read and write.
- Examples: **Python, C++, Java, JavaScript**

### How High-Level Languages Are Understood by Computers
1. **Compiler** – converts the *entire* source code into bytecode/machine code before execution.
   - Examples: C, C++, Java
2. **Interpreter** – executes source code *line by line* directly.
   - Example: **Python**

## 7. Uses of Programming Languages (General)
- Android app development
- Website development
- Machine learning
- Artificial Intelligence
- Game development
- Big data technology
- Desktop software development
- Hacking tool development

## 8. What is Python Programming?
- Python is a **high-level, interpreted** programming language.
- Very easy to learn, simple/readable syntax (e.g., `print` vs. C++'s `cout` vs. Java's `System.out.println`).

### History of Python
- Developed by **Guido van Rossum** in the late 1980s–early 1990s at the National Research Institute for Mathematics and Computer Science, Netherlands.
- Derived from: **ABC, Modula-3, C, C++, Algol-68, SmallTalk, Unix shell** and other scripting languages.
- Now maintained by a core development team; Guido van Rossum still plays a key role.

### Uses of Python (Specific)
- Data visualization
- Data analysis
- Machine learning
- Artificial intelligence
- Back-end web development (Django, Flask)
- Game development
- Hacking script writing

## 9. Installing Python
- **Windows:** download installer from the official website.
- **Linux:** usually comes pre-installed; otherwise install via `apt install python3`.
- Official site: **https://www.python.org/**

## 10. IDE vs. Code Editor
- **IDE (Integrated Development Environment):** software built to write & run a *specific* programming language.
  - Example: PythonIDE
- **Code Editor:** software that can write *any* programming language; can run code if compiling/interpreting features are added.
  - Example: **Sublime Text, VS Code**

### Setting Up VS Code for Python (Linux)
1. Open VS Code → install the **Python extension** (by Microsoft) from the Extensions panel.
2. Create a **New Text File**.
3. Write code, then **Save As** with a `.py` extension.
4. Click the **Run ▶** button (or use the terminal).
5. Output appears in the integrated **Terminal**.

Example test:
```python
print("hello world!")
```

## 11. Outputs and Comments

### Output — `print()`
- Syntax: `print(object='', sep='', end='')`
- In pseudocode, use the term **"Display"**.

```python
print('Python is powerful')
# Output: Python is powerful

print('Good Morning!', end=' ')
print('It is rainy today')
# Output: Good Morning! It is rainy today

print('New Year', 2023, 'See you soon!', sep='. ')
# Output: New Year. 2023. See you soon!
```

- Special characters: `\n` = new line, `\t` = tab space
- Multiple values: `print(text1, text2, text3...)`

### Comments
- Notes in code that are **not executed** — help explain code to yourself/others.
- Syntax: `# This is a comment line`

```python
# using input() to take user input
num = input('Enter a number: ')
print('You Entered:', num)
print('Data type of num:', type(num))
```

### Python Keywords
Reserved words with special meaning to the interpreter — cannot be used as variable names:
```
False   await   else     import    pass
None    break   except   in        raise
True    class   finally  is        return
and     continue for     lambda    try
as      def     from     nonlocal  while
assert  del     global   not       with
async   elif    if       or        yield
```

## 12. Variables
- Variables are **value holders / containers** that store data.
- The act of assigning a value is called **Variable Declaration**.
- The name holding the data is called an **Identifier**.
- In pseudocode, use the term **"Declared"**.

```python
gtst = 10
print(gtst)
# Output: 10

gtst = 10
print("You are ", gtst, " Years old!")
# Output: You are 10 Years old!

gtst = 21   # value can be changed
print("You are ", gtst, " Years old!")
# Output: You are 21 Years old!
```

### f-strings (formatted printing)
- Syntax: `print(f"yourtext {variable}")`
```python
name = 'Meklit'
print(f"Your name is {name}.")
# Output: Your name is Meklit.
```

### Identifier Naming Rules
- No spaces between words → use underscore `_` instead (e.g., `my_name`, not `my name`)
- Don't use numbers as an identifier name

## 13. Data Types
Python has several major data type categories:

| Data Type | Classes | Description |
|---|---|---|
| Numeric | `int`, `float`, `complex` | holds numeric values |
| String | `str` | holds sequence of characters |
| Sequence | `list`, `tuple`, `range` | holds collection of items |
| Mapping | `dict` | holds data in key-value pairs |
| Boolean | `bool` | holds `True` or `False` |
| Set | `set`, `frozenset` | holds collection of unique items |

### A) Numeric Data Types
- **int** – signed integers, non-limited length
- **float** – floating decimal points, accurate up to 15 decimal places
- **complex** – complex numbers (e.g., `1+2j`)
- Use `type()` to check a variable's data type

```python
num1 = 5
print(num1, 'is of type', type(num1))
# 5 is of type <class 'int'>

num2 = 2.0
# 2.0 is of type <class 'float'>

num3 = 1+2j
# (1+2j) is of type <class 'complex'>
```

### B) String Data
- A sequence of characters wrapped in single `' '` or double `" "` quotes.
```python
name = 'Python'
print(name)

message = 'Python for beginners'
print(message)
```

### C) Sequence Data
**1) Lists**
- Ordered collection of items (same or different types), enclosed in `[ ]`, comma-separated.
- Access items by **index** (starting at 0).
- Add items with `.append()`.
```python
languages = ["Swift", "Java", "Python"]
print(languages[0])        # Swift
print(languages[2])        # Python

languages.append("Amharic")
print(languages)           # ["Swift", "Java", "Python", "Amharic"]
```

**2) Tuples**
- Ordered sequence like a list, but **immutable** (cannot be modified after creation).
- Uses parentheses `( )`.
```python
product = ('Microsoft', 'Xbox', 499.99)
print(product[0])   # Microsoft
print(product[1])   # Xbox
```

### D) Dictionary Data
- Unordered collection stored as **key/value pairs**.
- Use the **key** to retrieve the matching **value** (not the reverse).
```python
capital_city = {'Nepal': 'Kathmandu', 'Italy': 'Rome', 'England': 'London'}
print(capital_city['Nepal'])       # Kathmandu
print(capital_city['Kathmandu'])   # Error! Can't use a value as a key
```

---

 

 
