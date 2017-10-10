# How to create classes

A class in simple terms is just like a blueprint where you can group code that handles almost any type of abstraction, for example a common application such as a custom CMS with a User class that will handle new registrations, login and associating new posts to that user.

```mysql
+-------------+
|    User     |
+-------------+
```

To create a class we just write the word class followed by the class name, it is important to note that the first letter of classes are capitalized, although not required, but it is good practice to follow these points:
* Capitalize the first Letter of the class
* Class names that contain more than one word are capitalized the same way as the class names with single words, except each new word should start with a capital letter

# Adding properties to a class

Properties are variables but in the context of classes the correct term for them are member variables.

Below we have a simple representation of a user class with three properties, depending on the functionality and requirements of our application we would need to declare some of our properties with different levels of accessibility: public, protected  and private, this defines how these properties will be accessed.

```mysql
+-------------+
|    User     |
+-------------+
|  name       |
|  email      |
|  password   |
+-------------+
```

A public property is accessible outside of the object context, they can be directly accessed or modified.

A protected property can not be accessed directly outside the object context, they must be accessed via getters or setters, and only the class where it was declared and the children classes (if this class is inherited by other classes) can access them.

A private property is the most restrictive type, it can only be accessed by the class where it was declared, not even the children classes that inherit them are able to access them, however they can be made accessible via getters and setters

```php
class User {
	protected $name;
	protected $email;
	protected $password;
}
```

# Adding methods to a class

Properties allows our class to store data, methods allows us to execute certain actions in our objects, we can restrict how our methods are called with the visibilty keywords: public, protected and private .

```mysql
+-------------+
|    User     |
+-------------+
|  name       |
|  email      |
|  password   |
+-------------+
| getName()   |
| getEmail()  |
| setName()   |
| setEmail()  |
+-------------+
```

We write methods in a similarly way as class properties:	

```php
class User {
	protected $name;
	protected $email;
	protected $password;

	public function getName() {
		// method body
	} 

	public function getEmail() {
		// ...
	} 

	public function setName() {
		// ...
	} 

	public function setEmail() {
		// ...
	} 
}
```

As seen in the class above, methods must be declared in the body of the class, they can have a number of arguments just like functions, and also the visibility keyword, if this is omitted it will default to public.



# The constructor method

A Constructor is a special method that is invoked when a new object is created, it is mainly used to initialize class properties prior to any object actions.

Before PHP version 5 the constructor name was the class name :

```php
    User() { }
```

This is deprecated and should not be used anymore, a constructor name begins with two underscore characters:

```php
class User {
    protected $name;
    protected $email;
    protected $password;

    // DECLARE AND INITIALIZE CLASS PROPERTIES
    public function __construct( $name, $email, $password ) {
        $this->name = $name ;
        $this->email = $email;
        $this->password = $password ;
    }

    public function getName() {
        // method body
    } 

    public function getEmail() {
        // ...
    } 

    public function setName() {
        // ...
    } 

    public function setEmail() {
        // ...
    } 
}
```

In the example above we see that our properties are being initialized, but as you may already know PHP is a loosely typed language, we dont need to tell the constructor which type of variables we are passing to it, this might create unintended behavior, for example if we were passing an Age value we wouldn't be 100% sure if what we are passing is in fact a number or a string representation of that number:

```php
$age = 30;
$age = "30" ;
```

Our constructor will accept either of those, in some cases we need to make sure that were are in fact passing an Integer value, not a string value. PHP provides type checking for Arrays and Objects:

```php
public function __construct( array $cities, Address $addr ) {
    // ...
}
```

for primitive types such as ints, strings, or decimals we don't have a way to type hint their type, so how do we make sure that were are receiving the correct value with the correct data type? 
We can make use of these PHP functions to check for the type of data we are getting:


| Function      | Function Type      | Description             |
|---------------|--------------------|-------------------------|
| is_null()     | Null               | Unassigned              |
| is_resource() | Resource           | Database or File Handle |
| is_object     | Object             | An Object               |
| is_array()    | Array              | An Array                |
| is_string()   | String             | Characters              |
| is_double()   | Double             | Floating point number   |
| is_float()    | (alias of Double)  | An alias of Double      |
| is_integer()  | Integer            | whole number            |
| is_int()      | (alias of Integer) | whole number            |
| is_long()     | (alias of Integer) | whole number            |
| is_bool()     | Boolean            | true or false           |


But having many of these type checks will only add more lines of code.
In PHP 7 we can now check for these primitive types without having to use the functions above:

```php
public function __construct( string $name, int $age, float $price  ) {
    // ...
}
```

# How to create Objects

Why do we need objects? In procedural programming code is organized in the global scope, where you can just call their function names, things are different in an Object Oriented world, anything inside a class can't just be accessed like in procedural programming because it is outside of scope, this is when objects allows us to access the class properties and also change its state.

To create a new object we use the new keyword:

```php
$student1 = new Student() ;
```

this $student1 variable will create a new instance of the Student class, now we can get, set and change the state of this $student1 object, we are not limited to creating a single instance of a class, we can create an unlimited amount of objects ( as long as we dont run out of memory) :

```php
// additional  objects
$student1 = new Student() ;
$student2 = new Student() ;
$student3 = new Student() ;
```

![alt tag](http://juancadima.com/wp-content/uploads/student.jpg)


# Adding  Object properties and methods

Each object will have different values assigned, for example we could set $student1's age to 20, $student2's age to 30, and $student3's age to $40, although they were created from the same class they are all unique.

```php
class Student {
    public $age;
    public $name;
    public $id;

    public function __construct() { } 

    public function getAge()  {
        return $this->age;
    }
    // ...
}

$student1 = new Student() ;
$student1->age = 20 ; // set value
echo $student1->age;  // access attribute value
echo $student1->getAge() ; // access value via method
```







