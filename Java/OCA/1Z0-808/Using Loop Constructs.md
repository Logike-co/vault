- Create and use while loops
- Create and use for loops including the enhanced for loop
- Create and use do/while loops
- Compare loop constructs
- Use break and continue  

# Control Flow Statements

 

## The If-Then Statement

The `if-then` statement is the most basic of all the control flow statements. It tells your program to execute a certain section of code only if a particular test evaluates to `true`. For example, the `Bicycle` class could allow the brakes to decrease the bicycle's speed only if the bicycle is already in motion. One possible implementation of the `applyBrakes()` method could be as follows:

```java
void applyBrakes() {
    // the "if" clause: bicycle must be moving
    if (isMoving){
        // the "then" clause: decrease current speed
        currentSpeed--;
    }
}
```

Copy

If this test evaluates to `false` (meaning that the bicycle is not in motion), control jumps to the end of the `if-then` statement.

In addition, the opening and closing braces are optional, provided that the "then" clause contains only one statement:

```java
void applyBrakes() {
    // same as above, but without braces
    if (isMoving)
        currentSpeed--;
}
```

Copy

Deciding when to omit the braces is a matter of personal taste. Omitting them can make the code more brittle. If a second statement is later added to the "then" clause, a common mistake would be forgetting to add the newly required braces. The compiler cannot catch this sort of error; you will just get the wrong results.

 

## The If-Then-Else Statement

The `if-then-else` statement provides a secondary path of execution when an "if" clause evaluates to `false`. You could use an `if-then-else` statement in the `applyBrakes()` method to take some action if the brakes are applied when the bicycle is not in motion. In this case, the action is to simply print an error message stating that the bicycle has already stopped.

```java
void applyBrakes() {
    if (isMoving) {
        currentSpeed--;
    } else {
        System.err.println("The bicycle has already stopped!");
    }
}
```

Copy

The following program, `IfElseDemo`, assigns a grade based on the value of a test score: an A for a score of 90% or above, a B for a score of 80% or above, and so on.

```java
class IfElseDemo {
    public static void main(String[] args) {

        int testscore = 76;
        char grade;

        if (testscore >= 90) {
            grade = 'A';
        } else if (testscore >= 80) {
            grade = 'B';
        } else if (testscore >= 70) {
            grade = 'C';
        } else if (testscore >= 60) {
            grade = 'D';
        } else {
            grade = 'F';
        }
        System.out.println("Grade = " + grade);
    }
}
```

Copy

The output from the program is:

```shell
Grade = C
```

Copy

You may have noticed that the value of `testscore` can satisfy more than one expression in the compound statement: `76 >= 70` and `76 >= 60`. However, once a condition is satisfied, the appropriate statements are executed (`grade = 'C';`) and the remaining conditions are not evaluated.

 

## The While and Do-while Statements

The `while` statement continually executes a block of statements while a particular condition is `true`. Its syntax can be expressed as:

```java
while (expression) {
     statement(s)
}
```

Copy

The `while` statement evaluates expression, which must return a `boolean` value. If the expression evaluates to `true`, the `while` statement executes the `statement(s)` in the while block. The `while` statement continues testing the expression and executing its block until the expression evaluates to `false`. Using the `while` statement to print the values from 1 through 10 can be accomplished as in the following `WhileDemo` program:

```java
class WhileDemo {
    public static void main(String[] args){
        int count = 1;
        while (count < 11) {
            System.out.println("Count is: " + count);
            count++;
        }
    }
}
```

Copy

You can implement an infinite loop using the `while` statement as follows:

```java
while (true){
    // your code goes here
}
```

Copy

The Java programming language also provides a `do-while` statement, which can be expressed as follows:

```java
do {
     statement(s)
} while (expression);
```

Copy

The difference between `do-while` and `while` is that `do-while` evaluates its expression at the bottom of the loop instead of the top. Therefore, the statements within the `do` block are always executed at least once, as shown in the following `DoWhileDemo` program:

```java
class DoWhileDemo {
    public static void main(String[] args){
        int count = 1;
        do {
            System.out.println("Count is: " + count);
            count++;
        } while (count < 11);
    }
}
```

Copy

 

## The For Statement

The `for` statement provides a compact way to iterate over a range of values. Programmers often refer to it as the "for loop" because of the way in which it repeatedly loops until a particular condition is satisfied. The general form of the `for` statement can be expressed as follows:

```java
for (initialization; termination; increment) {
    statement(s)
}
```

Copy

When using this version of the for statement, keep in mind that:

- The _initialization_ expression initializes the loop; it is executed once, as the loop begins.
- When the _termination_ expression evaluates to `false`, the loop terminates.
- The _increment_ expression is invoked after each iteration through the loop; it is perfectly acceptable for this expression to increment _or_ decrement a value.

The following program, `ForDemo`, uses the general form of the `for` statement to print the numbers 1 through 10 to standard output:

```java
class ForDemo {
    public static void main(String[] args){
         for(int i = 1; i < 11; i++){
              System.out.println("Count is: " + i);
         }
    }
}
```

Copy

The output of this program is:

```shell
Count is: 1
Count is: 2
Count is: 3
Count is: 4
Count is: 5
Count is: 6
Count is: 7
Count is: 8
Count is: 9
Count is: 10
```

Copy

Notice how the code declares a variable within the initialization expression. The scope of this variable extends from its declaration to the end of the block governed by the `for` statement, so it can be used in the termination and increment expressions as well. If the variable that controls a `for` statement is not needed outside of the loop, it is best to declare the variable in the initialization expression. The names `i`, `j`, and `k` are often used to control `for` loops; declaring them within the initialization expression limits their life span and reduces errors.

The three expressions of the `for` loop are optional; an infinite loop can be created as follows:

```java
// infinite loop
for ( ; ; ) {

    // your code goes here
}
```

Copy

The `for` statement also has another form designed for iteration through Collections and arrays. This form is sometimes referred to as the _enhanced for_ statement, and can be used to make your loops more compact and easy to read. To demonstrate, consider the following array, which holds the numbers 1 through 10:

```java
int[] numbers = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
```

Copy

The following program, `EnhancedForDemo`, uses the _enhanced for_ to loop through the array:

```java
class EnhancedForDemo {
    public static void main(String[] args){
         int[] numbers =
             {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
         for (int item : numbers) {
             System.out.println("Count is: " + item);
         }
    }
}
```

Copy

In this example, the variable `item` holds the current value from the numbers array. The output from this program is the same as before:

```shell
Count is: 1
Count is: 2
Count is: 3
Count is: 4
Count is: 5
Count is: 6
Count is: 7
Count is: 8
Count is: 9
Count is: 10
```

Copy

We recommend using this form of the `for` statement instead of the general form whenever possible.

 

## The Break Statement

The `break` statement has two forms: labeled and unlabeled. You saw the unlabeled form in the previous discussion of the `switch` statement. You can also use an unlabeled `break` to terminate a `for`, `while`, or `do-while` loop, as shown in the following `BreakDemo` program:

```java
class BreakDemo {
    public static void main(String[] args) {

        int[] arrayOfInts =
            { 32, 87, 3, 589,
              12, 1076, 2000,
              8, 622, 127 };
        int searchfor = 12;

        int i;
        boolean foundIt = false;

        for (i = 0; i < arrayOfInts.length; i++) {
            if (arrayOfInts[i] == searchfor) {
                foundIt = true;
                break;
            }
        }

        if (foundIt) {
            System.out.println("Found " + searchfor + " at index " + i);
        } else {
            System.out.println(searchfor + " not in the array");
        }
    }
}
```

Copy

This program searches for the number 12 in an array. The `break` statement, terminates the `for` loop when that value is found. Control flow then transfers to the statement after the `for` loop. This program's output is:

```shell
Found 12 at index 4
```

Copy

An unlabeled `break` statement terminates the innermost `switch`, `for`, `while`, or `do-while` statement, but a labeled `break` terminates an outer statement. The following program, `BreakWithLabelDemo`, is similar to the previous program, but uses nested `for` loops to search for a value in a two-dimensional array. When the value is found, a labeled `break` terminates the outer `for` loop (labeled "search"):

```java
class BreakWithLabelDemo {
    public static void main(String[] args) {

        int[][] arrayOfInts = {
            {  32,   87,    3, 589 },
            {  12, 1076, 2000,   8 },
            { 622,  127,   77, 955 }
        };
        int searchfor = 12;

        int i;
        int j = 0;
        boolean foundIt = false;

    search:
        for (i = 0; i < arrayOfInts.length; i++) {
            for (j = 0; j < arrayOfInts[i].length;
                 j++) {
                if (arrayOfInts[i][j] == searchfor) {
                    foundIt = true;
                    break search;
                }
            }
        }

        if (foundIt) {
            System.out.println("Found " + searchfor + " at " + i + ", " + j);
        } else {
            System.out.println(searchfor + " not in the array");
        }
    }
}
```

Copy

This is the output of the program.

```shell
Found 12 at 1, 0
```

Copy

The `break` statement terminates the labeled statement; it does not transfer the flow of control to the label. Control flow is transferred to the statement immediately following the labeled (terminated) statement.

 

## The Continue Statement

The `continue` statement skips the current iteration of a `for`, `while`, or `do-while` loop. The unlabeled form skips to the end of the innermost loop's body and evaluates the boolean expression that controls the loop. The following program, `ContinueDemo`, steps through a `String`, counting the occurrences of the letter `p`. If the current character is not a `p`, the `continue` statement skips the rest of the loop and proceeds to the next character. If it is a `p`, the program increments the letter count.

```java
class ContinueDemo {
    public static void main(String[] args) {

        String searchMe = "peter piper picked a " + "peck of pickled peppers";
        int max = searchMe.length();
        int numPs = 0;

        for (int i = 0; i < max; i++) {
            // interested only in p's
            if (searchMe.charAt(i) != 'p')
                continue;

            // process p's
            numPs++;
        }
        System.out.println("Found " + numPs + " p's in the string.");
    }
}
```

Copy

Here is the output of this program:

```shell
Found 9 p's in the string.
```

Copy

To see this effect more clearly, try removing the `continue` statement and recompiling. When you run the program again, the count will be wrong, saying that it found 35 `p`'s instead of 9.

A labeled `continue` statement skips the current iteration of an outer loop marked with the given label. The following example program, `ContinueWithLabelDemo`, uses nested loops to search for a substring within another string. Two nested loops are required: one to iterate over the substring and one to iterate over the string being searched. The following program, `ContinueWithLabelDemo`, uses the labeled `test` of `continue` to skip an iteration in the outer loop.

```java
class ContinueWithLabelDemo {
    public static void main(String[] args) {

        String searchMe = "Look for a substring in me";
        String substring = "sub";
        boolean foundIt = false;

        int max = searchMe.length() -
                  substring.length();

    test:
        for (int i = 0; i <= max; i++) {
            int n = substring.length();
            int j = i;
            int k = 0;
            while (n-- != 0) {
                if (searchMe.charAt(j++) != substring.charAt(k++)) {
                    continue test;
                }
            }
            foundIt = true;
                break test;
        }
        System.out.println(foundIt ? "Found it" : "Didn't find it");
    }
}
```

Copy

Here is the output from this program.

```shell
Found it
```

Copy

 

## The Return Statement

The next branching statements is the `return` statement. The `return` statement exits from the current method, and control flow returns to where the method was invoked. The `return` statement has two forms: one that returns a value, and one that does not. To return a value, simply put the value (or an expression that calculates the value) after the `return` keyword.

```java
return ++count;
```

Copy

The data type of the returned value must match the type of the method's declared `return` value. When a method is declared `void`, use the form of `return` that doesn't return a value.

```java
return;
```

Copy

The Classes and Objects section will cover everything you need to know about writing methods.

 

## The Yield Statement

The last branching statement is the `yield` statement. The `yield` statement exits from the current `switch` expression it is in. A `yield` statement is always followed by an expression that must produce a value. This expression must not be `void`. The value of this expression is the value produced by the enclosing `switch` expression.

Here is an example of a `yield` statement.

```java
class Test {
    enum Day {
        MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
    }

    public int calculate(Day d) {
        return switch (d) {
            case SATURDAY, SUNDAY -> 0;
                default -> {
                    int remainingWorkDays = 5 - d.ordinal();
                    yield remainingWorkDays;
                }
            };
    }
}
```

# Branching with Switch Statements

 

## Using Switch Statements to Control the Flow of Your Program

The `switch` statement is one of the five control flow statements available in the Java language. It allows for any number of execution path. A `switch` statement takes a selector variable as an argument and uses the value of this variable to choose the path that will be executed.

You must choose the type of your selector variable among the following types:

- `byte`, `short`, `char`, and `int` primitive data types
- `Character`, `Byte`, `Short`, and `Integer` wrapper types
- enumerated types
- the `String` type.

It is worth noting that the following primitive types cannot be used for the type of your selector variable: `boolean`, `long`, `float`, and `double`.

Let us see a first example of a `switch` statement.

```java
int quarter = ...; // any value

String quarterLabel = null;
switch (quarter) {
    case 0: quarterLabel = "Q1 - Winter"; 
            break;
    case 1: quarterLabel = "Q2 - Spring"; 
            break;
    case 2: quarterLabel = "Q3 - Summer"; 
            break;
    case 3: quarterLabel = "Q3 - Summer"; 
            break;
    default: quarterLabel = "Unknown quarter";
};
```

Copy

The body of a `switch` statement is known as a `switch` block. A statement in the `switch` block can be labeled with one or more `case` or `default` labels. The `switch` statement evaluates its expression, then executes all statements that follow the matching `case` label.

You may have noticed the use of the `break` keyword. Each `break` statement terminates the enclosing `switch` statement. Control flow continues with the first statement following the `switch` block. The `break` statements are necessary because without them, statements in `switch` blocks fall through. All statements after the matching `case` label are executed in sequence, regardless of the expression of subsequent `case` labels, until a `break` statement is encountered.

The following code uses fall through to fill the `futureMonths` list.

```java
int month = 8;
List<String> futureMonths = new ArrayList<>();

switch (month) {
    case 1:  futureMonths.add("January");
    case 2:  futureMonths.add("February");
    case 3:  futureMonths.add("March");
    case 4:  futureMonths.add("April");
    case 5:  futureMonths.add("May");
    case 6:  futureMonths.add("June");
    case 7:  futureMonths.add("July");
    case 8:  futureMonths.add("August");
    case 9:  futureMonths.add("September");
    case 10: futureMonths.add("October");
    case 11: futureMonths.add("November");
    case 12: futureMonths.add("December");
             break;
    default: break;
}
```

Copy

Technically, the final `break` is not required because flow falls out of the `switch` statement. Using a `break` is recommended so that modifying the code is easier and less error prone.

The `default` section handles all values that are not explicitly handled by one of the `case` sections.

The following code example, shows how a statement can have multiple `case` labels. The code example calculates the number of days in a particular month:

```java
int month = 2;
int year = 2021;
int numDays = 0;

switch (month) {
    case 1: case 3: case 5:   // January March May
    case 7: case 8: case 10:  // July August October
    case 12:
        numDays = 31;
        break;
    case 4: case 6:   // April June
    case 9: case 11:  // September November
        numDays = 30;
        break;
    case 2: // February
        if (((year % 4 == 0) && 
             !(year % 100 == 0))
             || (year % 400 == 0))
            numDays = 29;
        else
            numDays = 28;
        break;
    default:
        System.out.println("Invalid month.");
        break;
}
```

Copy

This code has one statement for more than one `case`.

 

## Choosing Between Switch Statements and If-then-else Statements

Deciding whether to use `if-then-else` statements or a `switch` statement is based on readability and the expression that the statement is testing. An `if-then-else` statement can test expressions based on ranges of values or conditions, whereas a `switch` statement tests expressions based only on a single integer, enumerated value, or `String` object.

For instance, the following code could be written with a `switch` statement.

```java
int month = ...; // any month
if (month == 1) {
    System.out.println("January");
} else if (month == 2) {
    System.out.println("February");
} ... // and so on
```

Copy

On the other hand the following could not be written with a `switch` statement, because `switch` statements do not support labels of type `boolean`.

```java
int temperature = ...; // any temperature
if (temperature < 0) {
    System.out.println("Water is ice");
} else if (temperature < 100){
    System.out.println("Water is liquid, known as water");
} else {
    System.out.println("Water is vapor");
}
```

Copy

 

## Using String as a Type for the Case Labels

In Java SE 7 and later, you can use a `String` object in the `switch` statement's expression. The following code example displays the number of the month based on the value of the `String` named month.

```java
String month = ...; // any month
int monthNumber = -1;

switch (month.toLowerCase()) {
    case "january":
        monthNumber = 1;
        break;
    case "february":
        monthNumber = 2;
        break;
    case "march":
        monthNumber = 3;
        break;
    case "april":
        monthNumber = 4;
        break;
    case "may":
        monthNumber = 5;
        break;
    case "june":
        monthNumber = 6;
        break;
    case "july":
        monthNumber = 7;
        break;
    case "august":
        monthNumber = 8;
        break;
    case "september":
        monthNumber = 9;
        break;
    case "october":
        monthNumber = 10;
        break;
    case "november":
        monthNumber = 11;
        break;
    case "december":
        monthNumber = 12;
        break;
    default: 
        monthNumber = 0;
        break;
}
```

Copy

The `String` in the `switch` expression is compared with the expressions associated with each `case` label as if the `String.equals()` method were being used. In order for this example to accept any month regardless of case, month is converted to lowercase (with the `toLowerCase()` method), and all the strings associated with the `case` labels are in lowercase.

 

## Null Selector Variables

The selector variable of a `switch` statement can be an object, so this object can be null. You should protect your code from null selector variables, because in this case the switch statement will throw a `NullPointerException`.

# Branching with Switch Expressions

 

## Modifying the Switch Syntax

In Java SE 14 you can use another, more convenient syntax for the `switch` keyword: the `switch` expression.

Several things have motivated this new syntax.

1. The default control flow behavior between switch labels is to fall through. This syntax is error-prone and leads to bugs in applications.
2. The `switch` block is treated as one block. This may be an impediment in the case where you need to define a variable only in one particular `case`.
3. The `switch` statement is a statement. In the examples of the previous sections, a variable is given a value in each `case`. Making it an expression could lead to better and more readable code.

The syntax covered in the previous section, known as _switch statement_ is still available in Java SE 14 and its semantics did not change. Starting with Java SE 14 a new syntax for the `switch` is available: the _switch expression_.

This syntax modifies the syntax of the switch label. Suppose you have the following _switch statement_ in your application.

```java
Day day = ...; // any day
int len = 0;
switch (day) {
    case MONDAY:
    case FRIDAY:
    case SUNDAY:
        len = 6;
        break;
    case TUESDAY:
        len = 7;
        break;
    case THURSDAY:
    case SATURDAY:
        len = 8;
        break;
    case WEDNESDAY:
        len = 9;
        break;
}
System.out.println("len = " + len);
```

Copy

With the _switch expression_ syntax, you can now write it in the following way.

```java
Day day = ...; // any day
int len =
    switch (day) {
        case MONDAY, FRIDAY, SUNDAY -> 6;
        case TUESDAY                -> 7;
        case THURSDAY, SATURDAY     -> 8;
        case WEDNESDAY              -> 9;
    };
System.out.println("len = " + len);
```

Copy

The syntax of switch label is now `case L ->`. Only the code to the right of the label is executed if the label is matched. This code may be a single expression, a block, or a throw statement. Because this code is one block, you can define variables in it that are local to this particular block.

This syntax also supports multiple constants per case, separated by commas, as shown on the previous example.

 

## Producing a Value

This switch statement can be used as an expression. For instance, the example of the previous section can be rewritten with a switch statement in the following way.

```java
int quarter = ...; // any value

String quarterLabel =
    switch (quarter) {
        case 0  -> "Q1 - Winter";
        case 1  -> "Q2 - Spring";
        case 2  -> "Q3 - Summer";
        case 3  -> "Q3 - Summer";
        default -> "Unknown quarter";
    };
```

Copy

If there is only one statement in the `case` block, the value produced by this statement is returned by the `switch` expression.

The syntax in the case of a block of code is a little different. Traditionally, the `return` keyword is used to denote the value produced by a block of code. Unfortunately this syntax leads to ambiguity in the case of the switch statement. Let us consider the following example. This code does not compile, it is just there as an example.

```java
// Be careful, this code does NOT compile!
public String convertToLabel(int quarter) {
    String quarterLabel =
        switch (quarter) {
            case 0  -> {
                System.out.println("Q1 - Winter");
                return "Q1 - Winter";
            }
            default -> "Unknown quarter";
        };
    return quarterLabel;
}
```

Copy

The block of code executed in the case where `quarter` is equal to 0 needs to return a value. It uses the `return` keyword to denote this value. If you take a close look at this code, you see that there are two `return` statements: one in the `case` block, and another one in the method block. This is where the ambiguity lies: one may be wondering what is the semantics of the first `return`. Does it mean that the program exits the method with this value? Or does it leave the `switch` statement? Such ambiguities lead to poor readability and error-prone code.

A new syntax has been created to solve this ambiguity: the `yield` statement. The code of the previous example should be written in the following way.

```java
public String convertToLabel(int quarter) {
    String quarterLabel =
        switch (quarter) {
            case 0  -> {
                System.out.println("Q1 - Winter");
                yield "Q1 - Winter";
            }
            default -> "Unknown quarter";
        };
    }
    return quarterLabel;
}
```

Copy

The `yield` statement is a statement that can be used in any `case` block of a `switch` statement. It comes with a value, that becomes the value of the enclosing `switch` statement.

 

## Adding a Default Clause

Default clauses allow your code to handle cases where the selector value does not match any `case` constant.

The cases of a switch expression must be exhaustive. For all possible values, there must be a matching switch label. Switch statements are not required to be exhaustive. If the selector target does not match any switch label, this switch statement will not do anything, silently. This may be a place for bugs to hide in your application, something you want to avoid.

In most of the cases, exhaustiveness can be achieved using a `default` clause; however, in the case of an `enum` `switch` expression that covers all known constants, you do not need to add this `default` clause.

There is still a case that needs to be dealt with. What would happen if someone adds an enumerated value in an enumeration, but forget to update the switch statements on this enumeration? To handle this case, the compiler adds a `default` clause for you in exhaustive switch statements. This `default` clause will never be executed in normal cases. It will be only if an enumerated value has been added, and will throw an `IncompatibleClassChangeError`.

Handling exhaustiveness is a feature of `switch` expressions that is not provided by traditional `switch` statements and that is used in other cases than `switch` on enumerated values.

 

## Writing Colon Case in Switch Expressions

A `switch` expression can also use a traditional `case` block with `case L:`. In this case the fall through semantics does apply. Values are yielded using the `yield` statement.

```java
int quarter = ...; // any value

String quarterLabel =
    switch (quarter) {
        case 0 :  yield "Q1 - Winter";
        case 1 :  yield "Q2 - Spring";
        case 2 :  yield "Q3 - Summer";
        case 3 :  yield "Q3 - Summer";
        default: System.out.println("Unknown quarter");
                 yield "Unknown quarter";
    };
```

Copy

 

## Dealing with Null Values

So far, `switch` statements do not accept null selector values. If you try to `switch` on a null value you will get a `NullPointerException`.

Java SE 17 has a preview feature that enhances `switch` expressions to allow for null values, so you can expect this situation to change.