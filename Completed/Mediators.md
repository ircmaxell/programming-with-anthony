Mediator Pattern
================

The mediator pattern is one of the basic Object Oriented Design Patterns.

At its core, it is designed to decouple a producer from a consumer.

But a producer of what?

One of the common use-cases for a mediator is for handling events.

If you've worked with jQuery or JavaScript events, 
you've already worked with a mediator.

When a user clicks on a link in a web page,
the browser creates a click event, and asks the document to handle it.

The document is our mediator.
It will lookup all event handlers that are registered to recieve that click event,
And call them one by one.

And that's all a mediator really does.
It doesn't implement any application logic itself.
It doesn't couple itself to anything in the application.
It just acts as a post office to deliver messages in an abstract manner

The pattern itself is very simple.
In fact, it can be implemented with as little as 2 methods:

    interface Mediator {
    	public function addListener($eventName, $callback);
    	public function notify($eventName);
    }

Where the addListener method registers a callback,
And the notify method triggers all registered callbacks for a particular event name.

So that defines a basic mediator. 

But what if we want some more advanced functionality?

Well, depending on our needs, we can add some really interesting things to the basic mediator.

For example, if we want to pass data to the callbacks,
We could add an arguments array to notify().

If we want more flexibility in listeners,
We could add wildcard event names.

If we want to allow listeners to pass data back to the producer,
We could have our notify() method keep track of return information.

If we want to allow listeners to "cancel" an event,
We could create an event object with a cancel method.
Which would then be passed to each callback.

The possibilities are really only limited by your imagination.

But at the core, a mediator is a great tool which allows you to decouple parts of an application.