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
print(Person) 

p = Person(150)
print(p) 

c = Car(2000, p)
print(Car.weight) 

print(c.weight) 

print(c.driver.weight) 

print(Car.driver.weight) 
```
