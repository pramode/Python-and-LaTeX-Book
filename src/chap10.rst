Handling non-numerical data
============================

Programming languages do many things other than performing mathematical
computations. In this chapter, we examine how Python performs string
handling.

What is a string?
-----------------
Let's say you are writing a program to handle information regarding students
in your school/college. You can represent a student in a Python program as a 
simple list containing attributes like the student's name, age, marks etc::

   >>> a = [Rahul, 18, 90]
   Traceback (most recent call last):
   File "<stdin>", line 1, in <module>
   NameError: name 'Rahul' is not defined
   >>>

Python shows you an error! The reason is Python treats the name *Rahul* as a variable name; 
we have not defined a variable called Rahul and so the error.

What we want to do is tell Python to treat *Rahul* not as a variable but as a simple sequence
of alphabets - this can be done by putting the name within single (or double) quotations. Such
sequences are called *strings* in programming language terminology::

   >>> a = ["Rahul", 18, 90]
   >>>

Elementary string handling
--------------------------

Try the following sequence of operations at the Python prompt::

   >>> a = "hello"
   >>> b = "world"
   >>> a + b
   'helloworld'
   >>> a[0]
   'h'
   >>> a[4]
   'e'
   >>> a * 3
   'hellohellohello'
   >>> len(a)
   5
   >>> a == b
   False
   >>>

In the first two lines, we are creating two variables, *a* and *b* referring to two strings *hello* and *world*. The addition 
operator can be applied on strings - it performs string concatenation (joins the strings together). 
Just like lists, strings too can be indexed; *a[0]* refers
to the first element in the sequence. The multiplication operator performs repeated concatenation. It's possible to compare
one string with another using the *==* operator; in the above case, the comparison gives us the result *False*.



