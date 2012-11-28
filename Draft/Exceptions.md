Exceptions
==========

Let's imagine for a minute that you've a pilot.
A big portion of your job is spent executing checklists.

Engine Start? There's a checklist for that.
Takeoff? There's a checklist for that.
Cruise? There's a checklist for that.

Having an emergency? There are a large number of checklists for that!

Looking at this through the eyes of a progammer,
we can picture each of these checklists as a separate program.

When we need to do something, we just lookup the proper program
and execute it.

Now imagine that you're tasked with writing these programs.
One of your goals is to reduce duplication,
as every time you duplicate a section, the chance for errors is increased.

As you may imagine, there's a lot of duplication in these checklists.
For example, steps to start an engine are included multiple times:

* The engine start checklist
* The engine failure checklist
* The engine restart checklist

So. one technique that we can use here, is to create a "sub-checklist".
We then move those common steps into this new "sub-checklist"
And everywhere we need to use those steps, we just put a reference "see sub-checklist A"

