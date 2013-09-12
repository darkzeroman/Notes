| Type  | Size (bytes) | Values |
|:-----:|:------------:|:------:|
|byte   | 1            | -128 to 127 |
|short  | 1            | -32,768 to 32,767 |
|int    | 1            | -2,147,483,648 |
|long   | 1            | -9,223,372,864,777,808|
|float  | 4            | 10^38 |
|double | 8            | 10^308 |
|char   | 2            | unicode, 0 to 65,535 |
|boolean| 1 bit        | true/false

1 Byte = 8 Bits

Two’s Complement:
make negative by flipping and adding one
Example: 0001 (1) -> 1110 -> 1111 (-1) . Then adding 1111+0001 = 0000

| (OR), ^ (XOR), & (AND)

* Bitwise: & | ; takes two ints and returns an int
* Logical: && || ; takes two booleans and returns a boolean
x>>y or x<<y shifts x y times

```>>>``` might fill 1 or 0s. in Java ```>>>``` fills zeros.

Shift operators multiply by powers of 2 quickly. For non-negative numbers, shifting to the right one bit is like dividing by 2. For negative numbers, depends on the language.

Endian: doesn’t matter for java, but not for C.

* big-endian: MSB has lower address
* little endian: LSB has lower address

Internal variables are the states. Methods are the what define the interaction

32 bit processor means that the 32 bit virtual address space is available to programs. programs running a 32 bit OS will use 32 bits as their fundamental word size. 

Object Reflection

* Helps in observing/manipulating the runtime behavior of applications.
* Can help with debugging/testing because of direct access to methods/constructors/fields
* Can call methods by name when we don’t know the method in advance. Ex. user can put in a class name, constructor parameters, and method name. doing this without reflection is near impossible.

#### Testing Strategies
| Software | Function | Random |
|:--:|:--:|:--:|
|Manual vs automated |Normal case|Uninitialized variable|
|Black vs white box|Extremes|Memory leak|
|Audience|Null/illegal| External dependency|
|Use cases|Strange input| Intended/unintended use?|
|Bounds of use| | Safety? Cost? |

Dividing up data

* Order of appearance
* By hash value. key, has key, mod hash value by # of machines, store data on that machine
* By actual value. Store similar data on the same machine
* Arbitrarily. using a lookup table to identify where data is stored. 

online algorithm: input can be processed in a serial fashion.

offline algorithm: the whole data is available

nearest neighbors algorithm: NP Hard. Non-deterministic polynomial time
