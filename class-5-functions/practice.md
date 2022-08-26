
# Practice Problems

## Here are some function definitions:

```
def a(x):
    return x+1

def b(x):
    return x + 1.0

def c(x,y):
    return x > y

def d(x,y,z):
    return x >= y and x<=z

def e(x,y):
    x + y - 2
```

1. What is the value of `a`?
2. What is the value of `a(6)`?
3. What is the value of `a("7")`?
4. What is the value of `b(5)`?
5. What is the value of `b(a(1))`?
6. What is the value of `c(1, 2)`?
7. What is the value of `c(a(5), b(-2))`?
8. What is the value of `d(1, 2, 3)`?
9. What is the value of `d(2, 1, 3)`?
10. What is the value of `d(2, a(1), b(3))`?
11. What is the value of `e(1, 2)`?

## Functions as objects

We did not learn about functions as objects, or lambda functions, in class. Here is an example:

If I have:
```
def a(x):
    return x + 1
```

then I make `b = a`. Now, I can call `b(1)` and it would give me `2`, and `b(3)` would give me `4`, etc.

Now for lambda functions, it's just a fancy keyword for creating a function without a name. If I have:
```
y = lambda x: x + 2
```

Then `lambda x: x + 2` is saying: "create a function that takes in variable `x` and returns `x+2`". Now, I've set `y` equal to this function, so this is the equivalent of doing:
```
def y(x):
    return x+2
```

Now do the following problems:

```
def foo(x):
   return x + 'a'
bar = foo
biz = lambda x: x + 'b'
```


## Practice writing functions
15. Write a function `get_circumference(r)` that takes in a radius and returns the circumference, and another function `get_area(r)` that returns the area of a circle. Now use a loop and find these values `for i in range(10)`!
16. Write a function `num_comp(x, y)` that takes in two numbers and returns the smaller of the two numbers.
17. Write a function `string_comp(x, y)` that takes in two strings and returns `True` if the strings share characters, and False if not. For example, `string_comp("abc", "a")` should return `True`, `string_comp("abc", "xyza")` should return `True`, but `string_comp("abc", "lmnop")` should return `False`.