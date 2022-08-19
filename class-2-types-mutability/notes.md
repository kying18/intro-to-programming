# Lecture 2: More Types and Mutability

# Sources

These notes were adapted or copied verbatim from from [Adam Hartz](https://hz.mit.edu/)'s MIT [6.145 readings](https://hz.mit.edu/catsoop/6.145/), as well as [Think Python 2e](https://greenteapress.com/wp/think-python-2e/) by [Allen Downey](http://www.allendowney.com/wp/).

# Sequences

Strings are actually sequences of characters. In Python, some may consider strings a primitive, and some may consider it of **compound** type (since it is comprised of characters). We can do many interesting operations in Python with sequences, but we'll start with strings, and then generalize.

## Indexing

In Python, we can extract a single character from a string (or more generally, a single value from a sequence) using square brackets. For example:

```
sequence = "this string"
character = sequence[1]
print(character)
```

Here, the `[1]` means we are selecting the character at position 1 from `sequence` and assigning it to the variable `character`. The `1` is called an **index**. The index must be an integer and it tells the program which value in the sequence we want.

In Python, we use `0-indexing`, which means that our sequences start at index `0`, rather than `1`. In the example above, we actually print out `h` and not `t`, which is what many people just starting to code might expect!

In our example above, any integer between 0 and 10 is a valid index. Any integer between -1 and -11 is also a valid index. This is how we can index from the end of a sequence! In the example above, `sequence[-1]` would give us `g`, `sequence[-2]` would give us `n`, and so on.

## Iteration

Sequences are also **iterable**, which means that we are allowed to iterate over them! In the context of strings, we would likely start the beginning, select each character turn after turn, do something with it, and then continue until the string ends. This is referred to as **looping**. In Python, we can have a `for` loop that, for example, can print each character in a string:

```
word = "cat"
for letter in word:
    print(letter)
print('done')
```

Basically, for each letter in the word, we print out that letter, and then after we iterate through the entire string, we print `done`.

We will come back to looping later. Let's cover more complex Python data types!

## Tuples

**Tuples** are sequences that can contain arbitrary objects (integers, floats, Booleans, None, or even other tuples!).

Tuples are specified as a comma-separated sequence of arbitrary objects, usually wrapped in parentheses. For example, the following is a tuple containing three different objects: `x = (7, -7.8, "blue")`.

We can perform many of the same operations on tuples that we could on strings. For example:

- we can index into a tuple (`x[1]` gives us `-7.8`)
- we can use + to concatenate two tuples (`x + (1, 2, 3)` gives us `(7, -7.8, "blue", 1, 2, 3)`)
- we can compare two tuples using `==`
- we can loop over the elements in a tuple

## Lists

**Lists** are one of the most useful Python types. It is also a sequence that can contain arbitrary objects (integers, floats, Booleans, None, lists/tuples), just like the tuple, but there is one big difference:

Lists are **mutable**!

This means that they can be changed _after_ they are created! However, strings and tuples cannot be. If we wanted to replace the 3rd item in a string or a tuple, we would need to create another tuple where the 3rd item is different. However, in a list, we can go in and edit the 3rd item without creating another one!

Tuples use round parentheses, while lists use square brackets. Here are some examples of lists:

```
cheeses = ['Cheddar', 'Edam', 'Gouda']
numbers = [42, 123]
another_list = [7, 12, 10]
empty = []  # we can also make a list that contains no elements!
```

### Mutability

What exactly do we mean when we say that lists are _mutable_, but tuples aren't?

We can _modify_ lists, such as replacing an item or adding/removing items from the list, but these methods will throw an error if we try to apply them to tuples. For example:

```
my_tuple = (1, 2, 3)
my_list = [1, 2, 3]

# modifying an element
my_tuple[0] = 5  # this will give us a TypeError
my_list[0] = 5
print(my_list)  # [5, 2, 3]

# appending elements
my_tuple.append(4)  # error
my_list.append(4)
print(my_list)  # [5, 2, 3, 4]

# we can append other things too
my_list.append("sky")  # [5, 2, 3, 4, "sky"]
my_list.append(my_tuple)  # [5, 2, 3, 4, "sky", (1, 2, 3)]

# pop removes, extend adds another list to the end
my_list.pop()  # [5, 2, 3, 4, "sky"]
my_list.extend([1, 2, 3])  # [5, 2, 3, 4, "sky", 1, 2, 3]
```

## Dictionaries

**Dictionaries** are also great. They provide a **mapping** between keys and values. Think about the English to French dictionary. Each English word gets mapped to its French counterpart, and in order to find the French word, we look up the English word. In Python, in some ways, the English word is the "key" and the corresponding French word (what the English word maps to) is the value.

These mappings are known as **key-value pairs**, and sometimes refered to as **items**.

Let's look at some examples to see how dictionaries work.

```
eng_to_fr = {}  # this is an empty dictionary
eng_to_fr["hello"] = "bonjour"  # this inserts a new key-value pair into the dictionary
print(eng_to_french)  # {"hello": "bonjour"}

# we can retreive the french word by looking up the english word
print(eng_to_french["hello"])  # "bonjour"

# note that we can also create a new dictionary like this:
eng_to_fr = {"hello": "bonjour", "goodbye": "au revoir"}

# note that it only works if we look up the keys
# if we look up the value, we get an error! (unless the value is equal to another key)
print(eng_to_french["goodbye"])  # "au revoir"
print(eng_to_french["bonjour"])  # error
```

Keys in the dictionary must be unique, meaning we cannot set `"hello"` to both `"bonjour"` and `"salut"`. Instead, the key will be overriden by the latest value:

```
print(eng_to_fr)  # {"hello": "bonjour", "goodbye": "au revoir"}
eng_to_fr["hello"] = "salut"
print(eng_to_fr["hello"])  # salut
```

Dictionaries can have arbitrary objects as values and arbitrary _immutable_ objects as keys. (Can you think of a reason why that might be?) Basically, anything can be a value, but lists and dictionaries (generally speaking) cannot be keys.

Let's see what happens if we use a list vs a tuple:

```
x = [1, 2, 3]
y = (1, 2, 3)
dictionary = {}

dictionary[x] = 2  # TypeError: unhashable type: 'list'
dictionary[y] = 2
print(dictionary)  # {(1, 2, 3): 2}
```

Note that dictionaries do not have any ordering. `dictionary[0]` will return an error unless `0` is a key in the dictionary.

## Sets

Finally, the last built-in object type we will talk about is a **set**. Sets are like lists, but they do not have any ordering and they do not contain any repeated values. Similar to dictionaries, they are denoted with curly brackets, but do not have any key-value pairs.

Let's look at an example:

```
my_set = set()  # usually, I use this to define a set, because my_set = {} would be a dictionary!
my_set.add(1)
my_set.add(2)
print(my_set)  # {1, 2}

# what happens if we add another 1 to the set?
my_set.add(1)
print(my_set)  # {1, 2}
```

Remember that sets cannot have repeated values! If we try to add a value already in the set, there is no error, but the values in the set do not change.

# Compound Object Operators

There are a few operators that we can use for sequences:

- length: we can call `len(obj)`, where `obj` is a tuple, list, dictionary, or set, and this will return the number of items in the object

```
print(len([1, 2, 3, 4]))  # returns 4
```

- presence of item: we can use the `in` operator to see if a value is in a tuple, list, set, or dictionary (as a _key_)

```
print('a' in [1, 2, 3])  # False
print('a' in [1, 'a', 3])  # True
```

- lack of presence: similarly to `in`, we can use the `not in` operator to see if a value is not in a tuple, list, set, or dictionary's keys

```
print('a' not in [1, 2, 3])  # True
print('a' not in [1, 'a', 3])  # False
```

# When To Use What??

When should we use what? It seems like all these built-in types are somewhat similar. The logic is not as straightforward as numbers vs strings vs booleans. Can you think of some use cases for each?

From my experience, here's some examples of use cases:

- Tuples: when I want to store values that are tied together, such as x-y coordinates or playing card representations (ex: `(3, 'spades')`)
- Lists: when I want a list of things. For example, if I am trying to implement poker, I might store a deck of playing cards as a list of tuples (ex: `[(2, 'spades'), (2, 'diamonds'), (3, 'spades'), ...]`)
- Dictionaries: when I want to associate something with a label or create any type of mapping. Also good for creating counters. For example, if I am counting occurrence of words in a sentence (`{'the': 5, 'and': 2, 'seashore': 1, 'dolphin': 1, etc.}`) or mapping stock tickers to company names (`{'TSLA': 'Tesla', 'AAPL': 'Apple', 'GOOGL': 'Alphabet', 'FB': 'Meta', etc.}`)
- Sets: when I want to keep track of values I've already encountered, or when I want to see how many unique values are in something

# More About Strings

There are a few more string operations that we can use:

We can split a string by the whitespace (any number of spaces together, including tabs).

```
"hello i like pi".split() # ["hello", "i", "like", "pi]
```

We can also capitalize and lowercase characters:

```
'a'.upper() # A
'abc'.upper() # ABC
'HELLO'.lower() # hello
```
