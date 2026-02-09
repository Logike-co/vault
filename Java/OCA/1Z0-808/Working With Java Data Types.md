- Declare and initialize variables (including casting of primitive data types)
- Differentiate between object reference variables and primitive variables
- Know how to read or write to object fields
- Explain an Object's Lifecycle (creation, "dereference by reassignment" and garbage collection)
- Develop code that uses wrapper classes such as Boolean, Double, and Integer  

# Creating Primitive Type Variables in Your Programs

You have already learned that objects store their state in fields. However, the Java programming language also uses the term _variable_ as well. This section discusses this relationship, plus variable naming rules and conventions, basic data types (primitive types, character strings, and arrays), default values, and literals.

 

## Primitive Types

The Java programming language is statically-typed, which means that all variables must first be declared before they can be used. This involves stating the variable's type and name, as you have already seen:

```java
int gear = 1;
```

Copy

Doing so tells your program that a field named `gear` exists, holds numerical data, and has an initial value of `1`. A variable's data type determines the values it may contain, plus the operations that may be performed on it. In addition to `int`, the Java programming language supports seven other primitive data types. A primitive type is predefined by the language and is named by a reserved keyword. Primitive values do not share state with other primitive values. The eight primitive data types supported by the Java programming language are:

- `byte`: The `byte` data type is an 8-bit signed two's complement integer. It has a minimum value of -128 and a maximum value of 127 (inclusive). The `byte` data type can be useful for saving memory in large arrays, where the memory savings actually matters. They can also be used in place of `int` where their limits help to clarify your code; the fact that a variable's range is limited can serve as a form of documentation.
- `short`: The `short` data type is a 16-bit signed two's complement integer. It has a minimum value of -32,768 and a maximum value of 32,767 (inclusive). As with `byte`, the same guidelines apply: you can use a short to save memory in large arrays, in situations where the memory savings actually matters.
- `int`: By default, the `int` data type is a 32-bit signed two's complement integer, which has a minimum value of -231 and a maximum value of 231-1.
- `long`: The `long` data type is a 64-bit two's complement integer. The signed long has a minimum value of -263 and a maximum value of 263-1.
- `float`: The `float` data type is a single-precision 32-bit IEEE 754 floating point. Its range of values is beyond the scope of this discussion, but is specified in the [Floating-Point Types, Formats, and Values](https://docs.oracle.com/javase/specs/jls/se24/html/jls-4.html#jls-4.2.3) section of the [Java Language Specification](https://docs.oracle.com/javase/specs/jls/se24/html/index.html). As with the recommendations for `byte` and `short`, use a `float` (instead of `double`) if you need to save memory in large arrays of floating point numbers. This data type should never be used for precise values, such as currency. For that, you will need to use the [`java.math.BigDecimal`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/math/BigDecimal.html) class instead. [Numbers and Strings](https://dev.java/learn/numbers-strings/) covers [`BigDecimal`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/math/BigDecimal.html) and other useful classes provided by the Java platform.
- `double`: The `double` data type is a double-precision 64-bit IEEE 754 floating point. Its range of values is beyond the scope of this discussion, but is specified in the [Floating-Point Types, Formats, and Values](https://docs.oracle.com/javase/specs/jls/se24/html/jls-4.html#jls-4.2.3) section of the [Java Language Specification](https://docs.oracle.com/javase/specs/jls/se24/html/index.html). For decimal values, this data type is generally the default choice. As mentioned above, this data type should never be used for precise values, such as currency.
- `boolean`: The `boolean` data type has only two possible values: `true` and `false`. Use this data type for simple flags that track true/false conditions. This data type represents one bit of information, but its "size" isn't something that's precisely defined.
- `char`: The `char` data type is a single 16-bit Unicode character. It has a minimum value of `\u0000` (or 0) and a maximum value of `\uffff` (or 65,535 inclusive).

Note that in Java SE 8 and later, you can use the `int` data type to represent an unsigned 32-bit integer, which has a minimum value of 0 and a maximum value of 232-1. Use the [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) class to use `int` data type as an unsigned integer. See the section [The Number Classes](https://dev.java/learn/numbers-strings/numbers/) for more information. Static methods like [`Integer.compareUnsigned()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#compareUnsigned\(int,int\)) have been added to the [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) class to support the arithmetic operations for unsigned integers.

In Java SE 8 and later, you can also use the `long` data type to represent an unsigned 64-bit long, which has a minimum value of 0 and a maximum value of 264-1. Use this data type when you need a range of values wider than those provided by `int`. The [`Long`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Long.html) class also contains methods like [`Long.compareUnsigned()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Long.html#compareUnsigned\(long,long\)), [`Long.divideUnsigned()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Long.html#divideUnsigned\(long,long\)) etc to support arithmetic operations for unsigned long.

In addition to the eight primitive data types listed above, the Java programming language also provides special support for character strings via the [`java.lang.String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class. Enclosing your character string within double quotes will automatically create a new [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) object; for example:

```java
String s = "this is a string";
```

Copy

[`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) objects are immutable, which means that once created, their values cannot be changed. The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class is not technically a primitive data type, but considering the special support given to it by the language, you will probably tend to think of it as such. You will learn more about the [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class in the section [Strings](https://dev.java/learn/numbers-strings/).

 

## Initializing a Variable with a Default Value

It is not always necessary to assign a value when a field is declared. Fields that are declared but not initialized will be set to a reasonable default by the compiler. Generally speaking, this default will be zero or null, depending on the data type. Relying on such default values, however, is generally considered bad programming style.

The following table summarizes the default values for the above data types.

|Data Type|Default Value (for fields)|
|---|---|
|byte|0|
|short|0|
|int|0|
|long|0L|
|float|0.0f|
|double|0.0d|
|char|`\u0000`|
|String (or any object)|null|
|boolean|`false`|

Local variables are slightly different; the compiler never assigns a default value to an uninitialized local variable. If you cannot initialize your local variable where it is declared, make sure to assign it a value before you attempt to use it. Accessing an uninitialized local variable will result in a compile-time error.

 

## Creating Values with Literals

You may have noticed that the `new` keyword is not used when initializing a variable of a primitive type. Primitive types are special data types built into the language; they are not objects created from a class. A literal is the source code representation of a fixed value; literals are represented directly in your code without requiring computation. As shown below, it is possible to assign a literal to a variable of a primitive type:

```java
boolean result = true;
char capitalC = 'C';
byte b = 100;
short s = 10000;
int i = 100000;
```

Copy

 

## Integer Literals

An integer literal is of type `long` if it ends with the letter `L` or `l`; otherwise it is of type `int`. It is recommended that you use the upper case letter `L` because the lower case letter `l` is hard to distinguish from the digit `1`.

Values of the integral types `byte`, `short`, `int`, and `long` can be created from `int` literals. Values of type `long` that exceed the range of `int` can be created from `long` literals. Integer literals can be expressed by these number systems:

- Decimal: Base 10, whose digits consists of the numbers 0 through 9; this is the number system you use every day
- Hexadecimal: Base 16, whose digits consist of the numbers 0 through 9 and the letters A through F
- Binary: Base 2, whose digits consists of the numbers 0 and 1 (you can create binary literals in Java SE 7 and later)

For general-purpose programming, the decimal system is likely to be the only number system you will ever use. However, if you need to use another number system, the following example shows the correct syntax. The prefix `0x` indicates hexadecimal and `0b` indicates binary:

```java
// The number 26, in decimal
int decimalValue = 26;

//  The number 26, in hexadecimal
int hexadecimalValue = 0x1a;

// The number 26, in binary
int binaryValue = 0b11010;
```

Copy

 

## Floating-Point Literals

A floating-point literal is of type `float` if it ends with the letter `F` or `f`; otherwise its type is `double` and it can optionally end with the letter `D` or `d`.

The floating point types (`float` and `double`) can also be expressed using `E` or `e` (for scientific notation), `F` or `f` (32-bit float literal) and `D` or `d` (64-bit double literal; this is the default and by convention is omitted).

```java
double d1 = 123.4;

// same value as d1, but in scientific notation
double d2 = 1.234e2;
float f1  = 123.4f;
```

Copy

 

## Character and String Literals

Literals of types `char` and `String` may contain any Unicode (UTF-16) characters. If your editor and file system allow it, you can use such characters directly in your code. If not, you can use a "Unicode escape" such as `\u0108` (capital C with circumflex), or "S\u00ED Se\u00F1or" (Sí Señor in Spanish). Always use 'single quotes' for `char` literals and "double quotes" for `String` literals. Unicode escape sequences may be used elsewhere in a program (such as in field names, for example), not just in `char` or `String` literals.

The Java programming language also supports a few special escape sequences for `char` and `String` literals: `\b` (backspace), `\t` (tab), `\n` (line feed), `\f` (form feed), `\r` (carriage return), `\"` (double quote), `\'` (single quote), and `\\` (backslash).

There is also a special `null` literal that can be used as a value for any reference type. The `null` literal may be assigned to any variable, except variables of primitive types. There is little you can do with a `null` value beyond testing for its presence. Therefore, `null` is often used in programs as a marker to indicate that some object is unavailable.

Finally, there is also a special kind of literal called a _class literal_, formed by taking a type name and appending `.class`; for example, `String.class`. This refers to the object that represents the type itself, of type [`Class`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Class.html).

 

## Using Underscore Characters in Numeric Literals

In Java SE 7 and later, any number of underscore characters (`_`) can appear anywhere between digits in a numerical literal. This feature enables you, for example. to separate groups of digits in numeric literals, which can improve the readability of your code.

For instance, if your code contains numbers with many digits, you can use an underscore character to separate digits in groups of three, similar to how you would use a punctuation mark like a comma, or a space, as a separator.

The following example shows other ways you can use the underscore in numeric literals:

```java
long creditCardNumber = 1234_5678_9012_3456L;
long socialSecurityNumber = 999_99_9999L;
float pi =  3.14_15F;
long hexBytes = 0xFF_EC_DE_5E;
long hexWords = 0xCAFE_BABE;
long maxLong = 0x7fff_ffff_ffff_ffffL;
byte nybbles = 0b0010_0101;
long bytes = 0b11010010_01101001_10010100_10010010;
```

Copy

You can place underscores only between digits; you cannot place underscores in the following places:

- At the beginning or end of a number
- Adjacent to a decimal point in a floating point literal
- Prior to an `F` or `L` suffix
- In positions where a string of digits is expected

The following examples demonstrate valid and invalid underscore placements in numeric literals:

```java
// Invalid: cannot put underscores
// adjacent to a decimal point
float pi1 = 3_.1415F;
// Invalid: cannot put underscores
// adjacent to a decimal point
float pi2 = 3._1415F;
// Invalid: cannot put underscores
// prior to an L suffix
long socialSecurityNumber1 = 999_99_9999_L;

// OK (decimal literal)
int x1 = 5_2;
// Invalid: cannot put underscores
// At the end of a literal
int x2 = 52_;
// OK (decimal literal)
int x3 = 5_______2;

// Invalid: cannot put underscores
// in the 0x radix prefix
int x4 = 0_x52;
// Invalid: cannot put underscores
// at the beginning of a number
int x5 = 0x_52;
// OK (hexadecimal literal)
int x6 = 0x5_2;
// Invalid: cannot put underscores
// at the end of a number
int x7 = 0x52_;
```

# Using the Var Type Identifier

 

## The Var Keyword

Starting with Java SE 10, you can use the `var` type identifier to declare a local variable. In doing so, you let the compiler decide what is the real type of the variable you create. Once created, this type cannot be changed.

Consider the following example.

```java
String message = "Hello world!";
Path path = Path.of("debug.log");
InputStream stream = Files.newInputStream(path);
```

Copy

In that case, having to declare the explicit types of the three variables `message`, `path` and `stream` is redundant.

With the `var` type identifier the previous code can be written as follow:

```java
var message = "Hello world!";
var path = Path.of("debug.log");
var stream = Files.newInputStream(path);
```

Copy

 

## Examples with Var

The following example shows you how you can use the `var` type identifier to make your code simpler to read. Here the `strings` variable is given the type [`List<String>`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/List.html) and the `element` variable the type [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html).

```java
var list = List.of("one", "two", "three", "four");
for (var element: list) {
    System.out.println(element);
}
```

Copy

On this example, the `path` variable is of type [`Path`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/nio/file/Path.html), and the `stream` variable is of type [`InputStream`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/InputStream.html).

```java
var path = Path.of("debug.log");
try (var stream = Files.newInputStream(path)) {
    // process the file
}
```

Copy

Note that on the two previous examples, you have used `var` to declare a variable in a for statement and in a try-with-resources statement. These two statements are covered later in this tutorial.

 

## Restrictions on Using Var

There are restrictions on the use of the `var` type identifier.

1. You can only use it for _local variables_ declared in methods, constructors and initializer blocks.
2. `var` cannot be used for fields, nor for method or constructor parameters.
3. The compiler must be able to choose a type when the variable is declared. Since `null` has no type, the variable must have an initializer.

Following the these restriction, the following class does not compile, because using `var` as a type identifier is not possible for a field or a method parameter.

```java
public class User  {
    private var name = "Sue"; // COMPILER ERROR

    public void setName(var name) {
        this.name = name;
    }
}
```

Copy

The same goes for the following code.

In that case, the compiler cannot guess the real type of `greetings` because is lacks an initializer. So this code does not compiler neither.

```java
public String greetings(int message) {
    var greetings; // COMPILER ERROR
    if (message == 0) {
        greetings = "morning";
    } else {
        greetings = "afternoon";
    }
    return "Good " + greetings;
}
```

# Enums

This page was contributed by [Daniel Schmid](https://dev.java/author/DanielSchmid) under the [UPL](https://oss.oracle.com/licenses/upl/)  

 

## What are enums?

Enums are classes where all instances are known to the compiler. They are used for creating types that can only have few possible values.

Enums can be created similar to classes but use the `enum` keyword instead of `class`. In the body, there is a list of instances of the enum called enum constants which are seperated by `,`. No instances of the enum can be created outside of enum constants.

```java
public enum DayOfWeek {
    // enum constants are listed here:
    MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}
```

Copy

All enums implicitly extend [`java.lang.Enum`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Enum.html) and cannot have any subclasses.

 

## Accessing, evaluating, and comparing enums

The values of an enum can be used as constants. In order to check whether two instances of an enum are the same, the `==` operator can be used.

```java
DayOfWeek weekStart = DayOfWeek.MONDAY;

if (weekStart == DayOfWeek.MONDAY) {
    System.out.println("The week starts on Monday.");
}
```

Copy

It is also possible to use `switch` for performing actions depending on the value of the enum.

```java
DayOfWeek someDay = DayOfWeek.FRIDAY;

switch (someDay) {
    case MONDAY ->
        System.out.println("The week just started.");
    case TUESDAY, WEDNESDAY, THURSDAY ->
        System.out.println("We are somewhere in the middle of the week.");
    case FRIDAY ->
        System.out.println("The weekend is near.");
    case SATURDAY, SUNDAY ->
        System.out.println("Weekend");
    default ->
        throw new AssertionError("Should not happen");
}
```

Copy

With [switch expressions](https://dev.java/learn/language-basics/switch-expression/), the compiler can check whether all values of the enum are handled. If any possible value is missing in a switch expression, there will be a compiler error. This is referred to as Exhaustiveness and can also be achieved with regular classes through [JEP 409: Sealed Classes](https://openjdk.org/jeps/409) and [pattern matching](https://dev.java/learn/pattern-matching/#switch).

```java
DayOfWeek someDay = DayOfWeek.FRIDAY;

String text = switch (someDay) {
    case MONDAY -> "The week just started.";
    case TUESDAY, WEDNESDAY, THURSDAY -> "We are somewhere in the middle of the week.";
    case FRIDAY -> "The weekend is near.";
    case SATURDAY, SUNDAY -> "Weekend";
};

System.out.println(text);
```

Copy

 

## Adding members to enums

Just like classes, enums can have constructors, methods and fields. In order to add these, it is necessary to add a `;` after the list of enum constants. Arguments to the constructor are passed in parenthesis after the declaration of the enum constant.

```java
public enum DayOfWeek {
    MONDAY("MON"), TUESDAY("TUE"), WEDNESDAY("WED"), THURSDAY("THU"), FRIDAY("FRI"), SATURDAY("SAT"), SUNDAY("SUN");
    
    private final String abbreviation;
    
    DayOfWeek(String abbreviation) {
        this.abbreviation = abbreviation;
    }
    
    public String getAbbreviation() {
        return abbreviation;
    }
}
```

Copy

 

## Special methods

All enums have a few methods that are added implicitly.

For example, the method `name()` is present in all enum instances and can be used to get the name of the enum constant. Similarly, a method named `ordinal()` returns the position of the enum constant in the declaration.

```java
System.out.println(DayOfWeek.MONDAY.name());    // prints "MONDAY"
System.out.println(DayOfWeek.MONDAY.ordinal()); // prints "0" because MONDAY is the first constant in the DayOfWeek enum
```

Copy

Aside from instance methods, there are also static methods added to all enums. The method `values()` returns an array containing all instances of the enum and the method `valueOf(String)` can be used to get a specific instance by its name.

```java
DayOfWeek[] days = DayOfWeek.values(); // all days of the week
DayOfWeek monday = DayOfWeek.valueOf("MONDAY");
```

Copy

Furthermore, enums implement the interface [`Comparable`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Comparable.html). By default, enums are ordered according to their ordinal number i.e. in the order of occurrence of the enum constant. This allows for comparing instances of enums as well as sorting or searching.

```java
public void compareDayOfWeek(DayOfWeek dayOfWeek){
    int comparison = dayOfWeek.compareTo(DayOfWeek.WEDNESDAY);
    if (comparison < 0) {
        System.out.println("It's before the middle of the work week.");
    } else if (comparison > 0){
        System.out.println("It's after the middle of the work week.");
    } else {
        System.out.println("It's the middle of the work week.");
    }
}
```

Copy

```java
List<DayOfWeek> days = new ArrayList<>(List.of(DayOfWeek.FRIDAY, DayOfWeek.TUESDAY, DayOfWeek.SATURDAY));
Collections.sort(days);
```

Copy

 

## Using enums as singletons

Since enums can only have a specific number of instances, it is possible to create a singleton by creating an enum with only a single enum constant.

```java
public enum SomeSingleton {
    INSTANCE;
    //fields, methods, etc.
}
```

Copy

 

## Abstract methods in enums

Even though enums cannot be extended, they can still have `abstract` methods. In that case, an implementation must be present in each enum constant.

```java
enum MyEnum {
    A() {
        @Override
        void doSomething() {
            System.out.println("a");
        }
    },
    B() {
        @Override
        void doSomething() {
            System.out.println("b");
        }
    };
    
    abstract void doSomething();
}
```

Copy

 

## Precautions

Care should be taken when using enums where the number (or names) of instances is subject to change. Whenever enum constants are changed, other code expecting the old version of the enum might not work as expected. This may manifest in compilation errors (e.g. when referencing a removed enum constant), runtime errors (e.g. if there is a `default` case even though the new enum constant should be handled separately) or other inconsistencies (e.g. if the value of the enum was saved to a file which is then read and expecting that value to still exist).

When changing enum constants, it is recommended to review all code using the enum. This is especially important in cases where the enum is also used by other people's code.

Furthermore, it might be worth considering to use other options in case of many instances since listing a lot of instances at a single location in code can be inflexible. For example, it may be better to use a configuration file for listing all instances and reading these configuration files in the program in cases like this.

 

## Conclusion

Enums provide a simple and safe way of representing a fixed set of constants while keeping most of the flexibilities of classes. They are a special type of class that can be used to write code that is elegant, readable, maintainable, and works well with other modern Java features like [switch expressions](https://dev.java/learn/language-basics/switch-expression/). Another special class is the Record class, introduced as a preview feature in Java 14 and made a standard feature in Java 16. Visit our [records tutorial](https://dev.java/learn/records/) to learn more.

To learn more about enums, visit the [`java.lang.Enum`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Enum.html) javadoc.

## [[Numbers and Strings]]

This part of the tutorial covers numbers with primitive types and wrapper classes, and string of characters.

### Numbers
Using numbers with primitive types and wrapper types, formatting numbers and using mathematical functions.

### Characters
Using characters, understanding char values and code point values.

### Strings
Creating strings of characters, exploring the String class to manipulate strings.

### String Builders
Using string builders to create strings of characters.

### Autoboxing and Unboxing
Understanding the automatic conversion between primitive types and their corresponding wrapper types.