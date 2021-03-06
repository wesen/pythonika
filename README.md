pythonika
=========

Pythonika is a MathLink module that allows you to write and evaulate Python code from within Mathematica Notebooks

Pythonika 1.0 - Python Interpreter Interface for Mathematica.
Copyright (c) 2005-2010 Ero Carrera <ero@dkbza.org>


Introduction:
-------------

Pythonika is a MathLink module that allows to write and evaluate Python code
from within Mathematica Notebooks.

Pythonika automatically translates all basic types from Mathematica into Python
and back. Python expressions returning complex, integer or long numbers,
strings, lists, tuples, sets or dictionaries will evaluate into the
corresponding objects in Mathematica. Dictionaries are returned as list of
lists containing key/value pairs.

It's also possible to define Mathematica functions which are just Python code 
where all the conversion of the arguments is done transparently. It's not even 
necessary to tell how many arguments the Python function is taking!! Pythonika 
is clever enough to figure it out.

Why?
----

Personally, I have always found Mathematica's Notebook interface to be
perfectly suited for the way I conduct research. Which usually requires me to
write code to test hypothesis or to develop concepts. Frequently the way I
approach a problem changes as I discover its details and gain insight. 

I find of great utility having the ability of writing notes together with code 
which I can readily evaluate in small blocks. Repeating small parts of an 
algorithm as necessary or grouping the code in different cells according to its 
functionality; for instance, data set loading, parsing and analysis.


Pythonika has been tested mainly with Python 2.5 and 2.4 but should work with
2.3 and probably other, older versions.

Pythonika should compile and work with Mathematica in all OS X, Linux and 
Windows operating systems.

My main working environment is OS X, so it has been more thoroughly tested on 
that platform. I successfully compiled and tested it on others. If someone
would find that it does not work on a certain environment I would be glad to
include whatever changes are found to be needed to get it to work correctly.


Requirements:
-------------

-Windows:

In order to build it I used Visual Express C++ and the Platform SDK. Both 
downloadable from Microsoft.
If not already set, one will need to setup all the appropriate environment
variables (INCLUDE & LIB) pointing to the include and library directories
provided by Visual C++ and the SDK.

-Linux/OSX:

GCC

-All:

The MathLink development kit is also needed and can be found at:

http://www.wolfram.com/solutions/mathlink/devkits.html

Mathematica is needed in order to run it.


Compilation:
------------

Be sure to link or add the path to the directory containing the needed
Mathematica files. Information is available in each architecture's Makefile.

It should suffice with running the appropriate platform's equivalent to "make" 
with the corresponding Makefile:

OS X: make -f Makefile.osx

Linux: make -f Makefile.linux

Windows: nmake -f Makefile.win

The compilation will produce a Pythonika executable. If this point has been 
reached successfully it should now be possible to just load it within 
Mathematica.


Installation:
-------------

In order to load Pythonika it should be enough with calling the Mathematica 
function Install["path/to/the/Pythonika/executable"].
If the loading is successful, calling Links["path/to/the/Pythonika/executable"] 
will return a list with a LinkObject pointing to Pythonika.

It should now all be ready to start writing Python code!


Usage:
------

For common usage examples, please refer to the example Notebook.

The Python instance is common to all Notebooks. So the global namespace is 
shared. And it's possible to share calculations and data across Notebooks.

It's possible to write multiline code in Pythonika. In order to enter multiline
code one must use "\<" "\>" which tells Mathematica to keep newlines as such.

Using double quotes is not a good idea, as Mathematica will interpret that as 
the end of the current string. The solution is using single quotes in the
Python code.

Unicode should be properly converted back and forth. I haven't thoroughly
tested this so there might be some problems.

Escape sequences: It's possible to use backslash escaped sequences although
it's necessary to double the backslashes for them to get to Pythonika as a
single backslash as Mathematica will try to interpret them.
