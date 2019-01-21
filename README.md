# Differences between Java and Python

Housekeeping notes:

- You can determine the version of your Python installation with `python --version`
- Python uses `print` to output to the console where Java uses `System.out.println`

## Structure

Java uses braces or curly brackets to organize code into classes, methods, and blocks. Indention and white space is generally optional; it is used mostly to help code readability. White space usage is a matter of personal taste and does not affect compilation of the program.

However, Python uses indentation to indicate blocks of code ("suites") and is therefore critical to the correct execution of the program. The compiler may alert the programmer when expected indentation is missing, for example:

    x = 5
    if x < 5:
    print ('less than 5')
    else:
    print ('5 or greater')
    
Results in 

    IndentationError: expected an indented block
    
Note that the compiler won't catch every instance of missing indentation. Consider the last line in this code:

    x = 5
    if x < 5:
        print ('less than 5')
    else:
        print ('5 or greater')
    x += 1          # Is this a mistake or intentional?

## Line Endings

Java requires semicolons at the end of assignment and procedure call lines. Semicolon usage to denote the end of a line in Python is optional, similar to Javascript. (It may be used to separate multiple statements on a single line.)

## Comments

Java uses block `/* ... */` and line `// ...` comments. Python uses the hash `# ...` to denote a comment (similar to various Unix shell scripting languages). The hash may appear anywhere in the line; text after the hash is included in the comment.

    # This is a comment
    x = 5 # So is this

## Types

While Java is statically typed, Python is dynamically typed: A variable's type is not explicitly provided, but derived from the assigned value.

_Java_:

    int x = 5;
    String y = "hello!";
    
_Python_: 

    x = 5
    y = "hello!"
    
Python has cardinal types similar to those found in Java: Strings, integers, floats, and booleans.

### Numbers

This includes integers and floats and negative numbers.

    x = 5
    y = 3.14159267
    z = -1.023

### Strings

Java only accepts the quote (") character when declaring static String objects, reserving the apostrophe for working with characters. Python permits the use of either quote or apostrophy (') on strings:

    x = 'hello'
    y = "world"

Like Java, strings may be concatenated with the arithmetic addition operator:

    z = x + y  # z will contain "helloworld"

### Booleans

Python has `True` and `False` boolean keywords (starting with Python 3); unlike Java the leading character must be capitalized.

    x = True
    y = False

## Arithmetic Operations

Python supports the same arithmetic operations that are found in Java: Addition, subtraction, multiplication, and division. Operation ordering and grouping works the same as it does in Java; higher order operators (multiplication and division) take presidence over lower order operations (addition and subtraction), and parenthesis can be used to group operations. Python also supports modulus with the '%' operator; the syntax is the same as it is in Java.
    
It's important to note that although Python is dynamically typed, variables of different types cannot be mixed in arithmetic operations. For example, the following code is permitted in Java but it will result in a compilation error in Python:

    x = 5
    y = "hello"
    z = x + y   # Results in a type error
    
Bitwise operators are also supported for numbers: AND, OR, XOR, complement, and shift left and right. They work the same as they do in Java.

NOTE: Python does not support the increment `++x` and decrement `--x` operators. Use `x += 1` and `x -= 1` instead.

### `//` and `**`

Python provides two convenience operators, `//` for division with an integer result and `**` for computing exponents.

    x = 5
    y = x // 2  # y equals 2

    y = x ** 2  # y equals 25

## Simple Data Structures

Both Java and Python have the concept of a simple array. Python uses "List" and "Tuple" for this data structure. Python also has Dictionaries for managing key-value pairs (similar to the Maps API present in Java's Collections framework). 

### Lists

Python lists and Java arrays work basically the same: They're dynamically allocated arrays that use zero-based index to access a single element. There is one important difference: Dynamic typing allows a Python list to easily contain different typed values. (One can accomplish this in Java using `Object[]` but this isn't a common practice.)

_Java_:

    int x[] = {1, 2, 3};
    String y[] = {"abc", "def"};
    
_Python_:

    x = [1, 2, "abc", True]
    
Both languages use square-bracket notation when accessing elements, although Python can use negative offsets as well as positive offsets to "wrap around" the list.

    x = [1, 2, 3, 4]
    y = x[0]        # y is 1
    y = x[-1]       # y is 4

Python has a list sub-range feature that Java programmers need library calls for:

    x = [1, 2, 3, 4]
    y = x[1:2]      # y is [2, 3]
    y = x[2:]       # y is [3, 4]

List length in Python is obtained by calling the `len` function and passing the list as the sole argument.
    
    x = [1, 2, 3]
    y = len(x)      # y is 3
    
Python also supports list concatenation with the addition operator (Java can accomplish this with library calls):
    
    x = [1, 2, 3]
    y = [4, 5, 6]
    z = x + y       # z is [1, 2, 3, 4, 5, 6]

### Tuples

Python provides tuples as an immutable alternative to lists. Whereas list elements can be replaced, attempting to write to a tuple will result in a runtime error.

    x = (1, 2, 3)
    x[3] = 4            # Runtime error

However, appending to the end of a tuple is permitted:

    x = (1, 2, 3)
    x = x + (4,)         # x is (1, 2, 3, 4)

Note a trailing comma is required to avoid a runtime error.

### Dictionaries

Dictionaries store key-value pairs. Keys may be strings or integers or floats, and values can be any type.

    x = {"name": "Sally", "age": 30, "height": 64}
    y = x["name"]        # y is "Sally"

Use the `len(...)` function to get the dictionary length.

## Control Structures

Like Java, Python supports `if`, `for`, and `while`. Note that `do...while` is not supported in Python.

### Conditionals

Python's `if` statements are conceptually similar to those in Java, but the syntax has important differences: 

- Parenthesis are not used to enclose expressions; instead they are terminated with a colon character
- `else if` is shortened to `elif`
- Curly braces are not used to provide scope; that is indicated with required indentation
- Use `and`, `or`, and `not` to combine expressions

_Java_: 

    int x = 5;
    if (x > 10) {
        System.out.println("Greater than 10");
    }
    else if (x >= 5 && x <= 10) {
        System.out.println("Between 5 and 10");
    }
    else {
        System.out.println("Less than 5");
    }

_Python_:

    x = 5
    if x > 10:
        print("Greater than 10")
    elif x >= 5 and x <= 10:
        print("Between 5 and 10")
    else:
        print("Less than 5")        
        
Note that blocks of a single line can be collapsed, for example:

    x = 5
    if x > 10: print("Greater than 10")
    
#### Comparison Expressions

Java and Python use the same set of comparison operators: equals `==`, not-equals `!=`, greater-than `>`, less-than `<`, greater-than-equals `>=`, and less-than-equals `<=`. However, Python uses `and` and `or` keywords to combine multiple comparisons into a single expression.

    x = 7
    if x < 5 and x > 10: print("x is in range")

### Loops

Python loop structures share similar concepts to those found in Java, but with some important syntactical differences. The `for ... in` loop is intended for iterating through lists and tuples, and the `while` loop will repeat a block of code while a condition holds true.

Perhaps the most important difference is that indention denotes the body of the loop in Python, and is therefore critical to the loop's operation.

#### `for...in`

_Java_:

    int[] values = {1, 2, 3};
    int sum = 0;
    for (int i = 0; i < values.length; i++) {
        sum += values[i];
    }
    System.out.println("sum = " + sum);
    
_Python_:

    values = (1, 2, 3)
    sum = 0;
    for i in values:
        sum += i;
    print ("sum = {0}".format(sum))

#### `while` 

_Java_:

    int[] values = {1, 2, 3};
    int sum = 0;
    int i = 0;
    while (i < values.length) {
        sum += values[i++];
    }
    System.out.println("sum = " + sum);
    
_Python_:

    values = (1, 2, 3)
    sum = 0
    i = 0
    while i < len(values):
        sum += values[i]
        i += 1
    print ("sum = {0}".format(sum))
    
Python also supports the `break` keyword inside of `while` loops. It can be used the same way it is used in Java.

    i = 0
    while True:
        if i < 10: i += 1
        else: break

## Functions

Functions in Python are independent, reusable units of code. They may exist outside the context of a class or object making them more like functions in C or Javascript. There isn't an analog for a Python function in Java where methods must belong to a class.

Aside from that, however, Java methods and Python functions have a lot in common. Functions may have parameters, and a value can be returned to the caller. Parameter types and the return type aren't declared because Python is dynamically typed.

Again, it's important to pay attention to indentation since that defines the body of the function.

    def square(value):
        return value * value
    
    y = 2
    x = square(y)
    
## Classes

Classes are the fundamental building blocks for object-oriented programs in both Java and Python. The concepts are similar, but the specifics are different in important ways.

- Python uses reserved function name `__init__` for the class constructor
- Class functions need to include `self` as the first parameter
- `__str__` function performs a similar function to Java's `toString` method

_Java_:

    public class Circle {
        private int x;
        private int y;
        private int radius;
        
        public Circle(int x, int y, int radius) {
            this.x = x;
            this.y = y;
            this.radius = radius;
        }
        
        public void move(int newX, int newY) {
            this.x = newX;
            this.y = newY;
        }
    }
    
    ...
    
    Circle c = new Circle(5, 5, 3);
    c.move(30, 10);
    
_Python_:

    class Circle:
    
        def __init__(self, x, y, radius):
            self.x = x
            self.y = y
            self.radius = radius
                    
        def __str__(self):
            return 'center at {0}, {1} and radius {2}'.format(self.x, self.y, self.radius)
            
        def move(self, new_x, new_y):
            self.x = new_x
            self.y = new_y
            
    c = Circle(5, 5, 3)
    c.move(30, 10)
    
### Inheritance

Python passes the superclass name into the subclass as a parameter whereas Java uses the `extend` keyword. Python also supports function overloading and overriding (see the `__str__` implementations for an example). 

Python also supports full multiple inheritance whereas Java does not.

_Java_:

    public class Shape {
        private int x;
        private int y;
        
        public Shape(int x, int y) {    
            this.x = x;
            this.y = y;
        }
        
        public void move(int newX, int newY) {
            this.x = newX;
            this.y = newY;
        }
    }
    
    ...

    public class Circle extends Shape {
        private int radius;
        
        public Circle(int x, int y, int radius) {
            super(x, y);
            this.radius = radius;
        }
    }
    
    ...
    
    Circle c = new Circle(5, 5, 3);
    c.move(30, 10);

_Python_:

    class Shape:
        
        def __init__(self, x, y):
            self.x = x
            self.y = y
        
        def move(self, new_x, new_y):
            self.x = new_x
            self.y = new_y
            
        def __str__(self):
            return 'center at {0}, {1}'.format(self.x, self.y)

    class Circle(Shape):

        def __init__(self, x, y, radius):
            super().__init__(self, x, y)
            self.radius = radius
        
        def __str__(self):
            return super().__str__() + ' and radius {0}'.format(self.radius)
        
    c = Circle(5, 5, 3)
    c.move(30, 10)

# References

https://wiki.python.org/
https://docs.python.org/3/reference/index.html
https://www.python-course.eu/python3_course.php
https://colab.research.google.com/github/GokuMohandas/practicalAI/blob/master/notebooks/01_Python.ipynb
https://www.apress.com/us/book/9781484232330
