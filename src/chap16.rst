
Pictures and Colours in LaTeX
==============================
It is possible to include pictures in your LaTeX document. It is also
possible to draw simple figures and change colours using LaTeX 
commands itself. This chapter explains how this is done.

.. note:: Using an additional package called "pstricks", it is possible
   to  generate complex figures (like plots of equations) in LaTeX. A 
   simple "pstricks" example is given in the last section of this chapter.

 
The LaTeX "picture" environment
--------------------------------

Create a file called *pic1.tex* containing the following lines::


   \documentclass {article}
   \begin{document}

   \section{This is a section}

   \begin{picture}(100,200)

   \put (0,0) {A}
   \put (100,0) {B}
   \put (100, 200) {C}
   \put (0, 200) {D}
   \end{picture}

   \end{document}

Here is the PDF/Postscript output produced by LaTeX:

.. image:: ../images/pic1.jpg

The LaTeX command::

   \begin{picture}(100, 200)

creates a "picture environment" of width 100 units and height 200 units (imagine
the picture environment producing a 100x200 box) - a unit
has a default value of about 0.35mm. The command::

   \put (0,0) {A}

writes the symbol "A" at location (0,0) of the box; location (0,0) is the 
(x, y) co-ordinate of the lower left corner of the box (it is the origin). 
The +ve X axis is towards the right and the upward direction represents 
+ve Y axis. The command::

   \put (100,200) {C}

places the symbol C at the top right corner. The commands::

   \put (100, 0) {B}
   \put (0, 200) {D}

places the symbols B and D at the bottom right and top left corners of the box.


Drawing Lines
---------------

Drawing lines in LaTeX is tricky business - due to certain limitations, it is not
possible to draw lines with any random slope. The natural way for a line drawing
command to work would be to accept the co-ordinates of the end points and draw 
a line connecting the points. But that is not the way it is done in LaTeX. To simplify
things, we consider three separate cases: drawing a horizontal line, drawing a vertical
line and drawing lines with many other slopes. For all three cases, we assume a box
of size 100x200 with origin (0, 0) at the bottom left corner (the
same box as in the previous section). 

Horizontal lines
~~~~~~~~~~~~~~~~

Let's say we wish to draw a horizontal line of length 40 units from point (30, 90). Here is how it
is done::

   \put(30,90){\line(1,0){40}}

We can identify two separate parts in this command; the first part::

   \put(30, 90)

says: *start the line at point (30, 90)*. The next part is::

   \line(1,0){40}

This is how it works: LaTeX draws a line of length 40 units and passing through the
points::

   (30, 90) and (30 + 1, 90 + 0)

and ending at (70, 90).


What if we write::

  \put(30, 90){ \line(-1, 0) {30} }

We get a line passing through (30, 90) and (30 - 1, 90 + 0) of length 30
units, ending at (0, 90).

So, the general command for drawing a horizontal line is::

   \put(x,y) { \line(A, 0){len} }

Where (x,y) is the starting co-ordinate of the line, A is +1 or -1 (depending on whether you want to 
draw to the right of (x, y) or left of (x, y) and *len* is the length of the line.

Vertical lines
~~~~~~~~~~~~~~
It should be easy to guess how vertical lines are drawn! Here is an example::

   \put(30,90) {\line(0,1) {40}}

This draws a vertical line connecting (30, 90) and (30, 91) of length 40 units ending at (30, 130). The
general command is::

   \put(x,y) { \line(0, A){len} }

Where (x, y) is the starting co-ordinate of the line, A is +1 or -1 depending on whether the line
goes up or down and *len* is the length of the line.

Slanted lines (neither vertical nor horizontal)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

What kind of line does LaTeX draw if we write::

   \put(30,90) {\line(1, -1) {40}}

LaTeX draws a line going through (30, 90) and (31, 89) (ie, sloping down to the right); what is the length
of this line? That is not specified here - the number 40 written in curly brackets simply
indicates the fact that  as the line moves down to the right, it will end at that point
where the X co-ordinate is 30 + 40.

What if we write::

   \put(40,90) {\line(-1, 1) {30}}

We get  a line starting at (40, 90), going through (39, 91) (going up to the left) 
and ending at a point whose X co-ordinate is 40 - 30, ie 10.

The general form of the command for a slanted line is::

   \put(x,y) {\line(p, q) {len}}

LaTeX has certain restrictions on the values of p and q - this places a limit on the slopes
of the lines which we can draw. Both p and q should be integers between -6 and +6, inclusive.
Also, they should have no common divisor bigger than 1. That is, p/q should be a fraction in
its simplest form - you can't have something like p = 2 and q = 4; you should write p = 1 and
q = 2. The following are all illegal values for p and q::

   (1.2, 3) --- no decimal permitted
   (3, 6) --- common divisor 3 bigger than 1
   (1, 7) --- one value bigger than +6

The smallest slanted line which LaTeX can draw is a line of length 10 points (about 3.5mm). LaTeX will
draw nothing if you try to draw slanted lines less than this length.

Circles, ovals and bezier curves
---------------------------------
.. note::
   We are assuming that the picture environment has width 100 units and height 200
   units in all the examples below.

Here is how you can draw a circle::

   \put(20,30) {circle{20}}

This draws a circle at centre (20,30) with diameter 20 points. 

The command::

   \put(20,30) {\circle*{20}}

draws a disc (a filled circle) at (20,30) with a diameter of 20 points.

LaTeX knows to draw discs/circles with only a certain fixed number of diameters - it will
choose the one whose diameter is closest to what you have specified. Also, the set of
possible diameters has an upper limit. 

The command::

   \put(30,30) {\oval(20,10)}

will draw an oval (a rectangle with rounded corners) of width 20 units and height 10 units.

The \qbezier command takes three points as arguments and draws a quadratic *bezier curve* connecting 
them::

   \qbezier (0,0) (50,100) (100, 0)


Using the "graphics" package
-----------------------------
Using a package called "graphics", we can include images in our LaTeX document, perform
manipulations like rotation/scaling, add colour etc.

Scaling, Rotation, Colour change
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Create a file called *pic2.tex* with the following lines in it::


   \documentclass {article}
   \usepackage{graphics}
   \usepackage{color}


   \begin{document}

   \scalebox{4}{Hello}

   \rotatebox{40} {Maths}

   Python \reflectbox{Python}

   \textcolor{red}{GNU/Linux} means Freedom!

   \colorbox{green}{Malayalam}

   \end{document}


Here is the output produced by LaTeX:

.. image:: ../images/pic2.jpg

The two lines at the beginning::

   \usepackage{graphics}
   \usepackage{color}

are essential for commands like \\scalebox, \\textcolor etc to work. You can think of them as being similar
to the *import* statement in Python - they make available additional functionality.

You can enlarge text by a constant scale factor using \\scalebox. For example::

   \scalebox{4}{Hello}

displays "Hello" enlarged by a factor of 4.

You can rotate text using \\rotatebox. For example::

   \rotatebox{40}{Maths}

displays the text "Maths" 40 degree rotated.

The \\reflectbox command generates a mirror image. For example::

   \reflectbox{Python}

displays the mirror image of the string "Python".

Color of text can be changed using \\textcolor. For example::

   \textcolor{red}{GNU/Linux}

displays the string "GNU/Linux" in red colour.

A string can be displayed in a coloured box using \\colorbox. 


Displaying images
~~~~~~~~~~~~~~~~~~~~

Sometimes, you may have to include an external image file (say a JPG or PNG file) in your LaTeX document. There are
two ways to do it. 

Suppose you are using the "pdflatex" command and want to display a photo of Ramanujan somewhere in your document.
Just write::

   \includegraphics{ramanujan.jpg}

Note that "pdflatex" supports only JPG and PNG formats. The file "ramanujan.jpg" should exist in the folder(directory) from
where you are issuing the "pdflatex" command.

If you are using the "latex" command, you will have to first convert your JPG/PNG image to what is called an *encapsulated postscript*
file. This can be done very easily on GNU/Linux systems by using a command called "convert". At the command prompt,
you should type::

   convert ramanujan.jpg ramanujan.eps

Once this is done, you can  use::

   \includegraphics{ramanujan.eps}

to incude the image in your document.


Using "pstricks" for advanced picture drawing
----------------------------------------------

We have seen that the facilities available by default in LaTeX for drawing lines, circles etc
are not very sophisticated. A package called "pstricks" can be used for generating complex
figures without too much trouble. Let's try to plot a curve using pstricks::


   \documentclass {article}
   \usepackage{pstricks}
   \usepackage{pst-plot}

   \begin{document}


   \begin{pspicture}(-3, -2)(3, 2)
   \psaxes(0,0)(-3,-2)(3,2)
   \psplot[plotstyle=curve] {-1.5} {1.5} {x 3 exp x sub}
   \end{pspicture}

   \end{document}


Two packages have to be included: *pstricks* and *pst-plot*. Also, "pdflatex" will not work
with the above file - you have to use the "latex" command itself.


The line::

   \begin{pspicture} (-3, -2) (3, 2)

starts a "pspicture" environment - think of it as a request to LaTeX to leave enough space for
a rectangle whose bottom left corner has co-ordinate (-3, -2) and top right corner has co-ordinate
(3, 2).

The next command::

   \psaxes(0,0) (-3, -2) (3, 2)

draws the co-ordinate axes. The X axis and Y axis meet at the point (0, 0) and they have
to be visualized as being enclosed in an imaginary rectangular box with bottom left corner at (-3, -2)
and top right corner at (3, 2).

We are plotting the curve::

   y = (x * x * x) - x

This equation has to be specified in a peculiar form called *postfix*. An arithmetic expression 
written in the usual way::

   2 * 3 + 4

is called an *infix expression*. Here is another way to write the same expression::

   2 3 * 4 +

This is called a *postfix expression*. The logic is simple. Read the expression from left to right. When you
encounter an operator, simply apply the operator to the two operands to the left. In the above case, the moment
we see the * operator (multiplication), we can rewrite the expression as::

  6 4 +

Now, when we encounter the + operator, we can rewrite the expression as::

  10

Let's examine this line in our LaTeX document::

  \psplot[plotstyle=curve] {-1.5} {1.5} {x 3 exp x sub}

We are asking LaTeX to plot a curve; the curve is given by the equation::

  y = x 3 exp x sub

(note: you need to specify only the right hand side of the equation).

This equation is written in postfix form; *exp* is the exponentiation operator and *sub* is the subtraction
operator. So we can read this as::

  y = (x raised to 3) minus x

The numbers -1.5 and +1.5 in brackets refers to the range of possible values for x.










