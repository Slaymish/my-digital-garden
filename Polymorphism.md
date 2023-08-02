---
dg-home: false
dg-publish: true
---
Related: #java #programming #
[[UNI MOC]]
Hamish Burke || 16-05-2023
***

# Polymorhpism in Java

Polymorphism is one of the [[four fundamental principles of Object-Oriented Programming]] (OOP) in Java, along with [[encapsulation]], [[Inheritance and Subtyping\|inheritance]], and abstraction. It allows objects of different classes to be treated as objects of a common superclass. This enables a *single method or function to handle different types of objects at runtime*, making the code more flexible and extensible.

## Types of Polymorphism

In Java, there are two types of polymorphism: 

1. **Compile-time polymorphism**: Also known as method overloading, this type of polymorphism occurs when multiple methods have the same name but different parameters in the same class. The compiler determines which method to call based on the arguments passed during the method call.

2. **Runtime polymorphism**: Also known as [[Dynamic dispatch\|dynamic method dispatch]] or method overriding, this type of polymorphism occurs when a subclass provides an implementation for a method that is already provided by its superclass. The JVM determines which method to call during runtime based on the object's actual type.

****

## Polymorphism with Inheritance

Polymorphism is closely related to inheritance since it allows a subclass object to be treated as an object of its superclass. Here's an example:

```java
class Animal {
    void makeSound() {
        System.out.println("The animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("The dog barks");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("The cat meows");
    }
}
```

Now we can create an array of Animal objects and process them in a loop:

```java
public class Main {
    public static void main(String[] args) {

        // Create an array of Animal objects
        Animal[] animals = new Animal[3];
        animals[0] = new Animal();
        animals[1] = new Dog();
        animals[2] = new Cat();

        // Make each animal make a sound
        for (Animal animal : animals) {
            animal.makeSound();
        }
    }
}
```

Output:

```
The animal makes a sound
The dog barks
The cat meows
```

Even though the array is of type `Animal`, it can hold objects of its subclasses, `Dog` and `Cat`. Polymorphism allows the correct makeSound() method to be called based on the