# Practice Questions Solutions

1. What is the value that is printed?

```
u = 3
v = 9
w = 1
for w in [2, 4, -1]:
    v = v - u*w

print([u, v, w])
```

`[3, -6, -1]` will get printed

2. What is the value that is printed?

```
r = 1
s = 6
t = 2
k = [None, False]
l = [True, r, 'twenty-five', k, 1]

while r < s:
    r = r * t
    l[r] = s
    s = s - t

print([r, s, t, k, l])
```

`[4, 2, 2, [None, False], [True, 1, 6, [None, False], 4]]` will get printed

3. What is the value that is printed?

```
a = 1
c = 'crumb'
x = 7

for x in [0, 2, 1]:
    a = a + x
    for y in 'r':
        c = c[a] * x + c
    c = c + y

print([a, c, x])
```

`[4, 'ummcrumbrrr', 1]` will get printed

## Finding the youngest person's name

4. Suppose we have a list of names and a list of corresponding ages. We want to find the name of the youngest person. How would be do this?

We can loop through the indices of the lists and ask if the age is younger than the youngest age recorded so far, and if it is, we look up the name at that index in our names list!


**Answer** 

```
ages = [15, 18, 17, 20, 16, 14, 18]
names = ["Ana", "Sarah", "Jessica", "Izzy", "Grace", "Madison", "Skyler"]

# we initialize our variables, which means we declare them to be some initial value
youngest_age = float('inf')
youngest_name = ""

# we loop through each index in the 'ages' list
for i in range(len(ages)):
    # if the age is younger than the youngest one we've seen, then we replace the
    # youngest's name with the current name and the youngest age with the current age
    if ages[i] < youngest_age:
        youngest_name = names[i]
        youngest_age = ages[i]

print(youngest_name)
```

## Approximating Square Roots

5. Another use case of loops is Newton's method. Newton's method allows us to approximate square roots. If we want to figure out the square root of `a` and we have some estimate `x`, we can compute better estimates using the formula: `y = (x + a/x)/2`.

Suppose we want the square root of 4 and we allow our approximation to be 3. We know that the answer should be 2. In this case, we let `a=4` and `x=3`:

```
a = 4
x = 3
y = (x + a/x) / 2
print(y)  # prints 2.16666666667
```

This is closer to the correct answer (2)! Let's try this again:

```
x = y
y = (x + a/x) / 2
print(y)  # prints 2.00641025641
```

Even better! Let's keep going.

```
x = y
y = (x + a/x) / 2
print(y)  # prints 2.00001024003

x = y
y = (x + a/x) / 2
print(y)  # prints 2.00000000003

x = y
y = (x + a/x) / 2
print(y)  # prints 2.0

x = y
y = (x + a/x) / 2
print(y)  # prints 2.0
```

Eventually, we get to the right answer! Instead of typing (or copy/pasting) a million times, we can instead use a loop to make the computer do this work for us. Try to write a loop.

**Answer**

```
a = 4
x = None
y = 3
while x != y:
    x = y
    print(x)
    y = (x + a/x) / 2
```

While in our case, checking for equality between `x` and `y` is okay, it's dangerous to test `float` equality because floats can't accurately represent all numbers! Instead, it's good practice to stop when `x` and `y` are small enough:

```
a = 4
x = None
y = 3
while abs(x-y) < 1e-12:
    x = y
    print(x)
    y = (x + a/x) / 2
```

Woah. How's that for a taste of how computer science works?