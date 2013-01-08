Dependency Injection
====================

What is Dependency Injection?
Well, the literal meaning is to inject dependencies.

So let's start by defining what a Dependency is.
A Dependency is just another object that your class needs to function

So if you have a model class that fetches data from a database object,
We can say that your model class has a dependency of the database object.

So now that we know what the dependency is, let's talk about what it means to inject dependencies.

Injecting dependencies just means that the dependency is pushed into the class from outside.

All that means is that you shouldn't instantiate dependencies with `new` inside of the class,
But instead take it as a constructor parameter or via a setter.

That's all there is to Dependency Injection. 

You don't need a fancy container or class to do it.
Sure, they may make your life easier, but you don't *need* them...

But Why should you inject dependencies in the first place?

Let's imagine for a minute that you're programming a house building robot.
You start with a pile of lumber, and program it to start building walls.

Then, when you get to a doorway, what do you do?

Do you program it to build a custom door out of raw materials? 
Or do program it to take a ready made door from a supplier and install it?

The most flexible way to do it would be to take the door from a supplier.

And that's exactly what dependency injection does.
It decouples your classes construction from the construction of its dependencies.

The reason that is so important is the Dependency Inversion Principle.

Basically, Dependency Inversion is the principle that code should depend on abstractions.
By depending on abstractions, we're decoupling our implementations from each other.

In PHP, that means that your code should depend on interfaces.
That way, we can substitute different dependencies, as long as they all satisfy that required interface.

By using Dependency Injection, we decouple our code from the lower-level implementations,
making our code cleaner, easier to modify and easier to reuse.

Now that we've adopted Dependency Injection, now we have another problem.
Each one of our classes require dependencies.

So now, to construct each and every class, we need to figure out what dependencies they need,
And figure out a way to get them to the line instantiating them.

Luckily for us there is a solution.
Enter the Dependency Injection Container.

At the root, the container is nothing more than a map of the dependencies that your classes need,
With the logic needed to create them if they haven't been created yet.

So every time you ask for a `DatabaseInterface`, the map tells it which dependency to use,
Then the container can check to see if it has one created already, and if it has, use that one.
Otherwise, it'll create the database instance, store it, and then provide it to your class.

So instead of constructing your class yourself, you ask the container for a new instance.
It will then resolve the dependencies, construct the object and return it to you.

The best part of it is that the container can resolve complex dependencies transparently.
And if you want to swap out a generic dependency, say if you're switching from APC to Memcached, 
You only need to update that dependency in the container once.

So write cleaner and more modular code.
Use Dependency Injection...
