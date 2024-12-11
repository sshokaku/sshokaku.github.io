# An invitation to OOP, key concepts in Python

In this mini-course of OOP I'll show you basic concepts used in this programming paradigm, this mini-course is designed to be an invitation to study OOP or remember key concepts, for those who are experienced with this paradigm, also it's important to say that in this mini-course we only work with Python, enjoy learning!!

## Classes and Objects
**Definition (Class):** A class is a template that defines the common characteristics and behaviors of an object (instance), which are defined from it. In a class we must define:
1) *Attributes:* Are the data or fields that will have the instances of the class.
2) *Methods:* Correspond to all functionalities that objects can do.

**Definition (Object):** An object is a particular case of a class, in an object we set specific attributes and it inherits methods from the class.

Below we can show a good example of a class:


```python
class human:
    # Constructor to attributes
    def __init__(self, name, weight):
        self.name = name #Attribute
        self.weight = weight #Attribute
    def eat(self,food): #Method of the class
        if self.weight <= 0:
            print(f' {self.name} has died of starvation, and cannot be fed :c')
        if food != '' and self.weight > 0:
            self.weight = self.weight + 1
            print(f' Yummy!! {self.name} has been eating {food}, and currently, his weight is {self.weight} kg.')
        elif food == '' and self.weight>0:
            self.weight = self.weight - 1
            print(f'{self.name} has not been eating; his current weight is {self.weight} kg.')
```

Now, we will create a particular instance of the template *human*, for example, me!


```python
me = human("Genner", 78)
```

The next thing I’ll do is eat!


```python
me.eat("Bandeja Paisa")
```

     Yummy!! Genner has been eating Bandeja Paisa, and currently, his weight is 79 kg.
    

Return to the code, you may be asked what this is:
```python
def __init__(self, name, weight):
```
This line defines the attributes of our class and is commonly called the *constructor*, after this line we initialize the attributes of our class.

If we set attributes in our class *human* we will obtain an object, in our example, the object *me*. We can call methods of an object with a dot, like we saw in our example; we can also get the attributes of our object:


```python
me.name
```




    'Genner'




```python
me.weight
```




    79



Note that the attribute weight has been modified by the method `eat`. We can modify this attribute again using the method eat.


```python
me.eat('')
```

    Genner has not been eating; his current weight is 78 kg.
    

Let's find out if the attribute *weight* has actually been modified:


```python
me.weight
```




    78



With this class we have an issue, because all attributes of the class *human* are public, that is to say, all users can modify them:


```python
me.weight = 0
me.eat('')
```

     Genner has died of starvation, and cannot be fed :c
    

## Encapsulation: Protected and private attributes


```python

```
