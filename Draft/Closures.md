Closures
========

The first interesting thing about closures in JavaScript
Is that they are no different from normal functions.

That's right, all functions in JavaScript are closures.

But what are closures?

To understand what a closure is, 
We first need to talk about variable scope.

Let's look at a different language first: PHP.

PHP has two main variable "scopes":
Global scope and Function scope.

The default scope is the one that you are currently operating in,
ignoring the concept of "super globals".

So if we assign a variable inside of a function, 
The variable is set to the function's scope.

If we wanted that variable to be in the global scope,
We would need to declare that as our intention.

So in PHP, when we declare a closure
we need to explicitly tell it which variables to import from the parent scope.

The important thing to note here is that the variables are *imported*.
The variables are actually copied into the closure's scope.

Therefore, in PHP, each "scope" is completely independent from every other scope.
And the only way to tie two scopes together is using variable references.

JavaScript on the other hand uses nested scopes.

The scopes nest based on where they are defined.

So if we define a closure within another function,
The closure's scope will be nested inside the function's scope.

That means that variable access traverses up the chain of scopes
until it finds the scope the variable was defined in.

This means that all functions which are defined inside of another function's scope
are always closures. 
Even if they are named functions!

And considering that the root scope is the global scope,
All functions are nested inside the global scope.

Therefore, all functions in JavaScript are automatically closures!


