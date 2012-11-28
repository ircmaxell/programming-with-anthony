Paradigm Soup Script
====================

When we talk about programming paradigms,
What are we really talking about?

One way to approach the question
Is by examining how we deal with state.

Let's look at Procedural code:
Each statement is simply a "step" to be executed,
with each "step" manipulating state.
State and the actions manipulating it are completely separate.

With Object Oriented Code on the other hand,
Each statement acts upon state.
But it doesn't just act upon state, it's encapsulated by state.
But the interesting thing, is that state and the action are deeply entangled together.

With Functional Code,
Each statement can only transform state.
Therefore, state is immutable,
meaning that functions cannot change state, 
they can only return new transformations of the original state.
Each function is therefore 100% deterministic.

So there we have it, we've defined the three paradigms
and how they differ from each other
by looking at nothing more than state.

So, here's a quick quiz:
What paradigm does this line use?

How about this one?

And what about this one?

The answer is that we simply can't tell.
One line is just not enough to understand what's going on.

The paradigm does not describe how code is written,
But how code is structured.
So we can only tell what paradigm a piece of code is using
If we can understand the structure of that code.

Now, if you notice, these definitions are very vague.
So what happens if we make some code that encapsulates state
But also modifies that state step-by-step?

What paradigm would this code fall under?

You could look at the objects and encapsulation
And call it Object Oriented.

Or you could look at the steps it uses and how it modifies state
and call it Procedural.

But in a weird way, it's both Procedural, and yet Object Oriented at the same time...

So now we have this nice triangle
except that there's this weird point out here...
For now, let's call it Class Oriented Programming

But we can do the same thing if we encapsulate state
But only ever "translate" it, never manipulating it.
We wind up with a weird hybrid of Object Oriented and Functional programming...
Which we could call Value Oriented Programming

And we can do the same thing with Functional and Procedural programming

So now if we look at our triangle,
We also have three dots outside the triangle
And if we connect them, we get another inverted triangle.

But we can go further.
We can make code that's mostly procedural, 
But also Class Oriented...
And mostly OOP, but also Class Oriented
And So On
And So On

So now, our nice triangle of paradigms
Has morphed into what looks like a circle.
But is it really a circle?

Well, if it was, Class Oriented Programming would be
the literal opposite of Functional programming.

It's not, so we can't really have a true circle.
Instead, if we treat the three paradigms as axis,
We wind up with this 1/8th sphere, taking only the regions
Where each paradigm has a positive value.

All non-trivial portions of code will fall somewhere on this surface.

So if we look at some large PHP codebases
We can find some very interesting trends.

Since most PHP tools haven't significantly adopted Functional programming,
We'll look at the average across just Object Oriented and Procedural.

As you can see,
There are a few that are mostly procedural
And a few that are mostly Object Oriented
But the majority falls somewhere in the middle.

And that's the point:
For any non-trivial application,
There will be Procedural parts
And Object Oriented parts
And Functional parts.

But There'll Also be these mixed parts,
that don't follow a strict paradigm

And there's nothing wrong with that!
So let's not get hung up on names,
And instead just get awesome things done!
