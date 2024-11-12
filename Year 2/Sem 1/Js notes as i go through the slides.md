Node.js uses REPL (Read-Eval-Print-Loop)
Not all website code can run on Node.js and vice versa
Javascript is JIT (Just In Time)
Translates everything and cache it for execution instead of one line at a time

number
	Infinity
	-Infinity
	NaN(Not a Number)
	5/0 = Infinity
	Infinity - Infinity = NaN
	0 - Infinity = -Infinity
	null = 0
string

boolean
(condition? <value when true>:<value when false>)

null: is an object
undefined: is undefined

undefined in any math operator will return NaN
Numbers with any operator unless it is + will run as math
null == null, null == undefined

fallback using ||
comparing strings with strings will use unicode 
but when comparing to numbers it will attempt to convert to number if possible (eg "8")

Binding names
	cannot start with digit
	can include $ and __ but nothing else

Function declarations are not part of the top to bottom flow, you can have a output on the function before the function is reached in the code