
# Practice Problems Solutions

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

1. What is the value of `a`? `function`
2. What is the value of `a(6)`? `7`
3. What is the value of `a("7")`? Error
4. What is the value of `b(5)`? `6.0`
5. What is the value of `b(a(1))`? `3.0`
6. What is the value of `c(1, 2)`?  `False`
7. What is the value of `c(a(5), b(-2))`? `True`
8. What is the value of `d(1, 2, 3)`? `False`
9. What is the value of `d(2, 1, 3)`? `True`
10. What is the value of `d(2, a(1), b(3))`? `True`
11. What is the value of `e(1, 2)`? `None`

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

12. What is the value of `foo('foo')`? `'fooa'`
13. What is the value of `bar('foo')`? `'fooa'`
14. What is the value of `biz('foo')`? `'foob'`

## Practice writing functions
15. Write a function `get_circumference(r)` that takes in a radius and returns the circumference, and another function `get_area(r)` that returns the area of a circle. Now use a loop and find these values `for i in range(10)`!

```
pi = 3.14
def get_circumference(r):
    return 2 * pi * r
def get_area(r):
    return pi * r ** 2

for i in range(10):
    circumference = get_circumference(i)
    area = get_area(i)

    print(i, circumference, area) # you can print whatever, or you dont even need to (the above is the important part)
```

16. Write a function `num_comp(x, y)` that takes in two numbers and returns the smaller of the two numbers.

```
def num_comp(x, y):
    if x < y:
        return x
    else:
        return y
```

17. Write a function `string_comp(x, y)` that takes in two strings and returns `True` if the strings share characters, and False if not. For example, `string_comp("abc", "a")` should return `True`, `string_comp("abc", "xyza")` should return `True`, but `string_comp("abc", "lmnop")` should return `False`.

There are many ways to do this! Here is one of the ways. It doesn't matter if you did something else, as long as yours also works!!

```
def string_comp(x, y):  
    # create a set containing letters in x
    x_set = set()
    for letter in x:
        x_set.add(letter)

    # now we'll go through y and ask if the letters are in x_set
    for letter in y:
        if letter in x_set:
            return True

    # if we get here, then we haven't returned a value, which means no letter in y was in x 
    return False
```
