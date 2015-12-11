## PHP CODING STANDARDS AND PRACTICES
###Table of Contents
1. [The Oh-Hell-No! List](#oh-hell-no)
	1. [Short Tags](#short-tags)
	2. [Bad Indenting](#bad-indenting)
	3. [Inconsistent Code Formatting](#inconsistent-code-formatting)
2. [Coding Standards](#coding-standards)
	1. [DocBlocks](#docblocks)
	2. [Type Hinting](#type-hinting)
	3. [Formatting](#formatting)

## <a name="oh-hell-no" href="#oh-hell-no">The Oh-Hell-Naw! List</a>
These are coding habits you **should** avoid and erase from your memory.
### <a name="short-tags" href="#short-tags">Short tags</a>
**Short tags** are bad habits to get into. Older versions of PHP have to have it enabled. They also can cause the code to look ugly.

```php
<? /* BAD! */
<?php /* GOOD! */

<?= /* BAD†! */
<?php echo /* GOOD! */
```

><sup>†</sup> There are some occasions that this is acceptable. Those occasions are if you are simply echoing out a known variable like `<?= $var; ?>`. If you are doing more than that, you are abusing the feature. You will also need to know what your scripts are being coded for, older versions of PHP will not like the Short tag option and you will have problems with compatability.

### <a name="" href="#">Bad Indenting</a>
**Indenting** is very important in keeping your codespace clean and organized. If you use ***Coda*** turn on visible whitespace ``View > Show Invisible Characters``. This will help keep things organized.

**Bad Version::**

```php
/* DONT BE LIKE THIS GUY! THIS IS AN EXAMPLE OF BAD INDENTING! */
public function myFunction( $arg1, $arg2, $arg3 = array() ) {
if($arg1 === true) {
$this->runFunc($arg1);
	foreach( $arg3 as $k => $v ) {
	if( in_array($k, $this->skip) ) continue;
	$append[] = $k;
	foreach( $v as $item => $details ) {
	if(in_array($item, $this->arr){
	$howConfusing = true;
		echo 'This code sucks!';
	}
		}
	}
}
}
```

**Good version::**


```php
/* BE THIS GUY! THIS IS VERY CLEAN! */
public function myFunction( $arg1, $arg2, $arg3 = array() ) {
	if($arg1 === true) {
		$this->runFunc($arg1);
		foreach( $arg3 as $k => $v ) {
			if( in_array($k, $this->skip) ) continue;
			$append[] = $k;
			foreach( $v as $item => $details ) {
				if(in_array($item, $this->arr){
					$howConfusing = false;
					echo 'This code rocks!';
				}
			}
		}
	}
}
```

### <a name="" href="#">Inconsistent Code Formatting</a>
It's important that you use consistent formatting for loops, functions and conditionals throughout the whole project. The more consistency there is the easier the code will read later in the project. Below I list the acceptable formats we use and should abide by.

**Bad Version::**

```php
/* Examples of inconsistent Functions() */
/*
 * 1) The arguments are not spaced between the parenthesis.
 * 2) Squiggly brackets ({}) are on the line below the function line.
 */
public function myFunction( $arg1, $arg2 )
{
}

public function myFunction($arg1, $arg2) {
}
```

```php
/* Examples of inconsistent Loops() */
/*
 * 1) The "key" and "var" are not spaced the same between the =>.
 * 2) Squiggly brackets ({}) are on the line below the function line.
 * 3) Spacing inconsistency in the for loop arguments.
 * 4) Using inline and block loops within the same code base.
 */

/* Foreach Loop */
foreach( $arr as $k => $v ) {
}

foreach( $arr as $k=>$v )
{
}

/* For Loop */
for ( $i=0;$i<=count($j);$i++) {
}

for( $i=0; $i<=count($j); $i++) {
}

/* For Loop Inline vs block */
for( $i=0; $i <= count($j); $i++ ) {
	//Im a block!
}

for( $i=0; $i <= count($j); $i++ )
	//Im a inline
```


## <a name="" href="#">Coding Standards</a>

### <a name="" href="#">Doc Blocks</a>
---
**Doc blocks** are _**required**_ for all functions/methods. The outline the purpose and functionality of the function/method.

**Template::** Coda snippet [download](https://www.dropbox.com/s/7grjb4ek306t4sy/PHP%20Doc%20Block.clips?dl=0 "Download me").

```php
/**
 * functionName
 * 
 * description of what the function does
 * 
 * @access functionVisibility
 * @params dataType argument (default: defaultValue)
 * @return returnDataType short description of what the return value is about. Include an explanation of what would cause false returns if applicable.
	 
 * @since Method available since Release x.x.x
 * @deprecated Method deprecated in Release x.x.x
 */
```

### <a name="" href="#">Type Hinting (possible removal)</a>
---
It is good practice to use **Type Hinting** with your code. It makes it easy to find bugs/errors and keeps the code easy to follow when you come back to it later on.

#### Type Hints
* String
* Integer
* Float (floating point numbers - also called double)
* Boolean
* Array
* Object
* NULL
* Resource

### <a name="" href="#">Strings</a>
---
#####Literal Strings
When defining a string that is literal and does not include any variable substitutions, the apostrophe AKA "single quote" should always be used. Using single quotes for literal strings will save fractions of a second on processing time compared to double quotes.

```php
$str = 'What nicely formated literal string';
```

#### Literal Strings with apostrophes
When a literal string contains apostrophes you should use quotations AKA "double quotes". The practice of escaping characters should be avoided. The code becomes cluttered and hard to follow when escaping characters.

```php
$str = "Isn't this a nice looking string?";
$str = "SELECT * FROM `orders` WHERE `id` = '2261589' ORDER BY `created` ASC";
```

#### Variable Substitution
When a variable is necessary within a string use "double quotes" and braces (aka "curly brackets" or "squiggly brackets"). These things `{ }`.

```php
$str = "Hello {$name}, thanks for learning how to code properly!";
```
> Here are some bade examples you should <b><u>always</u></b> avoid:
> 
```php
$str = "Hello ${name}, you do not know how to code properly!";
$str = "Hello $name, you should be ashamed of yourself!";
$str = 'Hello {$name}, this one will not work! Use double quotes!';
$str = "Hello, ".$name.", now you are just being a newb! This is awful!";
```

#### String Concatenation
When you must concatenate string data, the correct formatting is shown below. A space before and after the period (.) is required for consistency and readability.

```php
$str = 'Dr. Tobias Funke' . ' - ' . 'PhD.';
```

In most circumstances concatenating on a single line will suffice. In the event it is an SQL statement or long string that would wrap naturally, it is encouraged that you use line breaks.

```php
$sql = 'SELECT `id`, `name`, `created` '
	. 'FROM orders '
	. 'WHERE id >= 10 '
	. 'ORDER BY `created` ASC '
	. 'LIMIT 1000';
```

### <a name="" href="#">Arrays</a>

#### Numerically Indexed Arrays
Negative numbers are not permitted as indices. All indexed arrays must start with any non-negative number.

When declaring an indexed array with the `array()` function, a trailing space must be added after each comma delimiter to improve readability.

```php
$arr = array( 1, 2, 4, 'item', 'person', 'order' );
```

#### Associative Arrays
When declaring associated arrays with key => values special spacing and padding is necessary. Below is the format that should be followed.

The various `=>` should be spaced out to align veritcally.

The opening `array(` should be on the inital line and the closing parenthesis `)` should be inline with the opening line.

```php
$assocArr = array(
	'item'		=> 'some value',
	'item2'		=> 'anotherValue',
	'person' 	=> array(
		'subItem'	=> 'format',
		'gob' 		=> 'bluth'
	),
	'still'		=> 'aligned',
);
```


### <a name="" href="#">Formatting</a>
---

#### <a name="" href="#">Function formatting</a>
This is the preferred formatting for a function.
> ####Notice:
>* The arguments are 1 space away from the opening and closing parenthesis.
>* The curly braces start on the same line as the function then end indented the same as the beginning of the function.

```php
public function myFunction( $arg1, $arg2 = array() ) {
	/* Code here! */
}
```

#### <a name="" href="#">Loop formatting</a>
This is the preferred formatting for a loop.

```php
for( $i = 0; $i <= 100; $i++ ) {
	/* Code here! */
}

foreach( $arr as $k => $v ) {
	/* Code here! */
}

while( $i < 40 ) {
	/* Code here! */
}

do {
	/* Code here! */
} while ( $i < 40 );
```

#### <a name="" href="#">Conditional formatting</a>
This is the preferred formatting for a conditional.

```php
if( $var === true ) {
	/* Code here! */
}

if( $var === true ) {
	/* Code here! */
} else if( $var === false ) {
	/* Code here! */
} else {
	/* Code here! */
}

switch( $var ) {
	case true:
		/* Code here! */
		break;
	case false:
		/* Code here! */
		break;
	default:
		/* Code here! */
		break;
}

$ternary = ($var === true) ? 'Hello World' : 'Goodbye World';
```
>#### Special Conditional Circumstances
Sometimes you need to add a one liner conditional to a loop or similar. It is acceptable for you to break the formatting standards in this circumstance. You can do them in one line or two lines without curly braces.

>```php
for( $i = 0; $i <= 10; $i++ ) {
	/* Option 1 */
	if( $i % 4 == 0 && $i !== 0 ) continue;
>
	/* Option 2 */
	if( $i % 4 == 0 && $i !== 0 )
		continue;
}
```

## SQL Formatting! (WIP)
```php
$sql = 'SELECT
			`id`,
			CASE
				WHEN `purchased` = 1 AND `sold` IS NOT NULL
					THEN 1
				ELSE 
					NULL
			END AS `bought`
			`created`,
		FROM `orders`
		WHERE
			UNIX_TIMESTAMP(`created`) >= 1442258542
		GROUP BY
			`id`
		ORDER BY
			`created` ASC
		LIMIT 1000';
```
