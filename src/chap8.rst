Understanding the while loop
=============================

A set of Python statements can be executed repeatedly using a *while* loop. This chapter
examines the syntax of the while loop using some simple examples.

A simple while loop
--------------------

Type the following code at the Python prompt::

   >>> while (1 < 2):
   ...     print 'hello'
   ...     print 'world'
   ...


The Python *print* statement can be used for displaying a message on the screen; the
message should be in single (or double) quotations. Both the print statements should
be indented properly. You should type an empty line after the last print statement. 
You will see that Python keeps on printing the two messages *hello* and *world* repeatedly!

The general format of a *while* loop is::

   while (condition):
      body

The *body* can be either a single statement or multiple statements, all properly
indented (just like the body of a function or an if-else statement). Python first checks
the condition and if it is found to be true, the body gets executed. Once again, Python checks
the condition and if it is found to be true, the body is executed again. This process 
repeats until the condition becomes false. If the condition never becomes false, Python
will keep on repeating this process infinitely. In the above example, the condition is::

   1 < 2

and the body is composed of two statements::

   print 'hello'
   print 'world'

Python first checks the condition - 1 is definitely less than 2, so the condition is
true and the body (the two print statements) gets executed. Python once again checks
the condition - again, 1 is less than 2, condition is true and so the body gets 
executed. 1 is never going to be bigger than 2, so the condition will never become
false and as a result, Python will never stop executing the loop! If you wish, you
can type *Ctrl-c* (hold down the *Ctrl* key and press **c**) to forcibly terminate the
loop.

A loop which terminates
-----------------------
Here is a *while* loop which does something a bit more interesting than printing *hello*
and *world*::

   >>> i = 0
   >>> while (i < 5):
   ...      print i
   ...      i = i + 1
   ...
   
The condition is initially true - i has the value 0 and zero is less than 5. So the body gets executed. The
*print* statement displays the value of *i* on the screen. The next statement is::

   i = i + 1

You should read this as: *i assigned to i plus 1*. The logic is::

   New value of i is old value of i plus one.

So, the value of *i* becomes 1. Python once again checks the condition - it's  true (because 1 is less than
5). So the body gets executed again. The value of *i* is printed(this time, the value is 1). The next
statement(i = i + 1) changes the value of *i* to 2. The condition gets checked once more. Again, it is true (2 is less
than 5). So the body gets executed once more. The print statement displays 2 on the screen (value of *i* is now 2) and the
value of *i* gets changed to 3 in the next statement. This process repeats until the value of *i* becomes 5. At this
point, the condition becomes false and the loop terminates. Here is what you will see on the screen::

   0
   1
   2
   3
   4

Finding HCF using Euclid's method
----------------------------------

The term *algorithm* is commonly used in computer programming. It refers to a precise
set of rules for solving a problem. A very famous numerical algorithm exists to find
out the highest common factor (also called the greatest common divisor) of two numbers.
The algorithm was invented by Euclid; it's therefore called the *Euclid's algorithm*. 

Here is how the algorithm works. Say you wish to find out the HCF of two numbers A and B.
Simply repeat the following steps until both numbers become equal:

   * If A is greater than B, change A to A-B and do not modify B
   * If B is greater than A, change B to B-A and do not modify A

The value of A (and B) when both become equal will be the Highest Common Factor!

Let's try this out with two numbers, A=18 and B=42. 

B is greater than A, so B becomes 24 and A remains as 18. So, we have::

   A = 18, B = 24

If we repeat this process, we get::

   A = 18, B = 6
   A = 12, B = 6
   A = 6,  B = 6

Finally, both A and B become equal (both have value 6). The HCF of 18 and 42 is 6.

You can try out this procedure on different pairs of numbers and verify that it works
perfectly!

Even better, you can write a loop in Python to discover the HCF::

   >>> a = 18
   >>> b = 42
   >>> while (a <> b):
   ...    if (a > b):
   ...       a = a - b
   ...    else:
   ...       b = b - a
   ...
   >>> a
   6
   >>> b
   6
   >>>

Initially, *a* and *b* are not equal, so the condition "a <> b" (remember, '<>' is the *not equal to* operator)
is true. As *b* is greater then *a*, the *else* part of the *if-else* statement gets executed and value of *b*
changes to 24 while *a* remains unchanged. In the next iteration of the loop, *b* becomes 6 and *a* remains as 18.
This process repeats until both *a* and *b* become equal. At that point, the loop terminates. Now, if you examine
the value of *a* and *b*, you will see that both are 6.

A small problem with this approach is that any time you wish to calculate the HCF of two numbers, you have
type the whole loop all over again. This is difficult. 


Defining a function to compute HCF of two numbers
-------------------------------------------------

Look at the following Python program::

    >>> def hcf(a, b):
    ...     while (a <> b):
    ...        if (a > b):
    ...            a = a - b
    ...        else:
    ...            b = b - a
    ...     return a
    ...
    >>> hcf(18, 42)
    6
    >>> hcf(15,20)
    5
    >>>

The only change is that we are now writing the loop within a function called *hcf* (the name of the
function doesn't really matter. You can call it by any name you like). Now whenever you wish to find out
hcf of two numbers, you just have to call the function *hcf* with those two numbers as parameters. Say you
call::

   hcf(15,20)

Within the function, *a* will assume the value 15 and *b* will assume the value 20. The while loop will 
terminate when *a* and *b* both become equal to 5. Once the while loop is over, the *return* statement
will transmit the value 5 as value of the function *hcf(15,20)*.


