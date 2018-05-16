# Instance, Class and Static methods demystified 

In this tutorial, I'll help demystify what's behind class methods, static methods and instance methods. An intuitive understanding of the differences helps communicate the intent of the object-oriented code in Python and make the code easy to maintain. 

An `instance method` is a method bound to a class instance.
- It usually has `self` as the first argument to the function signature
- It can access instance members

A `class method` is defined in the class scope and decorated by **@classmethod**
- It usually has `cls` as the first argument
- It can access class member

A `static method` is decorated by **@staticmethod**
- It has neither self nor cls as an argument

## When to Use Class Methods

A typical use case is *factory methods*

```
# random Person
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod
    def fromBirthYear(cls, name, birthYear):
        return cls(name, date.today().year - birthYear)
```
factory methods ensures correct instance creation in derived class.

## When to Use Static Methods

Flagging a method as a static method is a hint that a class won't modify class or instance state. This restriction is enforced by the python runtime.

This restriction also makes writing unit test easy: setting up a class state is no longer needed.
