Strings, Tuples and Associative Arrays
======================================


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
~~~~~~~~~~~~~~~~~~~~~~~~~~~

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

What is a tuple?
----------------
A Python *tuple* looks similar to a list, but has some fundamental differences::

   >>> a = (1, 2, 3)
   >>> a
   (1, 2, 3)
   >>> a[0]
   1
   >>> a[0] = 10
   Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
   TypeError: 'tuple' object does not support item assignment
   >>> a.append(4)
   Traceback (most recent call last):
     File "<stdin>", line 1, in <module>
   AttributeError: 'tuple' object has no attribute 'append'
   >>>

A tuple is a set of values enclosed in "(" and ")". The major difference between a tuple and a list
is that it is not possible to modify the tuple. This means it's impossible to do things like adding
more elements to the tuple or modifying existing values.

What is an Associative Array?
-----------------------------
Suppose you wish to represent a telephone directory in a Python program::

   >>> d = {'Rahul':2150438, 'Roy':5128431, 'Vimal':7124196}
   >>> d['Vimal']
   7124196
   >>> s = 'Roy'
   >>> d[s]
   5128431
   >>>

A Python *associative array* (also called a *dictionary*) is created by enclosing
key/value pairs in "{" and "}". In every key/value pair, the key and value should
be separated by a colon. In the above case,::

   'Rahul':2150438

is one key/value pair with key being the string 'Rahul' and value being the number
2150438. Given a key, it is easy to extract a value; you just have to index the
associative array with that key.

Processing lists/tuples with *for* loops
-----------------------------------------

Examining each element of a list/tuple in sequence and performing some action based
on the value of that element is a common programming problem. For example, let's say
you are given a list::

   [10, 11, 14, 13, 17, 24, 78]

and asked to write some code to select the odd numbers (11, 13 and 17, in this case).:::

   >>> a = [10, 11, 14, 13, 17, 24, 78]
   >>> n = len(a)
   >>> i = 0
   >>> while (i < n):
   ...    if((a[i] % 2) == 1):
   ...         print a[i]
   ...    i = i + 1
   ...
   >>>
Here is a shorter (and clearer) version of the code using what is called a *for* loop::

   >>> a = [10, 11, 14, 13, 17, 24, 78]
   >>> for k in a:
   ...      if ((k % 2) == 1):
   ...          print k
   ...
   >>>

The general form of a *for* loop is::
 
   for variable_name in sequence:
       body

In the above case, the *variable_name* is *k* and the *sequence* is the list *a*; the body of the *for* loop
is an *if* statement. This is the way the *for* loop works: the statements in the body get executed as many
times as there are elements in the given sequence. In our example, the body gets executed seven times. Each
time the loop executes, varaible *k* will be assigned value of the next element in the sequence; so *k* will
be initially 10, then it becomes 11 (in the next iteration) and so on till 78.

The *for* loop is not a complete replacement for the *while* loop; it is useful only in those
situations where you have to process the individual elements of a sequence like a list or a tuple.
In all other cases, a *while* loop is the natural choice.

