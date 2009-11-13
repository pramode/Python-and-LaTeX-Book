Using Python Lists
==================

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
two brackets and you have what is called a Python *list*. In the above case, we can
say that the variable *p* represents a point with co-ordinates 2 and 3.

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




