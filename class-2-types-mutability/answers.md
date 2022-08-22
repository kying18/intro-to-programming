# Practice Questions

## Here's an array
```
x = [1.1, 2, [3, 'tomato', 4], 'cat']
```

1. What type is `x`? list
2. What type is `x[0]`? float
3. What type is `x[2]`? list
4. What type is `x[-1]`? string
5. What is the value of `x[2][2]`? 4
6. What is the value of `x[2][-1]`? 4
7. What is the value of `x[-1][2]`? 't'
8. What is the value of `x[4]`? Python will give an error
9. Let's say I run this line: `x[1] = 'hi'`. Now what is `x[1]`? `'hi'`
10. What is the value of `x` now? `[1.1, 'hi', [3, 'tomato', 4], 'cat']`
11. Let's say you want to add you name to the end of `x`. What is the command you need to do this? `x.append("kylie")`

## Here's a tuple
```
tup = (1, 2, "c")
```

12. What type is `tup`? tuple
13. What happens if I run `tup[0] = "a"`? Python will give you an error
14. Let's say you want to add you name to the end of `tup`. Can you do this?
This is a trick question. You cannot append to the tuple like we did above for the string. Python will give you an error if you try to do that. However, one way we can get around this is to create a *NEW* tuple with your name, and then set `tup` equal to that new variable: `tup = (1, 2, "c", "kylie")` or `tup = tup + ("kylie",)` (`("kylie",)` is a tuple with only 1 value in it).

## Additional questions
15. What is the value of `[1, 2]+[3,4]*2`? `[1, 2, 3, 4, 3, 4]`
16. What is the value of `['b'] + ['a' + 'n']*2 + ['a']`? `['b', 'an', 'an', 'a']`
17. What is the value of `"na"*8 + " batman"`? `'nananananananana batman'`

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

18. What does `name[3:]` give you? `a`
19. What does `hello[1:5]` give you? `ello`
20. What does `hello[0:8:2]` give you? `HloW`
21. What does `name[0:-2]` give you? `Li`
22. What does `hello[-3:]` give you? `rld`
23. We want to write `"Hello Lia"` using these strings above. How do I do that? `hello[:6] + name[:2] + name[-1]` is one way to do it.

## Use a dictionary for this exercise below!
24. Let's pretend we're about to go on vacation to Spain. BUT, we don't know Spanish! Let's use our computer to translate for us. Write a short script that will let you input a number in English (zero-nine), and it should output the Spanish translation.

For your convenience, here are the spanish numbers from 0 to 9: cero uno dos tres cuatro cinco seis siete ocho nueve

Also, to receive user input and store it as a value, you should use the `input` command: `x = input("Type something here: ")`. Whatever you type becomes a *string* and the variable `x` is set to that value!

```
dictionary = {
    "zero": "cero",
    "one": "uno",
    "two": "dos",
    "three": "tres",
    "four": "cuatro",
    "five": "cinco",
    "six": "seis",
    "seven": "siete",
    "eight": "ocho",
    "nine": "nueve"
}

word = input("Please input a number zero-nine: ")
translation = dictionary[word]
print("The translated letter is", translation)
```