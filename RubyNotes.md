Ruby
find/detect, find_all, any?, all

merge hashes. the one in arg will win over if hash names clash. or merge block
collect/map. always return array, even for hashes
spaceship operator: <=>
http://stackoverflow.com/questions/2642182/sorting-an-array-in-descending-order-in-ruby
sort_by


* a == b : checks whether a and b are equal. This is the most useful.
* a.eql? b : also checks whether a and b are equal, but it is sometimes more strict (it might check that a and b have the same type, for example). It is mainly used in Hashes.
* a.equal? b : checks whether a and b are the same object (identity check).
* a === b : used in case statements (I read it as "a matches b").
More

throw/catch and raise/rescue

Ruby Gotchas

Knowledge

Hash method arguments
Things are either expression or objects

Does haven’t abstract methods

Everything is an object

Metaprogramming is how the attribute accessors work.

Ruby scopes: top-level, class, module, method, and block
global variables are truly global

private methods can’t be called on anything except the implicit self, so can’t put self.private_method

Ruby has class level variables and class variables.

Ruby has a default value (nil) for non-existing keys.

Ruby strings are mutable

Assignments are expressions

symbols vs strings

Ranges: (1..2) is inclusive, (1...2) is exclusive

http://www.railstips.org/blog/archives/2006/11/18/class-and-instance-variables-in-ruby/




