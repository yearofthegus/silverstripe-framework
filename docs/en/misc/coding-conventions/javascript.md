# Coding Conventions - JavaScript

This document provides SilverStripe coding conventions specific to JavaScript.  For other general
conventions, please [the coding conventions homepage](/misc/coding-conventions).

These conventions have been adopted largely from the [jQuery style guide](http://contribute.jquery.org/style-guide/js/).

## Linting

Use JSHint to detect errors and potential problems.  Use the following configuration options:

    {
        "boss": true,
        "curly": true,
        "eqeqeq": true,
        "eqnull": true,
        "expr": true,
        "immed": true,
        "noarg": true,
        "onevar": true,
        "quotmark": "double",
        "smarttabs": true,
        "trailing": true,
        "undef": true,
        "unused": true
    }

## Boilerplate and global variables

All of your code should be wrapped in a closure to avoid polluting the global namespace.  Each
module may expose at most one global variable.

If you are using, jQuery, use the following boilerplate.

    (function($) {

        // your code here

    }(jQuery));

## Spacing

In general, make use of liberal spacing to improved human readability, and rely on the minification process to create a file that is optimized for browsers to read and process.

 * Indentation with tabs.
 * No whitespace at the end of line or on blank lines.
 * Lines should be no longer than 100 characters, and must not exceed 120 (counting tabs as 4 spaces).
 * Unary special-character operators (e.g., !, ++) must not have space next to their operand.
 * Any , and ; must not have preceding space.
 * Any ; used as a statement terminator must be at the end of the line.
 * Any : after a property name in an object definition must not have preceding space.
 * The ? and : in a ternary conditional must have space on both sides.
 * No filler spaces in empty constructs (e.g., {}, [], fn())
 * New line at the end of each file.

## Block spacing

An if statement with a single command and no

if/while statements can be written without braces if they are executing a single command, and the
there is no `else` statement exists.

In all other cases, if/else/for/while/try always have braces and always go on multiple lines. 

    // Good
    if(condition) doSomething();
     while(!condition) iterating++;

    if (condition) {
        doSomething();
    } else if ( otherCondition ) {
        somethingElse();
    } else {
        otherThing();
    }
     
    while (!condition) {
        iterating++;
    }
     
    for (; i < 100; i++) {
        object[ array[ i ] ] = someFn( i );
    }
     
    try {
        // Expressions
    } catch (e) {
        // Expressions
    }

    // Bad
    if(condition) doSomething();
    else somethingElse();

    for(var i=0;i<100;i++) object[array[i]] = someFn(i);

### Objects

Object declarations can be made on a single line if they are short (remember the line length limits). When an object delcration is too long to fit on one line, there must be one property per line. Property names only need to be quoted if they are reserved words or contain special characters:

    // Bad
    var map = { ready: 9,
        when: 4, "you are": 15 };
     
    // Good
    var map = { ready: 9, when: 4, "you are": 15 };
     
    // Good as well
    var map = {
        ready: 9,
        when: 4,
        "you are": 15
    };

## Arrays and Function Calls

Always include extra spaces around elements and arguments:

    array = [ "*" ];
     
    array = [ a, b ];
     
    foo( arg );
     
    foo( "string", object );
     
    foo( options, object[ property ] );
     
    foo( node, "property", 2 );

Exceptions:

    // Function with a callback, object, or array as the sole argument:
    // No space on either side of the argument
    foo({
        a: "alpha",
        b: "beta"
    });
     
    // Function with a callback, object, or array as the first argument:
    // No space before the first argument
    foo(function() {
        // Do stuff
    }, options );
     
    // Function with a callback, object, or array as the last argument:
    // No space after after the last argument
    foo( data, function() {
        // Do stuff
    });

## Multi-line Statements

When a statement is too long to fit on one line, line breaks must occur after an operator.

    // Bad
    var html = "<p>The sum of " + a + " and " + b + " plus " + c
        + " is " + (a + b + c);
     
    // Good
    var html = "<p>The sum of " + a + " and " + b + " plus " + c +
        " is " + (a + b + c);

Lines should be broken into logical groups if it improves readability, such as splitting each expression of a ternary operator onto its own line even if both will fit on a single line.

var firstCondition( foo ) && secondCondition( bar ) ?
    doStuff( foo, bar ) :
    doOtherStuff( foo, bar );

When a conditional is too long to fit on one line, successive lines must be indented one extra level to distinguish them from the body.

    if ( fistCondition() && secondCondition() &&
            thirdCondition() ) {
        doStuff();
    }

## Chained Method Calls

When a chain of method calls is too long to fit on one line, there must be one call per line, with the first call on a separate line from the object the methods are called on. If the method changes the context, an extra level of indentation must be used.

    elements
        .addClass( "foo" )
        .children()
            .html( "hello" )
        .end()
        .appendTo( "body" );

## Assignments

Assignments in a declaration must be on their own line. Declarations that don't have an assignment must be listed together at the start of the declaration. For example:

    // Bad
    var foo = true;
    var bar = false;
    var a;
    var b;
    var c;
 
    // Good
    var a, b, c,
        foo = true,
        bar = false;

## Equality
Strict equality checks (===) must be used in favor of abstract equality checks (==). The only exception is when checking for undefined and null by way of null.

// Check for both undefined and null values, for some important reason.
undefOrNull == null;

## Type Checks

 * String: `typeof object === "string"`
 * Number: `typeof object === "number"`
 * Boolean: `typeof object === "boolean"`
 * Object: `typeof object === "object"`
 * Plain Object: `jQuery.isPlainObject( object )`
 * Function: `jQuery.isFunction( object )`
 * Array: `jQuery.isArray( object )`
 * Element: `object.nodeType`
 * null: `object === null`
 * null or undefined: `object == null`
 * undefined:
   * Global Variables: `typeof variable === "undefined"`
   * Local Variables: `variable === undefined`
   * Properties: `object.prop === undefined`

## Comments

Comments are always preceeded by a blank line. Comments start with a captial first letter, but don't require a period at the end, unless you're writing full sentences. There must be a single space between the comment token and the comment text; for multi-line comments a new line may be used in place of a space.

Single line comments go over the line they refer to:

    // We need an explicit "bar", because later in the code foo is checked.
    var foo = "bar";

Multi-line comments may be used for long comments:

    /*
    Four score and seven—pause—minutes ago...
    */

Inline comments are allowed as an exception when used to annotate special arguments in formal parameter lists:

    function foo( types, selector, data, fn, /* INTERNAL */ one ) {
        // Do stuff
    }

## Quotes

Uses double quotes.

    var double = "I am wrapped in double quotes";

Strings that require inner quoting must use double outside and single inside.

    var html = "<div id='my-id'></div>";

## Semicolons

Use them. Never rely on ASI.

## Naming Conventions

Variable and function names should be full words, using camel case with a lowercase first letter. Names should be descriptive but not excessively so. Exceptions are allowed for iterators, such as the use of i to represent the index in a loop. Constructors do not need a capital first letter.

## DOM Node Rules

`.nodeName` must always be used in favor of `.tagName`.

`.nodeType` must be used to determine the classification of a node (not `.nodeName`).