# Lecture 3: Conditionals

# Sources

These notes were adapted or copied verbatim from from [Adam Hartz](https://hz.mit.edu/)'s MIT [6.145 readings](https://hz.mit.edu/catsoop/6.145/), as well as [Think Python 2e](https://greenteapress.com/wp/think-python-2e/) by [Allen Downey](http://www.allendowney.com/wp/).

# Conditional Statements

So far, all of our programs have continued in a relatively straightforward manner: Python executed all of the statements in a program in exactly the order they were specified.

![straightforward flow](../images/flow_1.png)

However, when we program more complex functionality, we might need to check a certain condition and change behavior of the program according to the result of that condition. **Conditional statements** give us this ability.

## `if` Statements

In order to write useful programs, however, we almost always need the ability to check conditions and change the behavior of the program accordingly. _Conditional statements_ give us this ability. The simplest form is the `if` statement:

```
# Absolute value
if x < 0:
    x = -x
```

The boolean expression after `if` is called the **condition**. If it is true (i.e., if it evaluates to `True`), the indented statement (the body) runs. If not, nothing happens.

![conditional flow](../images/flow_conditional.png)

We may have multiple statements in the body of the conditional statement. Any statements that have the indentation at the same level are part of the body, and all of them get executed if the conditional is true.

```
# This example also introduces a new concept: we can display a sequence of
# characters to the screen verbatim by surrounding them in quotes.

print("This will always print")
if x < 0:
    print("x is negative")
    print("so we'll print")
    print("a few extra things")
print("This will always print, too")
print("And so will this!")
```

In this case, if `x` is less than `0`, Python will execute all three indented lines; otherwise, it will skip all of them. Notice that only the execution of the indented lines is affected by the condition; the bottom two lines are not part of the conditional; they are always executed

There is no limit on the number of statements that can appear in the body, but there has to be at least one. Occasionally, it is useful to have a body with no statements (usually as a place keeper for code you haven't written yet). In that case, you can use the `pass` statement, which does nothing.

```
if x < 0:
    pass  # do nothing
```

## `if`-`else` Statements

A second form of the `if` statement makes Python run one of multiple possible alternative pieces of code. In this structure, there are two possibilities and the condition determines which one runs:

![Alternative flow](../images/flow_alternative.png)

The syntax looks like this:

```
if x % 2 == 0:
    print("x is even")

else:
    print("x is odd")
```

Basically, if the remainder of `x` divided `2` is `0`, then `x` is even, and we print the statement `"x is even"`. Otherwise, we know that `x` is odd, and we run the block under the `else:` branch, which prints the alternative statement `"x is odd"`.

The alternatives are called **branches**, because they are branches in the flow of execution.

## Chained Conditionals

Sometimes, it's not enough to simply have one statement and an alternative. Sometimes, we want to have multiple branches. Here, we can use a **chained conditional**:

```
if x < y:
    print('x is less than y')
elif x > y:
    print('x is greater than y')
else:
    print('x and y are equal')
```

`elif` is an abbreviation of "else if". Again, exactly one branch will run. There is no limit on the number of `elif` statements. If there is an `else` clause, it has to be at the end, but there doesn't have to be one.

Each condition is checked in order. If the first is false, the next is checked, and so on. If one of them is true, the corresponding branch runs and the statement ends. Even if more than one condition is true, only the first true branch runs.

## Nested Conditionals

The branches of a conditional can contain any valid Python code. This means that a conditional could contain another conditional!

![Complicated flow](../images/flow_complicated.png)

Previously, when we compared `x` and `y`, we could have written code like this:

```
if x == y:
    print("x and y are equal")
else:
    if x < y:
        print("x is less than y")
    else:
        print("x is greater than y")
```

Here, the outer conditional has two branches. The first branch is a simple statement, but the second branch contains another conditional that has two branches of its own. While it's possible to have nested conditionals, it's a good idea to avoid them when you can, because it's difficult to read sometimes!

Also, note that we can use logical operators that reduce to a boolean. For example:

```
if 0 < x:
    if x < 10:
        print("x is a positive single-digit number.")
```

can be simplified if we replace it with:

```
if 0 < x and x < 10:
    print("x is a positive single-digit number.")
```
