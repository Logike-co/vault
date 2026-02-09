#java 
___
**INDEX**
___
- Define the scope of variables. 
- Define the structure of a Java class.
- Create executable Java applications with a main method; run a Java program from the command line; produce console output.
- Import other Java packages to make them accessible in your code.
- Compare and contrast the features and components of Java such as: platform independence, object orientation, encapsulation, etc.

This part of the handbook covers the basics of the language, including: variables, operators, expressions, statements, blocks and control flow statements:

# Creating Variables and Naming Them

## Variables

As you learned in the previous section, an object stores its state in _fields_.

```java
int cadence = 0;
int speed = 0;
int gear = 1;
```

The [What Is an Object?](Oriented%20Object%20Programming.md) discussion introduced you to fields, but you probably have still a few questions, such as: What are the rules and conventions for naming a field? Besides `int`, what other data types are there? Do fields have to be initialized when they are declared? Are fields assigned a default value if they are not explicitly initialized? We'll explore the answers to such questions in this section, but before we do, there are a few technical distinctions you must first become aware of. In the Java programming language, the terms "field" and "variable" are both used; this is a common source of confusion among new developers, since both often seem to refer to the same thing.

The Java programming language defines the following kinds of variables:

- **Instance Variables (Non-Static Fields)** Technically speaking, objects store their individual states in "non-static fields", that is, fields declared without the `static` keyword. Non-static fields are also known as instance variables because their values are unique to each instance of a class (to each object, in other words); the `currentSpeed` of one bicycle is independent from the `currentSpeed` of another.
- **Class Variables (Static Fields)** A class variable is any field declared with the `static` modifier; this tells the compiler that there is exactly one copy of this variable in existence, regardless of how many times the class has been instantiated. A field defining the number of gears for a particular kind of bicycle could be marked as `static` since conceptually the same number of gears will apply to all instances. The code `static int numGears = 6;` would create such a `static` field. Additionally, the keyword `final` could be added to indicate that the number of gears will never change.
- **Local Variables** Similar to how an object stores its state in fields, a method will often store its temporary state in local variables. The syntax for declaring a local variable is similar to declaring a field (for example, `int count = 0;`). There is no special keyword designating a variable as local; that determination comes entirely from the location in which the variable is declared — which is between the opening and closing braces of a method. As such, local variables are only visible to the methods in which they are declared; they are not accessible from the rest of the class.
- **Parameters** You've already seen examples of parameters, both in the `Bicycle` class and in the main method of the "Hello World!" application. Recall that the signature for the main method is `public static void main(String[] args)`. Here, the `args` variable is the parameter to this method. The important thing to remember is that parameters are always classified as "variables" not "fields". This applies to other parameter-accepting constructs as well (such as constructors and exception handlers) that you'll learn about later in the tutorial.

Having said that, the remainder of this tutorial uses the following general guidelines when discussing fields and variables. If we are talking about "fields in general" (excluding local variables and parameters), we may simply say "fields". If the discussion applies to "all of the above", we may simply say "variables". If the context calls for a distinction, we will use specific terms (static field, local variables, etc.) as appropriate. You may also occasionally see the term "member" used as well. A type's fields, methods, and nested types are collectively called its _members_.
 
## Naming Variables

Every programming language has its own set of rules and conventions for the kinds of names that you're allowed to use, and the Java programming language is no different. The rules and conventions for naming your variables can be summarized as follows:

- Variable names are case-sensitive. A variable's name can be any legal identifier — an unlimited-length sequence of Unicode letters and digits, beginning with a letter, the dollar sign `$`, or the underscore character `_`. The convention, however, is to always begin your variable names with a letter, not `$` or `_`. Additionally, the dollar sign character, by convention, is never used at all. You may find some situations where auto-generated names will contain the dollar sign, but your variable names should always avoid using it. A similar convention exists for the underscore character; while it's technically legal to begin your variable's name with `_`, this practice is discouraged. White space is not permitted.
- Subsequent characters may be letters, digits, dollar signs, or underscore characters. Conventions (and common sense) apply to this rule as well. When choosing a name for your variables, use full words instead of cryptic abbreviations. Doing so will make your code easier to read and understand. In many cases it will also make your code self-documenting; fields named cadence, speed, and gear, for example, are much more intuitive than abbreviated versions, such as s, c, and g. Also keep in mind that the name you choose must not be a keyword or reserved word.
- If the name you choose consists of only one word, spell that word in all lowercase letters. If it consists of more than one word, capitalize the first letter of each subsequent word. The names `gearRatio` and `currentGear` are prime examples of this convention. If your variable stores a constant value, such as static final int NUM_GEARS = 6, the convention changes slightly, capitalizing every letter and separating subsequent words with the underscore character. By convention, the underscore character is never used elsewhere.

- Define the scope of variables 
- Define the structure of a Java class
- Create executable Java applications with a main method; run a Java program from the command line; produce console output
- Import other Java packages to make them accessible in your code
- Compare and contrast the features and components of Java such as: platform independence, object orientation, encapsulation, etc.

# Expressions, Statements and Blocks

 

## Expressions

An _expression_ is a construct made up of variables, operators, and method invocations, which are constructed according to the syntax of the language, that evaluates to a single value. You have already seen examples of expressions, illustrated in code below:

```java
int cadence = 0;
anArray[0] = 100;
System.out.println("Element 1 at index 0: " + anArray[0]);

int result = 1 + 2; // result is now 3
if (value1 == value2)
    System.out.println("value1 == value2");
```

Copy

The data type of the value returned by an expression depends on the elements used in the expression. The expression `cadence = 0` returns an `int` because the assignment operator returns a value of the same data type as its left-hand operand; in this case, `cadence` is an `int`. As you can see from the other expressions, an expression can return other types of values as well, such as `boolean` or `String`.

The Java programming language allows you to construct compound expressions from various smaller expressions as long as the data type required by one part of the expression matches the data type of the other. Here is an example of a compound expression:

```java
1 * 2 * 3
```

Copy

In this particular example, the order in which the expression is evaluated is unimportant because the result of multiplication is independent of order; the outcome is always the same, no matter in which order you apply the multiplications. However, this is not true of all expressions. For example, the following expression gives different results, depending on whether you perform the addition or the division operation first:

```java
x + y / 100    // ambiguous
```

Copy

You can specify exactly how an expression will be evaluated using balanced parenthesis: `(` and `)`. For example, to make the previous expression unambiguous, you could write the following:

```java
(x + y) / 100  // unambiguous, recommended
```

Copy

If you don't explicitly indicate the order for the operations to be performed, the order is determined by the precedence assigned to the operators in use within the expression. Operators that have a higher precedence get evaluated first. For example, the division operator has a higher precedence than does the addition operator. Therefore, the following two statements are equivalent:

```java
x + y / 100   // ambiguous

x + (y / 100) // unambiguous, recommended
```

Copy

When writing compound expressions, be explicit and indicate with parentheses which operators should be evaluated first. This practice makes code easier to read and to maintain.

 

## Floating Point Arithmetic

Floating point arithmetic is a special world in which common operations may behave unexpectedly. Consider the following code.

```java
double d1 = 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1;
System.out.println("d1 == 1 ? " + (d1 == 1.0));
```

Copy

You would probably expect that it prints `true`. Due to the way floating point addition is conducted and rounded, it prints `false`.

Presenting how floating point arithmetic is implemented in Java is beyond the scope of this tutorial. If you need to learn more on this topic, you may watch the following vide.

 

## Statements

Statements are roughly equivalent to sentences in natural languages. A statement forms a complete unit of execution. The following types of expressions can be made into a statement by terminating the expression with a semicolon (`;`).

- Assignment expressions
- Any use of `++` or `--`
- Method invocations
- Object creation expressions
- Such statements are called expression statements. Here are some examples of expression statements.

```java
// assignment statement
aValue = 8933.234;

// increment statement
aValue++;

// method invocation statement
System.out.println("Hello World!");

// object creation statement
Bicycle myBike = new Bicycle();
```

Copy

In addition to expression statements, there are two other kinds of statements: declaration statements and control flow statements. A declaration statement declares a variable. You have seen many examples of declaration statements already:

```java
// declaration statement
double aValue = 8933.234;
```

Copy

Finally, control flow statements regulate the order in which statements get executed. You will learn about control flow statements in the next section, Control Flow Statements.

 

## Blocks

A _block_ is a group of zero or more statements between balanced braces and can be used anywhere a single statement is allowed. The following example, `BlockDemo`, illustrates the use of blocks:

```java
class BlockDemo {
     public static void main(String[] args) {
          boolean condition = true;
          if (condition) { // begin block 1
               System.out.println("Condition is true.");
          } // end block one
          else { // begin block 2
               System.out.println("Condition is false.");
          } // end block 2
     }
}
```

# Creating Classes

 
## Declaring Classes

The introduction to object-oriented concepts in the section titled [Object, Classes and Interfaces](https://dev.java/learn/oop/) used a `Bicycle` class as an example, with racing bikes, mountain bikes, and tandem bikes as subclasses. Here is sample code for a possible implementation of a `Bicycle` class, to give you an overview of a class declaration. Subsequent sections will back up and explain class declarations step by step. For the moment, don't concern yourself with the details.

```java
public class Bicycle {
        
    // the Bicycle class has
    // three fields
    public int cadence;
    public int gear;
    public int speed;
        
    // the Bicycle class has
    // one constructor
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }
        
    // the Bicycle class has
    // four methods
    public void setCadence(int newValue) {
        cadence = newValue;
    }
        
    public void setGear(int newValue) {
        gear = newValue;
    }
        
    public void applyBrake(int decrement) {
        speed -= decrement;
    }
        
    public void speedUp(int increment) {
        speed += increment;
    }
}
```

Copy

A class declaration for a `MountainBike` class that is a subclass of `Bicycle` might look like this:

```java
public class MountainBike extends Bicycle {
        
    // the MountainBike subclass has
    // one field
    public int seatHeight;

    // the MountainBike subclass has
    // one constructor
    public MountainBike(int startHeight, int startCadence,
                        int startSpeed, int startGear) {
        super(startCadence, startSpeed, startGear);
        seatHeight = startHeight;
    }   
        
    // the MountainBike subclass has
    // one method
    public void setHeight(int newValue) {
        seatHeight = newValue;
    }   
}
```

Copy

`MountainBike` inherits all the fields and methods of `Bicycle` and adds the field `seatHeight` and a method to set it (mountain bikes have seats that can be moved up and down as the terrain demands).

You have seen classes defined in the following way:

```java
class MyClass {
    // field, constructor, and 
    // method declarations
}
```

Copy

This is a class declaration. The class body (the area between the braces) contains all the code that provides for the life cycle of the objects created from the class: constructors for initializing new objects, declarations for the fields that provide the state of the class and its objects, and methods to implement the behavior of the class and its objects.

The preceding class declaration is a minimal one. It contains only those components of a class declaration that are required. You can provide more information about the class, such as the name of its superclass, whether it implements any interfaces, and so on, at the start of the class declaration. For example,

```java
class MyClass extends MySuperClass implements YourInterface {
    // field, constructor, and
    // method declarations
}
```

Copy

means that `MyClass` is a subclass of `MySuperClass` and that it implements the `YourInterface` interface.

You can also add modifiers like `public` or `private` at the very beginning—so you can see that the opening line of a class declaration can become quite complicated. The modifiers `public` and `private`, which determine what other classes can access `MyClass`, are discussed later in this section. The section on interfaces and inheritance will explain how and why you would use the `extends` and `implements` keywords in a class declaration. For the moment you do not need to worry about these extra complications.

In general, class declarations can include these components, in order:

1. Modifiers such as `public`, `private`, and a number of others that you will encounter later. (However, note that the `private` modifier can only be applied to Nested Classes.)
2. The class name, with the initial letter capitalized by convention.
3. The name of the class's parent (superclass), if any, preceded by the keyword `extends`. A class can only extend (subclass) one parent.
4. A comma-separated list of interfaces implemented by the class, if any, preceded by the keyword `implements`. A class can implement more than one interface.
5. The class body, surrounded by braces, `{}`.

 

## Declaring Member Variables

There are several kinds of variables:

- Member variables in a class—these are called fields.
- Variables in a method or block of code—these are called local variables.
- Variables in method declarations—these are called parameters.
- The `Bicycle` class uses the following lines of code to define its fields:

```java
public int cadence;
public int gear;
public int speed;
```

Copy

Field declarations are composed of three components, in order:

1. Zero or more modifiers, such as `public` or `private`.
2. The field's type.
3. The field's name.

The fields of `Bicycle` are named `cadence`, `gear`, and `speed` and are all of data type integer (`int`). The `public` keyword identifies these fields as public members, accessible by any object that can access the class.

 

## Controlling who has Access to a Member

The first (left-most) modifier used lets you control what other classes have access to a member field. For the moment, consider only `public` and `private`. Other access modifiers will be discussed later.

- `public` modifier—the field is accessible from all classes.
- `private` modifier—the field is accessible only within its own class.

In the spirit of encapsulation, it is common to make fields private. This means that they can only be directly accessed from the `Bicycle` class. We still need access to these values, however. This can be done indirectly by adding public methods that obtain the field values for us:

```java
public class Bicycle {
        
    private int cadence;
    private int gear;
    private int speed;
        
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }
        
    public int getCadence() {
        return cadence;
    }
        
    public void setCadence(int newValue) {
        cadence = newValue;
    }
        
    public int getGear() {
        return gear;
    }
        
    public void setGear(int newValue) {
        gear = newValue;
    }
        
    public int getSpeed() {
        return speed;
    }
        
    public void applyBrake(int decrement) {
        speed -= decrement;
    }
        
    public void speedUp(int increment) {
        speed += increment;
    }
}
```

Copy

 

## Setting the Type of a Variable

All variables must have a type. You can use primitive types such as `int`, `float`, `boolean`, etc. Or you can use reference types, such as strings, arrays, or objects.

 

## Naming a Variable

All variables, whether they are fields, local variables, or parameters, follow the same naming rules and conventions that were covered in the Language Basics section, [Variables Naming](https://dev.java/learn/language-basics/variables/).

In this section, be aware that the same naming rules and conventions are used for method and class names, except that

- the first letter of a class name should be capitalized, and
- the first (or only) word in a method name should be a verb.


# Defining Methods

 

## Defining a Method

Here is an example of a typical method declaration:

```java
public double calculateAnswer(double wingSpan, int numberOfEngines,
                              double length, double grossTons) {
    //do the calculation here
}
```

Copy

The only required elements of a method declaration are the method's return type, name, a pair of parentheses, `()`, and a body between braces, `{}`.

More generally, method declarations have six components, in order:

1. Modifiers—such as `public`, `private`, and others you will learn about later.
2. The return type—the data type of the value returned by the method, or `void` if the method does not return a value.
3. The method name—the rules for field names apply to method names as well, but the convention is a little different.
4. The parameter list in parenthesis—a comma-delimited list of input parameters, preceded by their data types, enclosed by parentheses, `()`. If there are no parameters, you must use empty parentheses.
5. An exception list—to be discussed later.
6. The method body, enclosed between braces—the method's code, including the declaration of local variables, goes here.

Modifiers, return types, and parameters will be discussed later in this section. Exceptions are discussed in a later section.

> Definition: Two of the components of a method declaration comprise the method signature—the method's name and the parameter types.

The signature of the method declared above is:

```java
calculateAnswer(double, int, double, double)
```

Copy

 

## Naming a Method

Although a method name can be any legal identifier, code conventions restrict method names. By convention, method names should be a verb in lowercase or a multi-word name that begins with a verb in lowercase, followed by adjectives, nouns, etc. In multi-word names, the first letter of each of the second and following words should be capitalized. Here are some examples:

```java
run
runFast
getBackground
getFinalData
compareTo
setX
isEmpty
```

Copy

Typically, a method has a unique name within its class. However, a method might have the same name as other methods due to _method overloading_.

 

## Overloading Methods

The Java programming language supports overloading methods, and Java can distinguish between methods with different method signatures. This means that methods within a class can have the same name if they have different parameter lists (there are some qualifications to this that will be discussed in the section titled [Inheritance](https://dev.java/learn/numbers-strings/strings/)).

Suppose that you have a class that can use calligraphy to draw various types of data (strings, integers, and so on) and that contains a method for drawing each data type. It is cumbersome to use a new name for each method—for example, `drawString()`, `drawInteger()`, `drawFloat()`, and so on. In the Java programming language, you can use the same name for all the drawing methods but pass a different argument list to each method. Thus, the data drawing class might declare four methods named `draw()`, each of which has a different parameter list.

```java
public class DataArtist {
    ...
    public void draw(String s) {
        ...
    }
    public void draw(int i) {
        ...
    }
    public void draw(double f) {
        ...
    }
    public void draw(int i, double f) {
        ...
    }
}
```

Copy

Overloaded methods are differentiated by the number and the type of the arguments passed into the method. In the code sample, `draw(String s)` and `draw(int i)` are distinct and unique methods because they require different argument types.

You cannot declare more than one method with the same name and the same number and type of arguments, because the compiler cannot tell them apart.

The compiler does not consider return type when differentiating methods, so you cannot declare two methods with the same signature even if they have a different return type.

> Note: Overloaded methods should be used sparingly, as they can make code much less readable.


# Providing Constructors for your Classes

 

## Defining a Constructor

A class contains constructors that are invoked to create objects from the class blueprint. Constructor declarations look like method declarations—except that they use the name of the class and have no return type. For example, `Bicycle` has one constructor:

```java
public Bicycle(int startCadence, int startSpeed, int startGear) {
    gear = startGear;
    cadence = startCadence;
    speed = startSpeed;
}
```

Copy

To create a new `Bicycle` object called `myBike`, a constructor is called by the `new` operator:

```java
Bicycle myBike = new Bicycle(30, 0, 8);
```

Copy

The code `new Bicycle(30, 0, 8)` creates space in memory for the object and initializes its fields.

Although `Bicycle` only has one constructor, it could have others, including a no-argument constructor:

```java
public Bicycle() {
    gear = 1;
    cadence = 10;
    speed = 0;
}
```

Copy

The code `Bicycle yourBike = new Bicycle();` invokes the no-argument constructor to create a new `Bicycle` object called `yourBike`.

Both constructors could have been declared in `Bicycle` because they have different argument lists. As with methods, the Java platform differentiates constructors on the basis of the number of arguments in the list and their types. You cannot write two constructors that have the same number and type of arguments for the same class, because the compiler would not be able to tell them apart. Doing so causes a compile-time error.

You do not have to provide any constructors for your class, but you must be careful when doing this. The compiler automatically provides a no-argument, default constructor for any class without constructors. This default constructor will call the no-argument constructor of the superclass. In this situation, the compiler will complain if the superclass does not have a no-argument constructor so you must verify that it does. If your class has no explicit superclass, then it has an implicit superclass of `Object`, which does have a no-argument constructor.

You can use a superclass constructor yourself. The `MountainBike` class at the beginning of this lesson did just that. This will be discussed later, in the lesson on interfaces and inheritance.

You can use access modifiers in a constructor's declaration to control which other classes can call the constructor.

# Calling Methods and Constructors

 

## Passing Information to a Method or a Constructor

The declaration for a method or a constructor declares the number and the type of the arguments for that method or constructor. For example, the following is a method that computes the monthly payments for a home loan, based on the amount of the loan, the interest rate, the length of the loan (the number of periods), and the future value of the loan:

```java
public double computePayment(
                  double loanAmt,
                  double rate,
                  double futureValue,
                  int numPeriods) {
    double interest = rate / 100.0;
    double partial1 = Math.pow((1 + interest), 
                    - numPeriods);
    double denominator = (1 - partial1) / interest;
    double answer = (-loanAmt / denominator)
                    - ((futureValue * partial1) / denominator);
    return answer;
}
```

Copy

This method has four parameters: the loan amount, the interest rate, the future value and the number of periods. The first three are double-precision floating point numbers, and the fourth is an integer. The parameters are used in the method body and at runtime will take on the values of the arguments that are passed in.

> Note: _Parameters_ refers to the list of variables in a method declaration. Arguments are the actual values that are passed in when the method is invoked. When you invoke a method, the arguments used must match the declaration's parameters in type and order.

 

## Parameter Types

You can use any data type for a parameter of a method or a constructor. This includes primitive data types, such as doubles, floats, and integers, as you saw in the `computePayment()` method, and reference data types, such as objects and arrays.

Here is an example of a method that accepts an array as an argument. In this example, the method creates a new `Polygon` object and initializes it from an array of `Point` objects (assume that `Point` is a class that represents an `x`, `y` coordinate):

```java
public Polygon polygonFrom(Point[] corners) {
    // method body goes here
}
```

Copy

 

## Arbitrary Number of Arguments

You can use a construct called _varargs_ to pass an arbitrary number of values to a method. You use varargs when you do not know how many of a particular type of argument will be passed to the method. It is a shortcut to creating an array manually (the previous method could have used varargs rather than an array).

To use varargs, you follow the type of the last parameter by an ellipsis (three dots, ...), then a space, and the parameter name. The method can then be called with any number of that parameter, including none.

```java
public Polygon polygonFrom(Point... corners) {
    int numberOfSides = corners.length;
    double squareOfSide1, lengthOfSide1;
    squareOfSide1 = (corners[1].x - corners[0].x)
                     * (corners[1].x - corners[0].x) 
                     + (corners[1].y - corners[0].y)
                     * (corners[1].y - corners[0].y);
    lengthOfSide1 = Math.sqrt(squareOfSide1);

    // more method body code follows that creates and returns a 
    // polygon connecting the Points
}
```

Copy

You can see that, inside the method, `corners` is treated like an array. The method can be called either with an array or with a sequence of arguments. The code in the method body will treat the parameter as an array in either case.

You will most commonly see varargs with the printing methods; for example, this `printf()` method:

```java
public PrintStream printf(String format, Object... args)
```

Copy

allows you to print an arbitrary number of objects. It can be called like this:

```java
System.out.printf("%s: %d, %s%n", name, idnum, address);
```

Copy

or like this

```java
System.out.printf("%s: %d, %s, %s, %s%n", name, idnum, address, phone, email);
```

Copy

or with yet a different number of arguments.

 

## Parameter Names

When you declare a parameter to a method or a constructor, you provide a name for that parameter. This name is used within the method body to refer to the passed-in argument.

The name of a parameter must be unique in its scope. It cannot be the same as the name of another parameter for the same method or constructor, and it cannot be the name of a local variable within the method or constructor.

A parameter can have the same name as one of the class's fields. If this is the case, the parameter is said to shadow the field. Shadowing fields can make your code difficult to read and is conventionally used only within constructors and methods that set a particular field. For example, consider the following `Circle` class and its `setOrigin()` method:

```java
public class Circle {
    private int x, y, radius;
    public void setOrigin(int x, int y) {
        ...
    }
}
```

Copy

The `Circle` class has three fields: `x`, `y`, and `radius`. The `setOrigin()` method has two parameters, each of which has the same name as one of the fields. Each method parameter shadows the field that shares its name. So using the simple names `x` or `y` within the body of the method refers to the parameter, not to the field. To access the field, you must use a qualified name. This will be discussed later in this lesson in the section titled "Using the `this` Keyword."

 

## Passing Primitive Data Type Arguments

Primitive arguments, such as an `int` or a `double`, are passed into methods by value. This means that any changes to the values of the parameters exist only within the scope of the method. When the method returns, the parameters are gone and any changes to them are lost. Here is an example:

```java
public class PassPrimitiveByValue {

    public static void main(String[] args) {
           
        int x = 3;
           
        // invoke passMethod() with 
        // x as argument
        passMethod(x);
           
        // print x to see if its 
        // value has changed
        System.out.println("After invoking passMethod, x = " + x);
           
    }
        
    // change parameter in passMethod()
    public static void passMethod(int p) {
        p = 10;
    }
}
```

Copy

When you run this program, the output is:

```shell
After invoking passMethod, x = 3
```

Copy

 

## Passing Reference Data Type Arguments

Reference data type parameters, such as objects, are also passed into methods by value. This means that when the method returns, the passed-in reference still references the same object as before. However, the values of the object's fields can be changed in the method, if they have the proper access level.

For example, consider a method in an arbitrary class that moves `Circle` objects:

```java
public void moveCircle(Circle circle, int deltaX, int deltaY) {
    // code to move origin of circle to x+deltaX, y+deltaY
    circle.setX(circle.getX() + deltaX);
    circle.setY(circle.getY() + deltaY);
        
    // code to assign a new reference to circle
    circle = new Circle(0, 0);
}
```

Copy

Let the method be invoked with these arguments:

```java
moveCircle(myCircle, 23, 56)
```

Copy

Inside the method, `circle` initially refers to `myCircle`. The method changes the `x` and `y` coordinates of the object that circle references (that is, `myCircle`) by 23 and 56, respectively. These changes will persist when the method returns. Then `circle` is assigned a reference to a new `Circle` object with `x = y = 0`. This reassignment has no permanence, however, because the reference was passed in by value and cannot change. Within the method, the object pointed to by `circle` has changed, but, when the method returns, `myCircle` still references the same `Circle` object as before the method was called.

# Creating and Using Objects

 

## Understanding What Objects Are

A typical Java program creates many objects, which as you know, interact by invoking methods. Through these object interactions, a program can carry out various tasks, such as implementing a GUI, running an animation, or sending and receiving information over a network. Once an object has completed the work for which it was created, its resources are recycled for use by other objects.

Here is a small program, called `CreateObjectDemo`, that creates three objects: one `Point` object and two `Rectangle` objects. You will need all three source files to compile this program.

```java
public class CreateObjectDemo {

    public static void main(String[] args) {
        
        // Declare and create a point object and two rectangle objects.
        Point originOne = new Point(23, 94);
        Rectangle rectOne = new Rectangle(originOne, 100, 200);
        Rectangle rectTwo = new Rectangle(50, 100);
        
        // display rectOne's width, height, and area
        System.out.println("Width of rectOne: " + rectOne.width);
        System.out.println("Height of rectOne: " + rectOne.height);
        System.out.println("Area of rectOne: " + rectOne.getArea());
        
        // set rectTwo's position
        rectTwo.origin = originOne;
        
        // display rectTwo's position
        System.out.println("X Position of rectTwo: " + rectTwo.origin.x);
        System.out.println("Y Position of rectTwo: " + rectTwo.origin.y);
        
        // move rectTwo and display its new position
        rectTwo.move(40, 72);
        System.out.println("X Position of rectTwo: " + rectTwo.origin.x);
        System.out.println("Y Position of rectTwo: " + rectTwo.origin.y);
    }
}
```

Copy

Here is the `Point` class:

```java
public class Point {
    public int x = 0;
    public int y = 0;
    // a constructor!
    public Point(int a, int b) {
    x = a;
    y = b;
    }
}
```

Copy

And the `Rectangle` class:

```java
public class Rectangle {
    public int width = 0;
    public int height = 0;
    public Point origin;
 
    // four constructors
    public Rectangle() {
    origin = new Point(0, 0);
    }
    public Rectangle(Point p) {
    origin = p;
    }
    public Rectangle(int w, int h) {
    origin = new Point(0, 0);
    width = w;
    height = h;
    }
    public Rectangle(Point p, int w, int h) {
    origin = p;
    width = w;
    height = h;
    }
 
    // a method for moving the rectangle
    public void move(int x, int y) {
    origin.x = x;
    origin.y = y;
    }
 
    // a method for computing the area of the rectangle
    public int getArea() {
    return width * height;
    }
}
```

Copy

This program creates, manipulates, and displays information about various objects. Here's the output:

```shell
Width of rectOne: 100
Height of rectOne: 200
Area of rectOne: 20000
X Position of rectTwo: 23
Y Position of rectTwo: 94
X Position of rectTwo: 40
Y Position of rectTwo: 72
```

Copy

The following three sections use the above example to describe the life cycle of an object within a program. From them, you will learn how to write code that creates and uses objects in your own programs. You will also learn how the system cleans up after an object when its life has ended.

 

## Creating Objects

As you know, a class provides the blueprint for objects; you create an object from a class. Each of the following statements taken from the `CreateObjectDemo` program creates an object and assigns it to a variable:

```shell
Point originOne = new Point(23, 94);
Rectangle rectOne = new Rectangle(originOne, 100, 200);
Rectangle rectTwo = new Rectangle(50, 100);
```

Copy

The first line creates an object of the `Point` class, and the second and third lines each create an object of the `Rectangle` class.

Each of these statements has three parts (discussed in detail below):

1. Declaration: The code set in bold are all variable declarations that associate a variable name with an object type.
2. Instantiation: The `new` keyword is a Java operator that creates the object.
3. Initialization: The `new` operator is followed by a call to a constructor, which initializes the new object.

### Declaring a Variable to Refer to an Object

Previously, you learned that to declare a variable, you write:

```java
type name;
```

Copy

This notifies the compiler that you will use name to refer to data whose type is type. With a primitive variable, this declaration also reserves the proper amount of memory for the variable.

You can also declare a reference variable on its own line. For example:

```java
Point originOne;
```

Copy

If you declare `originOne` like this, its value will be undetermined until an object is actually created and assigned to it. Simply declaring a reference variable does not create an object. For that, you need to use the `new` operator, as described in the next section. You must assign an object to `originOne` before you use it in your code. Otherwise, you will get a compiler error.

A variable in this state, currently references no object.

### Instantiating a Class

The `new` operator instantiates a class by allocating memory for a new object and returning a reference to that memory. The `new` operator also invokes the object constructor.

> Note: The phrase "instantiating a class" means the same thing as "creating an object." When you create an object, you are creating an "instance" of a class, therefore "instantiating" a class.

The `new` operator requires a single, postfix argument: a call to a constructor. The name of the constructor provides the name of the class to instantiate.

The `new` operator returns a reference to the object it created. This reference is usually assigned to a variable of the appropriate type, like:

```java
Point originOne = new Point(23, 94);
```

Copy

The reference returned by the `new` operator does not have to be assigned to a variable. It can also be used directly in an expression. For example:

```java
int height = new Rectangle().height;
```

Copy

This statement will be discussed in the next section.

### Initializing an Object

Here is the code for the `Point` class:

```java
public class Point {
    public int x = 0;
    public int y = 0;
    //constructor
    public Point(int a, int b) {
        x = a;
        y = b;
    }
}
```

Copy

This class contains a single constructor. You can recognize a constructor because its declaration uses the same name as the class and it has no return type. The constructor in the `Point` class takes two integer arguments, as declared by the code `(int a, int b)`. The following statement provides 23 and 94 as values for those arguments:

```java
Point originOne = new Point(23, 94);
```

Copy

The result of executing this statement can be illustrated in the next figure:

![A Point Object](https://dev.java/assets/images/classes-objects/01_new-object.png)

A Point Object

Here is the code for the `Rectangle` class, which contains four constructors:

```java
public class Rectangle {
    public int width = 0;
    public int height = 0;
    public Point origin;

    // four constructors
    public Rectangle() {
        origin = new Point(0, 0);
    }
    
    public Rectangle(Point p) {
        origin = p;
    }
    
    public Rectangle(int w, int h) {
        origin = new Point(0, 0);
        width = w;
        height = h;
    }
    
    public Rectangle(Point p, int w, int h) {
        origin = p;
        width = w;
        height = h;
    }

    // a method for moving the rectangle
    public void move(int x, int y) {
        origin.x = x;
        origin.y = y;
    }

    // a method for computing the area of the rectangle
    public int getArea() {
        return width * height;
    }
}
```

Copy

Each constructor lets you provide initial values for the rectangle's `origin`, `width`, and `height`, using both primitive and reference types. If a class has multiple constructors, they must have different signatures. The Java compiler differentiates the constructors based on the number and the type of the arguments. When the Java compiler encounters the following code, it knows to call the constructor in the `Rectangle` class that requires a `Point` argument followed by two integer arguments:

```java
Rectangle rectOne = new Rectangle(originOne, 100, 200);
```

Copy

This calls one of `Rectangle`'s constructors that initializes origin to `originOne`. Also, the constructor sets width to 100 and height to 200. Now there are two references to the same `Point` object—an object can have multiple references to it, as shown in the next figure:

![A Rectangle Object](https://dev.java/assets/images/classes-objects/02_rectangle-object.png)

A Rectangle Object

The following line of code calls the `Rectangle` constructor that requires two integer arguments, which provide the initial values for `width` and `height`. If you inspect the code within the constructor, you will see that it creates a new `Point` object whose `x` and `y` values are initialized to 0:

```java
Rectangle rectTwo = new Rectangle(50, 100);
```

Copy

The `Rectangle` constructor used in the following statement does not take any arguments, so it is called a no-argument constructor:

```java
Rectangle rect = new Rectangle();
```

Copy

All classes have at least one constructor. If a class does not explicitly declare any, the Java compiler automatically provides a no-argument constructor, called the default constructor. This default constructor calls the class parent's no-argument constructor, or the `Object` constructor if the class has no other parent. If the parent has no constructor (`Object` does have one), the compiler will reject the program.

 

## Using Objects

Once you have created an object, you probably want to use it for something. You may need to use the value of one of its fields, change one of its fields, or call one of its methods to perform an action.

### Referencing an Object's Fields

Object fields are accessed by their name. You must use a name that is unambiguous.

You may use a simple name for a field within its own class. For example, we can add a statement within the `Rectangle` class that prints the `width` and `height`:

```java
System.out.println("Width and height are: " + width + ", " + height);
```

Copy

In this case, `width` and `height` are simple names.

Code that is outside the object's class must use an object reference or expression, followed by the dot (`.`) operator, followed by a simple field name, as in:

```java
objectReference.fieldName
```

Copy

For example, the code in the `CreateObjectDemo` class is outside the code for the `Rectangle` class. So to refer to the `origin`, `width`, and `height` fields within the `Rectangle` object named `rectOne`, the `CreateObjectDemo` class must use the names `rectOne.origin`, `rectOne.width`, and `rectOne.height`, respectively. The program uses two of these names to display the `width` and the `height` of `rectOne`:

```java
System.out.println("Width of rectOne: "  + rectOne.width);
System.out.println("Height of rectOne: " + rectOne.height);
```

Copy

Attempting to use the simple names `width` and `height` from the code in the `CreateObjectDemo` class does not make sense — those fields exist only within an object — and results in a compiler error.

Later, the program uses similar code to display information about `rectTwo`. Objects of the same type have their own copy of the same instance fields. Thus, each `Rectangle` object has fields named `origin`, `width`, and `height`. When you access an instance field through an object reference, you reference that particular object's field. The two objects `rectOne` and `rectTwo` in the `CreateObjectDemo` program have different `origin`, `width`, and `height` fields.

To access a field, you can use a named reference to an object, as in the previous examples, or you can use any expression that returns an object reference. Recall that the `new` operator returns a reference to an object. So you could use the value returned from new to access a new object's fields:

```java
int height = new Rectangle().height;
```

Copy

This statement creates a new `Rectangle` object and immediately gets its `height`. In essence, the statement calculates the default height of a `Rectangle`. Note that after this statement has been executed, the program no longer has a reference to the created `Rectangle`, because the program never stored the reference anywhere. The object is unreferenced, and its resources are free to be recycled by the Java Virtual Machine.

### Calling an Object's Methods

You also use an object reference to invoke an object's method. You append the method's simple name to the object reference, with an intervening dot operator (`.`). Also, you provide, within enclosing parentheses, any arguments to the method. If the method does not require any arguments, use empty parentheses.

```java
objectReference.methodName(argumentList);
```

Copy

or:

```java
objectReference.methodName();
```

Copy

The `Rectangle` class has two methods: `getArea()` to compute the rectangle's area and `move()` to change the rectangle's origin. Here's the `CreateObjectDemo` code that invokes these two methods:

```java
System.out.println("Area of rectOne: " + rectOne.getArea());
...
rectTwo.move(40, 72);
```

Copy

The first statement invokes `rectOne`'s `getArea()` method and displays the results. The second line moves `rectTwo` because the `move()` method assigns new values to the object's `origin.x` and `origin.y`.

As with instance fields, `objectReference` must be a reference to an object. You can use a variable name, but you also can use any expression that returns an object reference. The `new` operator returns an object reference, so you can use the value returned from `new` to invoke a new object's methods:

```java
new Rectangle(100, 50).getArea()
```

Copy

The expression `new Rectangle(100, 50)` returns an object reference that refers to a `Rectangle` object. As shown, you can use the dot notation to invoke the new `Rectangle`'s `getArea()` method to compute the area of the new rectangle.

Some methods, such as `getArea()`, return a value. For methods that return a value, you can use the method invocation in expressions. You can assign the return value to a variable, use it to make decisions, or control a loop. This code assigns the value returned by `getArea()` to the variable `areaOfRectangle`:

```java
int areaOfRectangle = new Rectangle(100, 50).getArea();
```

Copy

In this case, the object that `getArea()` is invoked on is the rectangle returned by the constructor.

 

## The Garbage Collector

Some object-oriented languages require that you keep track of all the objects you create and that you explicitly destroy them when they are no longer needed. Managing memory explicitly is tedious and error-prone. The Java platform allows you to create as many objects as you want (limited, of course, by what your system can handle), and you do not have to worry about destroying them. The Java runtime environment deletes objects when it determines that they are no longer being used. This process is called garbage collection.

An object is eligible for garbage collection when there are no more references to that object. References that are held in a variable are usually dropped when the variable goes out of scope. Or, you can explicitly drop an object reference by setting the variable to the special value `null`. Remember that a program can have multiple references to the same object; all references to an object must be dropped before the object is eligible for garbage collection.

The Java runtime environment has a garbage collector that periodically frees the memory used by objects that are no longer referenced. The garbage collector does its job automatically when it determines that the time is right.

# More on Classes

 

## More on Classes

This section covers more aspects of classes that depend on using object references and the dot operator that you learned about in the preceding sections on objects:

- Returning values from methods.
- The `this` keyword.
- Class vs. instance members.
- Access control.

 

## Returning a Value from a Method

A method returns to the code that invoked it when it

- completes all the statements in the method,
- reaches a `return` statement, or
- throws an exception (covered later),
- whichever occurs first.

You declare a method's return type in its method declaration. Within the body of the method, you use the `return` statement to return the value.

Any method declared `void` does not return a value. It does not need to contain a `return` statement, but it may do so. In such a case, a `return` statement can be used to branch out of a control flow block and exit the method and is simply used like this:

```java
return;
```

Copy

If you try to return a value from a method that is declared `void`, you will get a compiler error.

Any method that is not declared `void` must contain a `return` statement with a corresponding return value, like this:

```java
return returnValue;
```

Copy

The data type of the return value must match the method's declared return type; you cannot return an integer value from a method declared to return a `boolean`.

The `getArea()` method in the `Rectangle` class that was discussed in the sections on objects returns an integer:

```java
// a method for computing the area of the rectangle
public int getArea() {
    return width * height;
}
```

Copy

This method returns the integer that the expression `width*height` evaluates to.

The `getArea()` method returns a primitive type. A method can also return a reference type. For example, in a program to manipulate `Bicycle` objects, we might have a method like this:

```java
public Bicycle seeWhosFastest(Bicycle myBike, Bicycle yourBike, Environment env) {
    Bicycle fastest;
    // code to calculate which bike is 
    // faster, given each bike's gear 
    // and cadence and given the 
    // environment (terrain and wind)
    return fastest;
}
```

Copy

 

## Returning a Class or Interface

If this section confuses you, skip it and return to it after you have finished the section on interfaces and inheritance.

When a method uses a class name as its return type, such as `seeWhosFastest()` does, the class of the type of the returned object must be either a subclass of, or the exact class of, the return type. Suppose that you have a class hierarchy in which `ImaginaryNumber` is a subclass of `java.lang.Number`, which is in turn a subclass of `Object`, as illustrated in the following figure.

![The class hierarchy for `ImaginaryNumber`](https://dev.java/assets/images/classes-objects/03_class-hierarchy-imaginary.png)

The class hierarchy for `ImaginaryNumber`

Now suppose that you have a method declared to return a `Number`:

```java
public Number returnANumber() {
    ...
}
```

Copy

The `returnANumber()` method can return an `ImaginaryNumber` but not an `Object`. An instance of `ImaginaryNumber` is also an instance of `Number` because `ImaginaryNumber` a subclass of `Number`. However, an `Object` is not necessarily a `Number` — it could be a `String` or another type.

You can override a method and define it to return a subclass of the original method, like this:

```java
public ImaginaryNumber returnANumber() {
    ...
}
```

Copy

This technique, called _covariant return type_, means that the return type is allowed to vary in the same direction as the subclass.

> Note: You also can use interface names as return types. In this case, the object returned must implement the specified interface.

 

## Using the this Keyword

Within an instance method or a constructor, this is a reference to the _current object_ — the object whose method or constructor is being called. You can refer to any member of the current object from within an instance method or a constructor by using `this`.

### Using this with a Field

The most common reason for using the `this` keyword is because a field is shadowed by a method or constructor parameter.

For example, the `Point` class was written like this:

```java
public class Point {
    public int x = 0;
    public int y = 0;
        
    //constructor
    public Point(int a, int b) {
        x = a;
        y = b;
    }
}
```

Copy

but it could have been written like this:

```java
public class Point {
    public int x = 0;
    public int y = 0;
        
    //constructor
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

Copy

Each argument to the constructor shadows one of the object's fields — inside the constructor `x` is a local copy of the constructor's first argument. To refer to the `Point` field `x`, the constructor must use `this.x`.

### Using this with a Constructor

From within a constructor, you can also use the `this` keyword to call another constructor in the same class. Doing so is called an explicit constructor invocation. Here is another `Rectangle` class, with a different implementation from the one in the Objects section.

```java
public class Rectangle {
    private int x, y;
    private int width, height;
        
    public Rectangle() {
        this(0, 0, 1, 1);
    }
    public Rectangle(int width, int height) {
        this(0, 0, width, height);
    }
    public Rectangle(int x, int y, int width, int height) {
        this.x = x;
        this.y = y;
        this.width = width;
        this.height = height;
    }
    ...
}
```

Copy

This class contains a set of constructors. Each constructor initializes some or all of the rectangle's member variables. The constructors provide a default value for any member variable whose initial value is not provided by an argument. For example, the no-argument constructor creates a 1x1 Rectangle at coordinates 0,0. The two-argument constructor calls the four-argument constructor, passing in the `width` and `height` but always using the 0,0 coordinates. As before, the compiler determines which constructor to call, based on the number and the type of arguments.

If present, the invocation of another constructor must be the first line in the constructor.

 

## Controlling Access to Members of a Class

Access level modifiers determine whether other classes can use a particular field or invoke a particular method. There are two levels of access control:

- At the top level—`public`, or package-private (no explicit modifier).
- At the member level—`public`, `private`, `protected`, or package-private (no explicit modifier).

A class may be declared with the modifier `public`, in which case that class is visible to all classes everywhere. If a class has no modifier (the default, also known as package-private), it is visible only within its own package (packages are named groups of related classes — you will learn about them in a later section.)

At the member level, you can also use the `public` modifier or no modifier (package-private) just as with top-level classes, and with the same meaning. For members, there are two additional access modifiers: `private` and `protected`. The `private` modifier specifies that the member can only be accessed in its own class. The `protected` modifier specifies that the member can only be accessed within its own package (as with package-private) and, in addition, by a subclass of its class in another package.

The following table shows the access to members permitted by each modifier.

|Modifier|Class|Package|Subclass|World|
|---|---|---|---|---|
|`public`|Y|Y|Y|Y|
|`protected`|Y|Y|Y|N|
|_no modifier_|Y|Y|N|N|
|`private`|Y|N|N|N|

The first data column indicates whether the class itself has access to the member defined by the access level. As you can see, a class always has access to its own members.

The second column indicates whether classes in the same package as the class (regardless of their parentage) have access to the member.

The third column indicates whether subclasses of the class declared outside this package have access to the member.

The fourth column indicates whether all classes have access to the member.

Access levels affect you in two ways. First, when you use classes that come from another source, such as the classes in the Java platform, access levels determine which members of those classes your own classes can use. Second, when you write a class, you need to decide what access level every member variable and every method in your class should have.

### Tips on Choosing an Access Level:

If other programmers use your class, you want to ensure that errors from misuse cannot happen. Access levels can help you do this.

Use the most restrictive access level that makes sense for a particular member. Use `private` unless you have a good reason not to.

Avoid `public` fields except for constants. Many of the examples in the tutorial use `public` fields. This may help to illustrate some points concisely, but is not recommended for production code. This is not a good practice because `public` fields tend to link you to a particular implementation and limit your flexibility in changing your code.

 

## Understanding Class Members

In this section, we discuss the use of the `static` keyword to create fields and methods that belong to the class, rather than to an instance of the class.

### Class Variables

When a number of objects are created from the same class blueprint, they each have their own distinct copies of instance variables. In the case of the `Bicycle` class, the instance variables are `cadence`, `gear`, and `speed`. Each `Bicycle` object has its own values for these variables, stored in different memory locations.

Sometimes, you want to have variables that are common to all objects. This is accomplished with the `static` modifier. Fields that have the `static` modifier in their declaration are called `static` fields or _class variables_. They are associated with the class, rather than with any object.

Every instance of the class shares a class variable, which is in one fixed location in memory. Any object can change the value of a class variable, but class variables can also be manipulated without creating an instance of the class.

For example, suppose you want to create a number of `Bicycle` objects and assign each a serial number, beginning with 1 for the first object. This `ID` number is unique to each object and is therefore an instance variable. At the same time, you need a field to keep track of how many `Bicycle` objects have been created so that you know what `ID` to assign to the next one. Such a field is not related to any individual object, but to the class as a whole. For this you need a class variable, `numberOfBicycles`, as follows:

```java
public class Bicycle {
        
    private int cadence;
    private int gear;
    private int speed;
        
    // add an instance variable for the object ID
    private int id;
    
    // add a class variable for the
    // number of Bicycle objects instantiated
    private static int numberOfBicycles = 0;
        ...
}
```

Copy

Class variables are referenced by the class name itself, as in

```java
Bicycle.numberOfBicycles
```

Copy

This makes it clear that they are class variables.

> Note: You can also refer to static fields with an object reference like `myBike.numberOfBicycles` but this is discouraged because it does not make it clear that they are class variables.

You can use the `Bicycle` constructor to set the `ID` instance variable and increment the `numberOfBicycles` class variable:

```java
public class Bicycle {
        
    private int cadence;
    private int gear;
    private int speed;
    private int id;
    private static int numberOfBicycles = 0;
        
    public Bicycle(int startCadence, int startSpeed, int startGear){
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;

        // increment number of Bicycles
        // and assign ID number
        id = ++numberOfBicycles;
    }

    // new method to return the ID instance variable
    public int getID() {
        return id;
    }
        ...
}
```

Copy

### Class Methods

The Java programming language supports static methods as well as static variables. Static methods, which have the `static` modifier in their declarations, should be invoked with the class name, without the need for creating an instance of the class, as in

```java
ClassName.methodName(args)
```

Copy

> Note: You can also refer to static methods with an object reference like `instanceName.methodName(args)` but this is discouraged because it does not make it clear that they are class methods.

A common use for static methods is to access static fields. For example, we could add a static method to the `Bicycle` class to access the `numberOfBicycles` static field:

```java
public static int getNumberOfBicycles() {
    return numberOfBicycles;
}
```

Copy

Not all combinations of instance and class variables and methods are allowed:

- Instance methods can access instance variables and instance methods directly.
- Instance methods can access class variables and class methods directly.
- Class methods can access class variables and class methods directly.
- Class methods cannot access instance variables or instance methods directly—they must use an object reference. Also, class methods cannot use the `this` keyword as there is no instance for this to refer to.

### Constants

The `static` modifier, in combination with the `final` modifier, is also used to define constants. The `final` modifier indicates that the value of this field cannot change.

For example, the following variable declaration defines a constant named `PI`, whose value is an approximation of pi (the ratio of the circumference of a circle to its diameter):

```java
static final double PI = 3.141592653589793;
```

Copy

Constants defined in this way cannot be reassigned, and it is a compile-time error if your program tries to do so. By convention, the names of constant values are spelled in uppercase letters. If the name is composed of more than one word, the words are separated by an underscore (`_`).

> Note: If a primitive type or a string is defined as a constant and the value is known at compile time, the compiler replaces the constant name everywhere in the code with its value. This is called a compile-time constant. If the value of the constant in the outside world changes (for example, if it is legislated that pi actually should be 3.975), you will need to recompile any classes that use this constant to get the current value.

### The Bicycle Class

After all the modifications made in this section, the `Bicycle` class is now:

```java
public class Bicycle {
        
    private int cadence;
    private int gear;
    private int speed;
        
    private int id;
    
    private static int numberOfBicycles = 0;

        
    public Bicycle(int startCadence,
                   int startSpeed,
                   int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;

        id = ++numberOfBicycles;
    }

    public int getID() {
        return id;
    }

    public static int getNumberOfBicycles() {
        return numberOfBicycles;
    }

    public int getCadence() {
        return cadence;
    }
        
    public void setCadence(int newValue) {
        cadence = newValue;
    }
        
    public int getGear(){
        return gear;
    }
        
    public void setGear(int newValue) {
        gear = newValue;
    }
        
    public int getSpeed() {
        return speed;
    }
        
    public void applyBrake(int decrement) {
        speed -= decrement;
    }
        
    public void speedUp(int increment) {
        speed += increment;
    }
}
```

Copy

 

## Initializing Fields

As you have seen, you can often provide an initial value for a field in its declaration:

```java
public class BedAndBreakfast {

    // initialize to 10
    public static int capacity = 10;

    // initialize to false
    private boolean full = false;
}
```

Copy

This works well when the initialization value is available and the initialization can be put on one line. However, this form of initialization has limitations because of its simplicity. If initialization requires some logic (for example, error handling or a for loop to fill a complex array), simple assignment is inadequate. Instance variables can be initialized in constructors, where error handling or other logic can be used. To provide the same capability for class variables, the Java programming language includes _static initialization blocks_.

> Note: It is not necessary to declare fields at the beginning of the class definition, although this is the most common practice. It is only necessary that they be declared and initialized before they are used.

### Static Initialization Blocks

A static initialization block is a normal block of code enclosed in braces, `{ }`, and preceded by the `static` keyword. Here is an example:

```java
static {
    // whatever code is needed for initialization goes here
}
```

Copy

A class can have any number of static initialization blocks, and they can appear anywhere in the class body. The runtime system guarantees that static initialization blocks are called in the order that they appear in the source code.

There is an alternative to static blocks — you can write a private static method:

```java
class Whatever {
    public static varType myVar = initializeClassVariable();
        
    private static varType initializeClassVariable() {

        // initialization code goes here
    }
}
```

Copy

The advantage of private static methods is that they can be reused later if you need to reinitialize the class variable.

You should be aware that you cannot redefine the content of a static block. Once it has been written, you cannot prevent this block to be executed. If the content of the static block cannot be executed for whatever reason, then your application will not work properly, because you will not be able to instantiate any object for this class. This may happen if your static block contains code that accesses some external resource, like a file system, or a network.

### Initializing Instance Members

Normally, you would put code to initialize an instance variable in a constructor. There are two alternatives to using a constructor to initialize instance variables: initializer blocks and final methods.

Initializer blocks for instance variables look just like static initializer blocks, but without the static keyword:

```java
{
    // whatever code is needed for initialization goes here
}
```

Copy

The Java compiler copies initializer blocks into every constructor. Therefore, this approach can be used to share a block of code between multiple constructors.

A _final method_ cannot be overridden in a subclass. This is discussed in the section on [Inheritance](https://dev.java/learn/numbers-strings/strings/). Here is an example of using a final method for initializing an instance variable:

```java
class Whatever {
    private varType myVar = initializeInstanceVariable();
        
    protected final varType initializeInstanceVariable() {

        // initialization code goes here
    }
}
```

Copy

This is especially useful if subclasses might want to reuse the initialization method. The method is final because calling non-final methods during instance initialization can cause problems.

 

## Summary of Creating and Using Classes and Objects

A class declaration names the class and encloses the class body between braces. The class name can be preceded by modifiers. The class body contains fields, methods, and constructors for the class. A class uses fields to contain state information and uses methods to implement behavior. Constructors that initialize a new instance of a class use the name of the class and look like methods without a return type.

You control access to classes and members in the same way: by using an access modifier such as public in their declaration.

You specify a class variable or a class method by using the `static` keyword in the member's declaration. A member that is not declared as `static` is implicitly an instance member. Class variables are shared by all instances of a class and can be accessed through the class name as well as an instance reference. Instances of a class get their own copy of each instance variable, which must be accessed through an instance reference.

You create an object from a class by using the `new` operator and a constructor. The `new` operator returns a reference to the object that was created. You can assign the reference to a variable or use it directly.

Instance variables and methods that are accessible to code outside of the class that they are declared in can be referred to by using a qualified name. The qualified name of an instance variable looks like this:

```java
objectReference.variableName
```

Copy

The qualified name of a method looks like this:

```java
objectReference.methodName(argumentList)
```

Copy

or:

```java
objectReference.methodName()
```

Copy

The garbage collector automatically cleans up unused objects. An object is unused if the program holds no more references to it. You can explicitly drop a reference by setting the variable holding the reference to `null`.

# Nested Classes

 

## Nested Classes

The Java programming language allows you to define a class within another class. Such a class is called a nested class and is illustrated here:

```java
class OuterClass {
    ...
    class NestedClass {
        ...
    }
}
```

Copy

> Terminology: Nested classes are divided into two categories: non-static and static. Non-static nested classes are called _inner classes_. Nested classes that are declared static are called _static nested classes_.

```java
class OuterClass {
    ...
    class InnerClass {
        ...
    }
    static class StaticNestedClass {
        ...
    }
}
```

Copy

A nested class is a member of its enclosing class. Non-static nested classes (inner classes) have access to other members of the enclosing class, even if they are declared `private`. Static nested classes do not have access to other members of the enclosing class. As a member of the `OuterClass`, a nested class can be declared `private`, `public`, `protected`, or package private. Recall that outer classes can only be declared `public` or package private.

### Why Use Nested Classes?

Compelling reasons for using nested classes include the following:

- It is a way of logically grouping classes that are only used in one place: If a class is useful to only one other class, then it is logical to embed it in that class and keep the two together. Nesting such "helper classes" makes their package more streamlined.
- It increases encapsulation: Consider two top-level classes, `A` and `B`, where `B` needs access to members of `A` that would otherwise be declared private. By hiding class `B` within class `A`, `A`'s members can be declared `private` and `B` can access them. In addition, `B` itself can be hidden from the outside world.
- It can lead to more readable and maintainable code: Nesting small classes within top-level classes places the code closer to where it is used.

### Inner Classes

As with instance methods and variables, an inner class is associated with an instance of its enclosing class and has direct access to that object's methods and fields. Also, because an inner class is associated with an instance, it cannot define any static members itself.

Objects that are instances of an inner class exist within an instance of the outer class. Consider the following classes:

```java
class OuterClass {
    ...
    class InnerClass {
        ...
    }
}
```

Copy

An instance of `InnerClass` can exist only within an instance of `OuterClass` and has direct access to the methods and fields of its enclosing instance.

To instantiate an inner class, you must first instantiate the outer class. Then, create the inner object within the outer object with this syntax:

```java
OuterClass outerObject = new OuterClass();
OuterClass.InnerClass innerObject = outerObject.new InnerClass();
```

Copy

There are two special kinds of inner classes: local classes and anonymous classes.

### Static Nested Classes

As with class methods and variables, a static nested class is associated with its outer class. And like static class methods, a static nested class cannot refer directly to instance variables or methods defined in its enclosing class: it can use them only through an object reference. Inner Class and Nested Static Class Example demonstrates this.

> Note: A static nested class interacts with the instance members of its outer class (and other classes) just like any other top-level class. In effect, a static nested class is behaviorally a top-level class that has been nested in another top-level class for packaging convenience. Inner Class and Nested Static Class Example also demonstrates this.

You instantiate a static nested class the same way as a top-level class:

```java
StaticNestedClass staticNestedObject = new StaticNestedClass();
```

Copy

### Inner Class and Nested Static Class Example

The following example, `OuterClass`, along with `TopLevelClass`, demonstrates which class members of `OuterClass` an inner class (`InnerClass`), a nested static class (`StaticNestedClass`), and a top-level class (`TopLevelClass`) can access:

#### OuterClass.java

```java
public class OuterClass {

    String outerField = "Outer field";
    static String staticOuterField = "Static outer field";

    class InnerClass {
        void accessMembers() {
            System.out.println(outerField);
            System.out.println(staticOuterField);
        }
    }

    static class StaticNestedClass {
        void accessMembers(OuterClass outer) {
            // Compiler error: Cannot make a static reference to the non-static
            //     field outerField
            // System.out.println(outerField);
            System.out.println(outer.outerField);
            System.out.println(staticOuterField);
        }
    }

    public static void main(String[] args) {
        System.out.println("Inner class:");
        System.out.println("------------");
        OuterClass outerObject = new OuterClass();
        OuterClass.InnerClass innerObject = outerObject.new InnerClass();
        innerObject.accessMembers();

        System.out.println("\nStatic nested class:");
        System.out.println("--------------------");
        StaticNestedClass staticNestedObject = new StaticNestedClass();
        staticNestedObject.accessMembers(outerObject);

        System.out.println("\nTop-level class:");
        System.out.println("--------------------");
        TopLevelClass topLevelObject = new TopLevelClass();
        topLevelObject.accessMembers(outerObject);
    }
}
```

Copy

#### TopLevelClass.java

```java
public class TopLevelClass {

    void accessMembers(OuterClass outer) {
        // Compiler error: Cannot make a static reference to the non-static
        //     field OuterClass.outerField
        // System.out.println(OuterClass.outerField);
        System.out.println(outer.outerField);
        System.out.println(OuterClass.staticOuterField);
    }
}
```

Copy

This example prints the following output:

```shell
Inner class:
------------
Outer field
Static outer field

Static nested class:
--------------------
Outer field
Static outer field

Top-level class:
--------------------
Outer field
Static outer field
```

Copy

Note that a static nested class interacts with the instance members of its outer class just like any other top-level class. The static nested class `StaticNestedClass` cannot directly access `outerField` because it is an instance variable of the enclosing class, `OuterClass`. The Java compiler generates an error at the highlighted statement:

```java
static class StaticNestedClass {
    void accessMembers(OuterClass outer) {
       // Compiler error: Cannot make a static reference to the non-static
       //     field outerField
       System.out.println(outerField);
    }
}
```

Copy

To fix this error, access `outerField` through an object reference:

```java
System.out.println(outer.outerField);
```

Copy

Similarly, the top-level class `TopLevelClass` cannot directly access `outerField` either.

### Shadowing

If a declaration of a type (such as a member variable or a parameter name) in a particular scope (such as an inner class or a method definition) has the same name as another declaration in the enclosing scope, then the declaration shadows the declaration of the enclosing scope. You cannot refer to a shadowed declaration by its name alone. The following example, `ShadowTest`, demonstrates this:

```java
public class ShadowTest {

    public int x = 0;

    class FirstLevel {

        public int x = 1;

        void methodInFirstLevel(int x) {
            System.out.println("x = " + x);
            System.out.println("this.x = " + this.x);
            System.out.println("ShadowTest.this.x = " + ShadowTest.this.x);
        }
    }

    public static void main(String... args) {
        ShadowTest st = new ShadowTest();
        ShadowTest.FirstLevel fl = st.new FirstLevel();
        fl.methodInFirstLevel(23);
    }
}
```

Copy

The following is the output of this example:

```java
x = 23
this.x = 1
ShadowTest.this.x = 0
```

Copy

This example defines three variables named `x`: the member variable of the class `ShadowTest`, the member variable of the inner class `FirstLevel`, and the parameter in the method `methodInFirstLevel()`. The variable `x` defined as a parameter of the method `methodInFirstLevel()` shadows the variable of the inner class `FirstLevel`. Consequently, when you use the variable `x` in the method `methodInFirstLevel()`, it refers to the method parameter. To refer to the member variable of the inner class `FirstLevel`, use the keyword `this` to represent the enclosing scope:

```java
System.out.println("this.x = " + this.x);
```

Copy

Refer to member variables that enclose larger scopes by the class name to which they belong. For example, the following statement accesses the member variable of the class `ShadowTest` from the method `methodInFirstLevel()`:

```java
System.out.println("ShadowTest.this.x = " + ShadowTest.this.x);
```

Copy

### Serialization

Serialization of inner classes, including local and anonymous classes, is strongly discouraged. When the Java compiler compiles certain constructs, such as inner classes, it creates synthetic constructs; these are classes, methods, fields, and other constructs that do not have a corresponding construct in the source code. Synthetic constructs enable Java compilers to implement new Java language features without changes to the JVM.

However, synthetic constructs can vary among different Java compiler implementations, which means that `.class` files can vary among different implementations as well. Consequently, you may have compatibility issues if you serialize an inner class and then deserialize it with a different JRE implementation.

 

## Inner Class Example

To see an inner class in use, first consider an array. In the following example, you create an array, fill it with integer values, and then output only values of even indices of the array in ascending order.

The `DataStructure.java` example that follows consists of:

- The `DataStructure` outer class, which includes a constructor to create an instance of `DataStructure` containing an array filled with consecutive integer values (0, 1, 2, 3, and so on) and a method that prints elements of the array that have an even index value.
- The `EvenIterator` inner class, which implements the `DataStructureIterator` interface, which extends the `Iterator< Integer>` interface. Iterators are used to step through a data structure and typically have methods to test for the last element, retrieve the current element, and move to the next element.
- A main method that instantiates a `DataStructure` object (`ds`), then invokes the `printEven()` method to print elements of the array `arrayOfInts` that have an even index value.

```java
public class DataStructure {

    // Create an array
    private final static int SIZE = 15;
    private int[] arrayOfInts = new int[SIZE];

    public DataStructure() {
        // fill the array with ascending integer values
        for (int i = 0; i < SIZE; i++) {
            arrayOfInts[i] = i;
        }
    }

    public void printEven() {

        // Print out values of even indices of the array
        DataStructureIterator iterator = this.new EvenIterator();
        while (iterator.hasNext()) {
            System.out.print(iterator.next() + " ");
        }
        System.out.println();
    }

    interface DataStructureIterator extends java.util.Iterator<Integer> { }

    // Inner class implements the DataStructureIterator interface,
    // which extends the Iterator<Integer> interface

    private class EvenIterator implements DataStructureIterator {

        // Start stepping through the array from the beginning
        private int nextIndex = 0;

        public boolean hasNext() {

            // Check if the current element is the last in the array
            return (nextIndex <= SIZE - 1);
        }

        public Integer next() {

            // Record a value of an even index of the array
            Integer retValue = Integer.valueOf(arrayOfInts[nextIndex]);

            // Get the next even element
            nextIndex += 2;
            return retValue;
        }
    }

    public static void main(String s[]) {

        // Fill the array with integer values and print out only
        // values of even indices
        DataStructure ds = new DataStructure();
        ds.printEven();
    }
}
```

Copy

The output is:

```shell
0 2 4 6 8 10 12 14
```

Copy

Note that the `EvenIterator` class refers directly to the `arrayOfInts` instance variable of the `DataStructure` object.

You can use inner classes to implement helper classes such as the one shown in the this example. To handle user interface events, you must know how to use inner classes, because the event-handling mechanism makes extensive use of them.

### Local and Anonymous Classes

There are two additional types of inner classes. You can declare an inner class within the body of a method. These classes are known as local classes. You can also declare an inner class within the body of a method without naming the class. These classes are known as anonymous classes.

### Modifiers

You can use the same modifiers for inner classes that you use for other members of the outer class. For example, you can use the access specifiers `private`, `public`, and `protected` to restrict access to inner classes, just as you use them to restrict access do to other class members.

 

## Local Classes

Local classes are classes that are defined in a block, which is a group of zero or more statements between balanced braces. You typically find local classes defined in the body of a method.

This section covers the following topics:

- Declaring Local Classes
- Accessing Members of an Enclosing Class
- Shadowing and Local Classes
- Local Classes Are Similar To Inner Classes

### Declaring Local Classes

You can define a local class inside any block (see Expressions, Statements, and Blocks for more information). For example, you can define a local class in a method body, a for loop, or an if clause.

The following example, `LocalClassExample`, validates two phone numbers. It defines the local class `PhoneNumber` in the method `validatePhoneNumber()`:

```java
public class LocalClassExample {

    static String regularExpression = "[^0-9]";

    public static void validatePhoneNumber(
        String phoneNumber1, String phoneNumber2) {

        final int numberLength = 10;

        // Valid in JDK 8 and later:

        // int numberLength = 10;

        class PhoneNumber {

            String formattedPhoneNumber = null;

            PhoneNumber(String phoneNumber){
                // numberLength = 7;
                String currentNumber = phoneNumber.replaceAll(
                  regularExpression, "");
                if (currentNumber.length() == numberLength)
                    formattedPhoneNumber = currentNumber;
                else
                    formattedPhoneNumber = null;
            }

            public String getNumber() {
                return formattedPhoneNumber;
            }

            // Valid in JDK 8 and later:

//            public void printOriginalNumbers() {
//                System.out.println("Original numbers are " + phoneNumber1 +
//                    " and " + phoneNumber2);
//            }
        }

        PhoneNumber myNumber1 = new PhoneNumber(phoneNumber1);
        PhoneNumber myNumber2 = new PhoneNumber(phoneNumber2);

        // Valid in JDK 8 and later:

//        myNumber1.printOriginalNumbers();

        if (myNumber1.getNumber() == null)
            System.out.println("First number is invalid");
        else
            System.out.println("First number is " + myNumber1.getNumber());
        if (myNumber2.getNumber() == null)
            System.out.println("Second number is invalid");
        else
            System.out.println("Second number is " + myNumber2.getNumber());

    }

    public static void main(String... args) {
        validatePhoneNumber("123-456-7890", "456-7890");
    }
}
```

Copy

The example validates a phone number by first removing all characters from the phone number except the digits 0 through 9. After, it checks whether the phone number contains exactly ten digits (the length of a phone number in North America). This example prints the following:

```shell
First number is 1234567890
Second number is invalid
```

Copy

### Accessing Members of an Enclosing Class

A local class has access to the members of its enclosing class. In the previous example, the `PhoneNumber()` constructor accesses the member `LocalClassExample.regularExpression`.

In addition, a local class has access to local variables. However, a local class can only access local variables that are declared `final`. When a local class accesses a local variable or parameter of the enclosing block, it captures that variable or parameter. For example, the `PhoneNumber()` constructor can access the local variable `numberLength` because it is declared `final`; `numberLength` is a captured variable.

However, starting in Java SE 8, a local class can access local variables and parameters of the enclosing block that are `final` or _effectively final_. A variable or parameter whose value is never changed after it is initialized is _effectively final_. For example, suppose that the variable `numberLength` is not declared `final`, and you add the highlighted assignment statement in the `PhoneNumber()` constructor to change the length of a valid phone number to 7 digits:

```java
PhoneNumber(String phoneNumber) {
    numberLength = 7;
    String currentNumber = phoneNumber.replaceAll(
        regularExpression, "");
    if (currentNumber.length() == numberLength)
        formattedPhoneNumber = currentNumber;
    else
        formattedPhoneNumber = null;
}
```

Copy

Because of this assignment statement, the variable `numberLength` is not effectively final anymore. As a result, the Java compiler generates an error message similar to "local variables referenced from an inner class must be final or effectively final" where the inner class `PhoneNumber` tries to access the `numberLength` variable:

```java
if (currentNumber.length() == numberLength)
```

Copy

Starting in Java SE 8, if you declare the local class in a method, it can access the method's parameters. For example, you can define the following method in the `PhoneNumber` local class:

```java
public void printOriginalNumbers() {
    System.out.println("Original numbers are " + phoneNumber1 +
        " and " + phoneNumber2);
}
```

Copy

The method `printOriginalNumbers()` accesses the parameters `phoneNumber1` and `phoneNumber2` of the method `validatePhoneNumber()`.

Declarations of a type (such as a variable) in a local class shadow declarations in the enclosing scope that have the same name. See Shadowing for more information.

### Local Classes Are Similar To Inner Classes

Local classes are similar to inner classes because they cannot define or declare any static members. Local classes in static methods, such as the class `PhoneNumber`, which is defined in the static method `validatePhoneNumber()`, can only refer to static members of the enclosing class. For example, if you do not define the member variable `regularExpression` as `static`, then the Java compiler generates an error similar to "non-static variable regularExpression cannot be referenced from a static context."

Local classes are non-static because they have access to instance members of the enclosing block. Consequently, they cannot contain most kinds of static declarations.

You cannot declare an interface inside a block; interfaces are inherently static. For example, the following code excerpt does not compile because the interface `HelloThere` is defined inside the body of the method `greetInEnglish()`:

```java
public void greetInEnglish() {
    interface HelloThere {
       public void greet();
    }
    class EnglishHelloThere implements HelloThere {
        public void greet() {
            System.out.println("Hello " + name);
        }
    }
    HelloThere myGreeting = new EnglishHelloThere();
    myGreeting.greet();
}
```

Copy

You cannot declare static initializers or member interfaces in a local class. The following code excerpt does not compile because the method `EnglishGoodbye.sayGoodbye()` is declared static. The compiler generates an error similar to "modifier `static` is only allowed in constant variable declaration" when it encounters this method definition:

```java
public void sayGoodbyeInEnglish() {
    class EnglishGoodbye {
        public static void sayGoodbye() {
            System.out.println("Bye bye");
        }
    }
    EnglishGoodbye.sayGoodbye();
}
```

Copy

A local class can have static members provided that they are constant variables. (A constant variable is a variable of primitive type or type `String` that is declared `final` and initialized with a compile-time constant expression. A compile-time constant expression is typically a string or an arithmetic expression that can be evaluated at compile time. See Understanding Class Members for more information.) The following code excerpt compiles because the static member `EnglishGoodbye.farewell` is a constant variable:

```java
public void sayGoodbyeInEnglish() {
    class EnglishGoodbye {
        public static final String farewell = "Bye bye";
        public void sayGoodbye() {
            System.out.println(farewell);
        }
    }
    EnglishGoodbye myEnglishGoodbye = new EnglishGoodbye();
    myEnglishGoodbye.sayGoodbye();
}
```

Copy

 

## Anonymous Classes

Anonymous classes enable you to make your code more concise. They enable you to declare and instantiate a class at the same time. They are like local classes except that they do not have a name. Use them if you need to use a local class only once.

### Declaring Anonymous Classes

While local classes are class declarations, anonymous classes are expressions, which means that you define the class in another expression. The following example, `HelloWorldAnonymousClasses`, uses anonymous classes in the initialization statements of the local variables `frenchGreeting` and `spanishGreeting`, but uses a local class for the initialization of the variable `englishGreeting`:

```java
public class HelloWorldAnonymousClasses {

    interface HelloWorld {
        public void greet();
        public void greetSomeone(String someone);
    }

    public void sayHello() {

        class EnglishGreeting implements HelloWorld {
            String name = "world";
            public void greet() {
                greetSomeone("world");
            }
            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Hello " + name);
            }
        }

        HelloWorld englishGreeting = new EnglishGreeting();

        HelloWorld frenchGreeting = new HelloWorld() {
            String name = "tout le monde";
            public void greet() {
                greetSomeone("tout le monde");
            }
            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Salut " + name);
            }
        };

        HelloWorld spanishGreeting = new HelloWorld() {
            String name = "mundo";
            public void greet() {
                greetSomeone("mundo");
            }
            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Hola, " + name);
            }
        };
        englishGreeting.greet();
        frenchGreeting.greetSomeone("Fred");
        spanishGreeting.greet();
    }

    public static void main(String... args) {
        HelloWorldAnonymousClasses myApp =
            new HelloWorldAnonymousClasses();
        myApp.sayHello();
    }
}
```

Copy

### Syntax of Anonymous Classes

As mentioned previously, an anonymous class is an expression. The syntax of an anonymous class expression is like the invocation of a constructor, except that there is a class definition contained in a block of code.

Consider the instantiation of the `frenchGreeting` object:

```java
HelloWorld frenchGreeting = new HelloWorld() {
    String name = "tout le monde";
    public void greet() {
        greetSomeone("tout le monde");
    }
    public void greetSomeone(String someone) {
        name = someone;
        System.out.println("Salut " + name);
    }
};
```

Copy

The anonymous class expression consists of the following:

- The `new` operator
- The name of an interface to implement or a class to extend. In this example, the anonymous class is implementing the interface `HelloWorld`.
- Parentheses that contain the arguments to a constructor, just like a normal class instance creation expression. Note: When you implement an interface, there is no constructor, so you use an empty pair of parentheses, as in this example.
- A body, which is a class declaration body. More specifically, in the body, method declarations are allowed but statements are not.
- Because an anonymous class definition is an expression, it must be part of a statement. In this example, the anonymous class expression is part of the statement that instantiates the `frenchGreeting` object. (This explains why there is a semicolon after the closing brace.)

### Accessing Local Variables of the Enclosing Scope, and Declaring and Accessing Members of the Anonymous Class

Like local classes, anonymous classes can capture variables; they have the same access to local variables of the enclosing scope:

- An anonymous class has access to the members of its enclosing class.
- An anonymous class cannot access local variables in its enclosing scope that are not declared as final or effectively final.
- Like a nested class, a declaration of a type (such as a variable) in an anonymous class shadows any other declarations in the enclosing scope that have the same name. See Shadowing for more information.

Anonymous classes also have the same restrictions as local classes with respect to their members:

- You cannot declare static initializers or member interfaces in an anonymous class.
- An anonymous class can have static members provided that they are constant variables.

Note that you can declare the following in anonymous classes:

- Fields
- Extra methods (even if they do not implement any methods of the supertype)
- Instance initializers
- Local classes

However, you cannot declare constructors in an anonymous class.

# Using Record to Model Immutable Data

The Java language gives you several ways to create an immutable class. Probably the most straightforward way is to create a final class with final fields and a constructor to initialize these fields. Here is an example of such a class.

```java
public class Point {
    private final int x;
    private final int y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

Copy

Now that you have written these elements, you need to add the accessors for your fields. You will also add a [`toString()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#toString\(\)) method and probably an [`equals()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#equals\(java.lang.Object\)) along with an [`hashCode()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#hashCode\(\)) method. Writing all this by hand is quite tedious and error-prone, fortunately, your IDE is there to generate these methods for you.

If you need to carry the instances of this class from one application to another, either by sending them over a network or through a file system, you may also consider making this class serializable. If you do so, you may need to add some information on how the instances of this class are serialized. The JDK gives you several ways of controlling serialization.

In the end, your `Point` class may be a hundred lines long, mostly populated with code generated by your IDE, just to model an immutable aggregation of two integers that you need to write to a file.

Records have been added to the JDK to change this. Records give you all this with a single line of code. All you need to do is to declare the state of a record; the rest is generated for you by the compiler.

 

## Calling Records to the Rescue

Records are here to help you make this code much simpler. Starting with Java SE 14, you can write the following code.

```java
public record Point(int x, int y) {}
```

Copy

This single line of code creates the following elements for you.

1. It is an immutable class with two fields: `x` and `y`, of type `int`.
2. It has a canonical constructor, to initialize these two fields.
3. The [`toString()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#toString\(\)), [`equals()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#equals\(java.lang.Object\)) and [`hashCode()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#hashCode\(\)) methods have been created for you by the compiler with a default behavior that corresponds to what an IDE would have generated. You can modify this behavior if you need, by adding your own implementations of these methods.
4. It can implement the [`Serializable`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/Serializable.html) interface, so that you can send instances of `Point` to other applications over a network or through a file system. The way a record is serialized and deserialized follows some special rules that are covered at the end of this tutorial.

Records are making the creation of immutable aggregates of data much simpler, without the help of any IDE. It reduces the risk of bugs because everytime you modify the components of a record, the compiler automatically updates the [`equals()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#equals\(java.lang.Object\)) and [`hashCode()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#hashCode\(\)) methods for you.

 

## The Class of a Record

A record is class declared with the `record` keyword instead of the `class` keyword. Let us declare the following record.

```java
public record Point(int x, int y) {}
```

Copy

The class that the compiler creates for you when you create a record is final.

This class extends the [`java.lang.Record`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Record.html) class. So your record cannot extend any class.

A record can implement any number of interfaces.

 

## Declaring the Components of a Record

The block that immediately follows the name of the record is `(int x, int y)`. It declares the _components_ of the record named `Point`. For each component of a record, the compiler creates a private final field with the same name as this component. You can have any number of components declared in a record.

In this example, the compiler creates two private final fields of type `int`: `x` and `y`, corresponding to the two components you have declared.

Along with these fields, the compiler generates one _accessor_ for each component. This accessor is a method that has the same name of the component, and returns its value. In the case of this `Point` record, the two generated methods are the following.

```java
public int x() {
    return this.x;
}

public int y() {
    return this.y;
}
```

Copy

If this implementation works for your application, then you do not need to add anything. You may define your own accessor methods though. It may be useful in the case where you need to return a defensive copy of a particular field.

The last elements generated for you by the compiler are overrides of the [`toString()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#toString\(\)), [`equals()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#equals\(java.lang.Object\)) and [`hashCode()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html#hashCode\(\)) methods from the [`Object`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Object.html) class. You may define your own overrides of these methods if you need.

 

## Things you Cannot Add to a Record

There are three things that you cannot add to a record:

1. You cannot declare any instance field in a record. You cannot add any instance field that would not correspond to a component.
2. You cannot define any field initializer.
3. You cannot add any instance initializer.

You can create static fields with initializers and static initializers.

 

## Constructing a Record with its Canonical Constructor

The compiler also creates a constructor for you, called the _canonical constructor_. This constructor takes the components of your record as arguments and copies their values to the fields of the record class.

There are situations where you need to override this default behavior. Let us examine two use cases:

1. You need to validate the state of your record
2. You need to make a defensive copy of a mutable component.

 

## Using the Compact Constructor

You can use two different syntax to redefine the canonical constructor of a record. You can use a compact constructor or the canonical constructor itself.

Suppose you have the following record.

```java
public record Range(int start, int end) {}
```

Copy

For a record of that name, one could expect that the `end` is greater that the `start`. You can add a validation rule by writing the compact constructor in your record.

```java
public record Range(int start, int end) {

    public Range {
        if (end <= start) {
            throw new IllegalArgumentException("End cannot be lesser than start");
        }
    }
}
```

Copy

The compact canonical constructor does not need to declare its block of parameters.

Note that if you choose this syntax, you cannot directly assign the record's fields, for example with `this.start = start` - that is done for you by code added by the compiler. But you can assign new values to the parameters, which leads to the same result because the compiler-generated code will then assign these new values to the fields.

```java
public Range {
    // set negative start and end to 0
    // by reassigning the compact constructor's
    // implicit parameters
    if (start < 0)
        start = 0;
    if (end < 0)
        end = 0;
}
```

Copy

 

## Using the Canonical Constructor

If you prefer the non-compact form, for example because you prefer not to reassign parameters, you can define the canonical constructor yourself, as in the following example.

```java
public record Range(int start, int end) {

    public Range(int start, int end) {
        if (end <= start) {
            throw new IllegalArgumentException("End cannot be lesser than start");
        }
        if (start < 0) {
            this.start = 0;
        } else {
            this.start = start;
        }
        if (end > 100) {
            this.end = 10;
        } else {
            this.end = end;
        }
    }
}
```

Copy

In this case the constructor you write needs to assign values to the fields of your record.

If the components of your record are not immutable, you should consider making defensive copies of them in both the canonical constructor and the accessors.

 

## Defining any Constructor

You can also add any constructor to a record, as long as this constructor calls the canonical constructor of your record. The syntax is the same as the classic syntax that calls a constructor with another constructor. As for any class, the call to `this()` must be the first statement of your constructor.

Let us examine the following `State` record. It is defined on three components:

1. the name of this state
2. the name of the capital of this state
3. a list of city names, that may be empty.

We need to store a defensive copy of the list of cities, to ensure that it will not be modified from the outside of this record. This can be done by redefining the canonical constructor with a compact form that reassigns the parameter to the defensive copy.

Having a constructor that does not take any city is useful in your application. This can be another constructor, that only takes the state name and the capital city name. This second constructor must call the canonical constructor.

Then, instead of passing a list of cities, you can pass the cities as a vararg. To do that, you can create a third constructor, that must call the canonical constructor with the proper list.

```java
public record State(String name, String capitalCity, List<String> cities) {

    public State {
        // List.copyOf returns an unmodifiable copy,
        // so the list assigned to `cities` can't change anymore
        cities = List.copyOf(cities);
    }

    public State(String name, String capitalCity) {
        this(name, capitalCity, List.of());
    }

    public State(String name, String capitalCity, String... cities) {
        this(name, capitalCity, List.of(cities));
    }

}
```

Copy

Note that the [`List.copyOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/List.html#copyOf\(java.util.Collection\)) method does not accept null values in the collection it gets as an argument.

 

## Getting the State of a Record

You do not need to add any accessor to a record, because the compiler does that for you. A record has one accessor method per component, which has the name of this component.

The `Point` record from the first section of this tutorial has two accessor methods: `x()` and `y()` that return the value of the corresponding components.

There are cases where you need to define your own accessors, though. For instance, assume the `State` record from the previous section didn't create an unmodifiable defensive copy of the `cities` list during construction - then it should do that in the accessor to make sure callers can't mutate its internal state. You can add the following code in your `State` record to return this defensive copy.

```java
public List<String> cities() {
    return List.copyOf(cities);
}
```

Copy

 

## Serializing Records

Records can be serialized and deserialized if your record class implements [`Serializable`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/Serializable.html). There are restrictions though.

1. None of the systems you can use to replace the default serialization process are available for records. Creating a [`writeObject()`](https://docs.oracle.com/en/java/javase/24/docs/specs/serialization/output.html#the-writeobject-method) and [`readObject()`](https://docs.oracle.com/en/java/javase/24/docs/specs/serialization/input.html#the-readobject-method) method has no effect, nor implementing [`Externalizable`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/Externalizable.html).
2. Records can be used as proxy objects to serialize other objects. A [`readResolve()`](https://docs.oracle.com/en/java/javase/24/docs/specs/serialization/input.html#the-readresolve-method) method can return a record. Adding a [`writeReplace()`](https://docs.oracle.com/en/java/javase/24/docs/specs/serialization/output.html#the-writereplace-method) in a record is also possible.
3. Deserializing a record _always_ calls the canonical constructor. So all the validation rules you may add in this constructor will be enforced when deserializing a record.

This makes records a very good choice for creating data transport objects in your application.

 

## Using Records in a Real Use Case

Records are a versatile concept that you can use in many contexts.

The first one is to carry data in the object model of your application. You can use records for what they have been designed for: acting as an immutable data carrier.

Because you can declare local records, you can also use them to improve the readability of your code.

Let us consider the following use case. You have two entities modeled as records: `City` and `State`.

```java
public record City(String name, State state) {}
```

Copy

```java
public record State(String name) {}
```

Copy

Suppose you have a list of cities, and you need to compute the state that has the greatest number of cities. You can use the Stream API to first build the histogram of the states with the number of cities each one has. This histogram is modeled by a [`Map`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/Map.html).

```java
List<City> cities = List.of();

Map<State, Long> numberOfCitiesPerState =
    cities.stream()
          .collect(Collectors.groupingBy(
                   City::state, Collectors.counting()
          ));
```

Copy

Getting the max of this histogram is the following generic code.

```java
Map.Entry<State, Long> stateWithTheMostCities =
    numberOfCitiesPerState.entrySet().stream()
                          .max(Map.Entry.comparingByValue())
                          .orElseThrow();
```

Copy

This last piece of code is technical; it does not carry any business meanings; because is uses [`Map.Entry`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/Map.Entry.html) instance to model every element of the histogram.

Using a local record can greatly improve this situation. The following code creates a new record class, that aggregates a state and the number of cities in this state. It has a constructor that takes an instance of [`Map.Entry`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/Map.Entry.html) as a parameter, to map the stream of key-value pairs to a stream of records.

Because you need to compare these aggregates by the number of cities, you can add a factory method to provide this comparator. The code becomes the following.

```java
record NumberOfCitiesPerState(State state, long numberOfCities) {

    public NumberOfCitiesPerState(Map.Entry<State, Long> entry) {
        this(entry.getKey(), entry.getValue());
    }

    public static Comparator<NumberOfCitiesPerState> comparingByNumberOfCities() {
        return Comparator.comparing(NumberOfCitiesPerState::numberOfCities);
    }
}

NumberOfCitiesPerState stateWithTheMostCities =
    numberOfCitiesPerState.entrySet().stream()
                          .map(NumberOfCitiesPerState::new)
                          .max(NumberOfCitiesPerState.comparingByNumberOfCities())
                          .orElseThrow();
```

Copy

Your code now extracts a max in a meaningful way. Your code is more readable, easier to understand and less error-prone and in the long run easier to maintain.