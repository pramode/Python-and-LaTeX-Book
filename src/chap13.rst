Handling data files
======================
Operating systems use files for permanent data storage (usually on a hard disk, CD/DVD or thumb drive).
Python programs can read data stored in files; they can also write data to files. In this chapter, we
will examine how this is done.


Writing a message to a file
----------------------------
Here is a simple Python program which writes a message to a file::

   >>> f = open('abc', 'w')
   >>> f.write('good morning!')
   >>> f.close()
   >>>

The *open* function takes two parameters - the first one is the name of a file (in this case, *abc*)
and the second one is a *mode* (in this case, 'w' which means we wish to open the file for writing).
*Open* returns an object which is stored in *f*; if you wish to write a message (say 'good morning!') to the file, simply
execute::

   f.write('good morning!')

.. note::
   You can also store the string in a variable and pass the variable as parameter to f.write
 

If you are familiar with the GNU/Linux operating system, you will see a file called *abc* when you
browse the file system!

Once a message is stored in a file, it can be easily retrieved any time::

   >>> g = open('abc', 'r')
   >>> s = g.readline()
   >>> print s
   'good morning!'
   >>>

We are now opening the file for *reading* (note the 'r' as second parameter to *open*). The function::

   g.readline()

reads one line from the file; it is then stored in *s*. 


Writing and reading multiple lines
----------------------------------

What does the following Python program do?::

   >>> f = open('data', 'w')
   >>> f.write('hello\n')
   >>> f.write('world\n')
   >>> f.write('python\n')
   >>> f.close()

It opens a file 'data' for writing and writes three strings. Note the '\n' at the end of the strings - it stands for the
*newline* character (the character corresponding to the *Enter* key). We want the three strings to be stored as three
independent lines in the file.

We can read these lines back::

   >>> g = open('data', 'r')
   >>> a = g.readlines()
   >>> print a
   ['hello\n', 'world\n', 'python\n']
   >>>

The function::
   
    g.readlines()

reads all the lines in the file and returns a list containing these lines.


Writing and reading numerical data
------------------------------------
Let's try to store a number 10 into a file::

   >>> f = open('dat2', 'w')
   >>> i = 10
   >>> f.write(i)
   Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
   TypeError: argument 1 must be string or read-only character buffer, not int
   >>>

This does not work; the *write* function expects a string as its parameter and will not work with any
other type. A solution is to convert the integer 10 to a string and then write it to the file::

   >>> f.write(str(i))
   >>> f.close()

The *str* function returns a string representation of the value in *i* and it is then written to the file.

You have to be careful when you read back the data::

   >>> g = open('dat2', 'r')
   >>> s = g.readline()
   >>> i = int(s)
   >>>

The *readline* function returns the string representation of the integer stored in the file. It has to
be converted back to its original form by calling the function *int*.


