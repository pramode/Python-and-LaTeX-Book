Introduction to the LaTeX Document Preparation System
======================================================

What will you do if your teacher asks you to prepare a project report using 
the PC? You will open Microsoft Office, type the document, and save it as
a *doc* file. You will spend a good amount of time changing fonts, aligning the lines
and in general trying to make the document look "beautiful". 

There are many problems with this approach to document preparation especially
as you start writing lengthy (and technical) documents like scientific reports
or books. It is a bit difficult at this point to explain what these problems are;
we shall get into it later. The important thing  is to realize that using a word processor
like MS Office (or OpenOffice, on GNU/Linux) is not the only way to prepare
documents. A far superior method is available; this involves using a program called
LaTeX.

.. note::
   We will make heavy use of the operating system terminal/command line as well as a text
   editor program like *gedit* in the remaining part of this book. So it is a good
   idea to review the material in Chapter 1 as well as Appendix 1 before proceeding
   further.

A Simple  LaTeX document
------------------------

Use your favourite text editor (say *gedit*) and create a text file containing the 
following lines::

  \documentclass{article}
  \title{Srinivasa Ramanujan}

  \begin{document}

  \maketitle

  Srinivasa Ramanujan was an Indian mathematician and 
  self taught genius who, with almost no formal training 
  in pure mathematics, made substantial contributions to 
  mathematical analysis, number theory, 
  infinite series and continued fractions.

  \end{document}

Save the file as *ramanuja.tex*; this is your report on Srinivasa Ramanuja, the famous
Indian mathematician, which you are supposed to submit to your maths teacher tomorrow!

But wait, what are all those mysterious \\documentclass, \\title etc doing in the document?

The idea is that you can use a powerful program called LaTeX to convert this file into
a very good looking document which can be printed on paper. How do we do this?

Open a terminal and type the following command::

   pdflatex ramanuja.tex

"pdflatex" generates a new file "ramanuja.pdf" using the data contained in "ramanuja.tex";
you will see a lot of messages getting printed on the screen during this process - don't
worry about it as long as you get back the *command prompt* (in case there is some error, you
will not get the command prompt - we will see how to handle this towards the end of this
chapter).

A file with  name ending in .pdf can be given directly to a printer or it can be viewed on
the screen (on GNU/Linux) using one of two programs: either *xpdf* or *evince*. You simply
have to give the command::

   xpdf ramanuja.pdf

or::
   
   evince ramanuja.pdf

at the operating system command line.


Here is what you will see when you print (or view) the PDF document:

.. image:: ../images/lat1a.jpg


Sometimes, your GNU/Linux installation may not have the command *pdflatex* installed. In that case,
there is another way to generate printable output.

First, we run the command *latex*::

   latex ramanuja.tex

This will generate a new file called "ramanuja.dvi". You have to convert a .dvi file to either PDF or Postscript
by using the commands *dvipdf* or *dvips*::

   dvips 1.dvi

will generate a new Postscript file called "1.ps" which can be directly printed or viewed on the 
screen using *xpdf* or *evince*.

If you wish to generate PDF output, you can try::

   dvipdf 1.dvi


What does LaTeX really do?
---------------------------

If you look at the PDF document produced by LaTeX, you will see that it does not contain any of the lines
\\documentclass, \\title etc. Instead, what you see is neatly formatted output. The title has a bigger font
size and is centralized. The left and right ends of all the lines are perfectly aligned; the word "continued"
has been split to make the alignment perfect. Usually, when we prepare documents using MS-Word or OpenOffice,
we spend a lot of time doing all these things manually - the problem with the approach is that as the document
gets larger in size, we will be spending more and more time on this rather than concentrating on our writing.
It's here that LaTeX comes to our rescue. All the details involved in getting beautiful printed output is 
handled by LaTeX - we simply have to focus on our writing! This does not mean that we can simply type
an article and expect LaTeX to format it properly. For example, how does LaTeX know what the title of the article
is? 

Simple. When you write a line like::

   \title{Srinivasa Ramanujan}

you are telling LaTeX that  "Srinivasa Ramanujan" is the title of the article. This does not result in the title
being actually displayed - LaTeX simply notes down the fact that the title is "Srinivasa Ramanujan". It is displayed
when you type::

   \maketitle

Because it is the title, LaTeX gives it a bigger font size and displays it at the center.

Now, how does LaTeX know what font size is to be used in the body? If you are preparing a document which is to
be used as a presentation and projected onto  a screen (say using an LCD projector), the fonts have to be much
larger. This is where the "documentclass" becomes relevant. If you look at the kind of documents around you, you
will see articles, books, letters, slides etc. Each "kind" of document has its own logical structure. A letter
has a "From Address", "To Address", "Signature", "Salutation", "Subject", "Place", "Date" etc while an 
article does not have most of these. A book will have chapters, sections and sub-sections while an article won't 
have chapters in it. Before you start writing the content of a LaTeX document, you must tell LaTeX what kind of
document you are planning to write. That is what::

   \documentclass{article}

does; you are telling LaTeX that what you are going to prepare is an article and NOT a slide or a book or a letter.
Once you give this information to LaTeX, LaTeX will decide *how* your document is to be formatted. 

.. note::
   You can specify options to the \\documentclass command; say you wish the font to be 12 point in size and
   the display be in two columns, you can write:  \\documentclass[twocolumn,12pt]{article}

Once you specify the document class and title, you can write the actual content of the document - this has to be
written between the lines::

   \begin{document}

and::

   \end{document}


Sections and sub-sections
--------------------------
Create another text file, *sample1.tex*, with the following lines in it::


   \documentclass {article}
   \title{A sample document}
   \author{Pramode C.E}
   \date{23 Jan 2010}

   \begin{document}

   \maketitle

   \section{This is a section}

   Articles are usually organized as sections, sub-sections etc.

   \subsection{This is a sub section}

   A subsection is part of a section.

   \section{This is another section}

   This section does not have any sub-section!

   \end{document}

This is how the generated pdf/postscript file looks:

.. image:: ../images/sample1.jpg

The \\title, \\author and \\date commands set a title, author and date for the document (current date is automatically
used if date is not specified) - these are displayed only when \\maketitle is invoked.

A new section is specified by writing::

   \section{name of section}

LaTeX automatically numbers the section and chooses an appropriate font size. Likewise, a subsection is created by::

   \subsection{name of sub-section}

Note that LaTeX again saves us the effort involved in section numbering and font size selection. LaTeX is also
capable of automatically generating a table of contents for us using the section names specified!

Lists, Quotes and Quotations
----------------------------
Enter the following text into a file, say *sample2.tex*::

  \documentclass {article}

  \begin{document}

  Here is how you typeset a short quotation:
  \begin{quote}
  This is an example of a short quotation. It consists of a single
  para of text. See how it is formatted.
  \end{quote}

  And, here is an example of a longer quotation:
  \begin{quotation}
  This is an example of a longer quotation. It consists of more
  than one paragraph of text.

  This is the second para of the quotation.
  \end{quotation}

  Here is an example of an unnumbered list:
  \begin{itemize}
   \item Apple
   \item Orange
   \item Banana
  \end{itemize}

  And, an example of a numbered list:
  \begin{enumerate}
   \item Newton
   \item Pascal
   \item Euler
  \end{enumerate}

  \end{document}
  
Here is the PDF output produced by LaTeX:

.. image:: ../images/sample2.jpg

A short quotation of only one paragraph can be formatted by enclosing it within::

   \begin{quote}

and::

   \end{quote}

The \\begin command is said to introduce a LaTeX *environment*, the name of the  *environment* is what
is given in curly brackets. Note that LaTeX offsets the text within the *quote* a little bit to the right.

The *quotation* environment should be used for displaying longer (multiple paragraphs) quotations.

The *itemize* environment is used for displaying unnumbered lists. Each item in the list should be
written like this::

   \item name of item

If you want numbered list, you can use the *enumerate* environment.

Handling errors
----------------
Try this experiment: in *sample2.tex*, change::

   \end{enumerate}

to::

   \end{itemize}

and run *pdflatex* or *latex* once again. Instead of getting back the command prompt, you will see something
like this::

   ! LaTeX Error: \begin{enumerate} on input line 27 ended by \end{itemize}.

   See the LaTeX manual or LaTeX Companion for explanation.
   Type  H <return>  for immediate help.
   ...                                              
                                                  
   l.31 \end{itemize}
                  
   ? 

The error occurs because a \\begin{enumerate} should end with \\end{enumerate}. You should type **q**
to get back the command prompt and rectify the error.


