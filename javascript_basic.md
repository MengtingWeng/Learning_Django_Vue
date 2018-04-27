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
