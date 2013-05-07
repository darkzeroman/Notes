#####Language Comparison

C: System. Imperative/Procedural.  
C++: Application, System. Generic, Imperative, OO, Procedural, Functional.  
Common LISP: General. Functional, Generic, Imperative, OO, Reflective.  
Haskell: Application. Functional, Generic, Lazy Evaluation.  
Java: Application, Client/Server-side, General, Web. Generic, Imperative, OO, Reflective.  
Javascript: Client-side, Web. Functional, Imperative. Prototype-based. Reflective.  
Ruby: Application, Scripting, Web. Aspect-oriented, Functional, Imperative, OO, Reflective.

|Language| Type Strength| Type Safety| Type Expression | Type Compatibility Among Composites | Type Checking| 
|:--:|:--:|:--:|:--:|:--:|:--:|
|C|weak|unsafe|explicit|name-based, nominative|static|
|C++|strong|unsafe|explicit|name-based, nominative|static|
|C. Lisp|strong|safe|implicit with optional explicit|structural|dynamic|
|Haskell|strong|safe|implicit with optional explicit|property-based, nominative| static|
|Java|string|safe|explicit|name-basd, nominative|static|
|Javascript|weak|both|implicit|duck|dynamic|
|Ruby|strong|safe|implicit|property-based, duck|dynamic|

* Strong/weak typing: regarding rules what types that can be mixed. (“abc”-3). Said to be strong when it specifies one or more restrictions on how operations involving values of different data types can be intermix.
    * Java, C++: require variables to have defined type, use casts for conversion.
    * Ruby: strongly typed because typing errors (type safety) are prevented at runtime and do little implicit type conversion, but do not use static type checking. Duck typing is used to describe the dynamic typing paradigm.
    * Haskell: purely static type systems, compiler infers a precise type for all values. do not allow implicit type conversions.
    * Lisp: strongly typed because typing errors are prevented at runtime.
* Type safety: safe if language does not allow operations or conversions that lead to erroneous condition.
* Type expression: Haskell infers, while rest require type declarations.
* Type based:
    *  Nominative: two objects are same if they are the same class. 
    * Structural: every method in A should be in B.
    * Duck typing: checks if something has a required method, if it does, use it. on compile time. allows for polymorphism without inheritance.
* Type checking determines whether and when types are verified. 
    * Static checking occurs at compile-time. 
    * Dynamic checking occurs at run-time.
* A **dynamically** typed language is a language where the type of a variable can be altered at any time. (It is a string, now it is a Fixnum, now it is a Time object, etc.)
* A **statically** typed language is the opposite. (Decide what x is once for all and don’t change your mind!)
* A **strongly** typed language is a language that is being strict about what you can do with your typed variables. (Don’t mix them… or I will throw you an error in the face!)
* A **weakly** typed language is the opposite. (Do what you want with your different types. Mix them all! We’ll see what happens!)

* Static vs Dynamic Scoping  
    * Dynamic: when a symbol is referenced, the compiler/interpreter walks up the symbol-table stack to find the correct instance of the variable to use. 
        * Java finds the variables through static scoping, but the error handling is done through dynamic scoping. This allows for the proper try/catch to be found looking through the stack instead of looking through the code.
        * Algol, Ada, C, Pascal are statically scoped.
        * [Scoping Notes](http://www.cs.washington.edu/education/courses/cse341/95au/general/scoping.html)

##### Declarative vs Imperative
* Imperative: follow a set of instructions
    * Structured: loop, while loop, if
        * OO: is a form of structured.
        * Procedural: function based coding, but not OO.
* Declarative


###### Examples
* Declarative
    * Functional:			LISP/Scheme, ML, Haskell
    * Dataflow :		Id, Val
    * Logic, Constraint-based:	Prolog, spreadsheets
    * Template based:		XSLT
* Imperative
    * von Neumann:			C, Ada, Fortran
        * Scripting:		Perl, Python, PHP, bash, awk
    * Object-oriented:		Smalltalk, Eiffel, C++, Java

#####Random Notes
Declarative: focus is on what the computer is to do. Higher level.   
Imperative: focus on how to do it.

* Functional: recursive, lambda calculus
* Dataflow: model computation as the flow of information (tokens) among primitive functional nodes. Inherently parallel.
* Logic/CB: attempt to find values that satisfy certain specified relationships, using a goal-directed search  through a list of logical rules.
* von Neumann: are based on statements that influence subsequent computation via the side effect of changing value in memory
* Script: emphasizes "glueing" together different parts.
* OO: 


Javascript: Prototype-based scripting, dynamic, weakly typed, first class functions. imperative and functional and OOP. Key design principles are from the Self/Scheme languages. Conforming to ECMAScript implementations.

**Dynamic**: Dynamic typing, object based, runtime evaluation (eval).  
**Functional**: first class function, nested function and closures  
**Prototype-based**: prototype-inheritance, functions as object constructors, functions as methods

Java: concurrent, class-based, OOP, static, strong, safe. Automatic memory management.

C++: Bjarne Stroustrup in 1979. “C with classes”, C++ increment joke. At first, c++ compiler was something that preprocessed to code to C, then used the C compiler.

C: Dennis Ritchie and Ken Thompson at Bell Labs in 1972. No abstractions.

###### Java vs C++
C++: designed for systems and applications programming. Extends C, so adds OOP, exception handling, scoped resource management, generic programming, and STL.
* Supports procedural, functional, OOP, template metaprogramming
* Pass by value, pointers, references
* Operator overloading
* Multiple inheritance
* Compile time
Java: created initially as an interpreter. Uses JVM. 
* Reflection
* By value

Ruby

* OOP, multiple inheritance with mixins
* dynamic, imperative
* reflection
* default arguments
* operator overloading
* eval
* Ruby doesn’t really have functions. Rather, it has two slightly different concepts – methods and Procs (which are, as we have seen, simply what other languages call function objects, or functors). Both are blocks of code – methods are bound to Objects, and Procs are bound to the local variables in scope. Their uses are quite different.






