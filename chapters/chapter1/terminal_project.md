# Creating a Terminal Project
For this project, all you need is a plain text editor, access to the command line (terminal on Linux or Mac OS-X, or the Command window or Powershell on Windows), and the JDK installed on your system.

As I explained in the *Preface*, this book is going to attempt to teach Java by using the full-immersion language learning technique. So far, I have not shown that as my process, but for this chapter and the next one, we are going full-immersion. In order to do this, you just need to type the listing into your text editor and follow the instructions afterward to run the program. You will learn as you go what exactly is going on in the program.

As a last note before we begin, calling this a *terminal project* is overkill...this is actually just a simple terminal program. This distinction is important and one you will learn in the next part of the book when we get into the Apache NetBeans IDE. 

## The Program
With that all explained, let's write some code...here's the listing:

```java
public class HelloJava {
	
	public static void main(String[] args) {
		String name;
		if (args.length == 1) {
			name = args[0];
		}
		if (name == null || name.isBlank() || name.isEmpty()) {
			name = "Java";
		}
		
		System.out.println("Hello, " + name + "!");
	}
	
}
```

This class needs to be saved in a file called `HelloJava.java` somewhere on your disk. 

In your command or terminal window, you will run this file, *without* compiling it, by issuing the following command:

```
${Path2Java}/java HelloJava.java
```

The token `${Path2Java}` needs to be replaced by the actual path to the Java executable on your system, and you need to execute this command in the same directory where you saved the `HelloJava.java` file. If you have the `java` command(s) in your `$PATH` variable, you do not need to type out the path to the `java` executable. 

Once you run this program as described above, you will see the following output:

```
Hello, Java!
```

When that executes properly, rerun the program in this way:

```
${Path2Java}/java HelloJava.java ${FirstName}
```

The same rules apply for the `${Path2Java}` token in this command, however, you will want to replace the token `${FirstName}` with *your* first name. When I run this command, the output is:

```
Hello, Sean!
```

## How it works
Now that we have successfully executed this small program, let's discuss how it works and what it is doing. We will do this line-by-line...
### The Class Signature
...starting with the class signature:

```java
public class HelloJava {

}
```

The signature line of a class in Java includes key information. The form this signature takes is:

```
[public|protected||private] [static] [abstract] class ClassName [extends] SuperClass [implements] Interface1, Interface2, InterfaceN {

}
```

This is a lot to unpack, so let's take each item in turn:

* `[public|protected||private]`: Only one of these may be used for each class. These keywords describe the visibility of the class. There are four of these *access modifiers*:
   - `public`: This class is visible to all other classes running on the same JVM.
   - `protected`: This class is only visible within the package in which it is declared and to any classes that are *direct* descendants of the class.
   - *no keyword*: This class is strictly package private. In other words, it is only accessible from other classes within the same package in which it is declared. This is the *default* access modifier.
   - `private`: This class is only visible to the *class in which* it is declared. This keyword is used for nested classes.
* `[static]`: An optional keyword used for nested classes that allow them to be accessed from *outside* of the class in which it is declared, so that it can be accessed using the dot operator (`.`), such as `ClassName.NestedClassName`.
* `[abstract]`: An optional keyword used for declaring a class as being abstract. In other words, the class defines some methods that have implementations, but some methods that do not. You will see this when we work on our project because you will create a couple abstract classes.
* `class`: This is the keyword that defines the class *as being* a class and is required.
* `ClassName`: This is the name of the class by which you will access the class. The name must follow these rules:
   - Must begin with a letter.
   - May contain letters, numbers, and underscores ***only***.
   - Should use camelback notation, i.e., each word that makes up the class should start with a capital letter: `ThisIsMyClassName`. 
   - :dart: The name should give a good idea for what the class is used, i.e., `Logger`, `Contact`, etc.
* `[extends]`: An optional keyword to allow your class to extend the functionality of another class. This is the OOP concept of inheritance. It is important to note that Java only allows *single inheritance*, which means that a given class may extend only one other class<a href="#fn1" name="1"><sup>1</sup></a>.
   - If the `extends` keyword is used, then the `SuperClass` that is being extended *must be* named immediately after the `extends` keyword.
* `[implements]`: An optional keyword to all your class to implement the method signatures defined in an `interface`. This is the way that Java allows for *multiple inheritance*, though interfaces provide no functionality on their own and must have all methods they define implemented by the class that `implements` them, hence the keyword's name.
* `Interface1, Interface2, InterfaceN`: The list of interfaces that the class implements. For each of these interfaces that define methods, the methods must have implementation created. It should be noted that not all interfaces actually define methods, for example, the `java.io.Serializable` interface is simply a *marker interface*. Marker interfaces are simply used to decorate classes to tell the compiler and/or the JVM that the class can be used in a certain way. Marker interfaces are the original way Java allowed for this. Newer Java API provide *annotations* for decoration-only purposes like the `Serializable` interface, but that's a story for another day :wink:.

This about covers class signatures for now. You will learn more about these signatures as we go, because you will get an opportunity to use almost all of these different permutations of the class signature in our project.

### The `main` Method
The next code to discuss is the special method that is in our class:

```java
public static void main(String[] args) {

}
```

For the `public static` part of this method signature, you can look back at the bullets for the class signature, because they are identical. The only that I will note here is about the `static` keyword. This works similarly to how I explained it above, but it is important to note that for `static` methods, you do not access them via a class instance. You access `static` methods via the class name. I will explain this concept before the end of this chapter. For now, let's look at the rest of the method signature:

* `void`: This defines the return type from the method. This value can be any one of the following:
   - Any of the primitive data types.
   - Any of the primitive type wrapper classes.
   - Any object which can be instantiated.
   - Basically, the return type of a method can be any class in the Java API, any primitive type, or any class that you, yourself, write.
* `main`: This is the name of the method, which you use to access the method.
* `(String[] args)`: This is the list of parameters that the method requires. In this case, there is a list of only one parameter, named `args`, that is of the type `String[]`, which as you should remember is how to declare an array. Therefore, the `main` method takes a single `String` array parameter.

OK, so what makes this method so *special*, as I called it above? Every Java application, whether it is made up of a single class like our example, or made up of hundreds of classes, is required to have *at least one* special class called a *main class*. What makes this class so special is that it has a special method called a *main method*. This method that we just described ***is*** that main method. The main method *must* ***always*** be defined as `public static void main(String[] args)`, without exception. 

### Instance and `static` Method Access
I told you that I would explain the concept of access class methods versus accessing a class' `static` methods, so let's do that now.

Whenever you create a class, at some point you are going to want to use that class in your program. To use a class, you do the following:

```java
public class MyClass {
	private static MyClass instance;
	
	public MyClass() {
		// Initialize member fields.
	}
	
	public void doSomething() {
		// Do something.
	}
	
	public static MyClass getInstance() {
		if (instance == null) {
			instance = new MyClass();
		}
		
		return instance;
	}
}

public class Starter {
	
	public static void main(String[] args) {
		MyClass myClass = MyClass.getInstance();
		myClass.doSomething();

		MyClass myOtherClass = new MyClass();
		myOtherClass.doSomething();
	}
}
```

This is an oversimplification, though I am introducing you to a new class type. This new class type is called a *singleton class*. A singleton class only ever has one instance of it created. That instance is then retrieved using the *factory method* called `getInstance()`.

Notice that `getInstance` is defined as being `static`. All factory methods will be declared as `static`, because you are trying to get an instance of that object. In the `getInstance` method, you see that we test the `static` member field of type `MyClass`, called `instance`, to see if it has a `null` value. If it does, that means that the `getInstance` method had not been called before, so we instantiate the `instance` field by executing the line, `instance = new MyClass()`. That `new` keyword allows us to create a *new* instance of an object. This is how all<a href="#fn2" name="2"><sup>2</sup></a> objects are instantiated into object variables for use. The method called with the `new` keyword is not *actually* a method...notice that it has no return type associated with it. Paying attention to the method signature, you also notice that this method has the same name as the class. Therefore, this method is ***not*** a method at all, but is called a *constructor*. A constructor is used for just that, constructing a new instance of the object. In the constructor, you will initialize all of the member field variables and objects that your class defines. In this example, the only member field object defined is the instance of the class object. Since it is instantiated (initialized) in the `getInstance` method, you do not need to do so in the constructor (actually, that would cause an infinite loop). If `MyClass` defined other data fields, such as `int`s or `String`s, they would be initialized inside of the constructor. 

Because of all of this, you cannot access the `getInstance` method from an instance of `MyClass` simply because you don't yet have an instance of `MyClass`. So, in the first line, we declare `MyClass myClass = MyClass.getInstance()`. This is the way to access a `static` method by using the class name.

In the second line, we access the method `doSomething` by using the instance we just obtained. Therefore, if the method is declared *without* the `static` keyword, it is known as an instance method. This is because you can only access it from an instance variable of the object and not the class name for the class that is the type of the object.

In the third line, we declared `MyClass myOtherClass = new MyClass()`. This is not proper for a singleton class to allow, but I did this to show the two common ways of getting an instance of an object. Typically, there would be no way for you to call the constructor of a singleton class with the `new` keyword like we just did. The way the singleton class protects (hint, hint) its constructor is by declaring its constructor either `protected` or, most likely, `private`. Either of these ways protect the constructor from being called from outside of the `MyClass` class. Declaring the constructor as `protected`, however, will allow subclasses (classes that extend `MyClass` using the `extends` keyword) to override the constructor if they need.

## The `main` Method Functionality
The point of all of this was to show you how methods declared as being `static` work so that you'll understand why `main` is such a special method. This method, in our example is called by the JVM like this: `HelloJava.main(args)`. The `String[] args` parameter list provides to our program any arguments that may be passed on the command line. In our first run of the program, we didn't pass any arguments, but we did in our second run. That's why the first thing that we did inside of the `main` method was to test the length of the `args` parameter:

```java
String name;
if (args.length == 1) {
	name = args[0];
}
```

In this `if` block, we checked to see if there was a command line parameter. If there is, we set its value to the `String name` variable. Then, we checked the value of the `name` variable to see if is `null`, which it would only be (`String`s declared the way we declared `name` have the value `null` by default) if execution did not go into the `if` block:

```java
if (name == null) {
	name = "Java";
}
```

If the `name` variables value was not set to a command line argument, we set it to the value "Java". We could also have accomplished this with a single `if...else` block:

```java
String name;
if (args.length == 1) {
	name = args[0];
} else {
	name = "Java";
}
```

We also could have accomplished this same fete by only slightly changing the initial code by removing the `if (name == null)` check and just setting `String name = "Java";` when we created the `name` variable:

```java
String name = "Java";
if (args.length == 1) {
	name = args[0];
}
```

All of these ways of doing it are functionally equivalent and would still provide the same two outputs that we had gotten with our original version.

### Providing Information to the Terminal
The final line of our program was `System.out.println("Hello, " + name + "!");`. This line simply printed the phrase "Hello, Java!" or "Hello, Sean!" (in my case) to the terminal window. The `System` object is a useful one in Java and can be used for a lot of different purposes. The primary two purposes you will use it for, however, are to print messages to the terminal window using `System.out.print*` (there are many different `print` and `println` methods available) or to print out error messages to the terminal using `System.err.print*` (again, many different versions of the methods), which does the same thing as `System.out.print*`, but the text is highlighted in some way. For example, when I print messages to my terminal using the `System.err` stream, they are printed in a red font to highlight them as error messages.

## Conclusion
Now that we have written our first Java program and gone over it, how do you feel? Do you feel like it is all starting to make sense?

```java
if (so) {
	good();
} else {
	keepReadingToLearnMore();
}
```

:laughing::laughing:Sorry, but I couldn't help it...After all, this is supposed to be *full-immersion* Java.:laughing::laughing:

###### See Also
<a name="fn1" href="#1"><sup>1</sup></a> Techically, every class extends the base class `java.lang.Object`, so Java *does* allow for dual inheritance. However, the rule that Java has for single inheritance *is* accurate because no class needs to *explicitly* extend the `Object` class, as that is an *implicit* inheritance.

<a name="fn2" href="#2"><sup>2</sup></a> The primitive wrapper types do not need to be instantiated in this way. For example, to create a new `java.lang.String` variable, all you need to do is, `String myString = "The string value";`. The same goes for the other primitive wrappers. You do not have to use the `new` keyword to call the constructor of the class, you can just assign the value to the variable.