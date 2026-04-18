1. Inheritance

Question: What is the main benefit of Inheritance in OOP? Give a simple example of a Parent class and a Child class.

Answer:
The main benefit of inheritance is code reusability. It allows a child class to inherit properties and methods from a parent class, which reduces code duplication.

Example:

class Animal {
    public function eat() {
        echo "Animal is eating";
    }
}

class Dog extends Animal {
    public function bark() {
        echo "Dog is barking";
    }
}
2. The final Keyword

Question: What happens if you put the final keyword before a class or a method? Why would a developer want to use this?

Answer:
If the final keyword is used before a class, it cannot be inherited.
If it is used before a method, the method cannot be overridden.

Developers use it to protect important code from being modified or changed unintentionally.

3. Overriding Methods

Question: What does it mean to "override" a method in a child class? How can you call the original parent method from inside the child's overridden method?

Answer:
Overriding means redefining a method in the child class that already exists in the parent class, but with a different implementation.

To call the parent method, we use parent::

Example:

class Animal {
    public function sound() {
        echo "Animal sound";
    }
}

class Dog extends Animal {
    public function sound() {
        parent::sound();
        echo " - Dog barks";
    }
}
4. Abstract Class vs Interface

Question: What is the main difference between an Abstract Class and an Interface? Can a class implement multiple interfaces?

Answer:
The main difference is:

An Abstract Class can have both abstract and normal methods.
An Interface can only have abstract methods (no implementation).

A class can extend only one abstract class, but it can implement multiple interfaces.

5. Polymorphism

Question: What is Polymorphism? Provide a basic example.

Answer:
Polymorphism means using the same method name in different classes, but each class has its own implementation.

Example:

class Cat {
    public function sound() {
        echo "Meow";
    }
}

class Dog {
    public function sound() {
        echo "Bark";
    }
}

$animals = [new Cat(), new Dog()];

foreach ($animals as $animal) {
    $animal->sound();
}