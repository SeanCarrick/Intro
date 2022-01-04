[< Previous](java_language.md) | [[Table of Contents]](../../Cover_and_Contents.md) | [Next >](tools.md)

# Fundamentals
:zzz: Unfortunately, we are still on the boring stuff. However, this is a chapter that you should definitely read, since you will need to know this information in order to start writing Java applications. I apologize in advance for how boring this stuff is, but it will give you a decent basis for understanding all of the stuff that will be introduced later on. :zzz:

In this chapter, we are going to briefly discuss all of the intrinsic (built-in) data types, as well as one class type that you will use a lot in Java application development, how to declare and use variables, and the basics of arrays.

After that, we will (again) briefly talk about available operators, control statements, introduce you to classes, and, finally, give a brief synopsis of Java's package structures. 

With this overview in mind, let's get started so that we can get it over with :wink:. I truly hope that you don't die of complete boredom!:laughing:

## Data Types, Variables, and Arrays
To begin with, it is important to note that Java is a *strongly-typed* language. All this means is that you must declare a variable *prior* to attempting to use the variable. It also means that Java has specific data types available that are used to hold specific types of data. There are eight intrinsic (or, built-in), primitive (non-OOP) data types in Java:

* Whole numbers (integers) &mdash;
   * byte
   * short
   * int
   * long
* Decimal numbers (floating-point) &mdash;
   * float
   * double
* Characters &mdash;
   * char
* Boolean (true or false/yes or no/on or off) &mdash;
   * boolean
   
Each of these primitives has an OOP-style class that wraps them. Each of these classes have the same name as the primitive it wraps, except that the class name starts with a capital letter. Two other exceptions to the naming are the class objects that wrap the `int` and `char` primitives: the wrapper class for `int` is `Integer`, and the wrapper class for `char` is `Character`, but mostly you will use the class `String`, which wraps a bunch of characters, such as the text of this paragraph. Let's take a quick look at each of these primitive data types in turn, starting with the integer types.

### Integers
Integers are whole numbers that have no fractional part. They may be positive or negative in value, and each of the primitive integer types have a specific range. This range defines the amount of memory that a value of that type has allocated for it on a computer. We are going to discuss each of these briefly, while explaining the amount of memory they each take, as well as their value ranges. We will go from smallest to largest.

#### `byte`
This is the smallest integer type and only has a total range of 256 values:

| Memory Size | Min Value | Max Value |
| :---------: | :-------: | :-------: |
|8-bit | -128 | 127 |

To create a variable of this type, you do like this:

```java
byte myByte = 110;
```

#### `short`
The next size up the ladder from `byte` is the `short`, which has a total range of 65,535 values:

| Memory Size | Min Value | Max Value |
| :---------: | :-------: | :-------: |
|16-bit | -32,768 | 32,767 |

To create a variable of this type, you do like this:

```java
short myShort = 1100;
```

#### `int`
This is the second-largest integer type, and has a total range of 4,294,967,294 values:

| Memory Size | Min Value | Max Value |
| :---------: | :-------: | :-------: |
|32-bit | -2,147,483,648 | 2,147,483,647 |

To create a variable of this type, you do like this:

```java
int myInt = 152101;
```

#### `long`
This is the largest of the integer types, and has a range that may only be expressed in scientific notation when calculated on a calculator, 1.84467440737e+19:

| Memory Size | Min Value | Max Value |
| :---------: | :-------: | :-------: |
|64-bit | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807 |

To create a variable of this type, you do like this:

```java
long myLong = 117895346725891L;
// ~or~
long myLong = 117895346725891l;
```

:pencil2: Just as a reference, if each person on earth speaks an average of 13,500 words each day, with approximately 7.1 billion people on earth, that would only be 96,000,000,000,000 (96 trillion) words spoken each day. Therefore, to get to one quintillion spoken words, it would take 28 years, 7 months. So, the top or bottom range of `long` ***from zero*** is 9.223 *trillion* times that big, and *double that* to account for smallest to largest value! :open_mouth: In other words, it would take a long time to reach a number too large to be stored in this data type...

##### One Last Thing...
There is one more thing to mention regarding integers. When using integer *literals*, numbers you actually type, is that you can use commas or underscores to make them clearer while reading your source code. So, in the last two examples, you could do this to make them clearer to you:

```java
int myInt = 152,101;
// ~or~
long myLong = 117_895_346_725_891L;
```

By Java allowing this, it makes it much easier to determine while reading that the first value is one hundred fifty-two thousand, one hundred one, and the second value is some 117.895 trillion.

### Floating-Point Types
Since integers only hold whole number values without a fractional part, we have the floating-point types to hold fractional numbers. Unlike the integer data types, these value ranges, minimum and maximum values can ***only*** be expressed in scientific notation because of how many decimal places they are able to contain. Let's take a look at these two data types from smallest to largest.

#### `float`
The `float` type is a *single-precision* decimal value. It's memory size, minimum, and maximum values are:

| Memory Size | Min Value | Max Value |
| :---------: | :-------: | :-------: |
|32-bit | 1.4e-045 | 3.4e+038 |

To create a variable of this type, you do like this:

```java
float myFloat = 1.0;
// ~or~
float myFloat = 1.0f;
// ~or~
float myFloat = 1.0F;
```

#### `double`
The `double` type is a *double-precision* decimal value. It's memory size, minimum, and maximum values are:

| Memory Size | Min Value | Max Value |
| :---------: | :-------: | :-------: |
|64-bit | 4.9e-324 | 1.8e+308 |

To create a variable of this type, you do like this:

```java
double myDouble = 2.0d;
// ~or~
double myDouble = 2.0D;
```

##### One Last Thing...
Just like with the integer literals, you can separate the digits on the left side of floating point numbers with commas or underscores to group them into hundreds, thousands, millions, etc. It is also allowable for you to use underscores (only!) in the fractional portion of the number, as well:

```java
double myDouble = 9_423_497_.1_0_9;
```

### Characters
In Java, characters are stored in the `char` data type. This data type is used for both ASCII and Unicode characters, as Java defaults to Unicode. Unicode unifies all characters sets required for every human language spoken on the planet, such as Latin, Greek, Arabic, Cyrillic, Hebrew, Katakana, Hangul, and others. The ASCII character set still runs from 0-127, just as it always has. When Java was first created, the Unicode character set required 16-bits of memory to be stored. So, let's take a look at the `char` types memory size, minimum, and maximum values:

| Memory Size | Min Value | Max Value |
| :---------: | :-------: | :-------: |
| 16-bit | 0 | 65,536 |

To create a variable of this type, you do like this:

```java
char myChar = \u0061; // a

// ~or~ a character literal:
char myChar = 'a';
```

To assign a non-printing character, such as the newline character, to a variable of type `char`, you simply assign it as any other character literal:

```java
char newLineChar = '\n';
```

:bulb: Quick Tip: Notice that the single quote character (') is used above. You cannot assign a character to a `char` type variable using the double-quotes character ("), as this is how you assign `String` literals. We will talk about the `String` class in the [Introducing Classes](#Introducing-Classes) section.

:pencil2: Note that the `char` data type only allows positive values. This is known as an *unsigned* value, because a negative number cannot be stored, and the sign for a positive value is understood.

### Booleans
Boolean values only represent state, so to speak. The only two values allowed for a boolean data type are `true` or `false`. In Java, the primitive type is `boolean`.

To create a variable of this type, you do like this:

```java
boolean myBoolean = true; // or false
```

:bulb: Quick Tip: In some programming languages, `true` can be assigned by a non-zero value and `false` by a value of zero. However, this is ***not the case*** in Java. The only two legal values that may be assigned to a variable declared as the `boolean` type are `true` or `false`.

:mag: Booleans come from boolean algebra, which was invented by George Boole (November 2, 1815&mdash;December 8, 1864). He was an English mathematician who helped establish modern symbolic logic and whose algebra of logic, now called Boolean algebra, is basic to the design of digital computer circuits<sup>[1](#bool)</sup>.

### Life of Variables
The last thing that we need to briefly touch on before leaving this topic is the lifetime of variables. The important thing to note here is that in Java, you can declare a variable inside of any block of code:

```java
public class MyClass {
	private int counter;	// Available throughout this class.
	
	public void myMethod() {
		int counts; 	// Only available within myMethod.
		
		if (counts == 5) {
			int count = 0;	// Only available within this if statement.
		}
	}
}
```

As you can see in this example, blocks of code are designated by the curly braces `{` and `}`. A variable is only available between the pair of braces in which it is declared, so there is a very easy way to determine if your line of code has access to a specific variable: just see if your line of code is inside of the same pair of braces as the variable.

### Arrays
Let's discuss arrays very briefly, as you will get plenty of experience with them throughout this book.

Arrays provide a way of storing multiple values of the same type in the same variable. To declare an array of integers, for example, you would do this:

```java
int[] myIntArray;
```

The variable is declared as an array, not by the word "Array" being on the variable name, but by the empty square brackets after the keyword `int` (`[]`). This tells Java that you are going to be storing multiple integer values within the single variable `myIntArray`. If you want to assign a specific size to the newly created array, you would do sol like this:

```java
int[] myIntArray = {0, 1, 2, 3, 4, 5};
```

In this example, you use the curly braces to delimit the multiple values that you are assigning to the array of integers. In order to access the individual values later, you need to use their *element* number:

```java
int[] myIntArray = {15, 43, 27, 86};

int fifteen = myIntArray[0];
int fortyThree = myIntArray[1];
int twentySeven = myIntArray[2];
int eightySix = myIntArray[3];
```

Notice that it is not the *value* that you place between the square brackets in order to retrieve the value of the element, but the element number. In Java, array elements are *zero-based*, which means that you start counting at zero. If, at some point you need to find out the size (length) of your array, so that you know how many values it contains, you would find that out like this:

```java
int arrayLength = myIntArray.length;
```

Using the last example where we declared `myIntArray`, we know that the variable `arrayLength` will have the value `4` after this line executes. When you get the length of an array in Java, Java gives the *ordinal* amount, which means that counting starts at one, instead of at zero.

:pencil2: This may seem confusing right now, but once you use arrays, and loop over them, a couple of times, it will make perfect sense to you.

Let's try to speed this boring stuff up a little bit. Let's move on to operators...

## Operators
Operators in Java are pretty much common sense, but there are a couple we will need to discuss a little bit here to give you a little more understanding. To begin this topic, I'm just going to show all of the operators, with a brief definition, in a few tables.

### Mathematical Operators
First, let's look at mathematical operators:

| Operator | Definition |
| :------: | :--------- |
| + | Addition (also unary plus) |
| - | Subtraction (also unary minus) |
| * | Multiplication |
| / | Division |
| % | Modulus |
| ++ | Increment |
| += | Addition assignment |
| -- | Decrement |
| -= | Subtraction assignment |
| *= | Multiplication assignment |
| /= | Division assignment |

Most of these are pretty straight-forward. The only operators in this table that need a little bit of explanation are the modulus, increment, decrement and *assignment.

#### Increment and Decrement Operators
These two operators are used on a variable to either increase its value or decrease its value. Without worrying too much about the rest of the syntax, here is an example with the output the code will give:

```java
public static void main(String[] args) {
	int varOne = 0;
	int varTwo = 10;
	
	for (int x = 0; x < 10; x++) {
		System.out.println(String.format("varOne = %s and varTwo = %s", ++varOne, --varTwo));
	}
}
```

Output from the above program:
```
varOne = 1 and varTwo = 9
varOne = 2 and varTwo = 8
varOne = 3 and varTwo = 7
varOne = 4 and varTwo = 6
varOne = 5 and varTwo = 5
varOne = 6 and varTwo = 4
varOne = 7 and varTwo = 3
varOne = 8 and varTwo = 2
varOne = 9 and varTwo = 1
varOne = 10 and varTwo = 0
```

This example shows that if you use an increment or decrement operator *before* the variable, the operation will be performed, then the variable will be used. However, in the signature of the `for` loop, we see the part where `x` is incremented as `x++`. Since the incrementing of `x` is on the right side, the variable is used, then incremented. The same holds true for the decrement operator. You will use the increment operator so much while programming in Java that it will become second nature to you for how it works and you won't even need to think about it.

#### Modulus Operator
The modulus operator is a way of doing division, but instead of the quotient, you get the remainder. For example:

```java
public static void main (String[] args) {
	System.out.println(String.format("5 % 2 = %s", 5 % 2));
}
```

Output from the above program:
```
5 % 2 = 1
```

This output is because we used the modulus operator, instead of the division operator. If we used the division operator, we would have had to declare a variable of type `float`, because the division would have given us the quotient as a fractional number (`2.5`). Since we just wanted to know what the remainder is, we used modulus, so only the remainder was returned, which is why our result is `1`.

#### Mathematical Assignment Operators
These are also commonly called *compound assignment* operators. What these special mathematical operators do is perform the calculation and assign it to the variable. Consider the following as an example:

```java
int valueOne = 15;
int valueTwo = 20;

valueOne += valueTwo;
```

In this example, we assign the values `15` and `20` to variables `valueOne` and `valueTwo` respectively. Then, we increment `valueOne` by `valueTwo` and assign the sum back to `valueOne`. This is a shorthand for:

```java
valueOne = valueOne + valueTwo;
```

This line of code is functionally equivalent to the addition assignment line in the prior example. The only real difference is the amount of typing you have to do. Also, by using the addition assignment operator, your code becomes cleaner, more readable, and more maintainable.

Even though we only used the addition assignment operator in these examples, the other math assignment operators work similarly.

#### Assignment Operator
Whereas most people would read this operator, `=`, as equals, in Java it is called an *assignment operator*. This operator simply assigns the value (variable or literal) found on the right side of it to the variable on the left side of it. That is all there is to this operator, which is why I just included it in the Mathematical Operators section. Let's move on...

### Bitwise Operators
Java defines several of these operators that can only be applied to the integer types: `long`, `int`, `short`, `byte`, *and* `char`. Remember, the `char` type is actually a numerical type even though we use it for characters. Let's look at a table of definitions for these operators:

| Operator | Definition |
| :------: | :--------- |
| ~ | Bitwise unary not |
| & | Bitwise AND |
| | | Bitwise OR |
| ^ | Bitwise exclusive OR |
| >> | Shift right |
| >>> | Shift right zero fill |
| << | Shift left |
| &= | Bitwise AND assignment |
| |= | Bitwise OR assignment |
| ^= | Bitwise exclusive OR assignment |
| >>= | Shift right assignment |
| >>>= | Shift right zero fill assignment |
| <<= | Sift left assignment |

These operators are complex because they are used to shift the *bits*, internals, of the integer types. We are not going to go into these here any further than this table describes because these operators have very specific uses that we will not be going into in this book. Therefore, let's move on to some more operators that we will be using regularly.

### Relational Operators
These operators are pretty common in life, so the table of definitions should be enough for you, so that's about all we'll do here.

| Operator | Definition |
| :------: | :--------- |
| == | Equal to (here's the equality operator) |
| != | Not equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |

:pencil2: I should note that most these comparison operators are used for numerical data types. Characters and booleans can be compared with the equality operator (`==`). `String`s *can be* compared with the equality operator, but there is a much better way of comparing strings that we will come to later.

### Boolean Logical Operators
These operators only work on *boolean* operands. In other words, the value on each side of these operators must be able to be expressed as either `true` or `false`. Let's look at the definitions:

| Operator | Definition |
| :------: | :--------- |
| & | Logical AND |
| | | Logical OR |
| ^ | Logical XOR (exclusive OR) |
| || | Short-circuit OR |
| && | Short-circuit AND |
| ! | Logical unary NOT |
| &= | AND assignment |
| |= | OR assignment |
| ^= | XOR assignment |
| == | Equal to |
| != | Not equal to |
| ?: | Ternary if-then-else |

While a lot of these look familiar (from the Bitwise Operators), the context of their use changes their definitions. The most commonly used of these are the `&&`, `||`, `!`, and `?:`. Let's look at examples of each of these:

```java
public static void main(String[] args) {
	boolean untrue = false;
	boolean notUntrue = !untrue;	// Negates the value of untrue, making it true
	
	boolean oneAndOneAreEqual = 1 == 1; // Comparion is true
	boolean oneAndTwoAreNotEqual = 1 == 2; // Comparison is false

	int one = 1;
	int oneToo = 1;
	boolean oneAndOneTooAreTrue = one == oneToo; // This is a true statement
	
	int oneTwo = 12;
	boolean oneAndOneTwoAreTre = one == oneTwo; // This is a false statement
	
	boolean trueStory = false && true; // trueStory == false;
	boolean falseStory = false || true; // falseStory == true;
	
	String nullValue = null;
	String notNull = nullValue == null ? "Not Null" : nullValue;
}
```

I know, my variable names are just plain stupid :blush:...My apologies for that. The point is, we can now discuss each of these in turn.

* `boolean untrue = false`: this just sets the value `false` to the variable `untrue`.
* `boolean notUntrue = !untrue`: since `untrue` has the value `false`, by applying the not operator, `!`, we negate `untrue`'s value, which makes it `true`. Since the not operator acts on only a single operand, it is called a *unary* operator.
* The equality operator is self-explanatory, so we'll skip it for brevity's sake.
* `boolean trueStory = false && true`: this one is false, because both operands of the logical AND operator, `&&`, *must* be `true` for the statement to be true.
* `boolean falseStory = false || true`: this one is `true`, because one of the operands of the logical OR operator, `||`, is `true`, which makes the statement true.

The last one, the *ternary* operator, is a special operator that needs just a bit more explanation. This explanation, by the way, will make a nice segue into our next topic, Control Statements.

As you will learn in the next section, on of the most used control statements in Java (or any programming language for that matter) is the `if`...`then`...`else` statement. In practically every language, calling this construct a statement is actually a misnomer because it is actually a block (or two) of code. The basic format of the if...then...else structure in Java is:

```
if ([comparison test for true]) {
	[code to execute when true]
} else {
	[code to execute when false]
}
```

Since this construct is used so often, the Java developers created a shorthand for it, called the ternary operator, `?:`. The best way to show this operator is to give a short demonstration of a common use for an if...then...else block, followed by a demonstration of the ternary operator.

```java
public String getProperty(String propertyName, String defaultValue) {
	String property = properties.getProperty(propertyName);
	
	if (property == null) {
		return defaultValue;
	} else {
		return property;
	}
}
```

Without getting into what is happening here in detail, let's just look at the fact that a call to `java.util.Properties.getProperty` could return a `null` value if the named property either does not exist or has not been set. Therefore, in order to return the supplied default property value, you need to know if the named property has a valid value. To accomplish this, you test for `null` in an if statement. If the value returned from the call to get the property is `null`, then you want to return the default value that was supplied. Otherwise, you want to return the value of the requested property.

If you had to write that entire test block every time you wrote a method that relied on another method for the value you needed to return, your hands would cramp up bad. Therefore, instead of all of that, you can use the ternary operator shorthand like this:

```java
public String getProperty(String propertyName, String defaultValue) {
	return properties.getProperty(propertyName) == null ? defaultValue : properties.getPropertyName();
}
```

Both of these examples are functionally equivalent, but the second involves a bit less typing. The important thing to remember about the ternary operator is this: the `true` value goes after the question mark (`?`), and the `false` value goes after the colon (`:`):

```
[perform test for true] ? [true value code] : [false value code]
```

Believe me, you will learn to use the ternary operator whenever you are possibly able to do so!:wink: As I said, the ternary operator made a nice segue into the next section, so let's take a look at control statements...

## Control Statements
Control statements can be broken into two types: selection and iteration. Selection statements are used when you need to test values and take specific actions when the values have different states. The iteration statements are used when you need to execute the same code again and again, typically for a certain number of iterations, while a certain condition is met, or until a certain condition is met. Therefore, let us take a brief look at each of these in turn, beginning with the selection statements.

### Selection Statements
For selection statements, Java provides two options: `if` and `switch`. We have already been introduced to the `if` statement when we were discussing the ternary operator, so we won't need to spend a lot of time on this here. The `switch` statement is a great alternative to `if` when there are a number of set values that could be in place. Since the `if` statement will be quicker, we'll touch on it now, then get to the `switch`.

#### `if`...`then`...`else` Statement
The `if` statement provides branching to the logic of the method. To properly use it, you test for `true` in the `if` statement. When the test evaluates to `true`, the code inside of the `if` block executes. If the test evaluates to `false`, focus switches to the next statement. If that statement is an `else` statement, then the code in that block executes. However, though this describes a single test for truth, allowing for something to take place when the test is `true` and something else when the test is `false`, this is only the most basic use of the `if` statement. So, let's take a look at a simple `if`...`then`...`else` statement:

```java
if (value < 0) {
	doSomethingNegative();
} else {
	doSomethingPositive();
}
```

In the above example, if the `value` is a negative number, then the method `doSomethingNegative()` is called; otherwise, the method `doSomethingPositive()` is called.

That's all fine and everything, but what if I wanted to do something completely different if the value is zero (neither positive nor negative)? That's where the slightly enhanced `if` statement comes into play.

In this version of the `if` statement, you can have "nested" `if` statements. The easiest way to explain this is with another simple example:

```java
if (value == 0) {
	doSomethingNeutral();
} else if (value < 0) {
	doSomethingNegative();
} else {
	doSomethingPositive();
}
```

Instead of adding the new test case as the `if` statement, I could have left the original `if` statement as it was and made the test for equality with zero as the `else if` statement and the execution would still work the same. It's a personal choice how you go about doing this, but you should always design your logic with an eye to the future and also to readability of your code. By placing the equality test first, it makes it more clear that if the number is a positive value, `doSomethingPositive()` is called because the less than zero test failed. If I had placed the equality test as the `else if` test, the execution of `doSomethingPositive()` would not have been as clear.

"I get that the `if` statement, when paired with the `else if` statement allows for multiple tests, but, couldn't this get unwieldy if there are more than just a few tests?"

That is an ***excellent*** point and question!:smile: This is where the `switch` statement comes into play...

#### `switch` Statement
The `switch` statement should always be used if there are a number of tests to perform to decide which branch of the logic code should be executed. While there is no limit (of which I'm aware, anyway) on the number of `else if` clauses can be associated with a single `if` statement, it would get pretty unreadable pretty quickly. In order to keep your code readable, which greatly improves the ability to maintain the code, instead of a lot of nested `if`...`else if` statements, you should determine to use the `switch` statement.

The general format of the `switch` statement is as follows:

```
switch ([condition]) {
	case [Option1]:
		[code]
	case [Option2]:
		[code]
	case [OptionN]:
		[code]
	default:
		[code]
}
```

In this brief example, you see that the test condition goes with the `switch` statement, then you have different `case`s where you execute the required code for that case (or result of the condition). You can stack as many `case`s as you need for your program to execute correctly. However, notice the last `case` is called `default`. The `default` block is the equivalent of the `else` block in an `if` statement. If none of the other cases apply to the condition test, then the `default` block is executed. Just like with the `if` statement and the `else` not being a requirement, the `default` block is not required to be there as well.

However, *unlike* the `if` statement, once execution moves into a `case`, it will continue to run each `case` block until it does one of two things: a) executes *all* of the code from that `case` statement until the end of the `switch` block; or, b) hits a `break` statement. So, rewriting our quick example in a more proper manner, the `switch` would be:

```
switch ([condition]) {
	case [Option1]:
		[code]
		break;
	case [Option2]:
		[code]
		break;
	case [OptionN]:
		[code]
		break;
	default:
		[code]
}
```

Since the `default` case is usually placed at the end of the `switch` block (not a requirement), then it does not need to have a `break` statement, but there's no requirement that you *don't* put one there. The fact that a `switch` will continue to execute code until the end of the `switch` block, unless it hits a `break` statement, allows you to *stack* cases. What this means is that, if you need the same code to execute for different `case`s, you can just leave the code and the `break` statements out for all but the last `case` for which you need the code executed. For example:

```
switch ([condition]) {
	case [Option1]:	// I need the same code to execute for this case and Option2 case.
	case [Option2]:
		[code]
		break;
	case [OptionN]:
		[code]
		break;
	default:
		[code]
}
```

In this example, if the same code for `Option2` needs to be executed for `Option1`, you just don't put any code under `Option1`'s `case` block (and don't place a `break` in it either), then if `condition` meets either `Option1` or `Option2`, the same code will execute, then the `switch` will be exited.

As I just alluded to, the `break` statement causes the execution of the program to *break* out of the `switch` block and continue on with the rest of the method. You will see this again in the section on iteration. 

Just for giggles, let's look at example that will work for comparing the readability (and maintainability) between `if` statements with nested `else if` statements, versus the `switch` statement. For this, we're going to do a little planning...

##### The Plan
Let's say we are tasked to write a little program that accepts numerical scores and convert them into letter grades. The use case for the program is that anything less than 60 is an 'F', 60 to 69 is a 'D', 70 to 79 is a 'C', 80 to 89 is a 'B', and 90+ is an 'A'. Let's first do this in an `if` with nested `else if` statements:

```java
public char getLetterGrade(int score) {
	char grade;
	
	if (score < 60) {
		grade = 'F';
	} else if (score >= 60 && score < 70) {
		grade = 'D';
	} else if (score >= 70 && score < 80) {
		grade = 'C';
	} else if (score >= 80 && score < 90) {
		grade = 'B';
	} else {
		grade = 'A';
	}
	
	return grade;
}
```

Now, this may not be all that long or confusing, however, what if the user came back to us later on and asked to allow for the letter grades D-, D, D+, C-, C, C+, B-, B, B+, A-, A, and A+? In this situation, we would have to completely revamp our logic for splitting out the different scores to allow for this feature enhancement (which is what this would be).

So, let's take a look at how we could incorporate the same functionality using a `switch` statement, keeping our eyes on the possibility of future enhancements for including minus and plus grades, as well:

```java
public char getLetterGrade(int score) {
	char grade;
	
	switch (score) {
		case 100:
		case 99:
		case 98:
		case 97:
		case 96:
		case 95:
		case 94:
		case 93:
		case 92:
		case 91:
		case 90:
			grade = 'A';
			break;
		case 89:
		case 88:
		case 87:
		case 86:
		case 85:
		case 84:
		case 83:
		case 82:
		case 81:
		case 80:
			grade = 'B';
			break;
		case 79:
		case 78:
		case 77:
		case 76:
		case 75:
		case 74:
		case 73:
		case 72:
		case 71:
		case 70:
			grade = 'C';
			break;
		case 69:
		case 68:
		case 67:
		case 66:
		case 65:
		case 64:
		case 63:
		case 62:
		case 61:
		case 60:
			grade = 'D';
			break;
		default:
			grade = 'F';
	}
	
	return grade;
}
```

In this case, you may feel that the `if` with nested `else if` statements is more readable than this is. While that *may* be true, try to convert the `if` example to allow for plus and minus levels of each grade. To do so, you will need to change your existing `grade` variable and method return type to a `String` from a `char`, you will need to modify your current tests, and you will need to add ten more tests to cover the additional two ranges per letter grade. That's a lot of changes that are needed for this one little feature enhancement.

With the `switch` statement, on the other hand, you will still need to modify the return type of the method and the return variable from a `char` to a `String`, but then you will only need to add in the code at the bottom of the range for each subset of the grade. Here are the comparisons of the two different *modified* versions of the methods, with the `if` version first:

```java
public String getLetterGrade(int score) {
	String grade;
	
	if (score < 60) {
		grade = "F";
	} else if (score >= 60 && score < 64) {
		grade = "D-";
	} else if (score >= 64 && score < 67) {
		grade = "D";
	} else if (score >= 67 && score < 70) {
		grade = "D+";
	} else if (score >= 70 && score < 74) {
		grade = "C-";
	} else if (score >= 74 && score < 77) {
		grade = "C";
	} else if (score >= 76 && score < 80) {
		grade = "C+";
	} else if (score >= 80 && score < 84) {
		grade = "B-";
	} else if (score >= 84 && score < 87) {
		grade = "B";
	} else if (score >= 86 && score < 90) {
		grade = "B+";
	} else if (score >= 90 && score < 94) {
		grade = "A-";
	} else if (score >= 94 && score < 97) {
		grade = "A";
	} else {
		grade = "A+";
	}
	
	return grade;
}
```

Do you still think that has easy readability and maintainability? Let's see how we change the switch statement in the same way:

```java
public String getLetterGrade(int score) {
	String grade;
	
	switch (score) {
		case 100:
		case 99:
		case 98:
		case 97:
			grade = "A+";
			break;
		case 96:
		case 95:
		case 94:
			grade = "A";
			break;
		case 93:
		case 92:
		case 91:
		case 90:
			grade = "A-";
			break;
		case 89:
		case 88:
		case 87:
			grade = "B+";
			break;
		case 86:
		case 85:
		case 84:
			grade = "B";
			break;
		case 83:
		case 82:
		case 81:
		case 80:
			grade = "B-";
			break;
		case 79:
		case 78:
		case 77:
			grade = "C+";
			break;
		case 76:
		case 75:
		case 74:
			grade = "C";
			break;
		case 73:
		case 72:
		case 71:
		case 70:
			grade = "C-";
			break;
		case 69:
		case 68:
		case 67:
			grade = "D+";
			break;
		case 66:
		case 65:
		case 64:
			grade = "D";
			break;
		case 63:
		case 62:
		case 61:
		case 60:
			grade = "D-";
			break;
		default:
			grade = "F";
	}
	
	return grade;
}
```

As you can see, while we made the same modifications to the logic, the readability of the `switch` statement did not really change much. We added in 16 lines of code, and modified 7 lines. On the if statement we added in the same number of lines of code and modified 8 lines. While this is only one modified line of code more, it was more work to get the nested `if...else if` block updated to the new logic. It was way simpler to modify the `switch` statement by just adding in the new grade assignments where necessary. This is why, for such logic, `switch` statements should be used over `if...else if...else` blocks.

:dart: The best practice is to use `if...else if...else` blocks only where the `switch` statement cannot be used.

That's enough on selection statements, let's move onto iteration (loop) statements... 

### Iteration Statements
Iteration statements are just that, statements that let you iterator over a specific block of code multiple times. These types of statements are commonly referred to as *loops*. The common types of iteration statements are: `while`, `do-while`, `for`, enhanced `for` (also called `for-each`). Let's look at each of these in turn, beginning with the `while` loop.

#### `while` Loop
This is Java's most fundamental loop. It will continue to execute as long as its controlling expression (test) returns `true`. The basic format of this loop is:

```
while ([condition]) {
	[body of loop]
}
```

As a quick example of this type of loop, consider the following example:

```java
int x = 10;

while (x > 0) {
	System.out.println("T minus " + x--);
}
```

The output from this simple example would be:

```
T minus 10
T minus 9
T minus 8
T minus 7
T minus 6
T minus 5
T minus 4
T minus 3
T minus 2
T minus 1
```

As we discussed in the section on operators, this loop simply executes the line that prints the message to the terminal and decrements the variable `x` *after* it uses its value. In the operators section, I showed the reverse, where the variables were incremented and decremented *before* using the values.

Using the `while` loop, there is no guarantee that the loop will ever execute. If, for instance, the variable that is used in the loop control has already been changed to a value that fails the condition test, then the body of the loop will be skipped without being executed at all. If you need the loop to execute *at least* one time, you will need to use the next loop that we will discuss: the `do-while` loop.

#### `do-while` Loop
This loop works *exactly* the same as the `while` loop, with the simple exception that it is guaranteed that the loop body will execute *a minimum* of one time. This is simply because the `while ([condition])` is placed at the bottom of the loop body:

```
do {
	[body of loop]
} while ([condition])
```


## Introducing Classes

## Introducing Packages

###### See Also
<sup><a name="bool" href="#1">1</sup> Information from [Encyclopaedia Britannica](https://www.britannica.com/biography/George-Boole)

[< Previous](java_language.md) | [[Table of Contents]](../../Cover_and_Contents.md) | [Next >](tools.md)
