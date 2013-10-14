# Javascript the Good Parts

Good: functions, loose typing, dynamic objects, expressive objects literal notation

Javascript's functions ar efirst class objects with lexical scoping.

## Random Notes

* Strings are immutable
* Variables in functions are private
* Blocks do not create a new scope
* Equality operators: === (doesn't convert), == (converts)
* typeof(~) returns: number, string, boolean, undefined, function, object
* Objects are class free
* Use preiod for object if propery name is valid string literal
* `delete` operator removes property of object, not from prototype
* Falsy: false, null, undefined, 0, '', NaN
* Propery name can be an empty string
* use `||` for default values
* Bojects are passed by reference
* Prototype is chained  until at object: protype new property is shown in all subclasses
* Without var, variable is in global namespace
* Use `hasOwnProperty(~)` to test if property or found from protype chain when using for in enumerates property name (keys)

## Functions

* Function objects are linked to Function.prototype
* Every function has context and the code
* Invocation: 
	* Method Invocation Pattern: as a part of an object, can use `this` to access object
	* Function Invocation: `this` is global, use `that` instead
	* Constructor Invocation: use new ~. Created hidden link to function's prototype memeber, return changes
	* Apply Invocation: `apply(new_this, array of params)`
* If too many args != params, if too many, extra ones are ignored, if too few: undefined
* `arguments` var holds all arguments

Exception: `throw {name:'TypeError', message: 'add needs numbers'}`

Module: function/object presents an interface but hides state and implementation

Currying makes new function with a function and argument: 

```
Function.method("curry", function(){
	var args = arguments, that = this;
	return function(){
		return that.apply(null, args.concat(arguments))
	}
});
```

## Memoization: 
To Be Completed Soon

## Inheritance

* Lineage of object doesn't matter, loosely typed, never casts
* Javascript much richer code reuse patterns
* When function is created, function `constructor: this.prototype: { constructor: this};`


Object Specifiers

* `maker({first: ~, last: ~})`, args in any order
* object literal: `var x = {name: '~', says: function(){}}`
* differential inheritance: by customizing new object, specificy the differences on the new object. `var newCat = Object.create(Mammal)` => then overwrite
* Function: weakness of inheritance is privacy, can use module pattern
*

```
var constructor = function(spec, my){
	var that, other private instance vars
	my = my || {};
	[Add shared vars to my, 1]
	that = a new object
	[Add privileged methods to that, 2]
	return that;
}
```

* spec: contains all info needed to make instance, can be copied into private vars
* my: container of secrets that are shared by constructors in the inheritance chain
* vars/functions at [1] become private members of instance, inner functions have access to spec/my/that/private vars and assign them to my later
* [2] assign privileged methosd, define them and assign them to that so internally only the method name is needed

* Function pattern gives better encapsulation/information hiding/access to super methods. 
* Durable - not using this or that, durable object has collection to functions called capabilites, so cannot be compromised.
		
## Building by parts
To Be Completed Soon

## Array args

* array literatals : ['~', '~']
* can set value in array larger than length, not an upper bound, array expands
* can push onto array
* `delete arr[index]` leaves an undefined
* `arr.splice(ordinal, numToDelete)` => delete an element, not efficient
* use `for loop` for arrays with indices
* typeof arr is 'object'
* don't use `Object.create(arr)`, will not have length property



Personal Javascript Notes

`call` vs `apply`
* `call`: 
* `apply`: let the argments be put in an array
