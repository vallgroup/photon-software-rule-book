# Writing PHP for Photon Software

For the most part, at Photon Software we follow the same PHP coding standards that [The Wordpress Coding Standards](https://codex.wordpress.org/WordPress_Coding_Standards). Please make sure that you read through and understand these coding standards.

Always write Object Oriented PHP.

Always validate and escape data before displaying it or saving it to a database.

## If, then, else

```php
// GOOD
if ( isset( $array['key'] ) && ! empty( $array['key'] ) ) {
	// do something
}

// GOOD
if ( isset( $array['key'] )
	&& ! empty( $array['key'] ) ) {
	// do something
}

// BAD
if (isset($array['key']) && !empty($array['key'])) {
	// do something
}

// BAD
if ( isset( $array['key'] ) && ! empty( $array['key'] ) ) 
{
	// do something
}

// GOOD
if ( isset( $array['key'] )
	&& ! empty( $array['key'] )
	&& isset( $array['another_key'] )
	&& ! empty( $array['another_key'] ) ) {
	// do something
}

// BAD
if ( isset( $array['key'] ) && ! empty( $array['key'] ) && isset( $array['another_key'] ) && ! empty( $array['another_key'] ) ) {
	// do something
}
```

## Functions

```php
// GOOD
function my_new_function( $arg = null ) {
	// do something
}

// BAD
function my_new_function( $arg = null ) 
{
	// do something
}

// BAD - no spaces between paranthesis
function my_new_function($arg = null) {
	// do something
}

// calling a function and passing params

// GOOD
my_new_function( $arg );

// GOOD
my_new_function( array(
	'key' => 'value'
) );

// GOOD
my_new_function( [
	'this',
	'is also',
	'acceptable'
] );

// BAD
my_new_function($arg);

// BAD
my_new_function(array(
	'key' => 'value'
));

// BAD
my_new_function( [ 'this', 'is also', 'acceptable' ] );
```

## Classes

```php
// GOOD
/**
 * Some comments here
 */
class ClassName extends AnotherClass {
	
	function __construct( argument ) {
		# code...
	}
}

// BAD
/**
 * Braces do not go on next line.
 * There must be spaces in between paranthesis and args.
 */
class ClassName extends AnotherClass 
{
	
	function __construct(argument) 
	{
		# code...
	}
}
```

Go back to [Writing Code](../#technology-specific-rules)