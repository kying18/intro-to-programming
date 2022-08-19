# Lecture 1: Python Basic Types and Variables

# Sources

These notes were adapted or copied verbatim from from [Adam Hartz](https://hz.mit.edu/)'s MIT [6.145 readings](https://hz.mit.edu/catsoop/6.145/), as well as [Think Python 2e](https://greenteapress.com/wp/think-python-2e/) by [Allen Downey](http://www.allendowney.com/wp/).

# Primitive Types and Values

Python has four **primitive types**: **integers**, **floats**, **booleans**, and **strings**. Some also consider **NoneType** as a primitive as well. By primitive, we just mean these values cannot be broken down further into other types. They are the protons, neutrons, and electrons of the programming world!

In Python, these primitive types are associated with a **value**, which is the exact thing it represents. Think of phone numbers. If someone gives me their number, the type is a phone number, but the value is the exact digits in that person's number!

(Note: if you know particle physics, you know that protons and neutrons can be further broken down, but not everyone takes particle physics, so let's pretend for now that they are the building blocks of matter in the universe)

Let's discuss these primitive types:

1. `int` is a type used to represent integers. You've already experienced two integers in the example above: `2` and `3`. Integers in Python are written the way we normally write integers on the page, with one exception: commas cannot be used (we'll find out more later). So, for example, the following are integers: 2, 3, 0, -12, 10000.

2. `float` is a type used to represent real numbers. The most common way to specify a float is as a number with a decimal point. Any number with a decimal point in it is a float (for example, 5.0 or 6.2831 or 3.).

3. `bool` is used to represent the boolean values. In Python, these are represented as `True` and `False`.

4. `string` is used to represent a sequence of characters. We use single quotes (`'`) or double quotes (`"`) around some text to represent a string.

5. `NoneType` is a type with a single value: `None`. `None` is a special kind of object that is designed to represent the absence of a value. This might seem weird for now (indeed, the number 0 felt weird to many civilizations for many centuries!), but it should come to make more sense with time.

Some note about the `float`:
You might wonder why this type is not called "real" or "exact" or "decimal" (`float` seems like a pretty bizarre name, indeed!). The reason is that these values are represented in a computer in a representation called **floating point**. We won't go into detail about this representation in this class, but it is worth noting a few things:

- This representation is used by almost all modern programming languages, and we got that way because it has some nice features.
- However, it is worth noting that this representation cannot exactly represent all real numbers. As such, we will sometimes need to keep in mind that float objects are approximations of the numbers we actually want.
- To see an example of this behavior, try running 0.1 + 0.1 + 0.1. you'll see an unexpected result!

# Algebraic Expressions

We can combine the basic types using **operators**. Previously, we've already seen the `+` operator. Let's explore some other mathematical operators we can use:

- `+` denotes addition
- `-` denotes subtraction
- `*` denotes multiplication
- `/` denotes division
- `i**j` denotes exponentiation

## Order of Operations

If you've learned about order of operations, PEMDAS, it still holds in programming. In case not, we'll briefly cover the ordering here:

- Parentheses have the highest precedence and are evaluated first
- Exponentiation is next
- Multiplication and Division follow exponentiation
- Addition and Subtraction come last

For example, an expression like `5+(2*(4-1)+4**3)` would folloow the following order:

1. We evaluate what is inside the parentheses first: `2*(4-1)+4**3`.
2. We must also apply PEMDAS here as well. Evaluating the parentheses, we get: `2*3+4**3`.
3. Now, evaluating the exponent, we get: `2*3+64`.
4. Evaluating the multiplication, we get: `6+64`.
5. Finally, we perform the addition here, and get `70` for the final value of the parentheses.
6. For the value of the whole expression, we get `5+70`, which gives us then `75`.

## Strings

We cannot perform mathematical operations on strings, even if they look like numbers. For example `"stringa"-"stringb"`, `"100"/"20"` and `"4"*"2"` are not valid expressions. However, there are two exceptions: `+` and `*`.

The `+` operator allows us to join strings together. This is known as **string concatenation**. For example, `"Hello " + "World"` would give us `"Hello World"` (note that there is a space at the end of the first string... if it were just `"Hello"+"World"`, we would get `"HelloWorld"`)

The `*` operator allows us to repeat a string "multiplied" by an integer. For example, `"example"*3` would produce `"exampleexampleexample"`. We can treat `"example"*3` as `"example"+"example"+"example"`, but with less to type out, which will be a recurring theme in computer science. Usually, the less to type, the less code there is to contain a mistake!

# Boolean Expressions

A Boolean expression resolved to either true or false. In Python, this is an object of type `bool`, and the value is either `True` or `False`. For example. `5 == 5` returns `True`, but `5 == 6` returns `False`.

As we might guess, the `==` is an operator that determines whether or not two values are equal to one another, and results in a boolean value.

The `==` operator is a relational operator, which operates on arbitrary values and produce bool objects. Other relational operators include:

- `==` ("is equal to") compares two operands and produces `True` if they are equal, and `False` otherwise.
- `!=` ("is not equal to") compares two operands and produces `True` if they are not equal, and `False` otherwise.
- `>` ("is greater than") compares two operands and produces `True` if the first is greater than the second, and `False` otherwise.
- `<` ("is less than") compares two operands and produces `True` if the first is less than the second, and `False` otherwise.
- `>=` ("is greater than or equal to") compares two operands and produces `True` if the first is greater than or equal to the second, and `False` otherwise.
- `<=` ("is less than or equal to") compares two operands and produces `True` if the first is less than or equal to the second, and `False` otherwise.

There are also three operators that only operate on Boolean values:

- `and` produces `True` if both of its operands are `True`, and produces `False` otherwise (for example, `True and True` produces `True`; but `False and True` produces `False`).
- `or` produces `True` if at least one of its operands is `True`, and produces `False` otherwise (for example, `True or True` produces `True`; and `True or False` also produces `True`; but `False or False` produces `False`).
- `not` is a unary operator (it has only one operand) that produces `True` if its operand is `False`, and `False` if its operand is `True` (for example, `not False` produces `True`; and `not True` produces `False`.

Sounds pretty straightforward right? When will we ever need to know if `False or False` is `False`? That doesn't sound like it's very useful... However, in future chapters, we will see that there are more complex expressions that reduce to `True` and `False`, and the computer will rely on those expressions to decide how to proceed!

# Variables and Assignment

Up to now, we've only really looked at expressions. However, sometimes it's useful to **assign** a name to a value. We do this using **variables**.

Let's use an example:

```
x = 2 + 2
```

Here, we are assigning the result of `2+2` to the value `x`. So, if we ask the console what `x` is, we see that the result is `4`.

Let's try to explain this with some algebra. Ok so if we say `x = 2+2`, then we are basically setting the variable `x` as `4`. Now, if we type in `x+5`, we replace the name with the value, and this is the same as `4+5`, which returns `9`. We can even use another assignment operator with a different variable, `y = x+5`, and now, we have a variable `x` that equals `5` and a variable `y` that equals `9`.

Note, the `=` and `==` might seem similar, but the former is an operator that assigns a value to a variable, and the latter is an operator that checks whether two values are equal.

# Variable Names

In our example above, we could have replace `x` with some other name, such as `a` or `number` or `elephant`. Usually, we want to choose variable names that are somewhat descriptive, but short enough to type.

For example, can anyone tell me what this code is trying to do:

```
a = 6.28318
b = 2

c = a * b
d = 1 / 2 * a * b ** 2

e = 4 * d
f = 2 / 3 * a * b ** 3
```

In contrast, let's use some more descriptive variable names:

```
tau = 6.28318
radius = 2

circle_circumference = tau * radius
circle_area = 1 / 2 * tau * radius ** 2

sphere_surface_area = 4 * circle_area
sphere_volume = 2 / 3 * tau * radius ** 3
```

That makes the code a lot easier to understand right? It is possible to go a little too far, and then the variables are just annoying to type out:

```
the_ratio_between_the_circumference_and_the_radius_of_a_circle = 6.28318
the_radius_of_the_shapes_for_which_we_want_to_compute_values = 2
```

## Rules for variable names:

- Variable names must begin with an alphabetical character or the underscore character
- Variable names cannot begin with a number
- Variable names must be comprised of alphanumeric characters and underscores (`A-Z`, `a-z`, `0-9`, and `_`). This means no special characters such as `*`, `!`, and so on!
- Variable names are case-sensitive. This means that `wtp`, `WTP`, and `Wtp` are all different variables

## Examples of variable names:

```
# valid variable names
my_wtp_variable = "hello"
mywtpvariable = "hello"
myWtpVariable = "hello"
_my_wtp_variable = "hello"
WTPVAR = "hello"
wtpvar12345 = "hello"

# non-valid variable names
123var = "hello"
wtp-variable = "hello"
my wtp variable = "hello"
```

# Comments

We can add comments to our code to help ourselves/others understand the code better. These do not do anything functional to our code, but they allow us to, well, add comments! In Python, comments are denoted by a `#` symbol. For example, we can write this:

```
x = 2 + 2  # sets x to 4
```

The comment is just for the reader to know that that line is setting `x` to `4`, but the actual function of the code does not change.