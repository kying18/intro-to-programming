# Lecture 5: Functions

# Sources

These notes were adapted or copied verbatim from from [Adam Hartz](https://hz.mit.edu/)'s MIT [6.145 readings](https://hz.mit.edu/catsoop/6.145/), as well as [Think Python 2e](https://greenteapress.com/wp/think-python-2e/) by [Allen Downey](http://www.allendowney.com/wp/).

# Functions

The tools we've introduced in the past few lessons are already incredibly powerful. We have seen a few small examples of how we can apply it to problems that need to be solved. One even more powerful tool that will help us accomplish even more is a **function**.

Suppose we have the following piece of code to evaluate a polynomial. Here, the polynomial is represented by the coefficients, so `[7, 9, 2, 3]` would represent `7x**0+9x**1+2x**2+3x**3`, which is the same as `7+9x+2x**2+3x**3`. If we want to compute this at `x=4.2`, then our code would look something like this:

```
coeffs = [7, 9, 2, 3]
x = 4.2

result = 0
for index in range(len(coeffs)):
   result = result + coeffs[index] * x ** index
print(result)
```

Ok what if we wanted to compute it at `x = 4.2` and `x=1.5`? We could easily change what `x` is, but we would also have to rerun the lines that evaluate the polynomial. Same for if we wanted to change the coefficients. This is kind of annoying. Plus, what if we end up finding a bug in the copied code? We would have to go back and fix it in every single copy that we made! Annoying!!!

Wouldn't it be nice if we could write the code once, wrap it up, and simply use that every single time? Turns out we can. This is a **function**.

You have already seen certain functions, such as the `print`, `len`, and even `range` functions! We can evaluate the following expression: `len("dog")`. In this example, the name of the function is `len`. The parentheses indicate what we want to "call" the function (in other words, use the chunk of code that is inside the function). The value inside the parentheses is called an **argument**. The function then returns an integer representing the length of the argument!

What you might notice is that we can change the argument and the function will do something using the argument that we provide. Let's go back to our polynomial code and take a look at how we can wrap it into a function. This is called a **function definition**. `def` is the keyword to define your own function! The variables that get passed into the function are called **parameters** (not to be confused with the **arguments**, which are the values that we pass in).

```
coeffs = [7, 9, 2, 3]
x = 4.2

def eval_polynomial(coeffs, x):
    result = 0
    for index in range(len(coeffs)):
        result = result + coeffs[index] * x ** index
    print(result)
```

Note that a function definition only _DEFINES_ the function. It does not actually run any of the code in the body! It just lets our computer know that any time we call `eval_polynomial` (or whatever your function name is), we should run the code inside the function. Now, if we run:

```
eval_polynomial(coeffs, x)
```

Cool, we get our answer! If we set `y = len("dog")` and try `print(y)`, we see `3` as our answer. Can we set `y` equal to the output of this? Let's try:

```
y = eval_polynomial(coeffs, x)
print(y)
```

Oh no! Why are we printing `None`?

This is where the difference between `print` and `return` comes in. Our function is not actually returning a value because did not use the `return` keyword! Usually, this is confusing for first-time programmers, so let's discuss in detail.

## `return`

`return` is a keyword that literally tells our function to return a value to where it was called! Otherwise, our function is lazy and assumes it does not need to return anything. Instead of printing the result, let's define our function like this:

```
def eval_polynomial(coeffs, x):
    result = 0
    for index in range(len(coeffs)):
        result = result + coeffs[index] * x ** index
    return result  # notice the change here!!
```

Now, if we do this again,

```
y = eval_polynomial(coeffs, x)
print(y)
```

you'll notice that the None does not get printed out anymore... Do you know what's going on here?

In the original example, our function was printing the result, and then we were assigning the value returned by the function (`None`) to `y`, and then printing `y`. Now, our function is not printing out anything. Instead, we are returning the value of the `result` and setting `y` equal to that, then printing `y`.

# Scope

Up until now, all of our variables were defined in the same **scope**, meaning, we had access to all the variables we defined, from anywhere in the same script (after we've defined them of course)! However, with functions, this is no longer true.

For now, think of functions as a black box that take in certain arguments and then spit out a number (sometimes, as we've seen). We don't really care what happens inside the black box, as long as the function does what it's supposed to do. So, outside the function, we don't actually have access to the variables that are defined within the function. What exactly does this mean?

Suppose we have the function below, which wants to get the maximum of a list and the index where it occurs:

```
def get_max(input_list):
    maximum = -float('inf')
    max_index = None
    for i in range(len(input_list)):
        val = input_list[i]
        if val > maximum:
            maximum = val
            max_index = i

    return max_index
```

Let's try to print `maximum` and `max_index` outside the scope of the function. What do you think will happen?

```
print(maximum)
print(max_index)
```

We get an error!! This is telling us that these variables do not exist. That's because we are not in a scope were we can call them.

We say that variables that are defined within a function are **local variables**, belonging only to that function, used only in that function. However, variables that are defined in the main body of a Python script (outside of any function definitions) are known as **global variables**, and they have **global scope**. These can be called from the inside and outside of functions.

Note that the parameters of a function are also local variables. Let's take a look at this example below:

```
radius = 3
pi = 3.14

def circle_area(r):
    return pi * r ** 2

area = circle_area(radius)
print("Area", area)
print("radius", radius)
print("r", r)
```

# Alternate forms

Sometimes, functions have alternate forms that take varying number of arguments! In this class, we won't learn how to create these types of functions, but it's important to know they exist! We have actually already seen two of them:

- If `print` is given more than one argument, it will print all of its arguments on the same line, separated by spaces. If it is given no arguments (i.e., `print()`), it will simply make a blank line.

- `range` has three forms:
  - If `range` is given a single integer `x`, the object it returns contains the numbers from `0` to `x-1`, inclusive.
  - If `range` is given two integers `x` and `y`, the object it returns contains the numbers from `x` to `y-1`, inclusive.
  - If `range` is given three integers `x`, `y`, and `z`, the object it returns contains all values `x + i*z` such that `x <= x + i*z < y`, in increasing order of `i`.

Colloquially, the three arguments to range are often referred to as "start", "stop", and "step": the first is the value to start at (inclusive), the second is the value to stop at (exclusive), and the third is how many numbers to skip each time.

# Calling Functions Within Functions

We can call functions from other functions (or conditionals or loops). Let's walk through some (admittedly silly) code to understand how this (and scoping) works:

```
def f(x):
    x = x + y
    print(x)
    return x

def g(y):
    y = 17
    return f(2+x)

x = 3
y = 4
z = f(6)

a = g(y)

print(z)
print(a)
print(x)
print(y)
```

# Defining Functions Within a Function

Functions can also be defined within a function! Let's look at the example below:

```
x = 7
a = 2

def foo(x):
    def bar(y):
        return x + y + a
    z = bar(x)
    return z

print(foo(14))
print(foo(27))
```

What would happen if we tried this?

```
print(bar(5))
```

This is because of scoping again! When we define `bar` in the local scope of the `foo` function, it only exists there! We cannot access the function in the global frame.

While you may think that this is silly now, this eventually becomes a super helpful tool while building big software projects because sometimes we don't want someone to have access to all the functions!

# Functions Are Objects

We've seen how we can call functions by using parentheses. What if we did not have those? What would happen?

```
circle_area
```

The result looks something like this:

```
<function circle_area at 0x100c04550>
```

This is telling us that it's actually a function _object_ named `circle_area` located at some place in memory, `0x100c04550` (we won't worry about that last part in this class). However, this means that we can actually pass the `circle_area` function around as arguments to other function, we can return it from other functions, and assign it to variables!

Basically, if I wanted to assign a variable to the function `circle_area`, I could do so like this:

```
my_function = circle_area

# now let's try calling it
print("Output using my_function", my_function(2))
print("Output using circle_area", circle_area(2))
```

Both give the same result!

We also mentioned we could pass it into functions. Let's look at an example to see why this is useful:

```
# let's say point1 and point2 are (x, y) coordinates, represented by tuples
def dist(point1, point2):
    x1 = point1[0]
    y1 = point1[1]
    x2 = point2[0]
    y2 = point2[1]
    return ((x2 - x1) ** 2 + (y2 - y1) ** 2) ** 0.5
```

Ok great, we can get the _Euclidean distance_ between two points:

```
print(dist((-1, 5), (3, 2)))  # 5.0
```

However, let's say we're walking in the streets of NYC and we want to figure out how much we need to walk to get from `point1` to `point2`. Well, unfortunately we need to stay on the sidewalk, otherwise we might run into some buildings. The Euclidean distance is not really helpful. Instead, we should use a metric called the _Manhattan distance_ (see diagram), which represents the sum of the absolute difference between points in all dimensions.

That means we'd want our distance function to look something like this:

```
def dist(point1, point2):
    x1 = point1[0]
    y1 = point1[1]
    x2 = point2[0]
    y2 = point2[1]
    return abs(x2 - x1) + abs(y2 - y1)

print(dist((-1, 5), (3, 2)))  # 7

```

The two functions seem really similar right, only the bottom part changing a bit? We can actually instead create a single distance function and pass in the calculation definition as an argument. Let's see how that works:

```
def dist(point1, point2, dist_fxn):
    x1 = point1[0]
    y1 = point1[1]
    x2 = point2[0]
    y2 = point2[1]
    return dist_fxn(x1, y1, x2, y2)
```

Now, if we define our two distances,

```
def calc_euclidean_dist(x1, y1, x2, y2):
    return ((x2 - x1) ** 2 + (y2 - y1) ** 2) ** 0.5

def calc_manhattan_dist(x1, y1, x2, y2):
    return abs(x2 - x1) + abs(y2 - y1)
```

we can actually pass these into our original distance function during that function call!

```
distance_euc = dist((-1, 5), (3, 2), calc_euclidean_dist)  # 5.0
distance_man = dist((-1, 5), (3, 2), calc_manhattan_dist)  # 5.0

print(distance_euc)  # 5.0
print(distance_man)  # 7
```
