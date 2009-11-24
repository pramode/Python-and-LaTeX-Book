Functions with side effects
===========================
Python functions are almost like mathematical functions - you give the function some input (give the
number 2 to the *sqr* function), it performs some computation and gives you an output (4, in the case
of the *sqr* function). In fact, the only reason we are using a function is because we are interested in 
getting its output. 

But this need not be the case always. In this chapter, we examine how to write functions which have
*side effects*.


Modelling a bank account
-------------------------
Most useful computer programs are closely connected with the  real world. When you go
to a bank to deposit or withdraw money, you are interacting with a computer program
which knows everything about the accounting principles followed by that bank. Here is
a toy Python program which tries to do a bit of *banking*! ::

   >>>balance = 1000
   >>>def deposit(amount):
   ...    global balance
   ...    balance = balance + amount
   ...
   >>>
   >>>def withdraw(amount):
   ...    global balance
   ...    balance = balance - amount
   ...
   >>>

We first create a variable called *balance* initialized with the value 1000 (say we have 1000 Rupees balance
initially). Then we define two simple functions *deposit* and *withdraw*. The interesting things about
these functions are:

  * Both functions do not use *return* 
  * There is a new keyword in the body of both functions - *global*

The line::

    global balance

simply tells Python that the variable *balance* being used in the next line (and all the other lines of
the function, if any) refers to the variable
*balance* declared outside the function (such variables are called *global variables* in programming
language terminology). Let's see what happens when we call this function::

   >>> balance
   1000
   >>> deposit(100)
   >>> balance
   1100
   >>> deposit(30)
   >>> balance
   1130
   >>>

Initially, the variable *balance* has value 1000. When you compare the call::

   >>> deposit(100)
   >>>

with the call::
   
   >>> sqr(2)
   4
   >>>

one thing becomes clear - *deposit* is not *returning* any value, unlike *sqr* which gives back 4. This is because
we simply have not used a *return* statement in the body of *deposit*. Still, *deposit* does something useful; it adds
100 to the global variable *balance*. This is evident when we ask Python to display the value of *balance* - indeed, it
has changed to 1100. Yet another call to *deposit* with argument 30 results in 30 being added to the balance.

Similar is the case when you withdraw some money from our toy Python bank::

   >>> balance
   1130
   >>> withdraw(20)
   1110
   >>> withdraw(10)
   1100
   >>>

The two functions above (*deposit* and *withdraw*) are said to have a *side effect* - in this case, the *side effect* is 
altering the value of a global variable. Both these functions are useful precisely because they have this *side effect*.

If you go deeper into programming, you will see many situations where you will define functions mostly to generate some
kind of side effect, rather than to evaluate some  mathematical expressions. Those topics are beyond the scope of
this book. 



