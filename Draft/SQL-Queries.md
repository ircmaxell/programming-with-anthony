SQL Queries
===========

To explain prepared statements,
Let's take a look at how SQL works.

When we execute a query,
The application sends it as a single string
to the database server.

The server then parses that string,
and executes the query against the dataset.

It's useful to think of the query
as a program, which is executed against the dataset.

The traditional way of binding user input into a query
is to escape the input, and place it in as part of the query itself.

But SQL offers another way of executing the query:
SQL offers variables.

When we create a prepared statement,
We use variable placeholders
And send the variable's content to the server separately.

By doing this, our query is always separated from user input.
Therefore, things like SQL Injection are impossible.

Now, lets take a step back take a deeper look at SQL itself.

Its important to note that SQL is 
actually a programming language *Turing complete*

From there, we can treat each query as 
Nothing more than a program.

This is an important step, 
because it allows us to explore the similarities
Between SQL and php.

In both, we can hard code static values
Directly into the code.
And both support a form of variables.

So why would we deal with input differently between them?

Would you dynamically rewrite a php file replacing user input
Into the code directly and evaling the result?

Then why should it be OK to do it with SQL?