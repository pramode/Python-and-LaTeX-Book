Typesetting Mathematics
=========================

A big advantage of LaTeX is that it can be used to prepare documents containing
complex mathematical formulae. In this chapter, we examine how to typeset mathematics
with LaTeX.

The three environments - math, displaymath and equation
---------------------------------------------------------
Let us typeset an equation in three different ways. Here is the LaTeX document::


   \documentclass {article}
   \begin{document}


   Here is a formula: $E = mc^{2}$

   Same formula, but this is typeset differently: \[ E = mc^{2} \]

   Same formula again, different typesetting: 
    \begin{equation}
    E = mc^{2}
    \end{equation}

   Repeat:
    \begin{equation}
     E = mc^{2}
    \end{equation}

   \end{document}

This is the output which LaTeX generates:

.. image:: ../images/math1.jpg


When an equation is written between two "$" (dollar) signs, it is said to be in *math* mode. In the
above document::

   $E = mc^{2}$

is in math mode. The equation is displayed in the same line (it is called an in-text formula). When
the same equation is written between a "\\[" and "\\]", it is said to be in *displaymath* mode; it is
displayed on a line of its own. 

When the equation is written between a "\\begin{equation}" and "\\end{equation}", LaTeX gives it an
equation number - the first equation is given the number 1 and subsequent equations are numbered 2, 3
and so on.

Now, how do you really write an equation? Mathematical equations are full of symbols which we rarely
use when writing normal text - LaTeX has a syntax of its own for representing such symbols and symbol
combinations. The equation:

.. math::
   
   E = mc^{2}

itself is a good example. LaTeX displays the number 2 as a "superscript" when the "^" operator is used.

   
A few examples
----------------

Given below are a few samples of the kind of mathematical expressions you can create using LaTeX (the
expressions have to be in one of math, displaymath or equation modes - that is omitted in the examples).

LaTex Command::

   x_{i}

result:

.. math::
   x_{i}

LaTeX command::
   
   p = \frac{a+b}{a-b}

result:

.. math::
   p = \frac{a+b}{a-b}

LaTeX command::

   \sqrt{a+b}

result:

.. math::
   \sqrt{a+b}

LaTeX command::

   \sqrt[n]{2}

result:

.. math::
   \sqrt[n]{2}
   

LaTeX command::

   \alpha \beta \pi

result:

.. math::
   \alpha \beta \pi

LaTeX command::

   \leq

result:

.. math::
   \leq

LaTeX command::

  \not\leq

result:

.. math::
   \not\leq

LaTeX command::

   \sum_{i=1}^{n} x_{i} = \int_{0}^{1} f

result:

.. math::
   \sum_{i=1}^{n} x_{i} = \int_{0}^{1} f


LaTeX command::

   \lim_{n \rightarrow \infty} x = 0

result:

.. math::
   \lim_{n \rightarrow \infty} x = 0

LaTeX command::

   \overline{a+b}

result:

.. math::
   \overline{a+b}

LaTeX command::

   \underline{a+b}

result:

.. math::
   \underline{a+b}

LaTeX command::

   \overbrace{a+b+c+d}

result:

.. math::
   \overbrace{a+b+c+d}






