Getting started with Python
===========================

The Python programming language was created by a Dutch Computer Scientist called *Guido von Rossum*. Unlike languages like
C/C++/Java, Python is extremely friendly to beginners - famous Universities like MIT (Massachusettes Institute of
Technology) use it to teach introductory programming courses. It is also a modern, powerful general purpose programming 
language used by companies and research instituitions all over the world to solve complex computing problems.

First steps - use Python as a calculator!
-----------------------------------------
In the previous chapter, you had seen how to interact with the GNU/Linux Operating System by
typing commands. You can run Python by simply typing the command **python**. Here is how your 
screen would look like::

   [ram@knuth ~]$ python
   Python 2.6 (r26:66714, Mar 17 2009, 11:44:21) 
   [GCC 4.4.0 20090313 (Red Hat 4.4.0-0.26)] on linux2
   Type "help", "copyright", "credits" or "license" for more information.
   >>> 

Don't worry if the details shown above do not match exactly with what you see on your computer. It is
enough that the last line of the output matches what you see above exactly. The three *greater than* signs
constitute what is called the *python prompt*. When Python displays the prompt, you know that it is ready
to accept commands! Type 1 + 2, hit the *Enter* key and  see what happens::

   >>> 1 + 2
   3
   >>>

.. note::
   In examples like the one above, you should not type the three *greater than* signs - it is automatically
   displayed by Python.

After you hit *Enter*, Python displays the result 3 on the next line and displays the *prompt* once again.
This is Python's way of telling you that it is ready to accept more commands! Now you know that using Python is
as easy as using a calculator. 

Try a few more experiments::

   >>> 3 * 2
   6
   >>> 3 - 2
   1
   >>> 3 / 2
   1
   >>> 3.0 / 2
   1.5
   >>> 2 ** 3
   8
   >>>

The *star* symbol performs multiplication and the *double star* performs exponentiation. The only confusing
result is the output from the division operation 3/2. This is explained in detail in the next section.


A few things about the way Python treats numbers
------------------------------------------------

A number written like this::

   456

is treated as an *integer* by Python. A number written like this::

   456.01

is called a *floating point* number(or simply, a *float*). When division is performed, if both numerator and denominator are integers, the result
will be truncated to an integer. So, when you divide 3 by 2, you get 1 and not 1.5. If you wish to get the correct
answer, you have to make one (or both) of the numbers float.


.. note::
   This behaviour (of division) is confusing and it has been corrected in a more recent version of Python.
  

You will encounter some other problems when dealing with floating point numbers; problems mostly concerning accuracy
of the result. Here is a simple experiment you can try at the Python prompt::

   >>> 1.5 + 1
   2.6000000000000001
   >>>

You may be surprised at not getting exactly 2.6 as the result. The reason for this behaviour is somewhat complex and
it's explanation is beyond the scope of this book. At this point, it is sufficient to understand that floating point
arithmetic is tricky (in all programming languages, not just Python).

Arithmetic using very large integers
------------------------------------

Try the following experiment::

   >>> 2 ** 320
   21359870359209100823950217061695521146027045223566
   52769947041607822219725780640550022962086936576L
   >>>

Python can handle very large integer values. Note that the number shown above has an **L** at the end -
this is Python's way of saying that you are dealing with a *long* integer! 

Using variables
----------------
 
Just like  math, Python too has variables. The following example shows a simple use of variables::

   >>> x = 1
   >>> y = 2
   >>> x + y
   3
   >>>

Here, x and y are variables having values 1 and 2. A variable should always have a value assigned to it before
it is used. In the above example, Python will generate an error if you try to do x + y + z::

   >>> x + y + z
   Traceback (most recent call last):
     File "<stdin>", line 1, in <module>
   NameError: name 'z' is not defined
   >>>

Look at the last line - it says *Namerror: name 'z' is not defined* - the problem is, you have not given a value
to variable z (you need not bother with the other two lines in the error message - they can be safely ignored).

Mathematicians usually use single letter variable names like x, y, z, a, b etc. But Python has no problems with
longer names::

   >>> mark = 90
   >>> age = 19

Here, *mark* and *age* are two variables just like *x* and *y* in the previous example. There are restrictions on
the kind of words you can use as variables. For example, it's OK to use the name *twenty20* as a variable name, but
you can't use the name *20twenty*. The rule is that variable names have to start with an uppercase or lowercase 
alphabet (an  *underscore* symbol is also permitted, but digits like 0, 1, 2 etc are not).

Variable names are case-sensitive  - for example, the names *Abc* and *abc* represent two different variables.

Once you assign a value to a variable, it remains unchanged as long as you do not assign a new value::

   >>> x + y
   3
   >>> x = 10
   >>> y = 20
   >>> x + y
   30
   >>>

Initially, x and y have values 1 and 2 which are then changed to 10 and 20.

Mistakes made by beginners while using variables
---------------------------------------------------------

  * Not realizing that variable names are case-sensitive.
  * If variable x has value 1, writing x + 1 does not change the value of x to 2::
      
      >>> x = 1
      >>> x + 1
      2
      >>> x
      1
      >>>

  * If variable x has value 1, then writing x.1 does not give you 1.1. Variable names
    simply do not work that way!

The last mistake is not common, but I have seen students making it in the class!

Exiting Python
-------------------
If you wish to stop using Python, simply type 'Ctrl-d' (hold down the key labelled *Ctrl* on the
keyboard and then type the letter *d*). All the variable assignments which you have
made are lost if you exit Python.

.. note::
   It is assumed that you are running Python on a GNU/Linux system. On a Windows system, you have
   to type 'Ctrl-z' and then hit Enter.





