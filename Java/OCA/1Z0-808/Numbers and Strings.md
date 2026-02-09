## Numbers

This section begins with a discussion of the [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) class in the [`java.lang`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/package-summary.html) package, its subclasses, and the situations where you would use instantiations of these classes rather than the primitive number types.

This section also presents the [`PrintStream`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html) and [`DecimalFormat`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/text/DecimalFormat.html) classes, which provide methods for writing formatted numerical output.

Finally, the [`Math`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html) class in [`java.lang`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/package-summary.html) is discussed. It contains mathematical functions to complement the operators built into the language. This class has methods for the trigonometric functions, exponential functions, and so forth.

When working with numbers, most of the time you use the primitive types in your code. For example:

```java
int i = 500;
float gpa = 3.65f;
byte mask = 0x7f;
```

Copy

There are, however, reasons to use objects in place of primitives, and the Java platform provides wrapper classes for each of the primitive data types. These classes "wrap" the primitive in an object. Often, the wrapping is done by the compiler—if you use a primitive where an object is expected, the compiler boxes the primitive in its wrapper class for you. Similarly, if you use a number object when a primitive is expected, the compiler unboxes the object for you. For more information, see the section Autoboxing and Unboxing

All of the numeric wrapper classes are subclasses of the abstract class [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html):

![The Number Class Hierarchy](https://dev.java/assets/images/numbers-strings/01_numbers.png)

The Number Class Hierarchy

> Note: There are four other subclasses of [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) that are not discussed here. [`BigDecimal`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/math/BigDecimal.html) and [`BigInteger`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/math/BigInteger.html) are used for high-precision calculations. [`AtomicInteger`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/concurrent/atomic/AtomicInteger.html) and [`AtomicLong`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/concurrent/atomic/AtomicLong.html) are used for multi-threaded applications.

There are three reasons that you might use a [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) object rather than a primitive:

1. As an argument of a method that expects an object (often used when manipulating collections of numbers).
2. To use constants defined by the class, such as [`MIN_VALUE`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#MIN_VALUE) and [`MAX_VALUE`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#MAX_VALUE), that provide the upper and lower bounds of the data type.
3. To use class methods for converting values to and from other primitive types, for converting to and from strings, and for converting between number systems (decimal, octal, hexadecimal, binary).

The following table lists the instance methods that all the subclasses of the Number class implement.

The following methods convert the value of this [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) object to the primitive data type returned.

- [`byte byteValue()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#byteValue\(\))
- [`short shortValue()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#shortValue\(\))
- [`int intValue()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#intValue\(\))
- [`long longValue()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#longValue\(\))
- [`float floatValue()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#floatValue\(\))
- [`double doubleValue()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#doubleValue\(\))

The following methods compare this [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) object to the argument.

- [`int compareTo(Byte anotherByte)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Byte.html#compareTo\(java.lang.Byte\))
- [`int compareTo(Double anotherDouble)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Double.html#compareTo\(java.lang.Double\))
- [`int compareTo(Float anotherFloat)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Float.html#compareTo\(java.lang.Float\))
- [`int compareTo(Integer anotherInteger)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#compareTo\(java.lang.Integer\))
- [`int compareTo(Long anotherLong)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Long.html#compareTo\(java.lang.Long\))
- [`int compareTo(Short anotherShort)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Short.html#compareTo\(java.lang.Short\))
- [`boolean equals(Object obj)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#equals\(java.lang.Object\))

The method `equals(Object obj)` determines whether this number object is equal to the argument. The methods return `true` if the argument is not `null` and is an object of the same type and with the same numeric value. There are some extra requirements for [`Double`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Double.html) and [`Float`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Float.html) objects that are described in the Java API documentation.

Each [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) class contains other methods that are useful for converting numbers to and from strings and for converting between number systems. The following table lists these methods in the [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) class. Methods for the other [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) subclasses are similar:

|Method|Description|
|---|---|
|[`static Integer decode(String s)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#decode\(java.lang.String\))|Decodes a string into an integer. Can accept string representations of decimal, octal, or hexadecimal numbers as input.|
|[`static int parseInt(String s)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#parseInt\(java.lang.String\))|Returns an integer (decimal only).|
|[`static int parseInt(String s, int radix)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#parseInt\(java.lang.String,int\))|Returns an integer, given a string representation of decimal, binary, octal, or hexadecimal (radix equals 10, 2, 8, or 16 respectively) numbers as input.|
|[`String toString()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#toString\(\))|Returns a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) object representing the value of this [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html).|
|[`static String toString(int i)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#toString\(int\))|Returns a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) object representing the specified integer.|
|[`static Integer valueOf(int i)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#valueOf\(int\))|Returns an [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) object holding the value of the specified primitive.|
|[`static Integer valueOf(String s)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#valueOf\(java.lang.String\))|Returns an [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) object holding the value of the specified string representation.|
|[`static Integer valueOf(String s, int radix)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#valueOf\(java.lang.String,int\))|Returns an [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) object holding the integer value of the specified string representation, parsed with the value of radix. For example, if s = "333" and radix = 8, the method returns the base-ten integer equivalent of the octal number 333.|

 

## Formatting Numeric Print Output

Earlier you saw the use of the [`print`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#print\(int\)) and [`println`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#println\(int\)) methods for printing strings to standard output [`System.out`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/System.html#out). Since all numbers can be converted to strings, you can use these methods to print out an arbitrary mixture of strings and numbers. The Java programming language has other methods, however, that allow you to exercise much more control over your print output when numbers are included.

### The Printf and Format Methods

The [`java.io`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/package-summary.html) package includes a [`PrintStream`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html) class that has two formatting methods that you can use to replace [`print`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#print\(int\)) and [`println`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#println\(int\)). These methods, [`format`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)) and [`printf`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#printf\(java.lang.String,java.lang.Object...\)), are equivalent to one another. The familiar [`System.out`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/System.html#out) that you have been using happens to be a [`PrintStream`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html) object, so you can invoke [`PrintStream`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html) methods on [`System.out`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/System.html#out). Thus, you can use [`format`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)) or [`printf`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#printf\(java.lang.String,java.lang.Object...\)) anywhere in your code where you have previously been using [`print`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#print\(int\)) or [`println`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#println\(int\)). For example,

```java
System.out.format(.....);
```

Copy

The syntax for these two [`java.io.PrintStream`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html) methods is the same:

```java
public PrintStream format(String format, Object... args)
```

Copy

where [`format`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)) is a string that specifies the formatting to be used and args is a list of the variables to be printed using that formatting. A simple example would be

```java
System.out.format("The value of " + "the float variable is " +
     "%f, while the value of the " + "integer variable is %d, " +
     "and the string is %s", floatVar, intVar, stringVar); 
```

Copy

The first parameter, [`format`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)), is a format string specifying how the objects in the second parameter, `args`, are to be formatted. The [`format`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)) string contains plain text as well as format specifiers, which are special characters that format the arguments of `Object...` args. (The notation `Object...` args is called _varargs_, which means that the number of arguments may vary.)

Format specifiers begin with a percent sign (`%`) and end with a converter. The converter is a character indicating the type of argument to be formatted. In between the percent sign (`%`) and the converter you can have optional flags and specifiers. There are many converters, flags, and specifiers, which are documented in [`java.util.Formatter`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/Formatter.html).

Here is a basic example:

```java
int i = 461012;
System.out.format("The value of i is: %d%n", i)
```

Copy

The `%d` specifies that the single variable is a decimal integer. The `%n` is a platform-independent newline character. The output is:

```shell
The value of i is: 461012
```

Copy

The [`printf`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#printf\(java.lang.String,java.lang.Object...\)) and [`format`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)) methods are overloaded. Each has a version with the following syntax:

```java
public PrintStream format(Locale l, String format, Object... args)
```

Copy

To print numbers in the French system (where a comma is used in place of the decimal place in the English representation of floating point numbers), for example, you would use:

```java
System.out.format(Locale.FRANCE,
    "The value of the float " + "variable is %f, while the " +
    "value of the integer variable " + "is %d, and the string is %s%n", 
    floatVar, intVar, stringVar);
```

Copy

### An Example

The following table lists some of the converters and flags that are used in the sample program, `TestFormat.java`, that follows the table.

|Converter|Flag|Explanation|
|---|---|---|
|d||A decimal integer.|
|f||A float.|
|n||A new line character appropriate to the platform running the application. You should always use `%n`, rather than `\n`.|
|tB||A date & time conversion—locale-specific full name of month.|
|td, te||A date & time conversion—2-digit day of month. td has leading zeroes as needed, te does not.|
|ty, tY||A date & time conversion—ty = 2-digit year, tY = 4-digit year.|
|tl||A date & time conversion—hour in 12-hour clock.|
|tM||A date & time conversion—minutes in 2 digits, with leading zeroes as necessary.|
|tp||A date & time conversion—locale-specific am/pm (lower case).|
|tm||A date & time conversion—months in 2 digits, with leading zeroes as necessary.|
|tD||A date & time conversion—date as %tm%td%ty|
||08|Eight characters in width, with leading zeroes as necessary.|
||+|Includes sign, whether positive or negative.|
||,|Includes locale-specific grouping characters.|
||-|Left-justified.|
||.3|Three places after decimal point.|
||10.3|Ten characters in width, right justified, with three places after decimal point.|

The following program shows some of the formatting that you can do with format. The output is shown within double quotes in the embedded comment:

```java
import java.util.Calendar;
import java.util.Locale;

public class TestFormat {
    
    public static void main(String[] args) {
      long n = 461012;
      System.out.format("%d%n", n);      //  -->  "461012"
      System.out.format("%08d%n", n);    //  -->  "00461012"
      System.out.format("%+8d%n", n);    //  -->  " +461012"
      System.out.format("%,8d%n", n);    // -->  " 461,012"
      System.out.format("%+,8d%n%n", n); //  -->  "+461,012"
      
      double pi = Math.PI;

      System.out.format("%f%n", pi);       // -->  "3.141593"
      System.out.format("%.3f%n", pi);     // -->  "3.142"
      System.out.format("%10.3f%n", pi);   // -->  "     3.142"
      System.out.format("%-10.3f%n", pi);  // -->  "3.142"
      System.out.format(Locale.FRANCE,
                        "%-10.4f%n%n", pi); // -->  "3,1416"

      Calendar c = Calendar.getInstance();
      System.out.format("%tB %te, %tY%n", c, c, c); // -->  "May 29, 2006"

      System.out.format("%tl:%tM %tp%n", c, c, c);  // -->  "2:34 am"

      System.out.format("%tD%n", c);    // -->  "05/29/06"
    }
}
```

Copy

> Note: The discussion in this section covers just the basics of the [`format`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)) and [`printf`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#printf\(java.lang.String,java.lang.Object...\)) methods. Further detail can be found in the Basic I/O section of this tutorial, in the "Formatting" page. Using the [`String.format()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#format\(java.lang.String,java.lang.Object...\)) to create strings is covered in [`Strings`](https://dev.java/learn/numbers-strings/strings/).

 

## The DecimalFormat Class

You can use the [`java.text.DecimalFormat`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/text/DecimalFormat.html) class to control the display of leading and trailing zeros, prefixes and suffixes, grouping (thousands) separators, and the decimal separator. [`DecimalFormat`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/text/DecimalFormat.html) offers a great deal of flexibility in the formatting of numbers, but it can make your code more complex.

The example that follows creates a [`DecimalFormat`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/text/DecimalFormat.html) object, `myFormatter`, by passing a pattern string to the [`DecimalFormat`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/text/DecimalFormat.html) constructor. The [`format`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)) method, which [`DecimalFormat`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/text/DecimalFormat.html) inherits from [`NumberFormat`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/text/NumberFormat.html), is then invoked by `myFormatter`—it accepts a double value as an argument and returns the formatted number in a string.

Here is a sample program that illustrates the use of [`DecimalFormat`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/text/DecimalFormat.html):

```java
import java.text.*;

public class DecimalFormatDemo {

   static public void customFormat(String pattern, double value ) {
      DecimalFormat myFormatter = new DecimalFormat(pattern);
      String output = myFormatter.format(value);
      System.out.println(value + "  " + pattern + "  " + output);
   }

   static public void main(String[] args) {

      customFormat("###,###.###", 123456.789);
      customFormat("###.##", 123456.789);
      customFormat("000000.000", 123.78);
      customFormat("$###,###.###", 12345.67);  
   }
}
```

Copy

The output is:

```shell
123456.789  ###,###.###  123,456.789
123456.789  ###.##  123456.79
123.78  000000.000  000123.780
12345.67  $###,###.###  $12,345.67
```

Copy

The following table explains each line of output.

|Value|Pattern|Output|Explanation|
|---|---|---|---|
|123456.789|###,###.###|123,456.789|The pound sign (`#`) denotes a digit, the comma is a placeholder for the grouping separator, and the period is a placeholder for the decimal separator.|
|123456.789|###.##|123456.79|The `value` has three digits to the right of the decimal point, but the pattern has only two. The format method handles this by rounding up.|
|123.78|000000.000|000123.780|The `pattern` specifies leading and trailing zeros, because the 0 character is used instead of the pound sign (#).|
|12345.67|$###,###.###|$12,345.67|The first character in the `pattern` is the dollar sign (`$`). Note that it immediately precedes the leftmost digit in the formatted `output`.|

 

## Beyond Basic Arithmetic

The Java programming language supports basic arithmetic with its arithmetic operators: `+`, `-`, `*`, `/`, and `%`. The [`Math`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html) class in the [`java.lang`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/package-summary.html) package provides methods and constants for doing more advanced mathematical computation.

The methods in the [`Math`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html) class are all static, so you call them directly from the class, like this:

```java
Math.cos(angle);
```

Copy

> Note: Using the static import language feature, you don't have to write [`Math`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html) in front of every math function: `import static java.lang.Math.*;` This allows you to invoke the [`Math`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html) class methods by their simple names. For example: `cos(angle);`

### Constants and Basic Methods

The [`Math`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html) class includes two constants:

- [`Math.E`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#E), which is the base of natural logarithms, and
- [`Math.PI`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#PI), which is the ratio of the circumference of a circle to its diameter.

The [`Math`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html) class also includes more than 40 static methods. The following table lists a number of the basic methods.

#### Computing an Absolute Value

- [`double abs(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#abs\(double\))
- [`float abs(float f)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#abs\(float\))
- [`int abs(int i)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#abs\(int\))
- [`long abs(long lng)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#abs\(long\))

#### Rouding a Value

- [`double ceil(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#ceil\(double\)): Returns the smallest integer that is greater than or equal to the argument. Returned as a `double`.
- [`double floor(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#floor\(double\)): Returns the largest integer that is less than or equal to the argument. Returned as a `double`.
- [`double rint(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#rint\(double\)): Returns the integer that is closest in value to the argument. Returned as a `double`.
- [`long round(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#round\(double\)) and [`int round(float f)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#round\(float\)): Returns the closest `long` or `int`, as indicated by the method's return type, to the argument.

#### Computing a Min

- [`double min(double arg1, double arg2)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#min\(double,double\))
- [`float min(float arg1, float arg2)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#min\(float,float\))
- [`int min(int arg1, int arg2)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#min\(int,int\))
- [`long min(long arg1, long arg2)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#min\(long,long\))

#### Computing a Max

- [`double max(double arg1, double arg2)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#max\(double,double\))
- [`float max(float arg1, float arg2)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#max\(float,float\))
- [`int max(int arg1, int arg2)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#max\(int,int\))
- [`long max(long arg1, long arg2)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#max\(long,long\))

The following program, `BasicMathDemo`, illustrates how to use some of these methods:

```java
public class BasicMathDemo {
    public static void main(String[] args) {
        double a = -191.635;
        double b = 43.74;
        int c = 16, d = 45;

        System.out.printf("The absolute value " + "of %.3f is %.3f%n", 
                          a, Math.abs(a));

        System.out.printf("The ceiling of " + "%.2f is %.0f%n", 
                          b, Math.ceil(b));

        System.out.printf("The floor of " + "%.2f is %.0f%n", 
                          b, Math.floor(b));

        System.out.printf("The rint of %.2f " + "is %.0f%n", 
                          b, Math.rint(b));

        System.out.printf("The max of %d and " + "%d is %d%n",
                          c, d, Math.max(c, d));

        System.out.printf("The min of of %d " + "and %d is %d%n",
                          c, d, Math.min(c, d));
    }
}
```

Copy

Here's the output from this program:

```shell
The absolute value of -191.635 is 191.635
The ceiling of 43.74 is 44
The floor of 43.74 is 43
The rint of 43.74 is 44
The max of 16 and 45 is 45
The min of 16 and 45 is 16
```

Copy

### Exponential and Logarithmic Methods

The next table lists exponential and logarithmic methods of the [`Math`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html) class.

- [`double exp(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#exp\(double\)): Returns the base of the natural logarithms, e, to the power of the argument.
- [`double log(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#log\(double\)): Returns the natural logarithm of the argument.
- [`double pow(double base, double exponent)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#pow\(double,double\)): Returns the value of the first argument raised to the power of the second argument.
- [`double sqrt(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#sqrt\(double\)): Returns the square root of the argument.

The following program, `ExponentialDemo`, displays the value of `e`, then calls each of the methods listed in the previous table on arbitrarily chosen numbers:

```java
public class ExponentialDemo {
    public static void main(String[] args) {
        double x = 11.635;
        double y = 2.76;

        System.out.printf("The value of " + "e is %.4f%n",
                          Math.E);

        System.out.printf("exp(%.3f) " + "is %.3f%n",
                          x, Math.exp(x));

        System.out.printf("log(%.3f) is " + "%.3f%n",
                          x, Math.log(x));

        System.out.printf("pow(%.3f, %.3f) " + "is %.3f%n",
                          x, y, Math.pow(x, y));

        System.out.printf("sqrt(%.3f) is " + "%.3f%n",
                          x, Math.sqrt(x));
    }
}
```

Copy

Here is the output you will see when you run `ExponentialDemo`:

```shell
The value of e is 2.7183
exp(11.635) is 112983.831
log(11.635) is 2.454
pow(11.635, 2.760) is 874.008
sqrt(11.635) is 3.411
```

Copy

### Trigonometric Methods

The [`Math`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html) class also provides a collection of trigonometric functions, which are summarized in the following table. The value passed into each of these methods is an angle expressed in radians. You can use the [`toRadians(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#toRadians\(double\)) method to convert from degrees to radians.

- [`double sin(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#sin\(double\)): Returns the sine of the specified double value.
- [`double cos(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#cos\(double\)): Returns the cosine of the specified double value.
- [`double tan(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#tan\(double\)): Returns the tangent of the specified double value.
- [`double asin(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#asin\(double\)): Returns the arcsine of the specified double value.
- [`double acos(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#acos\(double\)): Returns the arccosine of the specified double value.
- [`double atan(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#atan\(double\)): Returns the arctangent of the specified double value.
- [`double atan2(double y, double x)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#atan2\(double,double\)): Converts rectangular coordinates (x, y) to polar coordinate (r, theta) and returns theta.
- [`double toDegrees(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#toDegrees\(double\)) and [`double toRadians(double d)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#toRadians\(double\)): Converts the argument to degrees or radians.

Here is a program, `TrigonometricDemo`, that uses each of these methods to compute various trigonometric values for a 45-degree angle:

```java
public class TrigonometricDemo {
    public static void main(String[] args) {
        double degrees = 45.0;
        double radians = Math.toRadians(degrees);
        
        System.out.format("The value of pi " + "is %.4f%n",
                           Math.PI);

        System.out.format("The sine of %.1f " + "degrees is %.4f%n",
                          degrees, Math.sin(radians));

        System.out.format("The cosine of %.1f " + "degrees is %.4f%n",
                          degrees, Math.cos(radians));

        System.out.format("The tangent of %.1f " + "degrees is %.4f%n",
                          degrees, Math.tan(radians));

        System.out.format("The arcsine of %.4f " + "is %.4f degrees %n", 
                          Math.sin(radians), 
                          Math.toDegrees(Math.asin(Math.sin(radians))));

        System.out.format("The arccosine of %.4f " + "is %.4f degrees %n", 
                          Math.cos(radians),  
                          Math.toDegrees(Math.acos(Math.cos(radians))));

        System.out.format("The arctangent of %.4f " + "is %.4f degrees %n", 
                          Math.tan(radians), 
                          Math.toDegrees(Math.atan(Math.tan(radians))));
    }
}
```

Copy

The output of this program is as follows:

```shell
The value of pi is 3.1416
The sine of 45.0 degrees is 0.7071
The cosine of 45.0 degrees is 0.7071
The tangent of 45.0 degrees is 1.0000
The arcsine of 0.7071 is 45.0000 degrees
The arccosine of 0.7071 is 45.0000 degrees
The arctangent of 1.0000 is 45.0000 degrees
```

Copy

 

## Random Numbers

The [`random()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#random\(\)) method returns a pseudo-randomly selected number between 0.0 and 1.0. The range includes 0.0 but not 1.0. In other words: `0.0 <= Math.random() < 1.0`. To get a number in a different range, you can perform arithmetic on the value returned by the random method. For example, to generate an integer between 0 and 9, you would write:

```java
int number = (int)(Math.random() * 10);
```

Copy

By multiplying the value by 10, the range of possible values becomes `0.0 <= number < 10.0`.

Using [`Math.random`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Math.html#random\(\)) works well when you need to generate a single random number. If you need to generate a series of random numbers, you should create an instance of [`java.util.Random`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/util/Random.html) and invoke methods on that object to generate numbers.

## Characters

Most of the time, if you are using a single character value, you will use the primitive `char` type. For example:

```java
char ch = 'a'; 
// Unicode for uppercase Greek omega character
char uniChar = '\u03A9';
// an array of chars
char[] charArray = { 'a', 'b', 'c', 'd', 'e' };
```

Copy

There are times, however, when you need to use a `char` as an object—for example, as a method argument where an object is expected. The Java programming language provides a wrapper class that "wraps" the `char` in a [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) object for this purpose. An object of type [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) contains a single field, whose type is `char`. This [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) class also offers a number of useful class (that is, static) methods for manipulating characters.

You can create a [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) object with the [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) constructor:

```java
Character ch = new Character('a');
```

Copy

The Java compiler will also create a [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) object for you under some circumstances. For example, if you pass a primitive `char` into a method that expects an object, the compiler automatically converts the `char` to a [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) for you. This feature is called _autoboxing_—or _unboxing_, if the conversion goes the other way. For more information on autoboxing and unboxing, see the section Autoboxing and Unboxing.

> Note: The [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) class is immutable, so that once it is created, a [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) object cannot be changed.

The following table lists some of the most useful methods in the [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) class, but is not exhaustive. For a complete listing of all methods in this class (there are more than 50), refer to the [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) API specification.

- [`boolean isLetter(char ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html#isLetter\(char\)) and [`boolean isDigit(char ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html#isDigit\(char\)) : Determines whether the specified `char` value is a letter or a digit, respectively.
- [`boolean isWhitespace(char ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html#isWhitespace\(char\)): Determines whether the specified `char` value is white space.
- [`boolean isUpperCase(char ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html#isUpperCase\(char\)) and [`boolean isLowerCase(char ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html#isLowerCase\(char\)): Determines whether the specified `char` value is uppercase or lowercase, respectively.
- [`char toUpperCase(char ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html#toUpperCase\(char\)) and [`char toLowerCase(char ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html#toLowerCase\(char\)): Returns the uppercase or lowercase form of the specified `char` value.
- [`toString(char ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html#toString\(char\)): Returns a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) object representing the specified character value — that is, a one-character string.

 

## Characters and Code Points

The Java platform has supported Unicode Standard starting with JDK 1.0.2. Java SE 15 supports Unicode 13.0. The `char` data type and the [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) class are based on the original Unicode specification, which defined characters as fixed-width 16-bit entities. The Unicode Standard has since been changed to allow for characters whose representation requires more than 16 bits. The range of legal code points is now U+0000 to U+10FFFF, known as Unicode scalar value.

A `char` value is encoded with 16 bits. It can thus represent numbers from `0x0000` to `0xFFFF`. This set of characters is sometimes referred to as the _Basic Multilingual Plane (BMP)_. Characters whose code points are greater than `0xFFFF` (noted U+FFFF) are called _supplementary characters_.

A `char` value, therefore, represents Basic Multilingual Plane (BMP) code points. An `int` value represents all Unicode code points, including supplementary code points. Unless otherwise specified, the behavior with respect to supplementary characters and surrogate char values is as follows:

- The methods that only accept a `char` value cannot support supplementary characters. They treat `char` values from the surrogate ranges as undefined characters.
- The methods that accept an `int` value support all Unicode characters, including supplementary characters.

You can refer to the documentation of the [`Character`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Character.html) class for more information.

 

## Escape Sequence

A character preceded by a backslash (`\`) is an escape sequence and has special meaning to the compiler. The following table shows the Java escape sequences:

|Escape Sequence|Description|
|---|---|
|`\t`|Insert a tab in the text at this point.|
|`\b`|Insert a backspace in the text at this point.|
|`\n`|Insert a newline in the text at this point.|
|`\r`|Insert a carriage return in the text at this point.|
|`\f`|Insert a form feed in the text at this point.|
|`\'`|Insert a single quote character in the text at this point.|
|`\"`|Insert a double quote character in the text at this point.|
|`\\`|Insert a backslash character in the text at this point.|

When an escape sequence is encountered in a print statement, the compiler interprets it accordingly. For example, if you want to put quotes within quotes you must use the escape sequence, ", on the interior quotes. To print the sentence

```shell
She said "Hello!" to me.
```

Copy

you would write

```java
System.out.println("She said \"Hello!\" to me.");
```

# Strings

 

## Creating Strings

Strings, which are widely used in Java programming, are a sequence of characters. In the Java programming language, strings are objects.

The Java platform provides the [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class to create and manipulate strings.

The most direct way to create a string is to write:

```java
String greeting = "Hello world!";
```

Copy

In this case, "Hello world!" is a string literal—a series of characters in your code that is enclosed in double quotes. Whenever it encounters a string literal in your code, the compiler creates a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) object with its value—in this case, _Hello world!_.

As with any other object, you can create [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) objects by using the `new` keyword and a constructor. The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class has thirteen constructors that allow you to provide the initial value of the string using different sources, such as an array of characters:

```java
char[] helloArray = { 'h', 'e', 'l', 'l', 'o', '.' };
String helloString = new String(helloArray);
System.out.println(helloString);
```

Copy

The last line of this code snippet displays `hello`.

> Note: The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class is immutable, so that once it is created a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) object cannot be changed. The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class has a number of methods, some of which will be discussed below, that appear to modify strings. Since strings are immutable, what these methods really do is create and return a new string that contains the result of the operation.

 

## String Length

Methods used to obtain information about an object are known as accessor methods. One accessor method that you can use with strings is the [`length()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#length\(\)) method, which returns the number of characters contained in the string object. After the following two lines of code have been executed, `len` equals 17:

```java
String palindrome = "Dot saw I was Tod";
int len = palindrome.length();
```

Copy

A _palindrome_ is a word or sentence that is symmetric—it is spelled the same forward and backward, ignoring case and punctuation. Here is a short and inefficient program to reverse a palindrome string. It invokes the [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) method [`charAt(i)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#charAt\(int\)), which returns the _ith_ character in the string, counting from 0.

```java
public class StringDemo {
    public static void main(String[] args) {
        String palindrome = "Dot saw I was Tod";
        int len = palindrome.length();
        char[] tempCharArray = new char[len];
        char[] charArray = new char[len];
        
        // put original string in an 
        // array of chars
        for (int i = 0; i < len; i++) {
            tempCharArray[i] = 
                palindrome.charAt(i);
        } 
        
        // reverse array of chars
        for (int j = 0; j < len; j++) {
            charArray[j] =
                tempCharArray[len - 1 - j];
        }
        
        String reversePalindrome =
            new String(charArray);
        System.out.println(reversePalindrome);
    }
}
```

Copy

Running the program produces this output:

```shell
doT saw I was toD
```

Copy

To accomplish the string reversal, the program had to convert the string to an array of characters (first `for` loop), reverse the array into a second array (second `for` loop), and then convert back to a string. The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class includes a method, [`getChars()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#getChars\(int,int,char%5B%5D,int\)), to convert a string, or a portion of a string, into an array of characters so we could replace the first for loop in the program above with

```java
palindrome.getChars(0, len, tempCharArray, 0);
```

Copy

 

## Concatenating Strings

The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class includes a method for concatenating two strings:

```java
string1.concat(string2); 
```

Copy

This returns a new string that is `string1` with `string2` added to it at the end.

You can also use the [`concat()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#concat\(java.lang.String\)) method with string literals, as in:

```java
"My name is ".concat("Rumplestiltskin");
```

Copy

Strings are more commonly concatenated with the `+` operator, as in

```java
"Hello," + " world" + "!"
```

Copy

which results in

```java
"Hello, world!"
```

Copy

The `+` operator is widely used in print statements. For example:

```java
String string1 = "saw I was ";
System.out.println("Dot " + string1 + "Tod");
```

Copy

which prints

```shell
Dot saw I was Tod
```

Copy

Such a concatenation can be a mixture of any objects. For each object that is not a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html), its [`toString()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#toString\(\)) method is called to convert it to a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html).

> Note: Up until Java SE 15, the Java programming language does not permit literal strings to span lines in source files, so you must use the `+` concatenation operator at the end of each line in a multi-line string. For example:

```java
String quote = 
    "Now is the time for all good " +
    "men to come to the aid of their country.";
```

Copy

Breaking strings between lines using the `+` concatenation operator is, once again, very common in `print` statements.

Starting with Java SE 15, you can write two-dimensional string literals:

```java
String html = """
              <html>
                  <body>
                      <p>Hello, world</p>
                  </body>
              </html>
              """;
```

Copy

 

## Creating Format Strings

You have seen the use of the [`printf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#printf\(java.lang.String,java.lang.Object...\)) and [`format()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)) methods to print output with formatted numbers. The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class has an equivalent class method, [`format()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#format\(java.lang.String,java.lang.Object...\)), that returns a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) object rather than a [`PrintStream`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html) object.

Using [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html)'s static [`format()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#format\(java.lang.String,java.lang.Object...\)) method allows you to create a formatted string that you can reuse, as opposed to a one-time print statement. For example, instead of

```java
System.out.printf("The value of the float " +
                  "variable is %f, while " +
                  "the value of the " + 
                  "integer variable is %d, " +
                  "and the string is %s", 
                  floatVar, intVar, stringVar); 
```

Copy

you can write

```java
String fs;
fs = String.format("The value of the float " +
                   "variable is %f, while " +
                   "the value of the " + 
                   "integer variable is %d, " +
                   " and the string is %s",
                   floatVar, intVar, stringVar);
System.out.println(fs);
```

Copy

 

## Converting Strings to Numbers

Frequently, a program ends up with numeric data in a string object—a value entered by the user, for example.

The [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) subclasses that wrap primitive numeric types ([`Byte`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Byte.html), [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html), [`Double`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Double.html), [`Float`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Float.html), [`Long`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Long.html), and [`Short`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Short.html) each provide a class method named [`valueOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#valueOf\(java.lang.String\)) that converts a string to an object of that type. Here is an example, `ValueOfDemo`, that gets two strings from the command line, converts them to numbers, and performs arithmetic operations on the values:

```java
public class ValueOfDemo {
    public static void main(String[] args) {

        // this program requires two 
        // arguments on the command line 
        if (args.length == 2) {
            // convert strings to numbers
            float a = (Float.valueOf(args[0])).floatValue(); 
            float b = (Float.valueOf(args[1])).floatValue();

            // do some arithmetic
            System.out.println("a + b = " +
                               (a + b));
            System.out.println("a - b = " +
                               (a - b));
            System.out.println("a * b = " +
                               (a * b));
            System.out.println("a / b = " +
                               (a / b));
            System.out.println("a % b = " +
                               (a % b));
        } else {
            System.out.println("This program " +
                "requires two command-line arguments.");
        }
    }
}
```

Copy

The following is the output from the program when you use `4.5` and `87.2` for the command-line arguments:

```shell
a + b = 91.7
a - b = -82.7
a * b = 392.4
a / b = 0.0516055
a % b = 4.5
```

Copy

> Note: Each of the [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) subclasses that wrap primitive numeric types also provides a `parseXXXX()` method. For example, [`parseFloat()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Float.html#parseFloat\(java.lang.String\)) can be used to convert strings to primitive numbers. Since a primitive type is returned instead of an object, the [`parseFloat()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Float.html#parseFloat\(java.lang.String\)) method is more direct than the [`valueOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#valueOf\(java.lang.String\)) method. For example, in the `ValueOfDemo` program, we could use:

```java
float a = Float.parseFloat(args[0]);
float b = Float.parseFloat(args[1]);
```

Copy

 

## Converting Numbers to Strings

Sometimes you need to convert a number to a string because you need to operate on the value in its string form. There are several easy ways to convert a number to a string:

```java
int i;
// Concatenate "i" with an empty string; conversion is handled for you.
String s1 = "" + i;
```

Copy

or

```java
// The valueOf class method.
String s2 = String.valueOf(i);
```

Copy

Each of the [`Number`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html) subclasses includes a class method, [`toString()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Number.html#toString\(\)), that will convert its primitive type to a string. For example:

```java
int i;
double d;
String s3 = Integer.toString(i); 
String s4 = Double.toString(d); 
```

Copy

The `ToStringDemo` example uses the [`toString()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#toString\(\)) method to convert a number to a string. The program then uses some string methods to compute the number of digits before and after the decimal point:

```java
public class ToStringDemo {
    
    public static void main(String[] args) {
        double d = 858.48;
        String s = Double.toString(d);
        
        int dot = s.indexOf('.');
        
        System.out.println(dot + " digits " +
            "before decimal point.");
        System.out.println( (s.length() - dot - 1) +
            " digits after decimal point.");
    }
}
```

Copy

The output of this program is:

```shell
3 digits before decimal point.
2 digits after decimal point.
```

Copy

 

## Getting Characters and Substrings by Index

The String class has a number of methods for examining the contents of strings, finding characters or substrings within a string, changing case, and other tasks.

You can get the character at a particular index within a string by invoking the [`charAt()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#charAt\(int\)) accessor method. The index of the first character is 0, while the index of the last character is `length() - 1`. For example, the following code gets the character at index 9 in a string:

```java
String anotherPalindrome = "Niagara. O roar again!"; 
char aChar = anotherPalindrome.charAt(9);
```

Copy

Indices begin at 0, so the character at index 9 is 'O', as illustrated in the following figure:

![Char indexes in a string](https://dev.java/assets/images/numbers-strings/02_chars.png)

Char indexes in a string

If you want to get more than one consecutive character from a string, you can use the substring method. The substring method has two versions:

- [`String substring(int beginIndex, int endIndex)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#substring\(int,int\)): Returns a new string that is a substring of this string. The substring begins at the specified `beginIndex` and extends to the character at index `endIndex - 1`.
- [`String substring(int beginIndex)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#substring\(int\)): Returns a new string that is a substring of this string. The integer argument specifies the index of the first character. Here, the returned substring extends to the end of the original string.

The following code gets from the Niagara palindrome the substring that extends from index 11 up to, but not including, index 15, which is the word "roar":

```java
String anotherPalindrome = "Niagara. O roar again!"; 
String roar = anotherPalindrome.substring(11, 15); 
```

Copy

![Extracting characters from a string with substring](https://dev.java/assets/images/numbers-strings/03_substring.png)

Extracting characters from a string with substring

 

## Other Methods for Manipulating Strings

Here are several other [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) methods for manipulating strings:

- [`String[] split(String regex)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#split\(java.lang.String\)) and [`String[] split(String regex, int limit)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#split\(java.lang.String,int\)): Searches for a match as specified by the string argument (which contains a regular expression) and splits this string into an array of strings accordingly. The optional integer argument specifies the maximum size of the returned array. Regular expressions are covered in the section titled [Regular Expressions](https://dev.java/learn/regex/).
- [`CharSequence subSequence(int beginIndex, int endIndex)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#subSequence\(int,int\)): Returns a new character sequence constructed from `beginIndex` index up until `endIndex - 1`.
- [`String trim()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#trim\(\)): Returns a copy of this string with leading and trailing white space removed.
- [`String toLowerCase()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#toLowerCase\(\)) and [`String toUpperCase()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#toUpperCase\(\)): Returns a copy of this string converted to lowercase or uppercase. If no conversions are necessary, these methods return the original string.

 

## Searching for Characters and Substrings in a String

Here are some other [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) methods for finding characters or substrings within a string. The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class provides accessor methods that return the position within the string of a specific character or substring: [`indexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#indexOf\(java.lang.String\)) and [`lastIndexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(java.lang.String\)). The [`indexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#indexOf\(java.lang.String\)) methods search forward from the beginning of the string, and the [`lastIndexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(java.lang.String\)) methods search backward from the end of the string. If a character or substring is not found, [`indexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#indexOf\(java.lang.String\)) and [`lastIndexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(java.lang.String\)) return -1.

The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class also provides a search method, contains, that returns `true` if the string contains a particular character sequence. Use this method when you only need to know that the string contains a character sequence, but the precise location is not important.

The search methods are the following:

- [`int indexOf(int ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#indexOf\(int\)) and [`int lastIndexOf(int ch)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(int\)): Returns the index of the first (last) occurrence of the specified character.
- [`int indexOf(int ch, int fromIndex)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#indexOf\(int,int\)) and [`int lastIndexOf(int ch, int fromIndex)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(int,int\)): Returns the index of the first (last) occurrence of the specified character, searching forward (backward) from the specified index.
- [`int indexOf(String str)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#indexOf\(java.lang.String\)) and [`int lastIndexOf(String str)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(java.lang.String\)): Returns the index of the first (last) occurrence of the specified substring.
- [`int indexOf(String str, int fromIndex)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#indexOf\(java.lang.String,int\)) and [`int lastIndexOf(String str, int fromIndex)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(java.lang.String,int\)): Returns the index of the first (last) occurrence of the specified substring, searching forward (backward) from the specified index.
- [`boolean contains(CharSequence s)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#contains\(java.lang.CharSequence\)): Returns `true` if the string contains the specified character sequence.

> Note: [`CharSequence`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/CharSequence.html) is an interface that is implemented by the [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class. Therefore, you can use a string as an argument for the [`contains()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#contains\(java.lang.CharSequence\)) method.

 

## Replacing Characters and Substrings into a String

The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class has very few methods for inserting characters or substrings into a string. In general, they are not needed: You can create a new string by concatenation of substrings you have removed from a string with the substring that you want to insert.

The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class does have four methods for replacing found characters or substrings, however. They are:

- [`String replace(char oldChar, char newChar)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#replace\(char,char\)): Returns a new string resulting from replacing all occurrences of `oldChar` in this string with `newChar`.
- [`String replace(CharSequence target, CharSequence replacement)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#replace\(java.lang.CharSequence,java.lang.CharSequence\)): Replaces each substring of this string that matches the literal target sequence with the specified literal replacement sequence.
- [`String replaceAll(String regex, String replacement)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#replaceAll\(java.lang.String,java.lang.String\)): Replaces each substring of this string that matches the given regular expression with the given replacement.
- [`String replaceFirst(String regex, String replacement)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#replaceFirst\(java.lang.String,java.lang.String\)): Replaces the first substring of this string that matches the given regular expression with the given replacement.

Regular expressions are discussed in the lesson titled [Regular Expressions](https://dev.java/learn/regex/).

 

## The String Class in Action

The following class, `Filename`, illustrates the use of [`lastIndexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(java.lang.String\)) and [`substring()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#substring\(int,int\)) to isolate different parts of a file name.

> Note: The methods in the following `Filename` class do not do any error checking and assume that their argument contains a full directory path and a filename with an extension. If these methods were production code, they would verify that their arguments were properly constructed.

```java
public class Filename {
    private String fullPath;
    private char pathSeparator, 
                 extensionSeparator;

    public Filename(String str, char sep, char ext) {
        fullPath = str;
        pathSeparator = sep;
        extensionSeparator = ext;
    }

    public String extension() {
        int dot = fullPath.lastIndexOf(extensionSeparator);
        return fullPath.substring(dot + 1);
    }

    // gets filename without extension
    public String filename() {
        int dot = fullPath.lastIndexOf(extensionSeparator);
        int sep = fullPath.lastIndexOf(pathSeparator);
        return fullPath.substring(sep + 1, dot);
    }

    public String path() {
        int sep = fullPath.lastIndexOf(pathSeparator);
        return fullPath.substring(0, sep);
    }
}
```

Copy

Here is a program, `FilenameDemo`, that constructs a `Filename` object and calls all of its methods:

```java
public class FilenameDemo {
    public static void main(String[] args) {
        final String FPATH = "/home/user/index.html";
        Filename myHomePage = new Filename(FPATH, '/', '.');
        System.out.println("Extension = " + myHomePage.extension());
        System.out.println("Filename = " + myHomePage.filename());
        System.out.println("Path = " + myHomePage.path());
    }
}
```

Copy

And here is the output from the program:

```shell
Extension = html
Filename = index
Path = /home/user
```

Copy

As shown in the following figure, our extension method uses [`lastIndexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(java.lang.String\)) to locate the last occurrence of the period (`.`) in the file name. Then substring uses the return value of [`lastIndexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(java.lang.String\)) to extract the file name extension — that is, the substring from the period to the end of the string. This code assumes that the file name has a period in it; if the file name does not have a period, [`lastIndexOf()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#lastIndexOf\(java.lang.String\)) returns -1, and the substring method throws a [`StringIndexOutOfBoundsException`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringIndexOutOfBoundsException.html).

Also, notice that the extension method uses `dot + 1` as the argument to [`substring()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#substring\(int,int\)). If the period character (`.`) is the last character of the string, `dot + 1` is equal to the length of the string, which is one larger than the largest index into the string (because indices start at 0). This is a legal argument to [`substring()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#substring\(int,int\)) because that method accepts an index equal to, but not greater than, the length of the string and interprets it to mean "the end of the string."

 

## Comparing Strings and Portions of Strings

The [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class has a number of methods for comparing strings and portions of strings. The following table lists these methods.

- [`boolean endsWith(String suffix)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#endsWith\(java.lang.String\)) and [`boolean startsWith(String prefix)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#startsWith\(java.lang.String\)): Returns `true` if this string ends with or begins with the substring specified as an argument to the method.
- [`boolean startsWith(String prefix, int offset)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#startsWith\(java.lang.String,int\)): Considers the string beginning at the index `offset`, and returns `true` if it begins with the substring specified as an argument.
- [`int compareTo(String anotherString)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#compareTo\(java.lang.String\)): Compares two strings lexicographically. Returns an integer indicating whether this string is greater than (result is > 0), equal to (result is = 0), or less than (result is < 0) the argument.
- [`int compareToIgnoreCase(String str)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#compareToIgnoreCase\(java.lang.String\)): Compares two strings lexicographically, ignoring differences in case. Returns an integer indicating whether this string is greater than (result is > 0), equal to (result is = 0), or less than (result is < 0) the argument.
- [`boolean equals(Object anObject)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#equals\(java.lang.Object\)): Returns `true` if and only if the argument is a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) object that represents the same sequence of characters as this object.
- [`boolean equalsIgnoreCase(String anotherString)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#equalsIgnoreCase\(java.lang.String\)): Returns `true` if and only if the argument is a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) object that represents the same sequence of characters as this object, ignoring differences in case.
- [`boolean regionMatches(int toffset, String other, int ooffset, int len)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#regionMatches\(int,java.lang.String,int,int\)): Tests whether the specified region of this string matches the specified region of the [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) argument. Region is of length `len` and begins at the index `toffset` for this string and `ooffset` for the other string.
- [`boolean regionMatches(boolean ignoreCase, int toffset, String other, int ooffset, int len)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#regionMatches\(boolean,int,java.lang.String,int,int\)): Tests whether the specified region of this string matches the specified region of the [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) argument. Region is of length `len` and begins at the index `toffset` for this string and `ooffset` for the other string. The boolean argument indicates whether case should be ignored; if `true`, case is ignored when comparing characters.
- [`boolean matches(String regex)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#matches\(java.lang.String\)): Tests whether this string matches the specified regular expression. Regular expressions are discussed in the lesson titled [Regular Expressions](https://dev.java/learn/regex/).

The following program, `RegionMatchesDemo`, uses the [`regionMatches()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#regionMatches\(int,java.lang.String,int,int\)) method to search for a string within another string:

```java
public class RegionMatchesDemo {
    public static void main(String[] args) {
        String searchMe = "Green Eggs and Ham";
        String findMe = "Eggs";
        int searchMeLength = searchMe.length();
        int findMeLength = findMe.length();
        boolean foundIt = false;
        for (int i = 0; 
             i <= (searchMeLength - findMeLength);
             i++) {
           if (searchMe.regionMatches(i, findMe, 0, findMeLength)) {
              foundIt = true;
              System.out.println(searchMe.substring(i, i + findMeLength));
              break;
           }
        }
        if (!foundIt)
            System.out.println("No match found.");
    }
}
```

Copy

The output from this program is `Eggs`.

The program steps through the string referred to by `searchMe()` one character at a time. For each character, the program calls the [`regionMatches()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html#regionMatches\(int,java.lang.String,int,int\)) method to determine whether the substring beginning with the current character matches the string the program is looking for.

# String Builders

 

## The StringBuilder Class

[`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) objects are like [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) objects, except that they can be modified. Internally, these objects are treated like variable-length arrays that contain a sequence of characters. At any point, the length and content of the sequence can be changed through method invocations.

Strings should always be used unless string builders offer an advantage in terms of simpler code (see the sample program at the end of this section) or better performance. Prior to Java SE 9, if you need to concatenate a large number of strings, appending to a StringBuilder object may be more efficient. String concatenation has been optimized in Java SE 9, making concatenation more efficient than [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) appending.

 

## Length and Capacity

The [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) class, like the [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class, has a [`length()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#length\(\)) method that returns the length of the character sequence in the builder.

Unlike strings, every string builder also has a capacity, the number of character spaces that have been allocated. The capacity, which is returned by the [`capacity()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#capacity\(\)) method, is always greater than or equal to the length (usually greater than) and will automatically expand as necessary to accommodate additions to the string builder.

You can use the following constructors of the [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) class:

- [`StringBuilder()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#%3Cinit%3E\(\)): Creates an empty string builder with a capacity of 16 (16 empty elements).
- [`StringBuilder(CharSequence cs)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#%3Cinit%3E\(java.lang.CharSequence\)): Constructs a string builder containing the same characters as the specified [`CharSequence`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/CharSequence.html), plus an extra 16 empty elements trailing the [`CharSequence`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/CharSequence.html).
- [`StringBuilder(int initCapacity)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#%3Cinit%3E\(int\)): Creates an empty string builder with the specified initial capacity.
- [`StringBuilder(String s)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#%3Cinit%3E\(java.lang.String\)): Creates a string builder whose value is initialized by the specified string, plus an extra 16 empty elements trailing the string.

For example, the following code

```java
// creates empty builder, capacity 16
StringBuilder sb = new StringBuilder();
// adds 9 character string at beginning
sb.append("Greetings");
```

Copy

will produce a string builder with a length of 9 and a capacity of 16:

![Length and capacity of a `StringBuilder`](https://dev.java/assets/images/numbers-strings/04_stringbuilder.png)

Length and capacity of a `StringBuilder`

The [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) class has some methods related to length and capacity that the [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) class does not have:

- [`void setLength(int newLength)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#setLength\(int\)): Sets the length of the character sequence. If `newLength` is less than [`length()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#length\(\)), the last characters in the character sequence are truncated. If `newLength` is greater than [`length()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#length\(\)), `null` characters are added at the end of the character sequence.
- [`void ensureCapacity(int minCapacity)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#ensureCapacity\(int\)): Ensures that the capacity is at least equal to the specified minimum.

A number of operations (for example, [`append()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#append\(java.lang.Object\)), [`insert()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#insert\(int,java.lang.Object\)), or [`setLength()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#setLength\(int\)) can increase the length of the character sequence in the string builder so that the resultant [`length()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#length\(\)) would be greater than the current [`capacity()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#capacity\(\)). When this happens, the capacity is automatically increased.

 

## StringBuilder Operations

The principal operations on a [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) that are not available in [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) are the [`append()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#append\(java.lang.Object\)) and [`insert()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#insert\(int,java.lang.Object\)) methods, which are overloaded so as to accept data of any type. Each converts its argument to a string and then appends or inserts the characters of that string to the character sequence in the string builder. The append method always adds these characters at the end of the existing character sequence, while the insert method adds the characters at a specified point.

Here are a number of the methods of the [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) class.

- You can append any primitive type or object to a string builder with an [`append()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#append\(java.lang.Object\)) method. The data is converted to a string before the append operation takes place.
- The [`delete(int start, int end)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#delete\(int,int\)) method deletes the subsequence from `start` to `end - 1` (inclusive) in the [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html)'s char sequence.
- You can delete the `char` at index `index` with the method [`deleteCharAt(int index)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#deleteCharAt\(int\)).
- You can insert any primitive type or object at the given `offset` with one of the [`insert(int offset)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#insert\(int,java.lang.Object\)) methods. These methods take the element to be inserted as a second argument. The data is converted to a string before the insert operation takes place.
- You can replace characters with the methods [`replace(int start, int end, String s)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#replace\(int,int,java.lang.String\)) and [`setCharAt(int index, char c)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#setCharAt\(int,char\)).
- You can reverse the sequence of characters in this string builder with the [`reverse()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#reverse\(\)) method.
- You can return a string that contains the character sequence in the builder with the [`toString()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#toString\(\)) method.

> Note: You can use any [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html) method on a [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) object by first converting the string builder to a string with the [`toString()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#toString\(\)) method of the [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) class. Then convert the string back into a string builder using the [`StringBuilder(String string)`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#%3Cinit%3E\(java.lang.String\)) constructor.

 

## StringBuilder in Action

The `StringDemo` program that was listed in the section titled "Strings" is an example of a program that would be more efficient if a [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) were used instead of a [`String`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/String.html).

`StringDemo` reversed a palindrome. Here, once again, is its listing:

```java
public class StringDemo {
    public static void main(String[] args) {
        String palindrome = "Dot saw I was Tod";
        int len = palindrome.length();
        char[] tempCharArray = new char[len];
        char[] charArray = new char[len];
        
        // put original string in an 
        // array of chars
        for (int i = 0; i < len; i++) {
            tempCharArray[i] = 
                palindrome.charAt(i);
        } 
        
        // reverse array of chars
        for (int j = 0; j < len; j++) {
            charArray[j] =
                tempCharArray[len - 1 - j];
        }
        
        String reversePalindrome =
            new String(charArray);
        System.out.println(reversePalindrome);
    }
}
```

Copy

Running the program produces this output:

```shell
doT saw I was toD
```

Copy

To accomplish the string reversal, the program converts the string to an array of characters (first `for` loop), reverses the array into a second array (second `for` loop), and then converts back to a string.

If you convert the palindrome string to a string builder, you can use the [`reverse()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html#reverse\(\)) method in the [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) class. It makes the code simpler and easier to read:

```java
public class StringBuilderDemo {
    public static void main(String[] args) {
        String palindrome = "Dot saw I was Tod";
         
        StringBuilder sb = new StringBuilder(palindrome);
        
        sb.reverse();  // reverse it
        
        System.out.println(sb);
    }
}
```

Copy

Running this program produces the same output:

```shell
doT saw I was toD
```

Copy

Note that [`println()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#println\(java.lang.Object\)) prints a string builder, as in:

```java
System.out.println(sb);
```

Copy

because `sb.toString()` is called implicitly, as it is with any other object in a [`println`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/PrintStream.html#println\(java.lang.Object\)) invocation.

> Note: There is also a [`StringBuffer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuffer.html) class that is exactly the same as the [`StringBuilder`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuilder.html) class, except that it is thread-safe by virtue of having its methods synchronized. Unless you absolutely need a thread-safe class, you do not need to use [`StringBuffer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/StringBuffer.html).


# Autoboxing and Unboxing

 

## Autoboxing and Unboxing

_Autoboxing_ is the automatic conversion that the Java compiler makes between the primitive types and their corresponding object wrapper classes. For example, converting an `int` to an [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html), a `double` to a [`Double`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Double.html), and so on. If the conversion goes the other way, this is called unboxing.

Here is the simplest example of autoboxing:

```java
Character ch = 'a';
```

Copy

The rest of the examples in this section use generics. If you are not yet familiar with the syntax of generics, see the [Generics section](https://dev.java/learn/generics/).

Consider the following code:

```java
List<Integer> ints = new ArrayList<>();
for (int i = 1; i < 50; i += 2)
    ints.add(i);
```

Copy

Although you add the `int` values as primitive types, rather than [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) objects, to `ints`, the code compiles. Because `ints` is a list of [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) objects, not a list of `int` values, you may wonder why the Java compiler does not issue a compile-time error. The compiler does not generate an error because it creates an [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) object from `i` and adds the object to `ints`. Thus, the compiler converts the previous code to the following at runtime:

```java
List<Integer> ints = new ArrayList<>();
for (int i = 1; i < 50; i += 2)
    ints.add(Integer.valueOf(i));
```

Copy

Converting a primitive value (an `int`, for example) into an object of the corresponding wrapper class [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) is called autoboxing. The Java compiler applies autoboxing when a primitive value is:

- Passed as a parameter to a method that expects an object of the corresponding wrapper class.
- Assigned to a variable of the corresponding wrapper class.

Consider the following method:

```java
public static int sumEven(List<Integer> ints) {
    int sum = 0;
    for (Integer i: ints) {
        if (i % 2 == 0) {
            sum+=i;
        }
    }
    return sum;
}
```

Copy

Because the remainder (`%`) and unary plus (`+=`) operators do not apply to [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) objects, you may wonder why the Java compiler compiles the method without issuing any errors. The compiler does not generate an error because it invokes the [`intValue()`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html#intValue\(\)) method to convert an [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) to an `int` at runtime:

```java
public static int sumEven(List<Integer> ints){
    int sum=0;
    for(Integer i:ints) {
        if(i.intValue()%2==0) {
            sum+=i.intValue();
        }
    }
    return sum;
}
```

Copy

Converting an object of a wrapper type [`Integer`](https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/lang/Integer.html) to its corresponding primitive (`int`) value is called unboxing. The Java compiler applies unboxing when an object of a wrapper class is:

- Passed as a parameter to a method that expects a value of the corresponding primitive type.
- Assigned to a variable of the corresponding primitive type.

The `Unboxing` example shows how this works:

```java
import java.util.ArrayList;
import java.util.List;

public class Unboxing {

    public static void main(String[] args) {
        Integer i = Integer.valueOf(-8);

        // 1. Unboxing through method invocation
        int absVal = absoluteValue(i);
        System.out.println("absolute value of " + i + " = " + absVal);

        List<Double> doubles = new ArrayList<>();
        doubles.add(3.1416);    // Π is autoboxed through method invocation.

        // 2. Unboxing through assignment
        double pi = doubles.get(0);
        System.out.println("pi = " + pi);
    }

    public static int absoluteValue(int i) {
        return (i < 0) ? -i : i;
    }
}
```

Copy

The program prints the following:

```shell
absolute value of -8 = 8
pi = 3.1416
```

Copy

Autoboxing and unboxing lets developers write cleaner code, making it easier to read. The following table lists the primitive types and their corresponding wrapper classes, which are used by the Java compiler for autoboxing and unboxing:

| Primitive type | Wrapper class |
| -------------- | ------------- |
| boolean        | Boolean       |
| byte           | Byte          |
| char           | Character     |
| float          | Float         |
| int            | Integer       |
| long           | Long          |
| short          | Short         |
| double         | Double        |