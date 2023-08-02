# Javascript

Related: #programming #terms 
Hamish Burke || 05-02-2023
***

## [[Console Object]]

String - console.log('');
Number - console.log('');

> [!Comments]
> Comments are made with '\/* \*/ 'or ''//'

## Data Types

- Num 
	- (any num [decimals as well])
- String 
	- (prefer '')
- Bool 
	- (true or false)
- Null 
	- (null) intentional absence of a value
- Undefined 
	- given value does not exist (eg points to nothing)
- Symbol
- Object 
	- collections of related data


Use .length on any string to return the length of it

## [[Javascript Methods]]

- .toUpperCase()
- .trim()
	- removes whitespace from left and right of a string

## [[Math Object]]

[JS math docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)
- .random()
	- between 0-1
- .floor()
- .ceil()

## [[Number Object]]

- .isInteger()
	- returns bool

> [!Operations]
> JS has the same operators #java 
> Eg: Increments, math ops, string concatenations

## Variables

### Var

- 'var' creates or declares a new var
- Name use [[camelCasing]]

```js
var myName = 'Hamish';
```

### Let

- Can be reassigned

```js
let changeMe = true;
changeMe = false;
```

### Const

- Can't be reassigned

```js
const entree = 'Enchiladas';
```

## Template Literals

- Used to insert variables into strings

```js
let myPet = 'hana';
console.log(`My pet is ${myPet}`);
```

## Typeof Operator

- Shows datatype of var

```js
console.log(typeof newVariable);
newVariable = 1;
console.log(typeof newVariable);
```

> [! ]
> ### Variables datatype's **can** be changed
> *as shown above (changes from string to num*