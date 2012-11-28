Encryption
==========

Let's just start with a number
Actually, scratch that, let's start with a string of numbers
These numbers have meaning, but what meaning isn't too important now
They are just numbers

Now, let's say that you wanted to get this number to a friend
But let's also say that there may be bad guys listenting
So we need a way of sharing them in secret.

We could substitute numerals for other numerals
So that only those people know the mapping
Can understand the meaning of the coded message

* So 1 becomes 4
* And 2 becomes 9
* And 4 becomes 7
* And so on...

Now, all we need to do is pre-share the mapping with our friend
And we can transmit our message securely
But how secure is it?

Well, there are only 3,628,800 possible mappings
And since we have no idea what the data might mean
We can never know if we have the right one!

But this is the real world
So let's assume that we know what the numbers mean
Let's assume that they represent letters

There's an interesting thing about letters though
They don't all come out with the same frequency
In fact, some letters are far more likely than others

So given enough encrypted number strings using the same "mapping" key
We can analize the numbers statistically
And start making very educated guesses

From those guesses, we can then derive the "mapping" used as a key
And voila, we have broken the encryption!
We can read any message sent using that key!

So, substituting numerals won't work
I know, let's create a fixed number key
And add that key to each number!

* So our key is 11
* 10 Becomes 21
* 43 Becomes 54
* 99 Becomes 10

We can simply share this "number" with our friend
And we can communicate securely!
Or can we?

As it turns out, this has the same problems as before
Given enough encrypted numbers, we can do some analysis
And determine the "key" statistically.

Note that this is known as a rotational cipher
In other words a "Caesar Cipher" or ROT13
So now what?

Well, we can take the natural next step
Let's change the number that we add for each position

* So first we add 10
* Then we add 23
* Then we add 5 
* Then we add 46

But now we have another problem
How do we communicate the series we're adding to?
Well, as it turns out, there are two types of solutions

We can pre-generate random pads to use
Then share these pre-generated pads with our friend
And use them to encrypt our numbers!

Notice that there's no way to statistically attack this
Since the pad amount changes for each character!
We've created perfect security!

Well, under one condition:
That we never re-use a random pad.
If we don't ever reuse it, it's called a one-time-pad
And demonstrates perfect security!

But that's not that useful because it requires a lot of these pads
There must be another way!
What if we had a function which generated these random strings for us?

Then, we could simply share the function with our friend
And we'd both use it to generate the pads

For a nieve function, that's no different than adding the same number,
Because we can statistically attack each character of multiple messages
So that's not good.

Instead, what if that function took an input?
Let's call it a "Key"
Then, we can just share that key and we're all good!

Well, not really. Since that's no different than using the nieve function
The one advantage that we have is we can re-use the same function with different keys
But we can do better.

Let's make that function take 2 arguments
A "Key" and an "Input"
Now, we can use the same secret key to generate many different pads!

The really cool part here, is that our security only depends
On the key being secret...
We can openly share the "input"

So, now we have this function that takes a key and an input, and produces a random looking output
And let's also build the opposite function (that takes the output and produces the input)
Let's call this pair of functions a Block Cipher

It's important to note that the function will always produce
an output of a fixed length.
So if we want to encrypt more than this length worth of data
we need to use it multiple time.

The first thought would be to encrypt data directly with the Cipher
So we feed the block of data into the input
And use the resulting output as the ciphertext

The name for this is Electronic Code Book or ECB
Note that the same input for the same key will always make the same output
That's not good

The problem is that we still can do statistical analaysis
We can still attack this mode pretty easily
Surely we can do better?

Well, what if we instead used a random input
Since the key is secret, we can share it openly.
Let's call this an Initialization Vector
or an IV for short.

One way to use this would be to encrypt the IV directly
Using the output to as a pad for our plain text

Let's call this Output Feedback

The interesting thing is that we can use the output of one block
as the input for the next.
So we're effectively chaining each block together,
feeding back the output of one block to the input of the next.

Using this, we can securely encrypt data of an arbitrary size.
To decrypt the data, we just perform the same operation,
swapping the ciphertext and plaintext.
Note that we only need "encrypt", never "decrypt"

And we've arrived at our first secure Cipher Mode
As long as key is secret, and we don't reuse IVs
This is secure!

There are other methods like this
That differ in how blocks are chained and fed back
Such as Cipher FeedBack and Cipher Block Chaining
But we don't need to go into those now

So, there we have it.
We've found two secure methods of encryption
Which is chosen depends on the needs of the user

There's a whole lot more we could go into
Packing Modes, Authentication, Verification, etc
But I think this is a good start

There's a lot to digest here
But one thing to keep in mind

The only practically 100% secure system
Is one that does not exist

All systems are subject to some kind of attack
Even if it's just social engineering

If you need to secure a system,
Above all,
Hire an Expert!