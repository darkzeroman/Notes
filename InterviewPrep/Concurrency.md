### Summary of Threads vs Process
1. Threads are easier to create than processes since they don't require a separate address space. Context switching is less expensive with threads.
2. Multithreading requires careful programming since threads share data structures that should only be modified by one thread at a time.  Unlike threads, processes don't share the same address space.
3.  Threads are considered lightweight because they use far less resources than processes.
4.  Processes are independent of each other.  Threads, since they share the same address space are interdependent, so caution must be taken so that different threads don't step on each other.  This is really another way of stating #2 above.
5.  A process can consist of multiple threads.

A process can spawn subprocess which need to communicate using IPC (interprocess communication communication). Architectural construct.

#####Issues with Threads
* Race conditions - one thread updates, other doesn’t get the update
* Deadlock - waiting on a lock
* Livelock- busy waiting: wasting resources on checking thread should be alive/dead,
* Overlocking - putting unnecessary code in wait. 
S* tarvation : not getting access regularly

Ways to deal with issues are: preemption, priority.

[Notify vs NotifyAll](http://stackoverflow.com/questions/37026/java-notify-vs-notifyall-all-over-again)

[Wait, Notify, NotifyAll](http://javarevisited.blogspot.com/2011/05/wait-notify-and-notifyall-in-java.html)

* Use  Object.{notify/notifyAll/Wait}, and must be called in synchronized blocks
* Methods can be synchronized, places a lock on the object or just go ahead and synchronize an object
* Use notifyAll and implement runnable instead of using just notify and extending threads.
* Implement Runnable vs Extend Thread.
    * The first is better because only one class can be extended (inherited). But many interfaces can be implemented.  Also runnable allows for the use of thread pools, etc.
* Be careful not to put non-thread safe things in the constructor.
* Lock on static class puts a lock on the class, lock on an object puts it on the object

Java Data Structures

| Threadsafe | Not Threadsafe |
|:-:|:-:|
| Vector, Hashtable, StringBuffer | ArrayList, Hashmap, StringBuilder

Busy-wait synchronization: thread runs a loop in which it keeps re-evaluating some condition until that condition becomes true.


