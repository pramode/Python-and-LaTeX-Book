An introduction to the GNU/Linux Operating System
=================================================

This  book teaches programming using Python and technical document preparation
using LaTeX. Both LaTeX and Python are Free Software, and the ideal way to learn
them is by using the GNU/Linux operating system. 
 

Installing GNU/Linux
---------------------
A complete GNU/Linux system is composed of thousands of applications, all available
for download on the Internet. Setting up a system by downloading and installing each
component individually is a very tough job - so we have what are called *Linux distributions*
which are simply CD's/DVD's packed with all the tools required to set up a fully
functional system. There are several GNU/Linux distributions - Fedora, Ubuntu and 
Debian are some of the more popular ones. These distributions basically differ in
the mix and match of software they provide - most people would advise beginners to
get started with Ubuntu.

A complete Ubuntu distribution can be downloaded from the web site: http://www.ubuntu.com. The
downloaded software should be written to a CD - this CD can be used to install Ubuntu
on to the hard disk. The installation process is usually  very easy and a person
moderately experienced in using computers, even if he is using GNU/Linux based systems for
the first time, should be able to complete it without too much trouble. We will not go
into the details of system installation in this book - it is assumed that you have a
working GNU/Linux system at hand.


Using GNU/Linux
----------------

Shown below is the screenshot of a Fedora GNU/Linux desktop.

.. image:: images/desktop1c.png


You will find menu's like **Applications**, **Places**, **System** etc. The menu layout and desktop appearance will
be different on different GNU/Linux distributions. But that shouldn't bother you too much. A little experimentation
is all that is required to get up and running fast!

Here are some common GNU/Linux applications for tasks like editing documents, browsing the web etc. 

   * Firefox - the standard web browser on GNU/Linux systems
   * OpenOffice - you can use this program for word processing, spreadsheet calculations.
   * GIMP - a powerful image manipulation program. You will love this if you are a graphics artist.


The GNU/Linux Commandline
--------------------------
The mouse based Graphical User Interface is ideal for beginners. But once you start writing programs 
you will have to interact with the operating system by typing commands. You need
to open a terminal for doing this. On a Fedora system, the terminal is available in the *Sytem tools* sub-menu
of the *Applications* menu (it's name is simply *Terminal*). The location of this program may be different on
other GNU/Linux distributions - so you will definitely have to experiment a bit!

Here is a screen shot of a Fedora desktop with the terminal application active.

.. image:: images/terminal.png

You can type commands within the terminal window and they would get executed. Say for example you wish to
see the current date - the command for doing this is simply  *date*. Here is what you might see if
you type *date*::

   [ram@knuth ~]$ date
   Wed Nov 11 12:28:19 IST 2009
   [ram@knuth ~]$ 

The message::
  
   [ram@knuth ~]$

which you see above is displayed automatically by the terminal - it is called a *command prompt*. The command prompt is
simply a visual indication of the fact that the terminal is ready to accept commands.

.. note::
   The actual message displayed as part of the command prompt will be different on your machine. No need to worry about
   it! Just keep in mind that you always type commands *after* the prompt.


In later chapters, you will have to use a few simple commands to interact with Python and LaTeX.

