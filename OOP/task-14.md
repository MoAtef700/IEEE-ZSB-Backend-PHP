1. Class vs Object

A Class is a blueprint or template used to define the structure and behavior of something.

An Object is an actual instance created from that class.

Real-world analogy:

Think of a car design:

The design (blueprint) = Class
The actual manufactured car = Object

So:

Class = idea or template
Object = real implementation of that idea
2. $this vs self::
$this
Refers to the current object instance
Used to access non-static properties and methods
self::
Refers to the class itself
Used to access static properties and methods
Difference:
$this → works with object-specific data
self:: → works with class-level (static) data
When to use:
Use $this when dealing with instance data
Use self:: when dealing with static members
3. Access Modifiers (Encapsulation)

There are three types of access modifiers:

1. public
Accessible from anywhere
2. protected
Accessible داخل الكلاس نفسه و الكلاسات اللي بتورث منه
3. private
Accessible only داخل نفس الكلاس
Example:
class User {
    private $password;
}
Why make a property private?

To protect sensitive data like passwords and prevent direct access or modification from outside the class.

4. Typed Properties

Typed properties mean defining the data type of a property.

Example:
class User {
    public string $name;
    public int $age;
}
Benefits:
Prevents assigning wrong data types
Reduces bugs
Makes the code clearer and more predictable
Example of error:
$user->age = "twenty"; //  Error
5. Constructor Method
__construct()

It is a special method that runs automatically when an object is created.

Example:
class User {
    public string $name;

    public function __construct($name) {
        $this->name = $name;
    }
}
Why is it useful?
Initializes object properties
Ensures required data is set when creating the object
Why pass arguments?

To allow each object to have different values.

Example:
$user1 = new User("Ahmed");
$user2 = new User("Ali");