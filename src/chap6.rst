
Defining Functions
====================

So far, we have been making use of functions (like *sin*, *linspace*) etc
provided by Python. In this chapter, we shall see how to create our own
functions.

Function basics
----------------
Try the following experiment at the Python prompt::

   >>> from math import *
   >>> sqrt(16)
   4.0
   >>> sqr(4)
   Traceback (most recent call last):
   File "<stdin>", line 1, in <module>
   NameError: name 'sqr' is not defined
   >>>
  
.. note::
   from math import *  is required because function *sqrt* is defined in the math library.
  
Python tells us that the name *sqr* is not defined; there is a function defined in the
math library for computing the square root, but there is no function for squaring a number!
Not just Python, but any programming language will provide you with only a limited set
of functions; if you wish, you can create your own functions!

You can define a *sqr* function of your own::

   >>> def sqr(x):
   ...     return x * x
   ...
   >>> 

A simple function works like this - you give it one or more numbers, it performs some calculations
using these numbers and gives back the result. In the above case, you are asking Python to::


   Define a function which takes in one number x and gives back x*x.

It is as simple as that; but you will have to follow a few syntax rules strictly
if you want your function definitions to work properly.

The first line of a new function definition starts out like this::

   def functionname ( variablename ) :

Here, *def* is a language keyword, which simply means *define a new function*. This should be followed
by the name of the function you are creating (in this case, *sqr*. There is nothing special
about function names, they are just like variable names - instead of *sqr*, you could have as
well used a name like *xyz* and Python will not bother about it), followed by a bracket, followed by
one (or more) variable names, followed by a closing bracket, followed by a *colon* symbol.

The remaining lines that you type forms the *body* of the function (the *body* is where the
function performs all of its computations) - in the above case the body is composed
of only one line::

   return x * x

The first thing that you note is that instead of the usual three greater-than signs, you are seeing::

   ...

This is Python's way of telling you that what you are typing right now is part of the *body* of the
function. You also note that the line "return x * x" is *indented* (that is, there are a few spaces
between the ... and "return x * x") - this is again part of Python's syntax - the lines in the body
of a function have to be uniformly indented (you can do it by typing a few spaces, or more conveniently,
by simply typing a *tab*. Never mix spaces and tabs - that is a syntax error in Python).

Now, what does the *return* statement do? For the moment, just think of it as another tiny bit of 
syntax!

How does Python know that you have finished typing the body of the function? When we type an empty line!
At this point, Python prints the original "three greater-than sign" prompt.


Once you have defined *sqr*, you can use it just like all the the other functions::

   >>> sqr(4)
   16
   >>> sqr(3)
   9
   >>> m = sqr(5)
   >>> m
   25
   >>> 

A few technical terms
~~~~~~~~~~~~~~~~~~~~~
In programming language terminology, a statement like this::

   sqr(3)

is called a::

   function call or function invocation

When you write::

   >>> def sqr(x):
   
the *x* within the brackets is called a function *parameter* or *argument*. The *argument* is always a variable. A function can
have more than one parameter. Here is a simple example::

   >>> def add(x, y, z):
   ...     return x + y + z
   ...
   >>>

You can call the above function in many ways::

   >>> add(1, 2, 3)
   6
   >>> p = 1
   >>> q = 2
   >>> r = 3
   >>> add(p, q, r)
   6
   >>>

In the first case, when you call::
 
    add(1, 2, 3)

the parameter *x* in *add* will assume the value 1; the parameters *y* and *z* will assume values 2 and 3.

In the second case, when you call::

   add(p, q, r)

the parameter *x* will assume value of variable *p*; parameters *y* and *z* will assume values of variables
*q* and *r*. 


What will happen if you try something like this::

   >>> add(1, 2)

Python will give you an error - this makes sense because in this case, you are not supplying a value for parameter
*z*.

Similar is the case if you try calling like this::

   >>> add(1, 2, 3, 4)

Now, you are trying to call the functions with more values than are required. This also is a serious error.


Functions with multiple statements in the body
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Length of a line segment connecting the points (a, b) and (c, d) is:

.. math::
   l = \sqrt{(c - a) ^ {2} + (d - b) ^ {2})}
   

Let's define a Python function *line_length* to compute this length::

   >>> from math import * 
   >>> def line_length(a, b, c, d):
   ...      return sqrt((c -a) * (c - a) + (d - b) * (d - b))
   ...
   >>>
   

.. note::
   You should give meaningful names to your functions. In the above case, the function is
   called line_length - in case your function name has multiple words in it, it's a good idea
   to separate the words using an *underscore* symbol, _. Python does not care even if you 
   call your function *linelength* - the underscore simply improves readability of your code.
   
 
Instead of writing a complicated expression in a single line, let's do it in
a different way::

   >>> def line_length(a, b, c, d):
   ...     m = (c - a) * (c - a)
   ...     n = (d - b) * (d - b)
   ...     return sqrt(m + n)
   ...
   >>>

.. note::
   Remember, you have to type an empty line after the last line in the body of the function
   to tell Python that you have finished typing the body.

Both the functions perform the same action - but in the second case, we are simplifying things a bit
by using two extra variables *m* and *n* and two additional lines in the body. The important
thing to be kept in mind here is that all the three lines in the body have to be at the same
level of indentation - that is, if the first line in the body is separated from the "..." by
say four spaces, then the two other lines too need to have exactly the same separation. An easy
way to achieve uniform spacing is to use the *tab* key instead of the *space bar* on your keyboard.

.. note::
   You should not mix tabs and spaces - either use tabs uniformly or use space uniformly.

Here is one more way to write the above function::
    
   >>> def line_length(a, b, c, d):
   ...      m = sqr(c - a)
   ...      n = sqr(d - b)
   ...      return sqrt(m + n)
   ...
   >>>

We can get rid of the two extra variables and write::
   
   >>> def line_length(a, b, c, d):
   ...      return sqrt(sqr(c-a) + sqr(d - b))
   ...
   >>>

You have to define the *sqr* function properly if both the above examples are to work. The idea
being conveyed here is that you can build more complex functions using simpler functions - we used
both *sqrt* and *sqr* to write *line_length* (maybe, you can imagine an even more complex function which 
uses *line_length* in its body)! 

What does 'return' do?
----------------------
It's time for us to examine the significance of *return*. Let's try to rewrite *sqr*::

   >>> def sqr(x)
   ...    x * x
   ...
   >>>

Now, let's  call it::
    
    >>> sqr(4)
    >>> m = sqr(3)
    >>> m
    >>>

You note that nothing is getting printed. Even though Python performs the computation 'x*x', the result
of the computation is made available to you only if there is a *return* statement. The function is next to
useless without the *return*.

There is another aspect of *return* which the following function illustrates::

   >>> def silly(a):
   ...     m = a + 1
   ...     return m
   ...     n = a - 1
   ...     return n
   ...
   >>> silly(10)
   11
   >>> silly(23)
   24
   >>>
   
We have used two return statements in the body of the function. The result of calling silly(10) is 11 and silly(23) is 
24; this means that the two lines written after the  *return m* have no effect at all. So, the big idea here is::

    Your function effectively stops executing after the first return.


Boolean Functions
------------------

Try the following experiments at the Python prompt::

   >>> 1 > 2
   False
   >>> 1 < 2
   True
   >>> 1 == 1
   True
   >>> 1 <> 2
   True
   >>> (8 % 2) == 0
   True
   >>> not True
   False
   >>> not False
   True
   >>>

The symbols *True* and *False* (in computing terminology, you call them *boolean* values) are used by Python to identify 
whether the result of a comparison operation is true or false.

The operator used to check whether two values are equal is '=='. Note that this is totally different from the '=' operator
(the *assignment* operator) which is used to give value to a variable. The '<>' operator returns True if the numbers
being compared are not equal. 


In the expression::

   (8 % 2) == 0

% is the remainder operator; remainder when 8 is divided by 2 is zero. So, the above expression becomes::

   0 == 0

which is True.

What does the following function do?::

   >>> def is_even(n):
   ...      return (n % 2) == 0
   ...
   >>> is_even(4)
   True
   >>> is_even(5)
   False
   >>>

is_even divides its parameter *n* by 2 and finds out the remainder which is either zero or one; zero if number
is even and one if number is odd. If, for example, n has the value 4, the expression::

   (n % 2) == 0

becomes::
   
   0 == 0

which is true! Effectively, *is_even* checks whether its parameter *n* is even. A function like *is_even* which returns True or
False is called a *boolean* function.



Using if-else statements 
------------------------- 

Look at the following function definition::

   >>> def maximum(a, b):
   ...     if (a > b):
   ...         return a
   ...     else:
   ...         return b
   ...
   >>> maximum(1, 2)
   2
   >>> maximum(20, 10)
   20
   >>>

You can see two new Python keywords here - *if* and *else*; together, they form an *if-else* statement. An *if-else* statement
is merely Python's way of saying::

    if this condition is true, do this action; otherwise, do some other action.

The general format of an *if-else* statement is::

    if (condition):
        body
    else:
        body

The *body* can be either a single statement or it can be multiple statements written one below the other. Special care should
be taken to make sure that the statement(s) in the body are uniformly *indented* (using equal number of spaces or a single tab).
In the case of our *maximum* function, because the *if-else* itself comes as the body of a function, we have two levels of
indentation. Here is how you should type the code::

     Type the first line - def maximum(a, b): and hit Enter
     Type a tab and then type - if (a > b): and hit Enter
     Type two tabs and then type - return a  and hit Enter. 
     Type a single tab and then type - else: and hit Enter
     Type two tabs and then type - return b and hit Enter
     Type one more Enter to insert a blank line

You need to type two tabs before typing "return a" and "return b" - this is because Python uses indentation levels
to decide whether a statement comes as the body of an *if* (or *else*) or a function definition. Only if the 
line "return a" is indented deeper than the line "if (a>b):" will Python assume that the "return a" is part of the
body of the *if* statement.  Getting the indentation levels wrong is a common mistake made by beginners!


Exercises
---------

   1) Define a function is_odd which checks whether a number is odd or not.
   2) Define a function maximum which returns the maximum of three numbers (Hint: you
      might first define a function which will find out maximum of two numbers and
      use that to write a function which will return maximum of three numbers).


  
