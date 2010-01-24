Appendix 1 - Writing Stand-alone Python programs
=================================================
Till now, we were using the interactive Python prompt to write
short programs. The disadvantage with this method is obvious - all
the code that you write is lost when you exit from Python. In this
chapter, we shall see how to store Python programs permanently in 
text files.

Using an editor in GNU/Linux
-----------------------------
An *editor* is a program which helps to create text files which
can be saved permanently in the computer's hard disk. The GNU/Linux
operating system comes with many editors; two of the most frequently
used are *vi* and *emacs*. Both of them are a bit difficult to use
for absolute beginners. A better choice might be a program called *gedit*.
You can run *gedit* by simply typing **gedit** at the operating system
command line (refer chapter 1 for a discussion about the command line).

*gedit* is easy to use. You can type whatever you want; once you are
finished with typing, it's time to save the data you have typed. For this,
choose the *Save* option from the *File* menu; *gedit* will now display
a new window where you will be asked to give a name to the file in which
you wish to save the typed data. Choose the *Quit* option from the *File*
menu to exit from *gedit*.


Writing a Python program using *gedit*
---------------------------------------
Run *gedit* and save the following line into a file called *hello.py*::

   print "Hello"

Quit *gedit* and type the following at the Operating System commandline::

   python hello.py

You will see the message "Hello" getting printed on the screen. 

Create another file using *gedit* and store the following code in it 
(you may name the file abc.py - the .py at the end tells us  that
we are dealing with a file containing Python code)::

   def sqr(x):
      return x*x
   m = sqr(3)
   print m

You can run the code by typing::

   python abc.py

at the operating system commandline.

.. note:: You should be more careful when writing Python code in this
   way. When you are typing code at the Python prompt, you get immediate
   feedback in case of syntax errors. That's not the case when you store
   and execute Python code from a file.

Performing keyboard input
--------------------------
Using *gedit*, store this program in a file called *test.py*::

   a = input()
   b = input()
   print a * b

Run the code by typing, at the operating system commandline::

   python test.py

The *input* function is waiting for you to enter some data from the keyboard; type the
number 10 and hit the *Enter* key. The number will be read and stored in the variable
*a*. Now type one more number (say 20) and hit *Enter*; it will be stored in *b*. The
program will print 200 as the output.


