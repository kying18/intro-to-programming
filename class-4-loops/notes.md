# Lecture 4: Loops

# Sources

These notes were adapted or copied verbatim from from [Adam Hartz](https://hz.mit.edu/)'s MIT [6.145 readings](https://hz.mit.edu/catsoop/6.145/), as well as [Think Python 2e](https://greenteapress.com/wp/think-python-2e/) by [Allen Downey](http://www.allendowney.com/wp/).

# Loops

Previously, we saw that we could iterate through sequences using loops. **Iteration** allows us to run a block of statements repeatedly (just like [Doctor Strange when he confronts Dormammu](https://youtu.be/LrHTR22pIhw?t=148)).

There are two kinds of loops: `for` loops and `while` loops. In this lesson, we'll discuss both of them.

## `for` Loops

`for` loops allow us to iterate over a sequence. This might be looping through each character of a string, as we saw in the previous lesson:

```
for char in 'cat':
    print(char)
print('done')
```

would output:

```
c
a
t
done
```

However, we can also iterate through lists, tuples, dictionary keys (and values and items, but that requires an extra step), and even sets:

```
l = [0, 1, 2]
for val in l:
    print(val)
    print(val+1)
```

would output:

```
0
1
1
2
2
3
```

### Building Related Lists

One use case of a loop might be that we have a list and we want to build a related list somehow. For example, if we have a list of numbers, and we want to create a list of the square of all those numbers. Instead of manually calculating it and instantiating a new list, we can simply iterate through the list of numbers, calculate the square, and append it to a new list!

```
numbers = [1, 3, 5, 9, 13]
squares = []

for num in numbers:
    square = num ** 2
    squares.append(square)

print(numbers)  # [1, 3, 5, 9, 13]
print(squares)  # [1, 9, 25, 81, 169]
```

### Looping Over Integers

One common looping pattern in computer science is looping over particular integer values!

Suppose we wanted to print the squares of all integers from 0 to 24. We would write:

```
for i in [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24]:
    print(i**2)
```

but remember how our goal as computer scientists is to write as little code as possible? (Yes, we are 1) lazy, but also 2) trying to give ourselves less space to make mistakes! Imagine if you accidentally skipped a number or mistyped it above. Not a big deal here, but if you're working on software for a self-driving car, that might have catastrophic consequences!)

Instead, we can use `range`. `range` produces a special _range_ object which can help us iterate over numerical values:

```
for i in range(25):
    print(i**2)
```

This would produce the same output as above, but with less space for error. Looping over `range(x)` would allow us to loop over values from `0` to `x-1`, giving us a total of `x` elements. `range(4)` would allow us to loop over the same values as `[0, 1, 2, 3]`, and `range(7)`: `[0, 1, 2, 3, 4, 5, 6]`. Let's say we wanted to loop over 1000 values. `range` would really save us a lot of time!

### Looping Over Indices of a List

One common use case of looping over integers is to loop through the indices of a list! Instead of looping through each value in the list, we can instead use `range` to loop through the length of the list and index into the list to get the value:

```
x = [15, "blue", 23]
for i in range(len(x)):  # usually we use len(list) because it helps us avoid mistakes!
    print(x)
```

## `while` Loops

Sometimes, we want to loop through a block of code until a certain conditional statement is met (in this case, until [Dormammu could not tolerate Doctor Strange anymore](https://youtu.be/LrHTR22pIhw?t=187)). This is where `while` loops come into play.

In a `while` loop, we continue looping while some condition is `True`, and exit the loop when that condition becomes `False`. If you get confused, this is just like English (but the following example is not proper Python syntax):

```
while this statement is true:
    do these things here
```

How would this work using proper Python syntax?

```
n = 5
while n > 0:
    print(n)
    n = n - 1
print('Blastoff!')
```

You can almost read the while statement as if it were English. It means, "While `n` is greater than 0, display the value of n and then decrement `n`. When you get to 0, display the word `Blastoff!`"

Slightly more formally, here is the flow of execution for a `while` statement:

1. Determine whether the condition is true or false.
2. If false, exit the `while` statement and continue execution at the next statement.
3. If the condition is true, run the body and then go back to step 1.

Our example above would output:

```
5
4
3
2
1
Blastoff!
```

However, when we use `while` loops we have to be careful. What happens if the condition is never `False`? For example, what would happen in the following loop?

```
while True:
    print("Hello World")
```

You and your computer would go crazy like Dormammu! In this case, it's easy to tell that this will turn into an **infinite loop**. In other cases, it's not so easy to tell... For example:

```
n = 27
while n != 1:
    print(n)
    if n % 2 == 0:  # n is even
        n = n / 2
    else:  # n is odd
        n = n*3 + 1
```

`n` sometimes increases and sometimes decreases. There are certain values of starting `n`s where the program will terminate (aka, when `n == 1`), but we cannot prove that this terminates for _all_ positive values of `n`!

# Nested Loops

Just like conditionals, the body (indented part) of a loop can contain any valid Python code! This means we could have a loop in a loop. Or a loop in a loop in a loop in a loop (but we try to avoid those usually).

Let's say we have a list of integers and we want to see if we can find two values in the list that add up to some number, `target`. The most straightforward way to do that is to use a nested loop:

```
l = [-1, 4, 3, -2, 10, -3, -5, 8]
target = 7
sum_to_target = False  # initially, we don't know, so we assume False

for val1 in l:
    for val2 in l:
        if val1 + val2 == target:
            sum_to_target = True # we change to True if there is a sum == target

print(sum_to_target)
```

## `break`ing

In this above example, our goal was to simply determine whether or not there were two numbers that sum up to the target. If we discover that there is, we don't actually need to continue iterating! Suppose our list was really really long, then it would take a long time for the loops to terminate.

We can avoid this by using a `break` statement. It works like this:

```
for val1 in l:
    for val2 in l:
        if val1 + val2 == target:
            sum_to_target = True # we change to True if there is a sum == target
            break
```

The `break` is indicating to Python that after finding a sum equal to the target, we want to discontinue running our program. We've already gotten the answer we're looking for!