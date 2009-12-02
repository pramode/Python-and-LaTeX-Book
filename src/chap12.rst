Exception Handling 
===================
An error detected during the execution of a program is called an 
*exception*. This chapter briefly explains Python exception handling
techniques.

.. note::
   Exception handling is a complicated subject; a detailed exposition is
   beyond the scope of this book.

Syntax Errors
-------------

As a beginner, you will make lots of syntax errors while writing Python
code::

   >>> def sqr(x)
     File "<stdin>", line 1
       def sqr(x)
             ^
   SyntaxError: invalid syntax 
   >>>

In the above case, the problem is with a missing colon after the first line of the
function definition. Such errors are usually not very difficult to identify and correct.

Exceptions
-----------

It is more difficult to troubleshoot errors which occur during program execution. Let's
look at a simple example.

The slope of a line segment with co-ordinates (x1, y1) and (x2, y2) is given by the
equation:

.. math::
   m = \frac{y_{2} - y_{1}}{ x_{2} - x_{1}}

Here is a Python function for computing the slope::

   >>> def slope(x1, y1, x2, y2):
   ...    m = (y2 - y1) / (x2 - x1)
   ...    print 'slope computed'
   ...    return m
   ...
   >>> slope(1.0, 1.0, 4.0, 4.0)
   slope computed
   1.0
   >>>

What happens if you try to find the slope of a vertical line with co-ordinates (1.0, 1.0) and (1.0, 4.0)?::

   >>> slope(1.0, 1.0, 1.0, 4.0)
   Traceback (most recent call last):
     File "<stdin>", line 1, in <module>
     File "<stdin>", line 2, in slope
   ZeroDivisionError: float division
   >>>

We are getting an error; the last line of the  message conveys the exact nature of this
error - it is a zero division error. You will get the same error if you try doing::

    1.0/0

at the Python prompt. 

The moment Python discovers that the division is going to result in an error, it
stops any further execution of the code and immediately prints an error message. The
problem with this behaviour is that the programmer might wish to have some control
over *how* his code should respond to the error. Here is a modified slope function::

   >>> def slope(x1, y1, x2, y2):
   ...     try:
   ...         m = (y2 - y1) / (x2 - x1)
   ...         print 'computed slope'
   ...     except ZeroDivisionError:
   ...         print 'unable to compute slope'
   ...         m = 'undefined'
   ...     return m
   ...
   >>> slope(1.0, 1.0, 4.0, 4.0)
   computed slope
   1.0
   >>> slope(1.0, 1.0, 1.0, 4.0)
   unable to compute slope
   undefined
   >>>

You can see two new keywords here: *try* and *except*. Python first attempts to execute statements between the
*try* and the *except* (note that these statements are indented). If there is no zero division error, the *except block* 
(the indented set of statements after the line "except ZeroDivisionError:") is skipped and the remaining part of the
function (which is only a single *return* statement) gets executed. If there is an error, the remaining statements
in the *try block* (statements between *try* and *except* constitute the *try block*) are skipped 
and control gets transferred to statements in
the *except block*. Once all the statements in the *except block* are executed, the remaining part of the function
gets executed. 

An informal description of this behaviour might be::

    Try the following statements. Stop if there is an error  and skip to the 
    matching *except block*. If there is no error, complete the statements 
    (between *try* and *except*) and skip the *except block*.

What have we achieved here? We now have a choice to decide *what* should be done in
case of an error. This is a basic requirement when writing real life code.


Exercises
-----------

   1) Create a Python list and index it beyond its limit. Do you get an exception?
      What is its name?





