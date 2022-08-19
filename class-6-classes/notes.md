# Lecture 6: Classes

# Sources

These notes were adapted or copied verbatim from from [Adam Hartz](https://hz.mit.edu/)'s MIT [6.145 readings](https://hz.mit.edu/catsoop/6.145/), as well as [Think Python 2e](https://greenteapress.com/wp/think-python-2e/) by [Allen Downey](http://www.allendowney.com/wp/).

# Objects, Classes, and Instances

Python comes with several built-in data types. Some of the ones we've seen already: `int`, `float`, `str`, `list`, `dict`, and a few others.

Objects are the main "things" that Python programs work with, and each object has both a type and a value: an object's value determines the exact thing it represents, and its type determines the kinds of things that programs can do to it (defines the set of valid operations on that type of object).

We will occasionally use different terminology: we can refer to an object's type as its class, and we can say that the object itself is an instance of that class.

For example, `int` is a class, and some examples of instances of that class are: `478`, `1`, and `3`. Similarly, `str` is a class, and some examples of instances of that class are: `"sandwich"`, `"1234"`, and `"name"`.

By virtue of being members of the same class of objects, we can operate on any string in exactly the same ways, regardless of the particular value an instance represents. For example: we can concatenate strings, we can use len to compute their length, we can loop over them with for, and we can index into them to find the characters at particular locations within them, and we can convert them to lower-case with `x.lower()`. Importantly, it is the object's type that determines the operations that are possible when dealing with that object.

Before we start discussing programming, let's step back and inspect our daily lives. Everyone pretty much has a cell phone these days. In this analogy, we might say that a cell phone is an object (or a class), and the specific cell phone that you own is an instance of that class! By all being cell phones, they all have phone numbers, phone brands, phone carrier companies, and so on, and they all can make calls, play voicemail messages, send texts, and so on.

However, if we inspect my cell phone, I have _my_ phone number, and my specific phone is an iPhone 11, and I make calls and send texts from my phone numbers, and I have a specific voicemail recording for voicemail, etc. You get the gist. If we look at your phone, you would have different _values_ for these different properties! If we wanted a way to represent a cell phone in Python with the types that we currently know about, chances are it would get very messy and complicated. Instead, what if we could have this abstract representation of a cell phone in our code?

That's exactly what classes are for. Let's dive into an example.

# Creating/Using a Class

In order to create a class, we use the `class` keyword (shocking, I know). Let's go through our cell phone example above:

```
class CellPhone:
    pass
```

Class definitions always start with the `class` keyword, followed by a name for the class (here, `CellPhone`), followed by an indented body.

For now, the body of this class definition is not particularly interesting: it consists of a single instruction to Python: `pass` (which is a Python statement that means: do nothing). You can define variables and functions inside a class definition, but we will get back to that later.

Executing this definition causes Python to do two things: firstly, it creates a `class` object to represent this class; and secondly, it binds the name `CellPhone` to this class object (in the scope it was defined).

## Creating Instances

We've actually created a class right there, despite it being quite useless for the time being. We can create an instance of the class (basically create a `CellPhone`) by calling it like a function.

```
kylies_phone = CellPhone()
```

The return value is a reference to a `CellPhone` object, which we assign to `kylies_phone`. Creating a new object is called **instantiation**. The object is an **instance** of the class.

## Attributes

Ok let's give our cell phone some more utility, so it's not just a dud. Let's add a phone number. This is known as an attribute. Think of an attribute as a variable associated with a class!

```
class CellPhone:
    phone_number = "123-456-7890"
```

Now, if I instantiate my phone again, we can actually retrieve the variable inside the class using dot notation:

```
kylies_phone = CellPhone()
print(kylies_phone.phone_number)  # 123-456-7890
```

We can set or change attributes of an instantiated class outside of the class definition as well.

```
kylies_phone = CellPhone()
print(kylies_phone.phone_number)  # 123-456-7890

# changing value of an attribute
kylies_phone.phone_number = "000-000-0000"
print(kylies_phone.phone_number)  # 000-000-0000

# setting new attribute
kylies_phone.voicemail_msg = "Hi, you've reached Kylie."
print(kylies_phone.voicemail_msg)  # Hi, you've reached Kylie.
```

How does this affect other instances? Let's create a phone for Mia:

```
mias_phone = CellPhone()
print(mias_phone.phone_number)  # 123-456-7890
print(mias_phone.voicemail_msg)  # Error!
```

We notice that even though we changed certain attributes for Kylie's phone, Mia's phone was unaffected. This is one of the reasons why we love classes. We can create classes to make abstract objects in Python for so many things - people, dogs, and eventually, abstract things! However, take note that because we could _change_ attributes of an object after it was created, this means that classes (in general) are _mutable_.

Let's put our cell phone analogy on pause right now. Instead, let's take a look at some geometry.

# Classes and Methods

Let's think about rectangles:

```
class Rectangle:
    pass
```

What characterizes a rectangle? First thing that comes to mind is width and height, so let's use those.

```
class Rectangle:
    width = 0.0
    height = 0.0

box = Rectangle()
# let's give the box a width and height
box.width = 100.0
box.height = 200.0
```

How can we calculate the area of a rectangle? Let's write a function for that.

```
def get_rec_area(width, height):
    return width * height
```

Ok... but we could also just pass in the `Rectangle` object since we know they have `width` and `height` attributes already!

```
def get_rec_area(rec): # note that rec is an object of class `Rectangle`
    return rec.width * rec.height
```

We can write other functions pertaining to the rectangle too:

```
# length of the diagonal from opposing corners of rectangle
def get_diagonal_length(rec):
    return (rec.width ** 2 + rec.height ** 2) ** 0.5  # hypotenuse

# returns an instance of Rectangle with 1/2 the width and 1/2 the height of the original
def get_mini_rec(rec):
    new_rec = Rectangle()
    new_rec.width = rec.width / 2
    new_rec.height = rec.height / 2
    return new_rec
```

However, just from looking at a program written in that style, it is not obvious that there is any connection between the functions we've defined, and the types of data they operate on. With some examination, however, it becomes apparent that all of the operations above take in an instance of `Rectangle` as an argument.

This observation is the motivation for methods. A **method** is a function that is associated with a particular class. Methods are using the same vocab as functions, but there are two differences:

- Methods are defined inside a class definition in order to make the relationship between the class and the method explicit
- The syntax for invoking a method is different from the syntax for calling a function.

Let's start by transforming one of these functions into a method. As a first step, all we have to do is to move the definition into the class (notice the change in indentation):

```
class Rectangle:
    width = 0.0
    height = 0.0

    # gets area of rec
    def get_rec_area(rec):
        return rec.width * rec.height

    # length of the diagonal from opposing corners of rectangle
    def get_diagonal_length(rec):
        return (rec.width ** 2 + rec.height ** 2) ** 0.5  # hypotenuse

    # returns an instance of Rectangle with 1/2 the width and 1/2 the height of the original
    def get_mini_rec(rec):
        new_rec = Rectangle()
        new_rec.width = rec.width / 2
        new_rec.height = rec.height / 2
        return new_rec
```

There are two ways to call these methods!

```
box = Rectangle()
box.width = 100.0
box.height = 200.0

print(Rectangle.get_rec_area(box))  # prints 20000.0
```

Here, Python is going to the class definition of `Rectangle`, looking up `get_rec_area`, and calling it and passing in `box` as an argument. But, this notation is actually really rare in the Python world. Instead, we usually do this:

```
print(box.get_rec_area())  # prints 20000.0
```

Woah. What just happened there?? Where did the argument go?

Turns out, if a method is looked up from an _instance_ instead of from a _class_, Python will automatically insert that instance as the _first argument_ to the method! Another example is with `append` on lists! When we create a list, `l = [1, 2, 3]`, and call append: `l.append(4)`, this is taking the instance of a `list`, `l` in this case, and adding a `4` to the end of the list!

In the CS world, we use a convention where we name the first parameter of a method in a class as `self`. It kinda makes sense because when we use `self`, we're literally referring to the object's instance of itself! So, more commonly, you would see this:

```
class Rectangle:
    width = 0.0
    height = 0.0

    # gets area of rec
    def get_rec_area(self):
        return self.width * self.height

    # length of the diagonal from opposing corners of rectangle
    def get_diagonal_length(self):
        return (self.width ** 2 + self.height ** 2) ** 0.5  # hypotenuse

    # returns an instance of Rectangle with 1/2 the width and 1/2 the height of the original
    def get_mini_rec(self):
        new_rec = Rectangle()
        new_rec.width = self.width / 2
        new_rec.height = self.height / 2
        return new_rec
```

## `self`

Let's expand a bit more on `self`.

Firstly, it's important to note that `self` is just a name, which is typically used as the first parameter to a method. This first argument, regardless of what it is called, always denotes the instance that is currently being operated on.

If a method is looked up via a class, it is up to the programmer to provide the instance of that class that the method should act on. If the method is looked up via an instance, however, Python will automatically insert that instance as the first argument to the method (the argument typically called self).

In our `Rectangle` class, we could have defined another function that took in additional arguments:

```
class Rectangle:
    width = 0.0
    height = 0.0

    # gets area of rec
    def get_rec_area(self):
        return self.width * self.height

    # length of the diagonal from opposing corners of rectangle
    def get_diagonal_length(self):
        return (self.width ** 2 + self.height ** 2) ** 0.5  # hypotenuse

    # returns an instance of Rectangle with 1/2 the width and 1/2 the height of the original
    def get_mini_rec(self):
        new_rec = Rectangle()
        new_rec.width = self.width / 2
        new_rec.height = self.height / 2
        return new_rec

    # returns bool, whether this rectangle is larger than another rec (passed in)
    def is_larger_than(self, other):
        self_size = self.get_rec_area()
        other_size = other.get_rec_area()
        return self_size > other_size
```

## Initializing Values

We might notice it doesn't seem logical that we're automatically setting `width` and `height` as 0 for our Rectangle. We also might notice it didn't seem too logical to set a phone number for each cell phone, since we know that cell phones should have unique phone numbers. Instead, maybe we can pass in these values to the object when we create an instance! We can do that by defining an initialization function inside of the class, using the `__init__` (two underscore characters, followed by init, and then two more underscores) function.

```
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
```

With this new method, we could then instantiate a `Rectangle` like this:

```
box = Rectangle(100.0, 200.0)
```

If arguments are passed in when creating an instance of a class, Python will pass them to the class's `__init__` method. In particular, Python will do the following in response to the code above:

1. Create a new instance of `Rectangle` and bind it to the name `box`.
2. Run the `__init__` method with `box` passed in as the first argument (in the example above, `Rectangle.__init__(box, 100.0, 200.0))`.
3. Inside of the body of the method, the name `self` refers to this new instance, so the method will store values `100.0` as `width` and `200.0` as `height`, inside the instance (so that they are accessible from outside the method as `box.width` and `box.height`).

It is common for the parameters of `__init__` to have the same names as the attributes. The statement:

```
self.width = width
```

stores the value of the parameter `width` as an attribute of `self` (the newly-created instance).

# Practice Questions

Assume we have the following class definitions:

```
class Car:
    weight = 1000

    def __init__(self, weight, driver):
        self.weight = weight
        self.driver = driver

class Person:
    weight = 100

    def __init__(self, weight):
        self.weight = weight
```

What results from the following print statements?

```
print(Person)  # class

p = Person(150)
print(p)  # instance

c = Car(2000, p)
print(Car.weight)  # 1000

print(c.weight)  # 2000

print(c.driver.weight)  # 150

print(Car.driver.weight)  # error
```
