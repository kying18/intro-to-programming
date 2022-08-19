# Practice problems for class 1

## For each of the following, determine what the type of the value is
```
# 1
True    # boolean

# 2
2.99    # float

# 3
None    # NoneType

# 4
3       # int

# 5
3.      # float

# 6
0       # int
```

## What about these combinations?

```
# 7
3. + 1      # float

# 8
25 - 16.    # float

# 9
-5 - 15     # int

# 10
32 > 335    # boolean

# 11
94.2 == 35  # boolean

# 12
4 == 4.     # boolean

# 13
34 / 322    # float

# 14
322 % 34    # int
```

## Entangling strings and numbers

15. What would `7+8` produce?

`15`

16. What about `7.+8`? How is this result different from the one above?

`15.0`. This is a float, the result above was an int.

17. What would happen if we tried `7+"8"`?

Error because we are adding an integer and a string

18. What about `"7"+"8"`?

`"78"` because adding two strings just combines them together


## Converting Between Types

What is the type (ex: integer, float, string, etc) and value (ex: 0, 3.14, "a", etc) of the result? Or is there an error?

```
# 19
int(7.8)  # 7

# 20
float(6)  # 6.0

# 21
str(6.0)  # "6.0"

# 22
int("2")  # 2

# 23
float("7.8")  # 7.8

# 24
int("tomato")  # error

# 25
int("7.8")  # error

# 26
float("6")  # 6.0

```

## Operators Practice

```
# 27
5 + 3 - 16      # -8

# 28
25 // 4         # 6

# 29
8+4*2           # 16

# 30
(8+4)*2         # 24

# 31
3 ** 5          # 243

# 32
3.0 ** 5        # 243.0

# 33
3/2             # 1.5

# 34
16.3 % 16       # 0.3

# 35
True or False       # True

# 36
True and False      # False

# 37
3 > 4 or 3 == 3     # True

# 38
not False           # True

# 39
not (4 > 3 and 100 > 6)     # False

# 40
4 == 2 + 2          # True
```

## Concept question

41. What if we make `x = 1` and then executed `x = x+5`? Do you think this is allowed? If so, what would `x` be equal to?

Yes, it's allowed. `x` is now `6`.

42. What is `new_amount` equal to after executing this piece of code?

```
amount = 3
amount - 5.3
new_amount = amount + 8.8
```

`new_amount` is equal to 11.8 because the second line (`amount - 5.3`) did not actually set the variable `amount` to anything.

43. Write some code to set `pi` equal to `3.14`, `r` equal to `10`, and `area` equal to `pi` times `r` squared.

```
pi = 3.14
r = 10
area = pi * r ** 2
```