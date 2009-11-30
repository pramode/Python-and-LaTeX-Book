Programming with classes and objects
====================================

Besides writing correct code, a programmer has to make sure that he
writes clear, readable code; code which others can read, understand and
modify easily. One way to do this is by structuring the program as
a collection of small functions. In this chapter, we examine another
powerful technique for achieving the same goal.

.. note::
   We are going to examine ideas which are a bit more complicated than what
   we have seen so far ... don't worry if you do not understand everything
   clearly.


Representing a student
----------------------

As discussed in the previous chapter, you can represent a student in a Python
program by a list::

   >>> p = ["Tom", 15, 78]
   >>> q = ["Jerry", 14, 81]
   >>> p[0]
   'Tom'
   >>> q[0]
   'Jerry'
   >>> p[1]
   15
   >>> q[1]
   14
   >>> p[2]
   78
   >>> q[2]
   81
   >>>

We have two students, *Tom* and *Jerry* aged 15 and 14 respectively. They have
scored marks 78 and 81 in the maths exam.

Let's write a Python function to find out the name of the student with higher
mark::

   >>> def better_student(a, b):
   ...      if(a[2] > b[2]):
   ...         return a[0]
   ...      else:
   ...         return b[0]
   ...
   >>> better_student(p, q)
   'Jerry'
   >>>

The *better_student* function works perfectly; it compares the marks of the two students
and returns name of the student with greater mark.

Imagine a situation where *better_student* is just one function in a big program composed of
hundreds of functions. How does another programmer reading your code know that *a[2]* and
*b[2]* represents the marks of the students without having to check out the definitions of
*p* and *q* which might be at a location far removed from where you are defining *better_student*?
Even when he  sees the actual definition of *p* and *q*, how does he know that *p[2]* and 
*q[2]* are the marks (rather than *p[1]* and *q[1]*)? Surely, we need a better 
way to represent our student!


Using  classes and objects
----------------------------

Look at the following Python program::

   >>> class student: 
   ...    pass
   ...
   >>> a = student()
   >>> a.age = 15
   >>> a.mark = 78
   >>> a.name = "Tom"
   >>> b = student()
   >>> b.age = 14
   >>> b.mark = 81
   >>> b.name = "Jerry"
   >>> a.age
   15
   >>> b.mark
   81
   >>>

The first two lines constitute a *class declaration*. What does it do?

Any data item in a Python program belongs to one of several categories. For example, the
number 12 belongs to the category *integer*, the sequence "hello" belongs to the category
*string*, the number 1.23  belongs to the category *float*. The class declaration simply
tells Python::

   We have a new category - let's call it student.

The statement::

    a = student()
   
tells Python to create a new student; in programming language terminology, we will call *a* an
*object*. 

The remaining lines::

   a.age = 15
   a.mark = 78
   a.name = "Tom"

simply instruct Python to::

   set the age, mark and name of the new student to 
   15, 78 and "Tom". 

*age*, *mark* and *name* are referred to as  *attributes* of the object.

We should examine the class declaration a bit more in detail. The first line of a class
declaration is the keyword *class* followed by a name::

   class name_of_class:

The body of a class declaration has to be indented (similar to functions, while loops and
if statements). The simplest class is one which has an empty body; in such cases, we should
write::

   pass

in the place of the body. An empty line should be typed as the last line of the class declaration
(similar to functions, while loops etc).


Rewriting *better_student*
---------------------------

Let's now rewrite *better_student* assuming that students are represented
as objects of class *student*::

   >>> def better_student(p, q):
   ...     if (p.mark > q.mark):
   ...          return p.name
   ...     else:
   ...          return q.name
   ...
   >>> better_student(a, b)
   'Jerry'
   >>>

.. note::
   The above code should be written after defining class student and creating two students
   *a* and *b*.


Which version of *better_student* is more readable? Obviously, the second one!

Improving the student class
---------------------------

What is wrong with the following Python code fragment?::

   >>> m = student()
   >>> m.age = 16
   >>> m.name = 'Rahul'
   >>> m.mark = 90
   >>> n = student()
   >>> n.age = 16
   >>> n.name = 'Rohit'
   >>> better_student(m, n)
   Traceback (most recent call last):
   File "<stdin>", line 1, in <module>
   File "<stdin>", line 2, in better_student
   AttributeError: student instance has no attribute 'mark'
   >>>

We haven't created an attribute *mark* for our student *Rohit*! The possibility for such errors can be reduced
if there is some way to make sure that a student object is always created with the three attributes *age*, *name*
and *mark* properly initialized. Here is a modified student class which takes care of this::


   >>> class student:
   ...     def __init__(self, a, n, m):
   ...        self.age = a
   ...        self.name = n
   ...        self.mark = m
   ...
   >>> m = student(16, "Rahul", 90)
   >>> m.age
   16
   >>> m.name
   'Rahul'
   >>> m.mark
   90
   >>> n = student()
   Traceback (most recent call last):
   File "<stdin>", line 1, in <module>
   TypeError: __init__() takes exactly 4 arguments (1 given)
   >>>

A class can have functions defined as part of its body. We are defining a function with a peculiar name::

   __init__

(two underscore symbols, then the name *init* and then two more underscore symbols). The function takes 
four parameters::

   self, a, n and m

When Python executes the statement::

   m = student(16, "Rahul", 90)

it creates a student and immediately calls the function *__init__* passing 16 as the value of parameter *a*,
"Rahul" as the value of *n* and 90 as the value of *m*. What does the parameter *self* refer to? Any function
written within a class has to have a first parameter named *self* (Python does not require that this parameter
be called specifically *self*, but it is a convention in the Python world to always use the name *self* as the
name of the first parameter of a function defined within a class). When the function executes, *self* refers
to the object as part of whose creation the *__init__* function was invoked. The job of the *__init__* function
is to add the required attributes to the newly created object and initialize them properly. If you try to do 
something like this::

   n = student()

Python will give you a syntax error - once you define a special function called __init__ as part of the body
of a class, you will be able to create an object only by specifying values for all the parameters of the function
(except *self*).

Note that you can define any kind of function within a class; only if your function is specifically called *__init__*
will it be automatically called every time an object of that class is created. The special function *__init__* is called
a *constructor* in programming language literature.


