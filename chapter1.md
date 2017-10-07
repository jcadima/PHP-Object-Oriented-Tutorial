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













