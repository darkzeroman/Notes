# Java Collections Framework

## Basic Definitions

* List : ordered list of objects, may be duplicated, random access
* Queue: ordered, no random access
* Set: not ordered, no duplicates
* Map: making a relationship between key and value
* Deque: supports insertion/removal at both ends

## Collection Interfaces
### `java.util.Collection`

* java.util.Set
* java.util.SortedSet
* java.util.NavigableSet
* java.util.Queue
* java.util.concurrent.BlockingQueue
* java.util.concurrent.TransferQueue
* java.util.Deque
* java.util.concurrent.BlockingDeque

### `java.util.Map`

Not true collections, these interfaces contain collection-view operations, which enable them to be manipulated as collections.

* java.util.SortedMap
* java.util.NavigableMap
* java.util.concurrent.ConcurrentMap
* java.util.concurrent.ConcurrentNavigableMap

### Key Concepts

Terms

* unmodifiable: collections which do not support modification operations
* immutable: guarantee that no change in the `Collection` object will be visible
* fixed-size: Lists that guarantee size remains constant
* random-access: supports fast random access operation

Collections can throw runtime exceptions (ClassCastException, IllegalArgumentException, or NullPointerException) if elements that violate the implementation's restrictions.



## Collection Implementations

Generally the classes that implement the collection interfces typically have names in the form of <implementation-style><interface>.


| Interface | Hash Table | Resizable Array | Balanced Tree | Linked List | Hash Table + Linked List|
|--|--|--|--|--|--|
| Set | HashSet| | TreeSet | | LinkedHashSet
|List | | ArrayList | | LinkedList|
|Deque| | ArrayDeque | | LinkedList |
|Map| HashMap | | TreeMap | | LinkedHashMap

## Concurrent Collections

To Do Later

---

[Java 7 API Doc Notes About Collections](http://docs.oracle.com/javase/7/docs/technotes/guides/collections/overview.html)