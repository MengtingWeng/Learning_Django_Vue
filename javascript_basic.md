# JavaScript Foundations
## The "script" tag
```
<script>
  alert( 'Hello, world!' );
</script>

<script src="/path/to/script.js"></script>
```
* Option1: insert the js code into script tag.
* Option2: use the attribute "src" to define the script path.
* We cannot use two options at the same time.

## Variables
### Let
```
let message;
message = 'Hello';

//or
let message = 'Hello'

//or
let user = 'John', age = 25, message = 'Hello';
```
* We can also use "var" to declares a variable but it exists in older scripts
* Variable name can only contain letters, digits, and ```$``` or ```_```. 
And the first character should not be a digit.
* CamelCase is commonly used.
* Reserved names: ```let```, ```class```, ```return```, ```function```.
* In old times, it is ok to lose ```let``` at the first time to use a variable. 
This still works if we do not use ```use strict```.

### Constants
```
const MY_BIRTHDAY = '18.04.1982';
const pageLoadTime = /* time taken by a webpage to load */;
```
* The variable cannot be changed.
* We always use uppercase + underscore to name the constant variable.
* capital-named constants are only used as aliases for “hard-coded” values.

## Data type
```
// no error
let message = "hello";
message = 123456;
```
* variable can contain any type, such as string, number, char.
### Number
* Both integer or float is OK.
* Special numeric values: ```Infinity```, ```-Infinity``` and ```NaN``` (computational error).
* Doing maths is safe in JavaScript. We can do anything: divide by zero, treat non-numeric strings as numbers, etc.
The script will never stop with a fatal error (“die”). At worst we’ll get NaN as the result.

### String
```
let str = "Hello";
let str2 = 'Single quotes are ok too';
let phrase = `can embed ${str}`;
```
* "" and '' are same in JS.
* Backticks can work with `${...}` which can get the variable's value.
```
let name = "John";

// embed a variable
alert( `Hello, ${name}!` ); // Hello, John!

// embed an expression
alert( `the result is ${1 + 2}` ); // the result is 3
```
### Boolean
```
let nameFieldChecked = true; // yes, name field is checked
let ageFieldChecked = false; // no, age field is not checked

let isGreater = 4 > 1;
alert( isGreater ); // true (the comparison result is "yes")
```

### The "null" value
```
let age = null;
```
* "null" value forms a separate type of its own.
* In JavaScript null is not a “reference to a non-existing object” or a “null pointer” like in some other languages.
* It’s just a special value which has the sense of “nothing”, “empty” or “value unknown”.

### The “undefined” value
* The special value `undefined` stands apart. It makes a type of its own, just like `null`.
* The meaning of `undefined` is “value is not assigned”.
* If a variable is declared, but not assigned, then its value is exactly `undefined`.
* Normally, we use `null` to write an “empty” or an “unknown” value into the variable, and `undefined` is only used for checks, to see if the variable is assigned or similar.

### The typeof operator
```
typeof undefined // "undefined"

typeof 0 // "number"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

typeof Math // "object"  (1)

typeof null // "object"  (2)

typeof alert // "function"  (3)
```
* The `typeof` operator returns the type of the argument. It’s useful when we want to process values of different types differently, or just want to make a quick check.
* two methods to call `typeof`
```
typeof 123
typeof(123)
```
## Type conversions
### ToString
```
let value = true;
alert(typeof value); // boolean

value = String(value); // now value is a string "true"
alert(typeof value); // string
```
* `String(value)` to convert other type into string
* `alert()` just automatically converts any value to a string

### ToNumber
```
alert( "6" / "2" ); // 3, strings are converted to numbers

let str = "123";
alert(typeof str); // string
let num = Number(str); // becomes a number 123
alert(typeof num); // number

let age = Number("an arbitrary string instead of a number");
alert(age); // NaN, conversion failed
```
* `Number(num)` convert other type into number
*  Numeric conversion rules:


| value | becomes |
| --- | --- |
| undefined | NaN |
| null | 0 |
| true or false | 1 or 0 |
| string | Whitespaces from the start and the end are removed. Then, if the remaining string is empty, the result is 0. Otherwise, the number is “read” from the string. An error gives NaN|

```
alert( Number("   123   ") ); // 123
alert( Number("123z") );      // NaN (error reading a number at "z")
alert( Number(true) );        // 1
alert( Number(false) );       // 0
```

### ToBoolean
```
alert( Boolean(1) ); // true
alert( Boolean(0) ); // false

alert( Boolean("hello") ); // true
alert( Boolean("") ); // false
```
* Values that are intuitively “empty”, like 0, an empty string, null, undefined and NaN become false.
* Other values become true.

## Operator, exponentiation
```
alert( 2 ** 2 ); // 4  (2 * 2)
alert( 2 ** 3 ); // 8  (2 * 2 * 2)
alert( 2 ** 4 ); // 16 (2 * 2 * 2 * 2)
```
## Comparison
### between different types
```
alert( '2' > 1 ); // true, string '2' becomes a number 2
alert( '01' == 1 ); // true, string '01' becomes a number 1
```
```
alert( true == 1 ); // true
alert( false == 0 ); // true
```
```
let a = 0;
alert( Boolean(a) ); // false

let b = "0";
alert( Boolean(b) ); // true

alert(a == b); // true!
```
* A regular equality check `==` has a problem. It cannot diff `0` from `false` or empty string, so we can use a strict equality operator `===` checks the equality without type conversion.

### between null and undefined
```
alert( null === undefined ); // false
alert( null == undefined ); // true
```
```
alert( null > 0 );  // (1) false
alert( null == 0 ); // (2) false
alert( null >= 0 ); // (3) true
```
* Check `==` and comparisons `> < >= <=` work differently. Comparisons convert `null` to a number, hence treat it as 0.
```
alert( undefined > 0 ); // false (1)
alert( undefined < 0 ); // false (2)
alert( undefined == 0 ); // false (3)
```
* Comparisons (1) and (2) return `false` because `undefined` gets converted to `NaN` And `NaN` is a special numeric value which returns `false` for all comparisons.
* The equality check (3) returns `false`, because `undefined` only equals `null` and no other value.

## Function
### Function declaration
```
function sayHi() {
  alert( "Hello" );
}
```
### Function Expression
```
let sayHi = function() {
  alert( "Hello" );
};
```
* Notice that for function expression, we have the semicolon. However, for the function declaration, we do not have that.
* A Function Expression is created when the execution reaches it and is usable from then on.
* A Function Declaration is usable in the whole script/code block.
* When a Function Declaration is made within a code block, it is visible everywhere inside that block. But not outside of it.
```
let age = prompt("What is your age?", 18);

// conditionally declare a function
if (age < 18) {

  function welcome() {
    alert("Hello!");
  }

} else {

  function welcome() {
    alert("Greetings!");
  }

}

// ...use it later
welcome(); // Error: welcome is not defined
```
So this is the time to use the function expression
```
let age = prompt("What is your age?", 18);

let welcome;

if (age < 18) {

  welcome = function() {
    alert("Hello!");
  };

} else {

  welcome = function() {
    alert("Greetings!");
  };

}

welcome(); // ok now
```
To simplify it, we can write as bellow:
```
let age = prompt("What is your age?", 18);

let welcome = (age < 18) ?
  function() { alert("Hello!"); } :
  function() { alert("Greetings!"); };

welcome(); // ok now
```
### Arrow function
```
let func = (arg1, arg2, ...argN) => expression
```
It is equally to:
```
let func = function(arg1, arg2, ...argN) {
  return expression;
}
```
For example:
```
let sum = (a, b) => a + b;
//Above line equals to:
let sum = function(a, b) {
  return a + b;
}
alert(sum(1,2));
```
If we only have one argument, then we can omit the parentheses:
```
let double = n => n * 2;
alert(doublt(3)); // 6
```
If there are no arguments, parentheses should be empty(but they should be present):
```
let sayHi = () => alert("Hello!");
sayHi();
```
Example:
```
let age = prompt("What is your age?", 18);

let welcome = (age < 18) ?
  () => alert('Hello') :
  () => alert("Greetings!");

welcome(); // ok now
```
If there are multilines for expression, we can use `{}` to enclose them.
```
let sum = (a, b) => {  // the curly brace opens a multiline function
  let result = a + b;
  return result; // if we use curly braces, use return to get results
};

alert( sum(1, 2) ); // 3
```
# Object
## The basic of object
An object can be created with figure brackets `{…}` with an optional list of properties. A property is a “key: value” pair, where `key` is a string (also called a “property name”), and `value` can be anything.
```
let user = new Object(); // "object constructor" syntax
let user = {};  // "object literal" syntax
```
```
let user = {     // an object
  name: "John",  // by key "name" store value "John"
  age: 30        // by key "age" store value 30
};
```
* Access the property
```
// get fields of the object:
alert( user.name ); // John
alert( user.age ); // 30
```
* Add a property
```
user.isAdmin = true;
```
* Remove a property
```
delete user.age;
```
* multiword property names, but then they must be quoted
```
let user = {
  name: "John",
  age: 30,
  "likes birds": true  // multiword property name must be quoted
};
```
* Access multiword property, use `[""]`
```
alert(user["likes birds"]); // true
```
* Accessing a non-existing property just returns `undefined`.
```
let user = {};

alert( user.noSuchProperty === undefined ); // true means "no such property"
```
* There also exists a special operator `in` to check for the existence of a property. return true or false.
```
"key" in object
```
 * To walk over all keys of an object, there exists a special form of the loop: for..in. This is a completely different thing from the for(;;) construct that we studied before.
 ```
 for(key in object) {
  // executes the body for each key among object properties
}
 ```
 * An object declared as `const` can be changed.
 ```
 const user = {
  name: "John"
};

user.age = 25; // (*)

alert(user.age); // 25
 ```
* The `const` would give an error if we try to set user to something else, for instance:
```
const user = {
  name: "John"
};

// Error (can't reassign user)
user = {
  name: "Pete"
};
```
* So `const` object can change the key or value inside the object but cannot reassign the object.

* How to clone a object? Use loop or `Object.assign`
```
let user = { name: "John" };

let permissions1 = { canView: true };
let permissions2 = { canEdit: true };

// copies all properties from permissions1 and permissions2 into user
Object.assign(user, permissions1, permissions2);

// now user = { name: "John", canView: true, canEdit: true }
```
* If the receiving object (user) already has the same named property, it will be overwritten.
* Copy a object instead of loop:
```
let user = {
  name: "John",
  age: 30
};

let clone = Object.assign({}, user);
```
## Object method
### Method examples:
```
let user = {
  name: "John",
  age: 30
};

user.sayHi = function() {
  alert("Hello!");
};

user.sayHi(); // Hello!
```
### Method shorthand:
```
// these objects do the same

let user = {
  sayHi: function() {
    alert("Hello");
  }
};

// method shorthand looks better, right?
let user = {
  sayHi() { // same as "sayHi: function()"
    alert("Hello");
  }
};
```
The second one just delete `:` and `function`.
### "this" in method
```
let user = {
  name: "John",
  age: 30,

  sayHi() {
    alert(this.name);
  }

};

user.sayHi(); // John
```
* "this" is not bound
```
function sayHi() {
  alert( this.name );
}
```
* The value of this is evaluated during the run-time. And it can be anything.
```
let user = { name: "John" };
let admin = { name: "Admin" };

function sayHi() {
  alert( this.name );
}

// use the same functions in two objects
user.f = sayHi;
admin.f = sayHi;

// these calls have different this
// "this" inside the function is the object "before the dot"
user.f(); // John  (this == user)
admin.f(); // Admin  (this == admin)

admin['f'](); // Admin (dot or square brackets access the method – doesn't matter)
```
* Actually, we can call the function without an object at all, just return undefined.


# Data type
## Methods of primitives
* In JavaScript there are 5 primitive types: undefined , null , boolean , string and number.
* JavaScript allows us to work with primitives (strings, numbers etc) as if they were objects.
### A primitive as an object
* The solution to transform the frimitive variable into object:
  * Primitives are still primitive. A single value, as desired.
  * The language allows access to methods and properties of strings, numbers, booleans and symbols.
  * When this happens, a special “object wrapper” is created that provides the extra functionality, and then is destroyed.
```
let str = "Hello";

alert( str.toUpperCase() ); // HELLO
```
* The special primitives null and undefined are exceptions. They have no corresponding “wrapper objects” and provide no methods. In a sense, they are “the most primitive”.

* An attempt to access a property of such value would give the error:
```
alert(null.test); // error
```
## Numbers
```
let billion = 1000000000;
let billion = 1e9;  // 1 billion, literally: 1 and 9 zeroes
let ms = 1e-6; // six zeroes to the left from 1

//Hex, binary and octal numbers
alert( 0xff ); // 255
alert( 0xFF ); // 255 (the same, case doesn't matter)
let a = 0b11111111; // binary form of 255
let b = 0o377; // octal form of 255
```
* The method `num.toString(base)` returns a string representation of num in the numeral system with the given base.
```
let num = 255;

alert( num.toString(16) );  // ff  hex
alert( num.toString(2) );   // 11111111 binary
```
## String
### Quotes
Strings can be enclosed within either single quotes, double quotes or backticks:
```
let single = 'single-quoted';
let double = "double-quoted";
let backticks = `backticks`;
```
Single and double quotes are essentially the same. Backticks, however, allow us to embed any expression into the string, including function calls:
```
function sum(a, b) {
  return a + b;
}

alert(`1 + 2 = ${sum(1, 2)}.`); // 1 + 2 = 3.
```
### Special character
| Character | Description |
| --------- | ----------- |
| \b        | Backspace   |
| \f        | Form feed   |
| \n        | New line    |
| \r        | Carriage return |
| \uNNNN    | A unicode symbol with the hex code NNNN, for instance `\u00A9` – is a unicode for the copyright symbol `©`. It must be exactly 4 hex digits.|
| \u{NNNNNNNN} | Some rare characters are encoded with two unicode symbols, taking up to 4 bytes. This long unicode requires braces around it.|
```
alert( "\u00A9" ); // ©
alert( "\u{20331}" ); // 佫, a rare chinese hieroglyph (long unicode)
alert( "\u{1F60D}" ); // 😍, a smiling face symbol (another long unicode)
```
* "escape character": `\`
```
alert( 'I\'m the Walrus!' ); // I'm the Walrus!
```
* More elegant solution, we could switch to double quotes or backticks instead:
```
alert( `I'm the Walrus!` ); // I'm the Walrus!
```
### String length
```
alert( `My\n`.length ); // 3
```
* Notice the length is 3 since `\n` just means one character.
### Accessing character
Use `[]` or `.charAt()` to access the character in the string
```
let str = `Hello`;

// the first character
alert( str[0] ); // H
alert( str.charAt(0) ); // H

// the last character
alert( str[str.length - 1] ); // o
```
* The only difference between them is that if no character is found, `[]` returns `undefined`, and `charAt` returns an empty string:
```
let str = `Hello`;

alert( str[1000] ); // undefined
alert( str.charAt(1000) ); // '' (an empty string)
```
* Use for loop to access 
```
for (let char of "Hello") {
  alert(char); // H,e,l,l,o (char becomes "H", then "e", then "l" etc)
}

```
### Strings are immutable
```
let str = 'Hi';

str[0] = 'h'; // error
alert( str[0] ); // doesn't work
```
* The usual workaround is to create a whole new string and assign it to str instead of the old one.
```
let str = 'Hi';

str = 'h' + str[1];  // replace the string

alert( str ); // hi
```
### Change the case
* `toLowerCase()`
* `toUpperCase()`
### Searching for a substring
* `str.indexOf(substr, pos)`, not find return -1
```
let str = 'Widget with id';

alert( str.indexOf('Widget') ); // 0, because 'Widget' is found at the beginning
alert( str.indexOf('widget') ); // -1, not found, the search is case-sensitive

alert( str.indexOf("id") ); // 1, "id" is found at the position 1 (..idget with id)
```
* Also can define the start position
```
let str = 'Widget with id';

alert( str.indexOf('id', 2) ) // 12
```
* `str.lastIndexOf(pos)`
* `includes`, `startsWith`, `endsWith`

### Getting a substring
* slice: Include the start but not the end.
```
let str = "stringify";
alert( str.slice(0, 5) ); // 'strin', the substring from 0 to 5 (not including 5)
alert( str.slice(0, 1) ); // 's', from 0 to 1, but not including 1, so only character at 0
```
* substring: This is almost the same as slice, but it allows start to be greater than end.
```
let str = "stringify";

// these are same for substring
alert( str.substring(2, 6) ); // "ring"
alert( str.substring(6, 2) ); // "ring"

// ...but not for slice:
alert( str.slice(2, 6) ); // "ring" (the same)
alert( str.slice(6, 2) ); // "" (an empty string)
```
* substr: Returns the part of the string from start, with the given length.
```
let str = "stringify";
alert( str.substr(2, 4) ); // ring, from the 2nd position get 4 characters
```
## Array
### declare
* Two methods
```
let arr = new Array();
let arr = [];  //More popular
let fruits = ["Apple", "Orange", "Plum"];
```
* We can replace an element:
```
fruits[2] = 'Pear'; // now ["Apple", "Orange", "Pear"]
```
* An array can store elements of any type.
```
// mix of values
let arr = [ 'Apple', { name: 'John' }, true, function() { alert('hello'); } ];

// get the object at index 1 and then show its name
alert( arr[1].name ); // John

// get the function at index 3 and run it
arr[3](); // hello
```
### Methods pop/push, shift/unshift
* Methods that work with the end of the array (`pop`, `push`):
```
let fruits = ["Apple", "Orange", "Pear"];

alert( fruits.pop() ); // remove "Pear" and alert it

alert( fruits ); // Apple, Orange
```
```
let fruits = ["Apple", "Orange"];

fruits.push("Pear");

alert( fruits ); // Apple, Orange, Pear
```
* Methods that work with the beginning of the array (`shift`, `unshift`)
```
let fruits = ["Apple", "Orange", "Pear"];

alert( fruits.shift() ); // remove Apple and alert it

alert( fruits ); // Orange, Pear
```
```
let fruits = ["Orange", "Pear"];

fruits.unshift('Apple');

alert( fruits ); // Apple, Orange, Pear
```
* Methods `push/pop` run fast, while `shift/unshift` are slow. 

### Loop:
* arr.length
```
let arr = ["Apple", "Orange", "Pear"];

for (let i = 0; i < arr.length; i++) {
  alert( arr[i] );
}
```
* for and of
```
let fruits = ["Apple", "Orange", "Plum"];

// iterates over array elements
for (let fruit of fruits) {
  alert( fruit );
}
```
* for, of and key

```
let arr = ["Apple", "Orange", "Pear"];

for (let key in arr) {
  alert( arr[key] ); // Apple, Orange, Pear
}
```
### A word about “length”
```
let fruits = [];
fruits[123] = "Apple";

alert( fruits.length ); // 124
```
* If we increase it manually, nothing interesting happens. But if we decrease it, the array is truncated. The process is irreversible, here’s the example:
```
let arr = [1, 2, 3, 4, 5];

arr.length = 2; // truncate to 2 elements
alert( arr ); // [1, 2]

arr.length = 5; // return length back
alert( arr[3] ); // undefined: the values do not return
```
