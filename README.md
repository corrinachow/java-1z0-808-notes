# Chapter 1 - Java Building blocks

## Summary

- Java begins program execution with a `main()` method, the most common signature for this method is `public static void main(String[] args)`
- Arguments are passed in after the class name, as in `java NameOfClass firstArgument`
- Java code is organised into folders called packages, and must be imported, a wildcard (`*`) ending an import statement imports all classes inside that package
	- `java.lang` is _automatically_ imported
- **Constructors** create Java objects, a constructor is a method matching the class name and omitting the return type
	- When an object is instantiated, **fields** and **blocks of code** are initialised first, _then_ the constructor is run
- Primitive types are the basic building blocks of Java types, they're assembled into **reference types**
	- Reference types can have methods and be assigned to `null`
	- In addition to "normal" numbers, numberic literals are allowed to begin with `0` (octal), `0x` (hex), `0X` (hex), `0b` (binary), or `0B` (binary)
	- Numeric literals are also allowed to contain underscores as long as they are directlybetween two other numbers
- Declaring a variable involves stating the data type and giving the variable a name
	- Variables that represent fields in a class are automatically initialised to their corresponding _"zero"_ or null value during object instantiation
	- Local variables must be specifically initialised
	- Identifiers may contain letters, numbers, `$`, or `_`
	- **Identifiers may not begin with numbers**
- There are three kinds of variables in Java, depending on their scope:
	- Instance variables
	- Class variables
	- Local variables
	- **Instance variables** are _non-static_ fields of your class
	- **Class variables** are _static_ fields within a class
	- **Local variables** are declared within a method
- Order within a file matters:
	- **package** statements come first if present
	- **import** statements
	- **class** declaration
	- fields and methods are allowed to be in any order within the class
- **Garbage collection** is responsible for removing objects from memory when they can never be used again
	- An object becomes eligible for garbage collection when there are _no more references_ to it or its references have all _gone out of scope_
	- The `finalize()` method will run once for each object if/when it is first garbage collected
- Java code is object oriented, meaning all code is defined in **classes**
	- Access modifiers allow classes to encapsulate data and is _platform independent_, compiling to **bytecode**
- There is **eight primitive types**: `byte` (from `-128` to `127`), `short`, `int`, `long` are respectively: `8`, `16`, `32`, `64`-bit; `float` and `double` are `32` and `64`-bit floating-point(=decimal), respectively; `char` is 16-bit Unicode


## Chapter 1 - Exam essentials

**Be able to write code using a `main()` method**: A `main()` method is usually written as `public static void main(String[] args)`
**Understand the effect and using of packages and imports**: Packages contain Java classes, classes can be imported by class name or wildcard. Wildcards _do not look at subdirectories_. In the event of a conflict, _class name imports take precedence_.
**Be able to recognise a constructor**: A constructor has the same name as the class, _it looks like a method without a return type_
**Be able to identify legal and illegal declarations and initialisations**: Multiple variables can be declared and initialised in the same statement when they share a type
**Be able to determine where variables go into and out of scope**: All variables go into scope when they're declared.
	- Local variables go out of scope when the block they are declared in ends
	- Instance variables go out of scope when the object is garbage collected
	- Class variables remain in scope as long as the program is running
**Be able to recognise misplaced statements in a class**: Package and import statements are optional, when they are present, they go _before the class declaration 
**Know how to identify when an object is eligible for garbage collection**: Draw a diagram to keep track of references and objects as you trave the code, when no arrows point to a box (object), it is eligible for garbage collection

# Chapter 2 - Operators and Statements

## Summary

Order of operator precedence

| Operator                        | Symbols and examples                               |
| ------------------------------- | -------------------------------------------------- |
| Post-uniary operators           | expression++, expression--                         |
| Pre-unary operators             | ++expression, --expression                         |
| Other unary operators           | +, -, !                                            |
| Multiplication/Division/Modulus | \*, /, %                                           |
| Addition/Subtraction            | +, -                                               |
| Shift operators                 | <<, >>, >>>                                        |
| Relational operators            | <, >, <=, >=, instanceof                           |
| Equal to/not equal to           | ==, !=                                             |
| Logical operators               | &, ^,                                              |  |
| Short-circuit logical operators | &&,                                                |  |  |
| Ternary operators               | boolean expression ? expression1 : expression2     |
| Assignment operators            | =, +=, -=, \*=, /=, %=, &=, ^=, !=, <<=, >>=, >>>= |

- `int` multiplied by `double` is type `double`
- **numeric promotion** occurs before the operation, for any operator
- `short` multiplied by `short` is integer (same for char) for binary operators

## Chapter 2 - Exam Essentials

**Be able to recognise which operators are associated with which data types**: Some operators may be applied only to numeric primitives, some only to `boolean` values, and some only to objects

**Understand Java operator precedence**: Look at the table
**Understand how `break` and `continue` can change flow control**

**Implicit Casting of a Primitive**: 

byte -> short -> int -> long -> float -> double
-------------------------------------------->
					widening

**Explicit Casting of a Primitive**: 

double -> float -> long -> int -> short -> byte
-------------------------------------------->
					narrowing

                    # Chapter 3 - Core Java APIs

## Summary

### Strings

- `String`s are immutable sequences of characters where the `new` operator is optional
- The concatenation operator (`+`) creates a new `String` with the content of the first String followed by the cotent of the second String
- **`String` literals are stored in the string pool**

Both string literals refer to the same object:
```java
String a = "abc"; 
String b = "abc";
System.out.println(a == b);  // true
```

Here, 2 different objects are created and have different references
```java
String c = new String("abc");
String d = new String("abc");
System.out.println(c == d);  // false
```
- `StringBuilder`s are mutable sequences of characters
- Most `StringBuilder` methods return a reference to the current object
- `StringBugger` is the same as `StringBuilder` but is thread safe
- Calling `==` on `String` objects will check whether they point to the same object in the pool
- Calling `==` on `StringBuilder` will check whether they are pointing to the same `StringBuilder` object
- Calling `equals()` on `String` objects will check whether the sequence of characters are the same
- Calling `equals()` on `StringBuilder` objects will check whether they are pointing to the same object rather than comparing the values

### Arrays
- An array is a **fixed-size** area of memory on the heap that has space for primitives or pointers to objects
- You specify the size when creating it -- `int[] a = new int[6]`
- Methods that are passed varargs(...) can be used as if a normal array was passed in
- A `ArrayList` can change size over its life
- `ArrayList` can be stored in an `ArrayList` or `List` reference

### LocalDateTime

-  Dates and times can be manipulated using `plusXXX` or `minusXXX` methods
- The `Period` class represents a number of days, months, or years to add or subtract from a `LocalDate` or `LocalDateTime`
- `DateTimeFormatter` is used to output dates and times in the desired format
- Date and time classes are all immutable, meaning the return value must be used

## Chapter 3 - Exam Essentials

**Be able to determine the output of code using `String`**: Know the rules for concatenating `Strings` and how to use common `String` methods. `substring()` gets the string up until right before the index of the second parameter

**Be able to determine the output of code using `StringBuilder`**: Know that `StringBuilder` is mutable and how to use common `StringBuilder` methods. `StringBuilder` methods return a reference to the correct instance of `StringBuilder`

**Understand the difference between `==` and `equals()`**: `==` checks object equality. `equals()` depends on the implementation of the object it is being called on. For `String`s, `equals()` checks the characters inside of ot

**Be able to determine the output of code using arrays**: Know how to declare and instantiate one-dimensional and multidimentional arrays

**Be able to determine the output of code using `ArrayList`**: Know that `ArrayList` can increase in size. Be able to identify the different ways of declaring and instantiating an `ArrayList` methods

**Recognise invalid uses of dates and times**: `LocalDate` does not contain tim fields and `LocalTime` does not contain date fields.

# Chapter 4 - Methods and Encapsulation

## Summary

- Java methods start with an **access modifier** of `public`, `private`, `protected`, or blank (default access, `package private`)
- This is followed by an **optional specifier** such as `static`, `final`, or `abstract`
- Next is the **return type**, which is `void` or a Java type
- The **method name** follows, using standard Java identifier rules

### Access Modifiers
- `private` means the code is only available from within the same class
- Default (package private), means the code is only available within the same package
- `protected` means the code is available from the same package or subclasses
- `public` means the code is available from anywhere
- `static` methods and variables are shared by the class
	- When referenced from outside the class, they are called using the classname, `StaticClass.method()`
- _Instance members are allowed to call static members, but static members are not allowed to call instance members_

- Java uses pass-by-value, meaning that calls to methods _create a copy of the parameters_
	- Assigning new values to those parameters in the method does not affect the caller's variables
- Calling methods on objects that are method parameters change the state of those objects and is reflect in the caller

### Overloaded Methods
- Overloaded methods are methods with the same name but different parameter list
- Java calls the most specific method it can find
- Exact matches are preferred, followed by wider primitives, followed by auto-boxing and varargs

### Constructors
- Constructors are used to instantiate new objects
- The default no-argument constructor is called when no constructor is coded 
- Multiple constructors are allowed and can call each other by writing `this()`
	- If `this()` is present, it must be the first statement in the constructor
- Constructors can refer to instance variables by writing `this` before a variable name to indicate they want the instance variable and not the method parameter with that name
- The order of initialisation is:
	
  1) The superclass
  2) Static variables and static initialisers
  3) Instance variables 
  4) Constructor

### Encapsulation
- Encapsulation refers to preventing callers from changing the instance variables directly
- This is done by making instance variables private and **getters/setters** public
- _Immutability refers to preventing callers from changing the instance variables at all_

### Lambda Expressions
- Lambda expressions allowed passing around blocks of code
- The full syntax is `(String a, String b) -> { return a.equals(b); }`
- The parameter types can be omitted
- When only one parameter is specified without a type, the parentheses can also be omitted
- The braces and return statement can be omitted for a single statement, making the short form `a -> a.equals(b)`
- Lambdas are passed to a method expecting to interface with another method
- `Predicate` is a common interface
- It has one method named `test` that returns a `boolean` and takes any type
- The `removeIf()` method on `ArrayList` takes a `Predicate`

## Chapter 4 - Exam Essentials

**Be able to identify correct and incorrect method declarations**: A sample method signature is `public static void method(String... args) throws Exception {}`

**Identify when a method or field is accessible**: Recognise when a method or field is accessed when the access modifier (`private`, `protected`, or default access) does not allow it

**Recognise valid and invalid uses of static imports**: Static imports import static members. They are written as `import static`. Make sure they are importing static methods or variables rather than classnames.

**State the output of code involving methods**: Identify when to call static rather than instance methods based on whether the classname or object comes before the method.

**Recognise the correct overloaded method**: Exact matches first, followed by wider primitives, followed by auto-boxing, followed by `varargs`. Assigning new values to method parameters does not change the caller, but calling methods on them does

**Evaluate code involving constructors**: Constructors can call constructors by calling `this()` as the first line of the constructor. Recognise when a default constructor is provided. Remember the order of initialisation is superclass, static variables/initialisers, instance variables/initialisers, and the constructor. 

**Be able to recognise when a class is properly encapsulated**: Look for `private` instance variables and `public` getters and setters when identifying encapsulation

**Write simple lambda expressions**: Look for the present or absence of optional elements in lambda code. Parameter types are optional. Braces are `return` keyword are optional when the body is a single statement. Parentheses are optional when only when parameter is specified and the type is implicit. The `Predicate` interface is commonly used with lambdas because it declares a single method called `test()`, which takes one parameter.

# Chapter 5 - Class Design

## Summary

### Inheritance
- Java classes follow a multilevel single-inheritance pattern in which every class has exactly one direct parent class, with all classes eventually inheriting from `java.lang.Object`
- Java interfaces simulate a limited form of multiple inheritance, since Java classes _may implement multiple interfaces_
- Inheriting a class **gives you access to all the the `public` and `protected` methods of the class**, but special rules for constructors and overriding methods must be followed or the code will not compile
	- For example, if the parent class doesn't include a no-argument constructor, an explicit call to a parent constructor must be provided in the child's constructors

### Overloaded, overriding methods
- When you override a method, you may reference the parent version of the method using the `super` keyword
- Overriding a method has limitations that the compiler follows:
	- The method in the child class must have the same signature as the method in the parent class
	- The method in the class must be at least as accessible or more accessible than the method in the parent class
	- The method in the child in the child class may not throw a checked exception that is new or boarder than the class of any exception thrown in the parent class method
	- If the method returns a value, it must be the same or a subclass of the method in the parent class, known as _covariant return types_
	- The method defined in the child class must be marked as `static` if it is marked as `static` in the parent class (**method hiding**). Likewise, the method must not be marked `static` in the child class if it is not marked as `static` in the parent class (**method overriding**)
- `final` methods cannot be overridden or hidden

### Inheriting Variables
- Can't override variable, but can hide it

```java
public class Rodent {
	protected int tailLength = 4; public void 	getRodentDetails() {
	System.out.println("[parentTail="+tailLength+"]"); 
	}
}

public class Mouse extends Rodent { 
	protected int tailLength = 8; public 	void getMouseDetails() {
	System.out.println("[tail="+tailLength +",parentTail="+super.tailLength+"]"); 
	}

	public static void main(String[] args) { 
	Mouse mouse = new Mouse(); 
	mouse.getRodentDetails(); 
	mouse.getMouseDetails();
} }

// [parentTail=4] 
// [tail=8,parentTail=4]
```

### Abstract classes
- An abstract class may include non-abstract methods and variables
- `abstract` methods cannot have a body

```java
public abstract class Turtle {
	public abstract void swim() {} // DOES NOT COMPILE 
	public abstract int getAge() { // DOES NOT COMPILE
		return 10; 
	}
}
```

- Abstract classes can't be marked as `final`
- Abstract methods can't be marked as `final`
- A method may not be marked as both `abstract` and `private`

### Concrete classes
- A _concrete class_ is the first non-abstract subclass that extends an abstract class and is required to implement all inherited abstract methods
- Has to implement all methods in parent classes

### Extending an Abstract Class
- Abstract classes can extend other abstract classes and are not required to provide implementations for any of the abstract methods
- A concrete class that `extends` an abstract class must implement all inherited abstract methods

```java
public abstract class Animal {
    public abstract String getName();
}
public abstract class BigCat extends Animal {
    public abstract void roar();
}
public class Lion extends BigCat {
    public String getName() {
        return "Lion";
    }
    public void roar() {
        System.out.println("The Lion lets out a loud ROAR!");
    }
}
```

#### Abstract Class Definition Rules
- Abstract classes cannot be instantiated directly
- Abstract classes may be defined with any number, including zero, of abstract and non-abstract methods
- Abstract classes may not be marked as `private` or `final`
- An abstract class that `extends` another abstract class inherits all of its abstract methods as its own abstract methods
- The first concrete class that `extends` an abstract class must provide an implementation for all of the inherited abstract methods

#### Abstract Method Definition Rules
- Abstract methods may only be defined in abstract classes
- Abstract methods may not be declared `private` or `final`
- Abstract methods must not provide a method body/implementation in the abstract class for which it is declared
- Implementing an abstract method in a subclass follows the same rules for overriding a method

### Implementing Interfaces
- Java doesn't allow multiple inheritance, but it does allow classes to implement any number of interfaces
- An _interface_ is an abstract data type that defines a list of abstract public methods that any class implementing the interface must provide
- Can include **constant variables** and **default methods**
- A class may implement multiple interfaces, each separated by a comma

#### Defining an Interface
- Interfaces cannot be instantiated directly
- An interface is not required to have any methods
- An interface may not be marked as `final`
- All the top-level interfaces are assumed to have `public` or default access, and they must include the `abstract` modifier in their definition. Marking an interface as `private` `protected` or `final` will trigger a compiler error, since it's incompatible with these assumptions
- All non-default methods in an interface are assumed to hav the modifiers `abstract` and `public` in their definition

#### Inheriting an Interface
1. A interface that `extends` another interface as well as an abstract class that `implements` and interface, _inherits all of the abstract methods as its own abstract methods_
2. The first concrete class that `implements` an interface, or `extends` an abstract class that `implements` an interface, must provide an implementation of all of the inherited abstract methods

```java

public interface HasTail { 
	public int getTailLength();
}

public interface HasWhiskers { 
	public int getNumberOfWhiskers();
}

public interface Seal extends HasTail, HasWhiskers { }
```
Any class that implements `Seal` must provide an implementation for all methods in the parent interfaces `getTailLength()` and `getNumberOfWhiskers()`

#### Abstract Methods and Multiple Inheritance

- A class can inherit from two interfaces that contain the same `abstract` method
	- If the signatures are the same, there's no conflict
	- If the signatures are different, the methods are considered a method overload

### Interface Variables
- Interface variables are assumed to be `public`, `static`, and `final`
- The value of an interface variable must be set when it's declared since it's marked as `final`
- Interface variables are constant variables defined on the interface level and **are accessible even without an instance of the interface**

### Default Interface Methods
- A _default method_ is a method defined within an interface with the `default` keyword in which a method body is provided
- A default method within an interface defines an abstract method with a default implementation
	- Classes have the option to override the default method if they need to but are not required to do so

#### Interface Rules
- A default method may only be declared within an interface and not within a class or abstract class
- A default method must be marked with the `default` keyword. If a method is marked as `default`, it _must_ provide a method body
- A default method is not assumed to be `static`, `final`. or `abstract`, as it may be used or overridden by a class that implements the interface
- Like all methods in an interface, a default is assumed to be `public` and will not compile if marked as `private` or `protected`

####Static Interface Methods
- A static method is assumed to be `public` and will not compile if marked as `private` or `protected`
- To reference the static method, a reference to the name of the interface must be used

```java
public class Bunny implements Hop { 
	public void printDetails() {
		System.out.println(Hop.getJumpHeight()); 
	}
}
```

#### Object vs. Reference
- All objects inherit `java.lang.Object`, and can be reassigned to `Object`

```java
Lemur lemur = new Lemur();

Object lemurAsObject = lemur;
```

- Even though the `Lemur` object has been assigned a reference with a different type, the object itself has not changed and still exists as a `Lemur` object in memory
- What changed is the ability to access methods within the `Lemur` class with the `lemurAsObject` reference, without an explicit cast back to `Lemur`, we no longer have access to the `Lemur properties of the object

1. The type of the object determines which properties exist within the object in memory
2. The type of the reference to the object determines which methods and variables are accessible to the Java program

### Casting Objects
- We can reclaim references defined in the subclass within an object by casting the object back to the specific subclass it came from

```java
Lemur lemur = new Lemur();

Primate primate = lemur;
Lemur lemur2 = primate; // DOES NOT COMPILE

Lemur lemur3 = (Lemur)primate; 
System.out.println(lemur3.age);
```

Rules of casting:
- Casting an object from a subclass to a superclass doesn't require an explicit cast
- Casting an object from a superclass to a subclass requires and explicit cast
- The compiler will not allow casts to unrelated types
- Even when the code compiles without issue, an exception may be throw at runtime if the object being cast is not actually an instance of that cast

Rule 3 example:
```java
public class Bird {}
public class Fish {
	public static void main(String[] args) {
	Fish fish = new Fish();
	Bird bird = (Bird)fish; // DOES NOT COMPILE }
}
```

Rule 4 example:
```java
public class Rodent { }

	public class Capybara extends Rodent { 
	public static void main(String[] args) {
		Rodent rodent = new Rodent();
		Capybara capybara = (Capybara)rodent; // Throws ClassCastException at runtime 
	}
}
```

#### Virtual Methods
- A method in which the specific implementation is not determined until runtime
- All non-final, non-static, and non-private Java methods are considered virtual methods since any can be overridden at runtime

### Polymorphic Parameters
- One of the most useful applications of polymorphism is the ability to pass instances of a subclass or interface to a method
- You can defined a method that takes an instance of an interface as a param


```java
public class Reptile {
    public String getName() {
        return "Reptile";
    }
}
public class Alligator extends Reptile {
    public String getName() {
        return "Alligator";
    }
}
public class Crocodile extends Reptile {
    public String getName() {
        return "Crocodile";
    }
}
public class ZooWorker {
    public static void feed(Reptile reptile) {
        System.out.println("Feeding reptile " + reptile.getName());
    }

    public static void main(String[] args) {
        feed(new Alligator());
        feed(new Crocodile());
        feed(new Reptile());
    }
}

// Feeding: Alligator 
// Feeding: Crocodile 
// Feeding: Reptile
```

## Summary

- Inheriting a class gives you access to all of the `public` and `protected` methods of the class, but special rules for constructors and overriding methods must be followed for the code will not compile
- If a parent class doesn't include a no-argument constructor, an explicit call to a parent constructor must be provided in the child's constructors
- Overloaded, overridden, and hidden methods 
- Abstract classes and interfaces and how they can be used to define a platform for other developers to interact with
- Polymorphism and how objects can be accessed in a variety of forms
- Casting and accessing objects and the difference between compile and runtime cast exceptions