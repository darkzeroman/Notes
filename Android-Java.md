##### Android Notes
SharedPreferences is nothing but a way to access xml files  
Can be accessed directly or using Preference activity  
Preferences should not hold sensitive information.  
They need default values because preferences can be deleted.  
Preference Event Listener  

##### Java Notes

FileReader and FileWriter for text files  
in try, parenthesis will automatically close files.  
Large files, wrap FileReader with BufferedReader   
Scanner(BufferedReader(FileReader))


static initializer/constructor gets called whenever a static variable is referenced  
instance field initializers gets called before the constructor  
local inner classes  
anonymous inner class  
Enumeration classes require private constructors, ex: override toString()

# Code Style Guidelines

## Java Language Rules

### Don't Ignore Exceptions

The following is bad because nothing is being done to handle the exception:

```
void setServerPort(String value) {
    try {
        serverPort = Integer.parseInt(value);
    } catch (NumberFormatException e) { }
}
```

Alternatives:

* Throw up the exception to caller of method
* Throw new exception that is appropriate
* Default to some value
* Catch the Exception and throw a new RuntimeException. This only makes sense if crashing is appropriate
* At least comment if there isn't a default action


### Don't Catch Generic Exception

Being too general can lead to headaches later. Only appropriate for test code and top-lvel code.

Alternatives:

* Catch each exception separately as separate catch blocks after a single try
* Refactor to have multiple try blocks
* Rethrow the exception

### Don't Use Finalizers

It may never be called, so instead use a `close()` method, like InputStream.

### Fully Qualify Imports

`import foo.Bar;` is better than `import foo.*;` for maintainability. Exceptions for util, io, and junit, though.

## Java Library Rules

Be Consistent!

## Java Style Rules

### Use Javadoc Standard Comments

Add Javadoc comment before nontrivial methods. Use 3rd person descriptive verb.

```
/** Returns the correctly rounded positive square root of a double value. */
static double sqrt(double a) {
    ...
}
```

### Write Short Methods

Try to have methods smaller than 40 lines.

### Define Fields in Standard Places

Fields should be defined either at the top of the file or immediately before the methods that use them.

### Limit Variable Scope

Scope of local variables should be kept to a minimum (Effective Java Item 29). 

### Order Import Statements

1. Android imports
2. Imports from third parties (com, junit, net, org)
3. java and javax

Have blank line between each major grouping.


### Use Spaces for Indentation

Use 4 space indents for blocks, 8 space indents for line wraps

### Follow Field Name Conventions

* Non-public, non-static field names start with m.
* Static field names start with s.
* Other fields start with a lower case letter.
* Public static final fields (constants) are ALL_CAPS_WITH_UNDERSCORES.

For example:

```
public class MyClass {
    public static final int SOME_CONSTANT = 42;
    public int publicField;
    private static MyClass sSingleton;
    int mPackagePrivate;
    private int mPrivate;
    protected int mProtected;
}
```

### Use Standard Brace Style

Braces are not on their own line. Always use braces for conditionals

### Limit Line Length

Line should be at most 100 characters long.

### Use Standard Java Annotations

If there are many annotations, one per line in alphabetical order.

* `@Deprecated`
* `@Override`
* `@SuppressWarnings`

Add More


### Treat Acronyms as Words

* Good: XmlHttpRequest, getCustomerId, class Html
* Bad: XMLHTTPRequest, getCustomerID, class HTML

### Use TODO Comments

Example: 

```
// TODO: Remove this code after the UrlTable2 has been checked in.
```

### Log Sparingly

Add more notes

### Be Consistent

Do what the rest of the code base does.

## Javatests Style Rules

### Follow Test Method Naming Conventions

Use underscore for naming test methods. Separate what is being tested from the specific case being tested. 


```
testMethod_specificCase1 testMethod_specificCase2

void testIsDistinguishable_protanopia() {
    ColorMatcher colorMatcher = new ColorMatcher(PROTANOPIA)
    assertFalse(colorMatcher.isDistinguishable(Color.RED, Color.BLACK))
    assertTrue(colorMatcher.isDistinguishable(Color.X, Color.Y))
}
```



