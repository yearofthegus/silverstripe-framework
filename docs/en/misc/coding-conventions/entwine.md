# Coding Conventions - Entwine.js

This document provides SilverStripe coding conventions specific to Entwine.js.

See also:

 * [General coding conventions](/misc/coding-conventions).
 * [JavaScript coding conventions](javascript).

## Namespacing and boilerplate

Use the entwine namespace support to namespace your code.  The following boilderplate is recommended:

	(function($) {
		$.entwine('yournamespace', function($){

			// Your code here

		});
	}(jQuery));

## onadd vs onmatch

(Hamish to complete.)