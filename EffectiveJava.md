#Effective Java Summary
1. Static factory methods vs. constructors.
    * customized meaningful names compared to constructors (BigInteger.probablePrime)
    * Able to return any subtype (getPlanner might give BFS/DFS/etc, Collections)
    * They can reuse existing objects. (Boolean.valueOf(boolean))
    * Associated with class instead of creating new objects (static factory methods form the basis of Service provider Framework including service/provider interface, etc)
    * not possible if classes has no public/protected constructors, so it can’t be  subclassed.
2. Consider a builder when faced with many constructor parameters
    * Telescoping constructor parameters is only good for small number of parameters
    * JavaBeans call parameterless constructor and then use setter methods for each parameter (class becomes immutable)
    * Builder pattern (using a third object as a builder, static class  member, so they can be chained)
3. Enforce the singleton property with private constructor or enum type
    * Can be implemented by: public field, static factory method, enum singleton (best)
    * Without enum, readResolve() needs to be added to avoid creating spurious instances when doing serialization.
4. Enforce non-instantiability with private constructor
    * Utility classes like java.lang.Math or java.util.Arrays are not designed to be instantiated. Make constructor private.
5. Avoid creating unnecessary objects
    * Do ‘String s = “string”;’ instead of ‘= new String(“string”);’
    * Be careful with boxed primitives.
6. Eliminate obsolete object references
    * A stack needs to null the references in its array to make sure GC knows it can be cleaned. Other cases: inside classes, cache, callbacks. (unintentional object retentions)
Essential when a class manages its own memory.
    * For caches and listeners/callbacks, use weak references and WeekHashMap Pr timer-based expiration.
    * LinkedHashMap has removeEldestEntry(), expires entries on insertion/access order depending on construction.
7. Avoid finalizers
    * Two legitimate uses: safety net and cleaning up noncritical native resources. Remember to use super.finalize
    * Explicit termination inside a “try finally” is preferable and reliable.
8. Contract of equals
When not overriding is ok:
    * Each instance of the class is inherently unique (e.g. Thread).
    * A logical equality test isn't really needed (e.g. java.util.Random).
    * A superclass already implements equals adequately (e.g. AbstractSet, AbstractList, AbstractMap).
    * Class is private or package-private, and you're certain equals will never be called. But, could implement anyway to at least throw UnsupportedOperationException, just to make sure.
When overriding is recommended:
    * When there's a concept of logical equality that's different from object identity.
    * Override hashCode when overriding equals
    * Required if object used as key in HashMap/Hashtable or value in HashSet.
    * Equal objects must have equal hash codes.
9. Override hashCode when overriding equals
    * equal objects according the equals() function must produce the same hashCode, but two unequal objects may have the same hashCode.
10. Override toString
11. Override clone judiciously
    * When a class implements the Cloneable interface and overrides the clone() method, super.clone() will return a field to field copy of this class object on which the method is called. Deep copy is needed if there are non-primitive fields/references.
    * Good for arrays. Use copy constructor and copy factory method.
        * public Yum(Yum yum); public static Yum newInstance(Yum yum)
12. Comparable
    * Equals and compareTo should be the same.
    * Just needs a positive, zero, or negative number. Be careful with overflows.
    * Check in order of most significant fields
13. Minimize accessibility
    * Exported API: public/protected.
    * Instance fields should never be public
    * Classes with public mutable fields are not thread-safe
    * Public static finals are only for constants
    * nonzero arrays are mutable, never be public
14. In public classes, use accessor methods
    * If package-private/private class, can get away with  exposing data fields
15. Minimizing Mutability
    * Make the immutable class to be final.
    * Immutable objects are inherently thread-safe; they require no synchronization.
    * Use companion class such as StringBuilder replacing String for performance.
    * Static factory is a good way for immutable class.
    * Classes should be immutable unless there’s a very good reason to make them mutable.
    * Make every field final unless there is a compelling reason to make it nonfinal.
    * Don’t provide a public initialization method separate from the constructor or static factory unless there is a compelling reason to do so.
16. Composition vs. inheritance
    * Inheritance breaks encapsulation.
17. Design and document inheritance or else prohibit it
    * Inheritance must document self-use (evidence of broken encapsulation).
    * Prohibit inheritance if not designed for inheritance
    * Must document precisely the effects of overriding any method.
    * May have to provide hooks into internal workings for subclass to use.
    * Constructors must not invoke overridable methods.
    * Neither clone nor readObject may invoke an overridable method, directly or indirectly.
18. Interfaces vs. abstract classes
    * Existing classes can be easily retrofitted to implement a new interface.
    * Interfaces are ideal for defining mixins.
    * Interfaces allow the construction of nonhierarchical type frameworks.
    * Interfaces enable safe, powerful functionality enhancements via the wrapper class idiom.
    * It is far easier to evolve an abstract class than it is to evolve an interface.
    * Abstract + Interface: AbstractSet, AbstractList
19. Use Interfaces only to define types
    * Proper use of interfaces: Don't use interfaces as a means of exporting constants.
    * Enum and utility classes are more appropriate for defining constants
20. Prefer class hierarchies to tagged classes
    * Don’t have class with enum type and unused fields, rather use inheritance.
    * Tagged classes should be replaced by abstract classes    
21. Use functions objects to represent strategies 
    * Strategy pattern ⇒ Interface
    * Concrete strategy ⇒ Concrete class implementing the interface
22. Static vs. nonstatic member classes
    * If you declare a member class that doesn't require access to an enclosing instance, put the static modifier in the declaration
    * Relationships from Java to C    
        * C structures => classes
        * C unions => class hierarchies
        * C enum => classes (in JDK 1.5, enum)
        * C function pointers => classes and interfaces
    * Validate method parameters
    * Document restrictions and enforce them with checks that throw runtime exceptions.
    * Nonpublic methods should generally check their parameters using assertions rather than normal checks.
23. Don't use raw types in new code
	* Use generics when using Collections for safety and expressiveness
	* List vs List<Object>
		* Can pass a List<String> as a List but not List<Object>
24. Eliminate unchecked warnings
25. Prefer lists to arrays
26. Favor generic types
27. Favor generic methods
28. Use bounded wildcards to increase API flexibility
29. Consider typesafe heterogeneous containers
30. Use enums instead of int constants
31. Use instance fields instead of ordinals
32. Use EnumSet instead of bit fields
33. Use EnumMap instead of ordinal indexing
34. Emulate extensible enums with interfaces
35. Prefer annotations to naming patterns
36. Consistently use the Override annotation
37. Use marker interfaces to define types
38. Check parameters for validity    
39. Defensive copies
    * You must program defensively with the assumption that clients of your class will do their best to destroy its invariants.
    * It's essential to make a defensive copy of each mutable parameter to the constructor.
    * Defensive copies are made before checking the validity of the parameters, and the validity check is performed on the copies rather than the originals -- prevents possible race with another thread.
    * Do not use the clone method to make a defensive copy of a parameter whose type is sub-classable by untrusted parties.
40. Method signature design
    * Choose method names carefully, following standard naming conventions (item 38).
    * Don't go overboard in providing convenience methods. When in doubt, leave it out.
    * Avoid long parameter lists. Long sequences of identically typed parameters are especially harmful.
    * Break up method into multiple methods, each with fewer parameters.
    * Create helper classes (aka parameter object) to hold aggregates of parameters.
    * For parameter types, favor interfaces over classes.
    * Avoid function objects unless there is good reason to use them.
41. Method overloading
    * The choice of which method overload to invoke is made at compile time.
    * Note: selection among overloaded methods is static, but selection among overridden methods is dynamic.
    * Avoid confusing uses of overloading. A safe, conservative policy is never to export two     * overloadings with the same number of parameters.
    * Use differently named methods instead - e.g. ObjectOutputStream's write* and read* methods.
42. Use Varargs judiciously
    * Think about Google Guava
43. Returning zero-length arrays/collections vs. null
    * Null causes special-case code to be in both the method and the client.
    * Zero-length arrays are immutable and thus can be shared freely.
    * There is no reason ever to return null from an array-valued method instead of returning a zero-length array.
44. Document all exported APIs
    * Every exported class, interface, and member should be preceded with a doc comment.
    * Method doc should succinctly describe the contract between the method and the client.
    * The contract should say what the method does rather than how it does its job.
    * Sometimes necessary to document overall architecture of a complex API in a separate document, linked from the related class or package doc comments.
45. Minimize local variable scope
46. Prefer for-each loops instead of traditional for loops
47. Know the libraries
48. Avoid float/double if exact answers
49. Prefer primitive types to boxed primitives
50. String vs. non-string
51. Performance of string concatenation
52. Refer to objects by their interfaces
53. Prefer Interfaces to reflection
54. Avoid native methods
55. Optimizing
56. Naming conventions
57. Proper use of Exceptions
58. Checked vs. runtime exceptions
59. Proper use of checked exceptions


Benefits of standard exceptions
Exceptions and abstraction
Document all thrown exceptions
Exception message detail
Failure atomicity
Don't ignore exceptions
Synchronize access to shared mutable data
synchronization has no effect unless both read and write operations are synchronized
Avoid excessive synchronization
Never invoke wait outside a loop
Don't depend on the thread scheduler
Document thread safety
Avoid thread groups
They are basically obsolete
Only useful bit is ThreadGroup.uncaughtException for handling an uncaught exception thrown from one of the threads in the group.


