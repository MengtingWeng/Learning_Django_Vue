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
