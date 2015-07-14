Spreadsheet in js
=================

One idea to implement a spreadsheet in html and javascript.

[Demo](http://soquel.github.io/spreadsheet-in-js/)

Features
========

* proof-of-concept code quality
* no error handling whatsoever (i.e. cycles in the sheet are not detected, erroneous formulas are not reported, etc.)
* doesn't support more than 26 columns (i.e. it can handle only A..Z columns, AA, AB, and so forth are not supported)
* written in pure js, no dependencies


How it works
============

Look in the source, it's very simple really.
Any `onchange` event in any cell causes recomputation of all cells.
If cell's input starts with `=`, it's parsed as a formula. Any `<letter><digit>`
in the string is replaced with a function call to compute that particular cell
formula. Once all the string replacements are done, an `eval` is called on the string.


Improvements
============

* add cycles' detection, so user can't exceeded stack size by running too much recursion
* add caching so not all formulas have to be recomputed on each change
* support detecting invalid formulas
* make it work without element ids and support multiple sheets on one page
* add support for mathematical functions like users are used to from spreadsheet
software (e.g. `=POWER()` instead of currently `Math.pow()`, and so on)
