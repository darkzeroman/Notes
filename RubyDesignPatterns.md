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

Abuses
Make sure the children composites are not treated as leafs.

Examples
* GUI (Similar to Java)

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
	* IO hash `each_line`, `each_byte`
	* Pathname has `each_filename`, `each_entry`
	* ObjectSpace has `each_object`
	

Wrapping Up
* Internal iterators are easy to use with Ruby, just use Procs/blocks


### Command Pattern




