####Chapter 1. Accustoming Yourself to C++####
Item 1. Federation of languages.

- C
- Object Oriented C++
- Template C++
- STL: template library

Item 2. Prefer consts, enums, and inlines to #defines.

Item 3. Use const whenever possible.

Item 4. Make sure that objects are initialized before they're used.

####Chapter 2. Constructors, Destructors, and Assignment Operators####


Item 5.

This is what the compiler writes if I had written an empty class.

```
class Empty{
public: 
	Empty() {…}
	Empty(const Empty& rhs) {…}
	~Empty() {…} // non-virtual
	Empty& operator=(cinst Empty& rhs) {…}
```

Example: 

```
Empty e1; // default constructor
Empty e2(e1); // copy constructor
e2 = e1; // copy assignment operator
```

Item 6. Disallow unneeded compiler-generated functions you do not want by making them private.

Item 7. Declare destructors virtual in polymorphic base classes.

Item 8. Prevent exceptions from leaving destructors.

Item 9. Never call virtual functions during construction or destruction.

Item 10. Have assignment operators return a reference to *this.

Item 11. Handle assignment to self in operator=.

Item 12.

####Chapter 3. Resourece Management####

####Chapter 7. Templates and Generic Programming####


Item 41. Understand implicit interfaces

