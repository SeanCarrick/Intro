[< Previous](../front_matter/preface.md) | [[Table of Contents]](../../Cover_and_Contents.md) | [Next >](fundamentals.md)

# The Java Language
:zzz: Fair warning: this little section is going to be a bit boring. It is not necessary to read it in order to work through the rest of this book. It is only hear for completeness. :zzz:

The Java language was created due to the advent and expansion of popularity of the World Wide Web and the internet in the mid- to late-nineties, which pushed the need for a language that would work well with these technologies, which the current standard, C/C++, was unable to meet. 

Sun Microsystems' employees James Gosling, Patrick Naughton, Chris Warth, Ed Frank, and Mike Seridan took 18 months, starting in 1991, to develop the first working version. It was originally named "Oak" (after the tree outside of James Gosling's office window), but was renamed to "Java" in 1995. The development and growth of Java, however, wasn't even because of the internet, though it proved to work well with that technology. The *actual* impetus for the Java language was the need for a platform-independent (that is, architecture-neutral) language that could be used to create software that could be embedded into various consumer devices, such as microwave ovens, refrigerators, remote controls, etc.

The current standard (at that time) was C/C++, and a few other languages. These languages, however, were designed to be compiled for a specific target system. For example, a developer would write an application, say a device driver, and compile it on a Microsoft Windows:tm: host. That driver would then only work on Microsoft Windows:tm: systems, as that was the architecture and platform for which it was compiled. If that same driver was needed for Mac OS or Linux, it would have to be recompiled on those hosts, so that it would have access to the platform and architecture on which they ran.

Consumer electronic devices, however, had hundreds, if not thousands, of permutations and it would be extremely difficult to recompile software across all of those platforms. Therefore, a language that would not target a specific platform was needed...Hence the creation and evolution of Java.

Over the years, and decades, Java has continued to be improved and has had many new libraries added to the core API.

## Overview of Java
Java, as well as all other programming languages, is very much interrelated and no part of Java can be discussed in isolation. Every piece of the core Java API works together as a cohesive unit that allows for robust and stable applications to be written. The best use of Java is when certain programming paradigms are followed, because that is how Java itself was designed. According to the authors of *Java: The Complete Reference, Eleventh Edition*:

> Object-oriented programming (OOP) is at the core of Java. In fact, all Java programs are to at least some extent object-oriented. OOP is so integral to Java that it is best to understand its basic principles before you begin writing even simple Java programs. 

With that stated, I am going to follow Herbert Schildt's (the author of the referenced book) example and cover the basics of OOP before we get any further into the language. However, I am only going to highlight the keys of the prinicples, without delving too deep into the paradigm.

### Object-Oriented Programming
Object-oriented programming organizes an application around its data, instead of around the processes that it has. The second idea, organizing around processes, is the paradigm known as process-oriented programming and was used for many decades for writing applications. As applications grew in size and complexity, process-oriented programming would start becoming "spaghetti" code, with `goto` statements peppering the source code, and the logic being very difficult to follow.

In the real world, we see things as objects: houses, cars, roads, trees, etc. Each of these objects have properties: color, size, girth, etc. The OOP principle takes these real world ideas and brings them into developing applications. In other words, programmers are able to conceptualize their data as real world type objects, assigning properties to the data, etc.

While process-oriented programming leads to much difficulty in maintaining the code over the years, object-oriented programming aides in code maintenance because of the way it is organized, which makes more sense to the human brain.

There are four key principles involved with OOP that we will briefly discuss here: abstraction, encapsulation, inheritance, and polymorphism. So, let's look at them briefly, then move on.

#### Abstraction
The best way to define abstraction is this: think of a car. You most likely just thought of a specific make and model, such as Pontiac GTO, maybe even my favorite iteration of that beast, the 1969 Judge model. This thought that you had *is* abstraction. You didn't think of the tires, the carburetor, the fan belt, the timing chain, the steering wheel, etc., etc. You simply thought of the entire car as a whole. However, a car is actually thousands, or tens of thousands if you count the bolts, washers, and nuts, of different parts. Instead of thinking of all of those details, you thought a specific year, make, and model of car, and probably your favorite or dream car.

This is exactly how abstraction works in programming. You start out by developing an idea for an application. As you are thinking about that application's overall design, you start digging into finer and finer details. Once you have fleshed out the details as best you can, you start to decide how to incorporate those details in the best manner in your application. The first thing that you will do is decide on your base objects. These objects will become the building blocks for more and more well-defined objects as you go. 

Going back to the concept of the car, you can determine certain characteristics that every car shares, such as color, body style, seating, etc. All cars also have certain actions that are available to the user, such as start, stop, drive forward, back up, go faster, slow down, etc., which are called "methods" in programming. You would then create a class that exposes these common characteristics, which are called properties in the computer world. You would also expose the common actions, which are called methods or functions in the computer world. As you define different makes and models of cars, you create a different class for each of these that extends the base car class because then you don't have to rewrite (reinvent the wheel) the common properties that all cars share. 

With that understanding, you can see that you could even abstract the car class even more and create a class called "vehicles" that provides fewer properties than the car class, but would also incorporate properties that are shared between cars, motorcyles, pickup trucks, commercial vehicles (big rigs), boats, and airplanes. Then you can build a general class for each of these that extends the vehicles class.

All of this brings us to the principle of *polymorphism*, which comes from the Greek, meaning "many things". So, let's take a quick look at polymorphism.

#### Polymorphism
This principle states that a single interface, or abstract class, can be used for many different classes that all offer common methods and/or properties, but do so in a different manner, and/or expose individual methods and/or properties. This way, you would only need to write the property, along with the methods to modify the property, and the common methods a single time. 

With our car example from the last section, there is only one way to open a door, regardless of the type of car (leaving out the existence of key fobs and fingerprint readers for the sake of simpliciy :wink:): you pull the handle. If the door doesn't open, you then have to unlock the door, then pull the handle. Either way, the only way to actually open the door is to pull the stupid handle! :grin: So, you would write the implementation for the `openDoor` method in the parent class and not have to write it again in any of the classes that extend the parent. 

However, with the advent of key fobs and fingerprint readers on door handles, a class that extends car is able to rewrite the `openDoor` method to account for these "improvements." This is known as *overriding* the parent class' method. So, while the 1969 Pontiac GTO Judge will rely on the car class' `openDoor` method, the 2020 Lambourghini Countach will override the parent class' `openDoor` method due to having both a key fob and a fingerprint reader on the door handle.

*This* is all there is to polymorphism, so we no longer need to be afraid of that word, nor that principle. It's really *not* as complicated as it sounds. So, let's now take a look at *encapsulation*...another scary-sounding term that you will find is not so scary and not as complex as some people may think.

#### Encapsulation
Encapsulation is the principle of binding code to data in such a way as to prevent the data from being corrupted by outside forces. It is really just a protective barrier between your class' data and the outside world. The way that the class protects its data is by defining very specific methods of accessing and/or changing that data. Since the class that owns the data knows everything about the data, it is able to prevent another class from placing bad or illegal values into the data that could cause issues for the application.

Consider your full name, for example. You have a first, possibly a middle, and a last name. You know what those values should be, so you are able to protect the data from being corrupted. For example, when you go the driver's license office, you always make sure that the clerk spells your name correctly. Why do you do this? I mean, as Shakespeare said:
> What's in a name? A rose by any other name would smell just as sweet.

The reason that you do this is because, while a rose by any other name may smell as sweet, Bryan (when your name is Brian) may have warrants out for his arrest, and you don't want to be mistaken for Bryan!:stuck_out_tongue_winking_eye: Therefore, you protect your data (your name) and make sure that is always correct.

The same concept is applied to classes that you will create: you will want to protect the data upon which they rely. You will do this by providing a specific way for outside forces (other classes) to set a value for that data. In that method, you will verify that the data the outside forces are attempting to set into your data field is 100% correct *and* legal for your data field. This is all encapsulation is, so, again, not as scary as you thought...

Now, let's look at the final principle of OOP: *inheritance*.

#### Inheritance
We have already brushed up against this topic while discussing polymorphism, so this should be pretty short and sweet...

Inheritance is when you write a class that extends another class. Your class inherits the properties and methods of the parent class (called super class in Java). Just like when you have children, you children inherit properties and behaviors from you and your spouse: eye color, hair color, *attitude* (though this one might be learned:wink:), etc. In the same way, the class you write that extends another class inherits *everything* from the super class.

As long as the features and properties of the super class are not intensely protected by the super class, you can even directly access those features and properties, even if another class cannot. You will learn how to allow this later on, but rest assured that it is possible.

This is pretty much all inheritance is in the world of computer programming. See, not scary at all!

### Conclusion
I have given you a brief introduction to the history and concepts of the Java programming language and the paradigm of Object-Oriented Programming (OOP), which is necessary to understand when writing applications in Java. Don't worry if it doesn't all make perfect sense to you at this point, because you will be using it so much throughout the rest of this book that you will have a solid understanding of it by time we are done. Just know that these concepts will come into play again and again as you develop Java applications, no matter how simple or complex.

[< Previous](../front_matter/preface.md) | [[Table of Contents]](../../Cover_and_Contents.md) | [Next >](fundamentals.md)