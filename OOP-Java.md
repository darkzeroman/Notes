####Definitions for OOP
* Inheritance: concept that when a class of object is defined, any subclass that is defined can inherit the definitions of one or more general classes.
* Polymorphism: characteristic of being able to assign a different meaning to a particular symbol or “operator” in different contexts. allows an object to be represented in multiple forms. derived classes have the same function, even though they may not have the same behavior. Determined at run-time (late/dynamic binding)
* Encapsulation: idea of a class of only letting access of private variables in through methods
* Abstraction: hide all but relevant data an in order to reduce complexity and increase efficiency. identifying common patterns that have systematic variations

| Modifier    | Class | Package | Subclass | World |
|:-----------:|:-----:|:-------:|:--------:|:-----:|
| public      |Y      |Y        |Y         |Y      | 
| protected   |Y      |Y        |Y         |N      | 
| no modifier |Y      |Y        |N         |N      | 
| private     |Y      |N        |N         |N      | 

Nested class has access to all private members.

####Random Java Notes
* Java sticks in a super during the construction call. Default is one with no arguments.
* Final: can’t be overwritten by subclasses. Class can’t be subclassed. Vars can’t change. 
* Constructors should generally have only final method calls
* Java passes by value. References are passed around unless primitives.
* Inherit only if you want to override some behavior. “Inherit less, interface more”


| Hashmap | Hashtable |
|:-------:|:---------:|
|Not threadsafe but can be made so | Legacy code, replaced by hashmap |
|One null key and no limit on null values | No null keys or values |



| String        | StringBuffer                    | StringBuilder           |
|:-------------:|:-------------------------------:|:-----------------------:|
| immutable     | mutable, threadsafe (so slower) | mutable, not threadsafe |


#### Abstract vs Interface
######Abstract
* can have fields that are not static and final, implemented methods. 
* if abstract class only has abstract method declarations, it should be used as an interface instead.
* cannot be instantiated, but can be subclassed. 
* 'extends'
* Abstract class is used across similar classes that have a lot in common, but slight differences. Example: drawing circles, rectangles, lines, etc. Many of these have similarities but slight variations.

######Interface
* Interfaces can be used across a wide variety of different objects to define an "API." 
* Interface is a reference type, similar to class, that can contain only constants, method signatures, and nested types, static variables or class variables. No method bodies. Cannot be instantiated, only implemented by classes or extended by other interfaces.
* Interface declaration contains signatures, but no implementations, for a set of methods and might also contain constant definitions


[More Info](http://mindprod.com/jgloss/interfacevsabstract.html)




