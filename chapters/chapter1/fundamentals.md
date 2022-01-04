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

## Operators

## Control Statements

## Introducing Classes

## Introducing Packages

###### See Also
<sup><a name="bool" href="#1">1</sup> Information from [Encyclopaedia Britannica](https://www.britannica.com/biography/George-Boole)

[< Previous](java_language.md) | [[Table of Contents]](../../Cover_and_Contents.md) | [Next >](tools.md)
