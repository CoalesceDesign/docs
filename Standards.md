The Coalesce standards for writing CSS, HTML, and JS. This document defines a uniform approach to writing code across all Coalesce projects.

_These are not merely guidelines_ — if you disagree with a standard, take it up with the group, but until the standard is revised it should be followed on all your Viget work.

- [General](#general)
- [HTML](#html)
- [CSS](#css)
- [JavaScript](#javascript)

<hr>

# General

### Indentation
Indent with hard tabs, not spaces. Do not mix tabs and spaces.

```
RIGHT
var handler = function() {
	var response = 'foo';
var error = 'bar';
	$(this).remove();
}

WRONG
var handler = function() {
  var response = 'foo';
  var error = 'bar';
  $(this).remove();
}

WRONG
var handler = function() {
var response = 'foo',
    error = 'bar';
$(this).remove();
}
```

<hr>

### Quotes
Use double quotes in HTML, single quotes everywhere else.

```
RIGHT
<html class="lt-ie7">
var html = '<a href="#">';
background-image: url('image.png');

WRONG
<html class='lt-ie7'>
var html = "<a href='#'>";
background-image: url("image.png");
```

<hr>

### Blank Lines
Use a single blank line to visually separate ideas. The first and last lines of a block are never blank.

```
RIGHT
// no methods, thus, no blank lines
myObject = {
	foo: bar,

	bar: foo
};

// has methods, has blanks
myMethods = {
	init: function() {},

	bindEvents: function() {}
};

/* @group reset */

	p {
		margin: 0 0 10px;
	}

	div {
		margin: 0 0 10px;

		p {

		}
	}

/* @end */


WRONG

myMethods = {
	init: function() {},
	bindEvents: function() {}
}

/* @group reset */

	p {

		margin: 0;

	}
	div {
		margin: 0 0 10px;
	}

/* @end */
```

<hr>

### Comments
Comments are either single-line, or multi-line with indents. JavaDoc style (starting each line with a *) is not used.

```
RIGHT
/* Single-line comment */
// Single-line comment
<!-- Single-line comment -->
<!--
Multi-line comment
-->
/*
Multi-line
comment
*/

WRONG
// Multi-line
// Comment
/**
 * Multi-line
 * Comment
 */
```

<hr>

### Grouping
CSSedit syntax are used for groups in CSS or JS. The contents of a group are indented. Group titles are lowercase. Groups are surrounded by blank lines.

```
RIGHT
/* @group wysiwyg text */

	p {
		margin: 0 0 5px;
	}

	/* @group lists */

	/* @end */

/* @end */

WRONG (VIM STYLE)
/* wysiwyg text {{{ */

p {
	margin: 0 0 5px;
}

/* lists {{{*/

/* }}} */

/* }}} */

WRONG (NO GROUPS)
/* Wysiwyg Text */

p {
	margin: 0 0 5px;
}

/* Lists */
```

<hr>

### Existing code
These standards are applied to all work, including new code written in existing projects. When practical, existing project should be updated to meet these standards.

<hr>

# HTML

### Tags
Close all tags. Lowercase element names. Don't use trailing slashes for self-closing tags. Use HTML5 booleans when appropriate.

```
RIGHT
<p class="intro">Text goes here.</p>
<input type="checkbox" checked>

WRONG
<P class="Intro">Text goes here.
<input type="checkbox" checked="checked" />
```

<hr>

### IDs & Classes
IDs/class names are lowercase, and they do not contain underscores.

```
RIGHT
<p id="intro-text">Text goes here.</p>
<img class="header-highlighted-image" src="image.jpg">

WRONG
<P class="Intro_text">Text goes here.
<img src="image.jpg">
```

<hr>

### Long Tags
When HTML tags get too long, their attributes are broken out and indented. In this case, the closing caret is on its own line, at the original indentation level.
```
RIGHT
<div class="products">
	<div class="product">
		<a href="http://www.amazon.ca/gp/product/B005SH65UO/r_ri_gw...
class="track-link product-link highlighted product-link"
data-to-track="Product,Click,Frozen Planet"
>
	</div>
</div>

WRONG
<div class="products"><div class="product">
		<a href="http://www.amazon.ca/gp/product/B005SH65UO/r_ri_gw... class="track-link product-link highlighted product-link"
data-to-track="Product,Click,Frozen Planet">
</div></div>
```

<hr>

### Server-side Tags
Keep markup out of PHP echo statements. Multiline PHP blocks should have their start and end functions on separate lines, with code indented one additional tab level between them.

```
RIGHT
<ul class="products">
	<?php foreach($products as $product): ?>
		<li><?php echo $product['name']; ?></li>
	<?php endforeach; ?>
</ul>

WRONG
<div class="products">
<?php foreach($products as $product) {
	echo '<li>'.$product['name'].'</li>';
} ?>
</div>
```

<hr>

# CSS

### Font sizing
Don't use ems unless you have a really special case. Line-height on broad selectors (body, p) should be unitless.

```
p {
	font-size: 15px;
	line-height: 1.45;
}
```

<hr>

### Sass Syntax
Use Sass, Use the SCSS syntax.

<hr>

### CSS Selector Names
Try to always use classes if possible. Shorter the better. Try to use single words - no more than 3 words is best. However, clarity is much more important than being overly concise.

IDs are written in CamelCase:
```
#MainWrapper
```
Classes are written in CamelBack:
```
.productName
```

<hr>

### CSS Formatting
Each CSS selector and property is on its own line. If an property has comma-separated values and becomes too long, it can be broken out into multiple lines, with the first value on a new line.

```
RIGHT
.mainContent h2,
.mainContent h3 {
	@include background(
		linear-gradient(
			left,
			rgba(255, 255, 255, 1) 0%,
			rgba(255, 255, 255, 1) 100%
		);
	);
	box-shadow:
		0 0 2px rgba(0,0,0,0.3),
		inset 0 0 2px rgba(0,0,0,0.3);
	font-size: 20px;
}

WRONG
.mainContent h2, .mainContent h3 {
	@include background(linear-gradient(left, rgba(255, 255, 255, 1) 0%, rgba(255, 255, 255, 1) 100%));
	box-shadow: 0 0 2px rgba(0,0,0,0.3),
inset 0 0 2px rgba(0,0,0,0.3);
	font-size: 20px;
}

NOT EVEN CLOSE
.mainContent h2, .mainContent h3 { box-shadow: 0 0 2px rgba(0,0,0,0.3), inset 0 0 2px rgba(0,0,0,0.3); font-size: 20px; }
```

<hr>

# JavaScript

### Var and method names
All JavaScript var names are formatted as camelBack. The only exception is any var that's used as a class/constructor (which are TitleCased).
jQuery/Zepto objects are always preceded with $.
Use "self" to reference or minify "this" when necessary.
Use "init" to define the first method called on an object.

```
RIGHT
var clickHandler = function(){};
var $timerContainer = $('.timer');
var isReady = true;
var Timer = function() {
	this.init();
};
var timer = new Timer();

WRONG
var click_handler = function(){};
var TimerContainer = $('.timer');
var ready = true;
var timer = function() {
	this.init();
};
var timer = new Timer();
```

<hr>

### Whitespace
Opening braces are preceded by a space.

```
RIGHT
for (var i = 0, j = arr.length; i < j; i++) {
// Do something.
}
WRONG
for ( var i = 0, j = arr.length; i < j; i++ )
{
		// Do something.
}

WRONG
for(var i=0,j=arr.length;i<j;i++){
// Do something.
}
```

<hr>

### Var declarations
Vars are declared at the start of scope. They each have their own line, and begin with the var keyword.

```
RIGHT
var doStuff = function() {
var a = true;
var b = false;
var d = true;
var e = false;
}

OH MY GOD
var doStuff = function(){
var a = true, b = false
c = true;
alert('Vars are set!');
var d = true
, e = false;
}
```

<hr>

### Functions
Functions are declared as variables, to avoid problems with JavaScript's name hoisting. A space follows the argument parens.

```
RIGHT
var doStuff = function() {
};

WRONG
function doStuff(){
}
```

<hr>

### Object/Array Syntax
Use linebreaks, unless you have a single-property array or object. Put a space after each colon. Don't quote object literal keys unless they contain special characters. (The exception is writing a string to be parsed as JSON, which requires double quotes on keys and values)

```
RIGHT
{
	year: 1970,
	month: 'January'
}
arr.push({
	year: 1970,
	month: 'January'
});
[
	'January',
	'February'
]
{year: 1970}
['January']

WRONG
{'year' : 1970,
'month' : 'January'}
['January',
'February',
'March']
[
'January'
]
```

<hr>

### "Optional" Syntax
Although semicolons and braces can be parser-optional, we use them.
Semicolons follow a statement.
Conditional blocks go on a new line.
Else/else if/catch go on the same line as the brace.

```
RIGHT
if (true) {
	alert('true!');
} else {
	alert('false!');
}

WRONG
if (true)
	alert('true!')
else alert('false')

WRONG
if (true)
{
	alert('true!')
} else { alert('false!') }
```

<hr>

### Flow control with operators
Use of &&, ||, and ternary operators to control execution flow and variable declaration is totally okay.

```
RIGHT
timer.timeout = timer.timeout || setTimeout(timer.loop, 5000);
isTimerReady ? timer.start() : timer.wait();
isTimerReady || timer.wait();
isTimerReady && timer.start();
timer[isTimerReady ? 'start' : 'wait']();
```

<hr>

### Strictness
=== is preferred to == when applicable.
Window properties (not methods) are prefixed with "window".
parseInt() always gets a second argument of 10 (unless you really do want to parse an octal or a binary number).

<hr>

### Eval
Don't use eval() to solve any problem except executing user-written JS. Don't pass strings to setTimeout().

<hr>

### Script Tags
HTML comments, CDATA, etc don't belong in script tags. Neither do language or type attributes.

```
RIGHT
<script>
	doStuff();
</script>
<script src="dostuff.js"></script>

WRONG
<script src="dostuff.js" language="javascript" type="text/javascript"></script>
<script language="javascript" type="text/javascript">
	<!--
		doStuff();
	-->
</script>
```
