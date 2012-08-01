JavaScript: The Good Parts (video)
http://ontwik.com/javascript/javascript-the-good-parts/
Douglas Crockford
-----------------
* a language of many contrasts - some of the best & worst ideas put into a
  programming language
* massive range of skills of JavaScript programmers
* basically Scheme with C syntax
* Crockford contends the DOM api is why the browser programming experience is
  awful, not because of JavaScript itself
* JavaScript influences from Self, Java, Scheme, and Perl
  * Self - prototypal inheritance, dynamic objects
  * Java - syntax, conventions
  * Scheme - lambda, loose typing
  * Perl - regex (Crockford says this is a bad part)
* Bad parts: global variables, + adds & concatenates, semicolon insertion,
  typeof, with and eval, phony arrays, == and !=, false, null, undefined, 
  and NaN
* typeof on a null says "object" so it is wrong
* with is just bad
* eval is generally a bad construct to use
* equality does type coercion (bad)
* 0 == '' // true (yikes)
* === does not do type coercion
* 0 === '' // false
* for .. in is troublesome (deep dive into object inheritance)
* recommends always putting curly braces in and not use blockless statements
* recommends against using ++ and -- due to the number of mistakes people make
  while using them
* JSLint - code quality tool for JavaScript
* recommends against using the switch statement and falling through logic
* Good parts: lambda, dynamic objects, loose typing, object literals
* Prototypal inheritance (not classical)
* In prototypal inheritance, objects inherit from other objects, there are
  no classes
* Crockford no longer uses new - considered too dangerous
* 4 ways to create an object, 1. object literal, 2. new, 3. Object.create,
  4. call another power constructor
* * 
