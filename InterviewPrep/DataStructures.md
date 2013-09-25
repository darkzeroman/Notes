Great Summary of Data Structures Complexity: [Big O Cheat Sheet](http://bigocheatsheet.com/)

#####Trees

* Trees - has nodes with 0,1,or many references to other nodes.
* Terms: Parent, child, descendant, ancestor, leaves
* Lookup: O(logn) because 2^x = n. Only if search is nearly halved on each iteration. if everything only has one child, we just have a linked list, which then becomes O(n)

#####Traversals  (use recursion)

* Preorder - root, left, right
* In order - left, root, right
* Postorder - left, right, root
* BFS: find node: O(n). Avoid this type of search for large trees. Uses lots of memory to track child nodes
* DFS: Good for lower tree searching, lower memory requirements.

###### Examples:

* Binary Trees - each node has no more than 2 children
* Binary Search Trees - children to the left are lesser value, and right are greater value
* Heap Tree : the max/min value is always the root. Not possible to find next-higher node to a given node in O(log n) time or print out sorted order in O(n). Can be stored in array.
    * Binary heap: each parent has higher value than children.

Prep: http://courses.csail.mit.edu/iap/interview/materials.php

##### Linked Lists
* Need push/pop. Because the stack will be uses a linked list, the pointer to the stack will be a pointer to the head of the list, since the function needs the stack it’s operating on.
* Since there will be changes to the head, and any changes will not be propagated back, we need to use point point to the stack.
* Errors: push needs to allocate memory, but this can fail. So it can return true and false to indicate success. Pop can fail if there is an empty stack. So we need return value and success. So how about NULL for failure and return for success. Or return address to a reserved memory block, an indicator.

##### Dynamic Arrays  vs Linked Lists
* Random access to array elements O(1) vs O(n) for Linked Lists.
* As dynamic array grows, may need to be resized. Which means new array is made and old values are copied in. Computationally expensive.
* Linked Lists overhead can be big for small sized elements.
* If array resizing can be minimized (heuristic), dynamic array based stack is better.

##### Hash tables

* Hash tables allow for the storage and retrieval of data in O(1) time or constant time.
* At the most basic level, a hash table is just an array. Data is stored into specific indices designated by a hash function. A hash function maps the set of input data to a set of integers.
* There are issues of collisions which requires addressing with either chaining and load factor.

