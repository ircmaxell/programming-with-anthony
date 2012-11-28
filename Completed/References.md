References in PHP
=================

To explore how references work in PHP
We need to first take a step back
And take a look at how variables work in PHP.

Typically, we're taught to visualize a variable
as a named container for a value.

But we often find ourselves in a situation
where we need to copy a variable.

Copies can be as straight forward as directly assigning one variable to another.
But copies can also occur in other situations,
Such as when passing a variable to a function,
When returning a variable from a function
Or when iterating over an array.

So when we copy a variable,
we're copying the contained value as well.

And that makes sense. 
If we have two different variables with different names,
we'd expect the containers to be different.

So if we edit one container, 
we expect the other to remain the same.

But this has some problems as well.
Every time we copy a variable,
we need to duplicate the contained value as well.

This can lead to severe memory duplication,
which can result in major performance issues.

The PHP solves this problem
Is by separating the variable from the value container.

Variables then become nothing but pointers to a value.

When we copy a variable, we are just copying that pointer.

This introduces a new problem:
When we delete a variable,
How do we know if we can delete the value?

The way PHP solves this,
Is by keeping a count of the number of references to a value.

So the value container, now has two fields
The value itself,
And a reference counter, also known as a "refcount"

Every time we copy a variable, we increase this refcount
And every time we delete a variable, we decrease this refcount.

If the refcount ever hits 0, we can safely delete the value.

But we also have another problem.
If we edit the copy of a variable,
We're also editing the original one.

This is because they are using the same value container.

Luckily, we already have a way of fixing this.
We can use the "refcount" to tell us when we can edit,
Or when we need to copy the value.

So when we are editing a value, if the refcount is 1,
We can directly edit the value.

If the refcount is greater than 1,
We need to copy the value first,
And then we can edit the copy.

This is also known as "copy on write".

So far so good.

Now, what happens when we want two variables to be edited together at the same time?
In PHP, we would use the ampersand reference operator.
But what is that doing under the hood?

Well, to implement this feature, all we need to do is disable copy-on-write.
But we only want to disable this for referenced values.

The way we can identifiy this, is to add one more field to the value container.
This is a simple boolean value, which we'll call "is_ref".

If is_ref is true while we're editing a varible, we don't copy the value first.

But now what happens if we try to do a normal copy of a referenced value?
We can't just increase the refcount, because then we'd be doing a reference instead.

So we need to do a full copy of the value.
Therefore, anytime that we use references, 
We lose all of the benefits that copy-on-write gives us.

In PHP4, this was how all variables worked.

Starting with PHP5, objects are treated in a slightly different way.

Instead of storing the object on the value itslef,
there's a second layer of abstraction.

Objects are stored in their own container,
And pointed to by the value.

What that means for us, is that even if we copy an object variable,
all edits still go to the same place.

So we don't need to use variable references at all when dealing with objects.

If we want to make a copy of an object value, 
We need to use the "clone" operator.

When writing modern PHP code,
Don't try to outsmart the system.

Using references to try to save memory usually will wind up costing you more memory.
Let PHP handle variables for you.
It's smarter than you think.

