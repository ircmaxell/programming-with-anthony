Closures
========

The first interesting thing about closures in JavaScript
Is that they are no different from normal functions.

That's right, all functions in JavaScript are closures.

But what are closures?

To understand what a closure is, 
let's first look at a different language: PHP.

PHP has two main variable "scopes":
Global scope and Function scope.

The default scope is the one that you are currently operating in,
ignoring the concept of "super globals".

So if we assign a variable inside of a function, 
The variable is set to the function's scope.

If we wanted that variable to be in the global scope,
We would need to declare that was our intention.

So in PHP, when we declare a closure
we need to explicitly tell it which variables to import from the parent scope.

The important thing to note here is that the variables are *imported*.
The variables are actually copied into the closure.

Therefore, in PHP, each "scope" is completely independent from every other scope.

JavaScript on the other hand uses nested scopes.
