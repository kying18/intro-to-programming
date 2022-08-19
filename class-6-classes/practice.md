# Practice Questions

## Assume we have the following class definitions:

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
