
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

## Assume we have the following function:

```
def foo(x):
   return x + 'a'
bar = foo
biz = lambda x: x + 'b'
```

12. What is the value of `foo('foo')`?
13. What is the value of `bar('foo')`?
14. What is the value of `biz('foo')`?
