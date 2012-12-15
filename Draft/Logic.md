When discussing boolean logic when it relates
to programming, it's often useful to step back
and look at the foundations of logic.

At the root of logic are two fundimental values: True and False.

For purposes of this discussion, we're also going to be using
variables.

Before we get into the different logical operators,
there's one more tool that I want to introduce called
a Truth Table

To use one, we simply enumerate all possible permutations
of the variables involved.

For a single variable, there will be 2 permutations.
For two variables, there will be 4,
For three variables, there will be 8
And so on.

Then, when we add operators, we can see the effect for 
all possible input states.

Let's introduce our first logical operator
called "NOT".
It's a UNARY operator, which means that it only operates
on one value at a time.

All the NOT operator does, is switch TRUE to FALSE
and vice versa. It inverts the value.
So far, so good.

The next important logical operator is the "AND" operator.
It's a binary operator, which means that it operates on 
exactly two values.

When both values are true, the AND of them is also true.
In all other cases, the AND is false.

Next comes the "OR" operator, another binary operator.
It is True when any one of the inputs is true.
It is only False, when BOTH of the inputs are false.

The final operator is the exclusive OR operator.
It is True only when the inputs are different.
Therefore, it is only True when exactly one of the values is true.

Now that we have our basic operators,
We can start to do some really interesting things.

Let's try combining two operators to create a composite.
`(A AND B) OR A`

To see how this will result, let's create a truth table
and populate step by step.

First, we evaluate the inner most logical element.
So we compute `A AND B`.

Next, we take that result, and compute the OR with A.

Very quickly, we can see the exact states that the original
composite represented.

Notice that the values of the expression `(A AND B) OR A`
are identical to the values of A itself.
This means that `(A AND B) OR A` is logically equivilant to just A.

However, there is a very important difference that makes
them not identical.

PHP uses what's known as "Short-Circuit Logic".
Basically, that means that if it knows the result of a 
composite statement partially through executing it,
It stops executing it.

That means that FALSE AND A will never evaluate A.
It also means that TRUE OR B will never evaluate B.

So now, when we look back, we can see that B
will only be evaluated if A is True.

Therefore, reducing `(A AND B) OR A` to it's logical eqivilant `A`
prevents the execution of B if A is true.

Now, there's one more thing that I want to show you
called De Morgan's Laws.

Basically, De Morgan's Laws are a set of logical equivalences
that are very useful when handling negation.

The rules are:

    !(A AND B) == !A OR !B
    
and

    !(A OR B) == !A AND !B

To see why these work, let's create a truth table.

First, let's create `!A` and `!B`
Next, let's create `A AND B`.
Now, we can negate `A AND B` to get `!(A AND B)`
Finally, we can create `!A OR !B`

See how they have the identical values?

This is extremely useful when you want to negate complex logic
and still have it provide semtantic meaning.

To apply that in a real world example, let's look at a case
where we want to turn off debugging for a section of code:

    if (!($site->isDev() || $site->isDebug()))

It takes a minute to figure out what's going on there, 
since we have a lot of things in the way.

Using De Morgan's Laws, we can rewrite this in a more clear way:

    if (!$site->isDev() AND !$site->isDebug())

Now, our code is clearer, because we can read it left to right as
"If the site is not dev, and it is not in debug mode, then"

Using these simple logical analysis tools,
we can do some very powerful things.

And above all, we can help make our code more readable at the same time.
