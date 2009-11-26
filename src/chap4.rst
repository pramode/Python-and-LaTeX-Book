
Introduction to Numeric Arrays
===============================

Let's try an experiment with lists::

   >>> a = [1, 2, 3, 4]
   >>> a + 1
   Traceback (most recent call last):
   File "<stdin>", line 1, in <module>
   TypeError: can only concatenate list (not "int") to list
   >>>

Our idea is to check whether it is possible to add 1 to each element of the list
by simply writing::

    a + 1

Unfortunately, Python does not let us do this (there is very good reason as to why the
language behaves in this way). But that does not mean that there is no way to do 
arithmetic on a sequence of numbers; Python offers  powerful  *Numeric Arrays* using
which we can do all kinds of tricky  number sequence manipulations. But before we 
use Numeric Arrays, we have to understand how to use *modules* in Python.

Using Modules in Python
-----------------------

Try this experiment::

   >>> sin(0)
   Traceback (most recent call last):
   File "<stdin>", line 1, in <module>
   NameError: name 'sin' is not defined
   >>>

We are unable to calculate sin of 0 - Python tells us that *name `sin' is not defined*!
The reason is simple; functions like *sin*, *cos* etc are not part of the *core* Python
language. They are defined in additional *modules* (also called *libraries*). We have to
use a special notation to tell Python that we wish to use the functions defined in a module::

   >>> from math import *
   >>> sin(0)
   0.0
   >>> cos(0)
   1.0
   >>>

.. note::
   Functions like sin, cos etc need angles to be specified in radian.

The first line::

   from math import *

simply means::

   Use all the functions available in a module called `math'.

The *star* symbol should not be interpreted as a multiplication operator in this context - it simply means *ALL*.

In general, if you wish to use all the functions defined in a module called *xyz*, just type::

   from xyz import *

Another way to use modules
~~~~~~~~~~~~~~~~~~~~~~~~~~
One of the things which makes programming languages tricky to learn is that there will be many
different ways to express the same idea. Here is another way to use a module::

   >>> import math
   >>> sin(0)
   Traceback (most recent call last):
   File "<stdin>", line 1, in <module>
   NameError: name 'sin' is not defined
   >>> math.sin(0)
   0.0
   >>> math.cos(0)
   1.0
   >>>

The statement::

   import math

is similar to the one which we saw in the previous section - the difference is that now we have to write *math.sin* and
*math.cos* instead of simply *sin* and *cos*.

What do you do if you wish to get a list of all the functions present in a module?::

   >>> import math
   >>> dir(math)
   ['__doc__', '__file__', '__name__', '__package__', 
   'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 
   'atanh', 'ceil', 'copysign', 'cos', 'cosh', 'degrees', 
   'e', 'exp', 'fabs', 'factorial', 'floor', 'fmod', 
   'frexp', 'fsum', 'hypot', 'isinf', 'isnan', 'ldexp', 
   'log', 'log10', 'log1p', 'modf', 'pi', 'pow', 'radians', 
   'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'trunc']

The function *dir* can be used to display list of all functions defined in a module. You can ignore the names
starting with two  *underscore* signs in the above list.

The working of many of these functions should be evident from their names. If you wish, you can get
information about what the function actually does by using *help*::

   >>> help(math)
   hypot(...)
    hypot(x,y)
    
    Return the Euclidean distance, sqrt(x*x + y*y).
   >>>

Creating Numeric Arrays
------------------------
A Python *Numeric Array* looks like a list - with the difference that it is more suited for
mathematical computations. Here is how you can create a Numeric array::

   >>> from pylab import *
   >>> a = [10, 20, 30, 40]
   >>> b = array(a)
   >>> b
   array([10, 20, 30, 40])
   >>> b + 1
   array([11, 21, 31, 41])
   >>> b * 2
   array([20, 40, 60, 80])
   >>>

The first statement::

   from pylab import *

simply makes available all the functions in a module called *pylab*. If you get an error while executing this statement, it
means the module is not installed on your system. Read the Appendix of this book to learn how you can install additional software
on your GNU/Lnux system.

We are making use of only one function from the *pylab* module in the above example; a function called *array*. What does *array*
do? It acts on an ordinary Python list *a* and produces a *Numeric sequence* called (in this example) *b*.  You can now 
add 1 to all the elements of the sequence by just writing::

   b + 1

Similiarly, you can multiply all the elements of *b* with 2 by doing::

   b * 2

Now, just relax for a moment and think of the power that you have in your hands! A numeric array (like *b* above) can
contain hundreds of thousands of numbers. With a simple statement like "b+1", you can operate on all the
elements of the sequence!  Working with a million numbers at once has become as easy as working with one or two numbers.

You will see how to use this power to do some interesting math in the next chapter!



