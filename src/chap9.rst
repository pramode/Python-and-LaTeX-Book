
Finding square root by Newton's iteration
=========================================

We have used Python to write tiny programs, programs which are less than
ten lines of code. Most useful programs are much longer; for example, the
core of the Linux operating system (called the *kernel*) has a few million
lines of code written in the C programming language! Such a system is the 
collective effort of hundreds of programmers. These programmers spend their
time reading code written by others, making improvements and correcting 
errors. As a programmer, it is your responsibility to write clear, readable
code. In this chapter, we examine how to use functions to achieve this
objective.


Programming as Essay writing
-----------------------------

How do you go about writing an essay (or a book, newspaper article, whatever)?
First, you form an idea in your mind as to what exactly you wish to convey to
your audience. The message you wish to convey should be presented in
a structured manner; you will divide your essay into sections, sub-sections
and paragraphs. You will make sure that ideas flow logically from one section
to the next. If you are trying to explain something very complex, you will first
introduce your audience to simpler (but related) ideas and then try to build up
the more complex idea on the basis of the simpler ones. You will uphold clarity
as one of your biggest virtues.

Writing a program is similar to composing an essay. Ultimately, your program
has to run on a computer and provide correct output. But it should also be easy
for other people to read, understand and modify your code. Let's study the Python
implementation of a simple square root finding algorithm to understand how
functions can be used to write clear code (the code I have presented here is
the Python version of a program presented in the famous book *Structure and
Interpretation of Computer Programs*).


Finding square roots
--------------------

There is a very simple technique for calculating the square root of a number based
on what is called the *Newton's method*. Let's say you wish to calculate square root
of 16 (we will call this X). We make a guess that the root is 1::

   X = 16, Guess = 1.0

Now, is this guess good enough? We can find out by taking the square of Guess and checking 
whether it is close to X. In this case, our guess is not good enough.

So, we will improve our initial guess; our "improved" guess should  be, according to *Newton's method*::

   Average of two numbers: Guess and X/Guess

In this case, it will be average of 1 and 16, that is 8.5. 

This improved guess is also not good enough, so we shall improve it by again taking average of 
Guess and X/Guess where Guess is now 8.5. The value we get will be::

    (8.5 + 16/8.5) / 2 = 5.19

We repeat this process a few times::

    (5.19 + 16/5.19) / 2 = 4.13
    (4.13 + 16/4.13) / 2 = 4.00

In just two more steps, we reach close enough to the required value!

Writing a square root finding program
-------------------------------------
In describing the root finding algorithm, we used terms like "improve", "average", "good enough"
etc. The Python programming language has no idea what these terms stand for. But we can "teach"
Python the meaning of these words by defining functions whose names are *improve*, *average* and
*good_enough*. Let's give it a try.

Defining *average*
~~~~~~~~~~~~~~~~~~

Here is our function *average*::

   >>> def average(a, b):
   ...     return (a + b) / 2.0
   ...
   >>> average(1, 2)
   1.5
   >>>

Defining *improve*
~~~~~~~~~~~~~~~~~~

An *improved* guess is average of Guess and X/Guess. So, we define *improve* as::

   >>> def improve(guess, x):
   ...      return average(guess, x/guess)
   ...
   >>> improve(1.0, 16)
   8.5
   >>>

We give the names *guess* and *x* to the parameters of *improve*; we could have as well used
any other names, say, *a* and *b*. The use of the names *guess* and *x* makes the code more
readable.

Note the way we are using one function to build another (*improve* makes use of *average*).

Defining good_enough
~~~~~~~~~~~~~~~~~~~~

We can say that *p* is square root of *q* if the difference between square of *p* and *q* is less than a 
small number say 0.001. We use this idea to define a *boolean function* called *good_enough* which checks
whether its parameter *guess* is good enough to be the square root of *x*::

   >>> from math import *
   >>> def good_enough(guess, x):
   ...     d = abs(guess*guess - x)
   ...     return (d < 0.001)
   ...
   >>> good_enough(1, 16)
   False
   >>> good_enough(4.0, 16)
   True
   >>>

The *import* statement is required because we are using a function called *abs* which is defined in the
*math* library. *abs* returns the absolute value of its argument::

   >>> abs(1)
   1
   >>> abs(-1)
   1
   >>>

We need to take the absolute value of the difference between guess*guess and *x* because guess*guess
may be either greater than *x* or less than *x*; unless the absolute value is taken, this will cause problem
when comparing with 0.001 in the next line.

The statement::

   (d < 0.001)

is either True or False depending on whether *d* is less than or greater than 0.001. 

Defining the square root function
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The  square root algorithm is very simple; basically, it says::

    As long as the guess is not good enough, keep on improving the guess

Here is a function which implements this algorithm::

   >>> def square_root(guess, x):
   ...     while(not good_enough(guess, x)):
   ...         guess = improve(guess, x)
   ...     return guess
   ...
   >>> square_root(1, 16)
   4.0000006366929393
   >>> square_root(1, 25)
   5.000023178253949
   >>>


           
For finding square root of 16, we will call our function like this::

   square_root(1, 16)

This will result in the parameter *guess* getting the value 1 and parameter *x*
getting the value 16. In the condition part of the while loop, we have written::

   not good_enough(guess, x)

Python calls the function *good_enough* with parameters 1 and 16 - *good_enough* will return
False. The "not" operator, when it acts on the boolean value False, returns the value True.
So we have the boolean value True in the condition part of the while loop. As condition is true,
the body will get executed. The body is::

   guess = improve(guess, x)

The *improve* function, given the values 1 and 16, returns 8.5. This becomes the new value of *guess*.
The condition checking part of the while loop gets executed again; function *good_enough* gets called
with parameters 8.5 and 16 and it returns False. The not operator returns True and so the body of the
loop gets executed once more. This process stops only when *good_enough* returns True (in which case
the condition becomes False because not True is False). If::

   good_enough(guess, x)

is True, that means *guess* may be taken to be square root of *x*. When the loop terminates, the next
statement::

   return guess

returns the value of guess as the value of the function square_root(1, 16). 

The only problem with our *square_root* function is that we have to call it with two 
parameters, the first one being the initial value for "guess". It is more natural to
have a square root function which takes only one parameter - the number whose square root
is required. We can manage this very easily by defining an additional function::

   >>> def my_sqrt(x):
   ...     r = square_root(1, x)
   ...     return r
   ...
   >>>

Conclusion
-----------
We developed our square root function on top of other, simpler functions. Each function we wrote
performed one simple computation and was easy to read and understand. The final *square_root* 
function too was very simple (all the hard work was being done by the other functions). Finding
the square root is definitely not a big deal, and real life programs are incredibly more complex
than this toy example. But the approach we have taken scales well - most big programs are written
this way, as a collection of simple functions.










