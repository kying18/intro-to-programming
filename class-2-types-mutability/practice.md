# Practice Questions

## Here's an array
```
x = [1.1, 2, [3, 'tomato', 4], 'cat']
```

1. What type is `x`?
2. What type is `x[0]`?
3. What type is `x[2]`?
4. What type is `x[-1]`?
5. What is the value of `x[2][2]`?
6. What is the value of `x[2][-1]`?
7. What is the value of `x[-1][2]`?
8. What is the value of `x[4]`?
9. Let's say I run this line: `x[1] = 'hi'`. Now what is `x[1]`?
10. What is the value of `x` now?
11. Let's say you want to add you name to the end of `x`. What is the command you need to do this?

## Here's a tuple
```
tup = (1, 2, "c")
```

12. What type is `tup`?
13. What happens if I run `tup[0] = "a"`?
14. Let's say you want to add you name to the end of `tup`. Can you do this?

## Additional questions
15. What is the value of `[1, 2]+[3,4]*2`?
16. What is the value of `['b'] + ['a' + 'n']*2 + ['a']`?
17. What is the value of `"na"*8 + " batman"`?

## More slicing

In Python, we can also take "slices" of sequences (strings, tuples, lists). Let's say `sentence = "Hello World!"`. We can take sub-sequences of this word like this:

```
sentence[0:4]  # gives us the first 4 characters --> "sent"
sentence[:4]  # also gives us "sent"
sentence[6:]  # gives us the remainder of the sentence starting from index 6 ("W") --> "World!"
sentence[2:5] # gives us indices 2, 3, 4 of the string --> "llo"
```

Here are some exercises:
```
hello = "Hello World"
name = "Lisa"
```

18. What does `name[3:]` give you?
19. What does `hello[1:5]` give you?
20. What does `hello[0:8:2]` give you?
21. What does `name[0:-2]` give you?
22. What does `hello[-3:]` give you?
23. We want to write `"Hello Lisa"` using these strings above. How do I do that?

## Use a dictionary for this exercise below!
24. Let's pretend we're about to go on vacation to Spain. BUT, we don't know Spanish! Let's use our computer to translate for us. Write a short script that will let you input a number in English (zero-nine), and it should output the Spanish translation.

For your convenience, here are the spanish numbers from 0 to 9: cero uno dos tres cuatro cinco seis siete ocho nueve

Also, to receive user input and store it as a value, you should use the `input` command: `x = input("Type something here: ")`. Whatever you type becomes a *string* and the variable `x` is set to that value!