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
```
let message;
message = 'Hello';

//or
let message = 'Hello'

//or
let user = 'John', age = 25, message = 'Hello';
```
* We can also use "var" to declares a variable but it exists in older scripts
* Variable name can only contain letters, digits, and ```$``` or ```_```
