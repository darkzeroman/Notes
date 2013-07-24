Default arguments are evaluated once and then re-used

if 1<x < 3

Anything top level is global

Python has error for non-existing keys in dict

Python has mutable strings


http://jjinux.blogspot.com/2009/02/ruby-python-programmers-perspective_9838.html

http://wit.io/posts/the-ugliness-of-python

http://stackoverflow.com/questions/4769004/learning-python-from-ruby-differences-and-similarities


### Sequence Types
Sequences represent ordered sets of objects indexed by >0 integers and include strings, lists, and tuples. 

### Lists
list(s) converts any iterable type to a list.

### Strings
* a = "Your name is {0} and your age is {age}" 
* a.format("Mike", age=40)
* range or xrange([i,], j[, stride]) : range of k integers i <= k < j

### Mapping Types
mapping object: arbitrary collection of objects that are indexed by another collection of nearly arbitrary key values. Unordered, can be indexed by numbers, strings, and other objects. Mutable.

Key must be immutable object (strings, numbers, tuples, etc, not lists, dictionaries, mutable tuples). 

### Set
No indexing/slicing operations. No key/values associated with object. Items in set must be immutable. Set is mutable, frozenset is an immutable set.

Can interact with any iterable object (sets, lists, tuples, strings.)