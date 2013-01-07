Iterators
=========

In general, an iterator is nothing more than a sequence generator.

But what is a sequence?

At its most basic level, a sequence is an ordered list of values.
Values can be repeated in the list multiple times,
And their order does not need to be sorted.

The most basic type of sequence in programming is the array.

Array elements can be any value, and can be positioned randomly.
But once they are set, the array has a defined order.

If we then loop over that array,
each loop will have the next item in the sequence.
Until we run out of items, that is.

    foreach ($array as $key => $value) {
        echo $value;
    }

If we looped over an array manually, we'd write a for loop.
Let's see what's happening in that for loop.

    for ($i = 0; $i < count($array); $i++) {
        echo $array[$i];
    }

The first step, we set `$i` to 0.
Then we check to see if `$i` is less than the length of the array.
Then we execute the body of the loop.
Finally, we increment $i, and go back to step 2.

Without realizing it, every time you write a for loop like this,
you're building an iterator!

An iterator is just an abstraction of the for loop.
We have a `rewind()` method, which is the same as setting `$i` to 0.
We have a `valid()` method, which is the same as check if `$i` is less than the length of the array.
We have a `next()` method, which is the same as incrementing `$i`.

And finally, we have 2 functions that are useful in the body:
The `key()` method, which translates to fetching `$i`,
And the `current()` method, which gets the value of the array at `$i`.

So our for loop can be rewritten as a for loop with iterators:

    for ($it->rewind(); $it->valid(); $it->next()) {
        $current = $it->current();
        echo $current;
    }

In reality, that's all `foreach` does internally anyway.
Except that `foreach` exposes `$key` and `$value` automatically for us!
So our original foreach call becomes this:

    foreach ($it as $key => value) {
        echo $value;
    }

Note that it looks identical as the first foreach!
When using `foreach`, arrays and iterators are interchangable.

So let's build our first actual iterator.
Let's build our for loop as an iterator:

    class ForLoopIterator implements Iterator {
        protected $array;
        protected $i = 0;
        public function __construct(array $array) {
            $this->array = $array;
        }
        public function rewind() {
            $this->i = 0;
        }
        public function valid() {
            return isset($this->array[$this->i]);
        }
        public function next() {
            $this->i++;
        }
        public function key() {
            return $this->i;
        }
        public function current() {
            return $this->array[$this->i];
        }
    }

First, we need to make our class implement the `Iterator` interface.
This interface defines the 5 methods we need.
But it also enables some behind the scenes magic that lets us use an iterator in foreach statements.

Other than that, this class should look like nothing more than a verbose for statement.

It's worth noting that in practice we wouldn't write this class custom, but would instead use the core ArrayIterator
Which basically does the same thing (although it does deal with non-integer keys better).

