# Practice Questions Answers

# Conditional Example

```
a = 7
c = 9
a = 4
if a > 6:
    b = 9
else:
    b = 10

if a > 7:
    d = 3
if a > 3:
    d = 2
else:
    d = 1
```

1. What are the values of `a`, `b`, `c`, and `d`?

```
a = 4
b = 10
c = 9
d = 2
```

## Spot the Difference

Here are three different pieces of code:

```
# Code A

x = int(input("Enter a number: "))

if x > 0:
    print("x is positive")
else:
    if x < 0:
        print("x is negative")
    else:
        print("x is zero")
```

```
# Code B

x = int(input("Enter a number: "))

if x > 0:
    print("x is positive")
elif x < 0:
    print("x is negative")
else:
    print("x is zero")
```

```
# Code C 

x = int(input("Enter a number: "))

if x > 0:
    print("x is positive")
if x < 0:
    print("x is negative")
else:
    print("x is zero")
```

2. What if you enter 10 as `x`? What is the output for code A, B, C?

A output: `x is positive`

B output: `x is positive`

C output:
```
x is positive
x is zero
```

In C, there is an if statement, followed by an if-else statement! The if-else statement has no "information" on the first statement, so it's asking "is `x<0`?", which `x` is not, so it executes the code under the `else`.

3. What if you enter 0 as `x`? What is the output for code A, B, C?

A output: `x is zero`

B output: `x is zero`

C output: `x is zero` (the first conditional is not true, unlike the previous question)

4. What is the difference between A and B?
A and B functionally do the same thing. However, the `if-elif-else` structure in B just makes the code more readible to the person who's looking at it!
5. What is the difference between A and C?

A is checking if `x>0`, and if it is, it prints `"x is positive"`, and if not, it checks if `x<0`. If `x<0`, then it prints `"x is negative"`, and if not, it prints `"x is zero"`.

On the other hand, C is checking if `x>0`, and if it is, it prints `"x is positive"`, and if not, we continue to the next if-else statement. If `x<0`, then we print `"x is negative"`, and if not (in other words, if `x>=0`), then we print `"x is zero"`.

6. What is the difference between B and C?

Same answer as above.

7. Between A and B, which piece of code is more readible?

A!

# Write Some Code!

8. Suppose we want a piece of code that allows you to take in some user-input number (use this: `x = int(input("Enter a number: "))`) and output whether the code is even, odd, or zero. Implement this.

```
x = int(input("Enter a number: "))

if x == 0:
    print("x is zero")
elif x % 2 == 0:
    print("x is even")
else:
    print("x is odd")
```


9. Suppose we are given three numbers `x`, `y`, and `z` and assume that the three values will never be equal (in other words, `x != y`, `y != z`, `x != z`). Write a piece of code that will print the largest of the three numbers (for ex: if `x=1`, `y=10`, and `z=-2.3`, the code should print `10`).

```
x = int(input("Enter a number: "))
y = int(input("Enter a number: "))
z = int(input("Enter a number: "))

# check if x is greatest
if x > y and x > z:
    print(x)
elif y > z: # we know x is less than y or z if we get here, so we can just check y and z (but you're allowed to be more specific too)
    print(y)
else:
    print(z)
```