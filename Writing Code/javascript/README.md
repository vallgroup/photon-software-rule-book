# Javascript Coding Standards

### Objects

```js
// GOOD
const MyObject = {
	firstName: 'Mario',
	lastName: 'Vallejo',
}

// BAD
const MyObject = { firstName: 'Mario', lastName: 'Vallejo', }

// BAD
const MyObject = { firstName: 'Mario', 
	lastName: 'Vallejo', }
```

### Arrays

```js
// GOOD
const myArray = [
	'Mario',
	'Vallejo',
]

// BAD
const myArray = [ 'Mario', 'Vallejo', ]

// BAD
const myArray = [ 'Mario', 
	'Vallejo', ]
```

### If, then, else

```js
let someVar = 'Something'

// GOOD
if (someVar) {
	callSomeFunc(someVar)
} else {
	doSomethingElse()
}

// BAD
if (someVar) { callSomeFunc(someVar) } else { doSomethingElse() }

// BAD
if (someVar) {
 callSomeFunc(someVar) 
} 
else {
 doSomethingElse() 
}

// GOOD
if ('This' === someVar) {
	callSomeFunc(someVar)
} else 
if ('That' === someVar) {
	doSomethingElse()
}

// GOOD - spacing between paranthesis is acceptable
if ( 'This' === someVar ) {
	callSomeFunc( someVar )
} else 
if ( 'That' === someVar ) {
	doSomethingElse()
}

// BAD
if ('This' === someVar) 
{
	callSomeFunc(someVar)
} 
else if ('That' === someVar) 
{
	doSomethingElse()
}

// BAD
if ('This' === someVar) 
{
	callSomeFunc(someVar)
} else if ('That' === someVar) 
{
	doSomethingElse()
}

// BAD
if (
    firstCondition() &&
    secondCondition() &&
    thirdCondition()
) {
    doStuff();
}

// BAD
if (
    someThing
) {
    doStuff();
}

// GOOD
(someVar) ? 'we fit in' : 'one line'

// GOOD
(someVar) 
	? 'This is' 
	: 'even better'

// BAD
(someVar) ? 
	'This is' : 
	'not good'

// BAD
(someVar) 
? 'This is' 
: 'not good'

// GOOD
(someVar) && doSomething()

// GOOD
someVar
	&& someOtheVar
	&& doSomething()

// BAD
someVar &&
someOtheVar &&
doSomething()

// BAD
someVar &&
	someOtheVar &&
	doSomething()

// BAD
someVar && someOtheVar && doSomething()
```

### Left-Hand Operators

```js
// GOOD
if (0 < someArray.length) {
	// do something
}

// GOOD
if ('' !== someString) {
	// do something
}

// GOOD
if ('function' !== typeof funcToTest) {
	// do something
}

// BAD
if (someArray.length > 0) {
	// do something
}

// BAD
if (someString !== '') {
	// do something
}

// BAD
if (typeof funcToTest !== 'function') {
	// do something
}
```

### for loop

```js
// GOOD - loop through an array
let i;
for (i = 0; i < someArray.length; i++) {
	// do something with someArray[i]
}

// BAD
for (i = 0; i < someArray.length; i++) {
	// do something with someArray[i]
}

// BAD
for (i = 0; i < someArray.length; i++) 
{
	// do something with someArray[i]
}

// GOOD - loop through an object
for (let i in someObject) {
	if (someObject.hasOwnProperty(i)) {
		// do something with someArray[i]
	}
}

// GOOD
for (let i = 0; i < Object.keys(someObject).length; i++) {
	// do something with someObject[i]
}

// BAD
for (let i in someObject) 
{
	if (someObject.hasOwnProperty(i)) 
	{
		// do something with someArray[i]
	}
}

// BAD
for (let i in someObject) {
	// do something with someArray[i]
}

// BAD
for (let i in someObject) {
	if (someObject[i]) {
		// do something with someArray[i]
	}
}
```

### try, catch

```js
// GOOD
try {
    // Expressions
} catch ( e ) {
    // Expressions
}

// BAD
try 
{
    // Expressions
} catch ( e ) 
{
    // Expressions
}

// BAD
try {
    // Expressions
} 
catch ( e ) {
    // Expressions
}

// ABSOLUTELY WRONG!
try {
    // Expressions
}
```

### No jQuery

Unless working on outdated technology, no Photon Software developer will resort to jQuery to build new functionality.

When writing functionaity for the front end, ir shall be written in either React or pure JavaScript.

### Naming Variables

Always use semantic names.

Only use `_` underscores on private variables.

Always user `const` and `let` over `var`.

Declare variables that do not change only once. Declare all other variables when you first need them, and always keep a cached version to avoid re declaring if the value has not changed.