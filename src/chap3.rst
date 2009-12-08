Using Python Lists
===================

We have seen how Python works with numerical data. Now, let's look at some of
the techniques used by Python programmers to handle large collections of data.

Elementary list manipulation
----------------------------

Creating a list
~~~~~~~~~~~~~~~
A point in the cartesian plane is represented by two numbers - its X and Y co-ordinates. Using
simple Python variables, we might write::

   >>> x = 2
   >>> y = 3
   >>>

But this does not in any way make it clear that we are referring to the x and y
coordinates of a single point; we need  some way to group together these two 
numbers. Python provides a powerful *list* notation to do this::

   >>> p = [2,3]
   >>>

The idea is simple - just write a sequence of numbers (separated by comma) within
two brackets (note that we are using *square brackets* here) and you have what is called a Python *list*. 
In the above case, we can say that the variable *p* represents a point with co-ordinates 2 and 3.

The number of elements in a list is not limited - you can have as many as you like::

   >>> marks = [80, 75, 66, 55, 95]
   >>>

In this case, *marks* represents the mark of five students in an exam. 

Indexing a list
~~~~~~~~~~~~~~~

The variable *marks* represents a set of marks *as a whole*. Suppose you wish to know the mark of each
student individually. Here is how it is done::

   >>> marks
   [80, 75, 66, 55, 95]
   >>> marks[0]
   80
   >>> marks[1]
   75
   >>> marks[4]
   95
   >>>

When you write marks[0], you are asking Python to display the first mark in the sequence and when you 
write marks[4], you are asking Python to display the fifth mark in the sequence. Note that Python is
counting from zero, that is why the first mark is marks[0] and not marks[1].

You can read the statement marks[0] as either *marks zero* or *marks of zero*. The operation of looking
at individual elements of a list is called *indexing*.

What will happen if you write *marks[5]*? Let's find out::

   >>> marks[5]
   Traceback (most recent call last):
   File "<stdin>", line 1, in <module>
   IndexError: list index out of range
   >>> 

Look at the last line of the error message; it says *IndexError: list index out of range*. The elements of 
the list are numbered from 0 to 4 - you are asking Python to display an element in the sequence which is
simply not present and so you get an error!


Modifying the elements of a list
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Let's say you wish to change the mark of the first student from 80 to 65. Here is how it is done::

   >>> marks[0] = 65
   >>> marks
   [65, 75, 66, 55, 95]
   >>>

Appending elements to a list
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
How do you append a new mark to the *marks* list?::

   >>> marks.append(41)
   >>> marks
   [65, 75, 66, 55, 95, 41]
   >>> marks.append(15)
   >>> marks
   [65, 75, 66, 55, 95, 41, 15]
   >>>

Deleting an element from a list
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Say you wish to delete the third element of the *marks* list::

   >>> del marks[2]
   >>> marks
   [65, 75, 55, 95, 41]
   >>> 




