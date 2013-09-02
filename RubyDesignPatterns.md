## Patterns in Ruby

### Template Pattern
build abstract base class with skeletal method. 

Example: formal report in HTML, plaintext, etc

Hook methods: non-abstract methods that can be overriden in concrete classes (like initialize())

### Strategy Pattern
* make algorithms interchangeable, based on composition/delegation
* context: user of strategy
* Can use Procs/blocks for strategies
	* `hello = lambda { puts "Hello"}`
* Proc picks up surrounding env when created
* do/end have lower precedence than brackets
* & converts a Proc into a code block

### Observer Pattern
Publisher/Subscriber

* Publisher: keeps track of all of the objects that need notifications.
* Easy way to do this in ruby is override assignment method. And can implement the code using modules. Or use Ruby's Observable:
	* Need to call method `changed` before `notify_observers`.
	
* Can use code blocks as observers. Instead of passing an object, just pass a code block which will do whatever it needs to.

Variations of the Observer Pattern

* Pull/Push
	* Pull: Having a single method in the observer whose only argument is the subject.
	* Push: Subject send the observers a lots of details about the change. Disadvantage is that if all the observers are not interested in all the details, extra work is done.
* Can have individual methods for individual changes

Abuses

* Make sure the change is valid
* Order of observations (eg. salary before title)
* Errors/exceptions during observations

Examples

* ActiveRecord: clients stay informed of when DB recrods are created/read/written/deleted.
	* `after_create`, `after_update`, etc
	* ActiveRecord does not need to register observer, figures it out from class name
	
	
Wrapping Up

* Observer and Strategy pattern look similar. Both have an object (Observer - observable, Strategy - context) that makes call out to some other object. Difference is intent, informing in Observer, and computation in Strategy. 
* Observer pattern is similar to hook methods of Template Method, both keep an object informed of current events. Template Method pattern will only talk to subclasses.

### Composite Pattern
Parts:

* Component: common interface/base class.
* Leaf: Simple, indivisible building blocks of process.
* Composite: Where multiple leafs/composites can reside

Goal: make leaf objects same as composite object. But should leaf/composites act the same? What happens if add_child is called on a leaf?

Abuses: Make sure the children composites are not treated as leafs.

Examples: GUI (Similar to Java)

Wrapping Up

* Recursive in nature.
* Intepreter pattern is specialization of Composite.
* Uses the iterator pattern

### Iterator
Provides a way of accessing elements of aggregate object sequentially without exposing its underlying representation.

* External iterator: iterator is a separate object from the aggregate.
* Internal iterator: code-block iterators which occur inside the object (use `yield`)
* Internal Iterators vs External Iterators
	* With external iterators won't call next until necessary, internal has to push through
	* Merging two sorted arrays is easy with external iterator
	* External iterators are shareable, bad for multiple threads
	* Internal iterators are simple, clearer. External iterators have an extra part, "iterator object."

Include `enumerable` mixin, needs internal iterator method `each` and elements implement `<=>` comparison operator. Also has `include?`, `min`, `max`, `all?`, `sort` methods.

Abuses: 

* Account for changes while iterating

Examples of Iterators

* Internal:
	* String has `scan` which uses regex
	* Hash has `each_key`, `each`, 
* External:
	* IO has `each_line`, `each_byte`
	* Pathname has `each_filename`, `each_entry`
	* ObjectSpace has `each_object`

Wrapping Up

* Internal iterators are easy to use with Ruby, just use Procs/blocks


### Command Pattern
Command pattern command is an instruction to do something, something specific. Command pattern command can be executed now or later. Examples: Used in GUIs, or undo

Problem: Buttons need to inherit to overwrite on_button_push.

Easier way: put command in an object for complex operations to carry around variables. Use code blocks for simple operations.

Sounds similar to Rails migrations, installers queue commands, batch DB calls

Madeleine

* Ruby implementation of Prevayler. Transactional, high-performance, object persistence framework. Relies on the Marshal package (converting live Ruby objects into bytes/turning those bytes back into objects). 
* Saves the original state and then changes.
* Saves the state of the object to disk at intervals. So if there is a failure, can use a backup to restore.

For undoing a delete operation, need to save the contents of the original file, before we delete it. In a real world example, the file maybe saved somewhere temporarily.

Using/Abusing: "Remember" to do this. Destructive commands need to save state.

Wrapping Up

Good for keeping a list of things to do, remember things done.
Command/Observer are a lot in common. Both idefintify an object, command or observer, that is called from other participant. Both can be seen as the same thing that's passed to a button, such as a command.

### Adapter Pattern

Example: Want to use file encrypter code, but now want to use a string. Wrap string in an object that uses it like a file. 

Another example is that a text renderer object needs to be adapted for another type of object.

Ruby allows to define methods to classes.
Can also modify a single instance

*Edit*: "Ruby calls the methods that are unique to an object singleton methods. It turns out that most Ruby objects, along with their regular classes, have a second, more or less secret class. As shown in Figure 9-3, this second, singleton class is actually the first place where Ruby looks when you call a method, so any method defined in the single- ton class will override the methods in the regular class.4 The preceding code modifies the singleton class of the bto object. All of this is done with the utmost discretion, and even after it has been modified the object will still claim to be of its old, original class."

Advantage of duck typing allows creating part of target interface the client will use. 

Examples: Adapter pattern used in ActiveRecord to wrap SQL from different database types.

### Proxy Pattern
Good for controlling access to object, providing location-independent way of getting at object, or delaying its creation.

Protection proxy: each operation requires approval before making change.
Remote proxies: 
Virtual proxy: doesn't connect until necessary

To not have to re-write all methods of Real Service, in Ruby, use: 
```
def method_missing(name, *args)    puts("Warning, warning, unknown method called: #{name}")    puts("Arguments: #{args.join(' ')}")end
```
Use/Abuse
Methods inherited from object will be implemented for proxies.

Examples: Ruby SOAP client, Distributed Ruby package (drb)

Wrapping Up
Similar to Adapter except it does not change the interface, only tries to control access to it.

### Decorator Pattern
Enables to easily add an enhancement to an existing object. 

Incorporates lots of delegation. Can use `method_missing` technique or `forwardable` module. 

`def_delegators(instance_attribute, methods)`
This gives more control to programmer.

``` 
class WriterDectorator
	extend Forwardable
	def_delegators :@real_writer, :write-line, :rewind, :pos, :close
	def initialize(real_writer)
		@real_writer = real_writer
	end
end
```
include (instance methods) vs extend (add-class level methods)

An alternative to Forwardable is to use dynamic/runtime methods.

```
w = SimpleWriter.new('out')class << w  alias old_write_line write_line  def write_line(line)    old_write_line("#{Time.new}: #{line}")  end
end```
`alias` changes the name of a method, but doesn't work well for more than one change.
Can use modules for decorator pattern. Need to put every decorator classes into modules.
`extend` inserts a module into object's inheritance tree before its regular class.

```
module NumberingWriter
	attr_reader :line_number
	def write_line(line)
		...
	end
end

class Writer
	…
end	
w.extend(NumberingWriter)```
For run-time techniques, it is hard to undo. 
Abuses

Hard to use, performance overhead, method_aliasing makes debugging harder

Examples

ActiveSupport (support utilities used by rails). `alias_method_chain` allows us to decorate methods with any number of features.

```
def write_line_with_numbering(line)  @number = 1 unless @number  write_line_without_numbering("#{@number}: #{line}")  @number += 1endalias_method_chain :write_line, :numbering
```
Wrapping Up
Each decorator supports the same core interface, but has an unique twist. 

### Singleton Pattern
One object that has global access

Class variables are attached to whole inheritance hierarchy. Class shares a common set of class variables with its superclass and all of its subclasses. 

Need to make constructor(new) method private by:
` private_class_method :new`
Or use Singleton module
Lazy vs eager instantiation
`$var` makes it global, not really a good option
Make singleton a class. Good: no second instance, bad: lazy initiation, no control over timing of initialization
Make singleton a module. Good: no instantiation

Ruby's clone method is a way around all this.

Testing: Make tests use a non-singleton version of the class.

Using/Abusing: Hard for unit tests, hard to use

Examples: Rails, Rake

### Factory Pattern and Abstract Factory Pattern

Very similar to Template Method pattern applied to problem of creating new objects.

* Creator: Pond
* Concrete Creators: DuckPong, FrogPond
* Products: Duck, Frog

TO DO MORE

### Builder Pattern


Builder pattern is a middle man which holds the configuration which is passed on to another object which does the building.

Builders make creating complex objects easier, but also hide the implementation details.

Builders can ensure sane objects, can hold sane logic.

Reusable builders

TO DO MORE

### Interpreter Pattern

Good for when another language is good for a task, such as SQL.

Abstract Syntax Tree (AST): how to interpret expressions

Use an interpreter to find files example. Can use terminal/nonterminal nodes to create a tree.

Can use YAML/XML for representing simple data. Racc is good for more complex languages. 

Uses/Abuses
SQL, Intepreter has a computation overhead.

Examples: Ruby, regular expressions, Runt (library provides simple language for expressing things lie date/time ranges/schedules)
 
Conclusion
Good for solving well-bounded problems such as query or configuration languages. Is a good option for combining chunks of existing functionality together.
Core of Interpreter Pattern is AST. Which can be slow but powerful. Similar to DSL

## Ruby Patterns

### Domain-Specific Languages

Goal is to make a language understandable by domain experts. While Interpreter assumed an AST already exists, DSL is how the AST might be built.

External DSL: external parser, interpreter
Internal DSL: the domain is coded in the language



