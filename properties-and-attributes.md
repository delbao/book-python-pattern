Getters and setters are common practice in object-oriented programming to ensure the principle of data encapsulation. A Javaesque way is a private attribute with public getter and setter methods. For example,

```
class Person:
    def __init__(self, height):
        self.__height = height
    
    def get_height(self):
        return self.__height
        
    def set_height(self, height):
        self.__height = height
```

This way of implementation has a readability issue. The code below is easier to write and read than the Javaesque expression.

```
p1 = Person(180)
p2 = Person(90)
p1.set_height(p1.get_height()+p2.get_height())
```

This is why the Pythonic way to introduce attributes is to make them public.

```
p1.height = p1.height + p2.height
```

## Data encapsulation

We can hear people howling and screaming about no data encapsulation. True, it is a serious argument: what happens if we want to change the implementation of getter and setter in the future? Getter and setter methods will prevent us from changing every attribute accesses scattered across the code base.

Fortunately, python has a rescue: **Properties**. The class with a property looks like this:

```
class Person:
    def __init__(self, height):
        self.__height = height
    
    @property
    def height(self):
        return self.__height
    
    @height.setter
    def height(self, height):
        self.__height = height
```

* getter is decorated by "@property" and named by the attribute name: height.
* setter is decorated by "@height.setter" and also named by height
* internally, the attribute is private

The access looks like the attribute is public. Problem solved!!

```
p1.height = p1.height + p2.height
```



