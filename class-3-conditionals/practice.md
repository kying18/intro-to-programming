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
3. What if you enter 0 as `x`? What is the output for code A, B, C?
4. What is the difference between A and B?
5. What is the difference between A and C?
6. What is the difference between B and C?
7. Between A and B, which piece of code is more readible?

# Write Some Code!

8. Suppose we want a piece of code that allows you to take in some user-input number (use this: `x = int(input("Enter a number: "))`) and output whether the code is even, odd, or zero. Implement this.

9. Suppose we are given three numbers `x`, `y`, and `z`. Write a piece of code that will print the largest of the three numbers (for ex: if `x=1`, `y=10`, and `z=-2.3`, the code should print `10`).