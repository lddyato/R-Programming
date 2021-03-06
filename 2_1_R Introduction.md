Introduction
============

R as a programming language:

* Start with the basic building blocks of R like data types and low-level details
* Writing and formulating R scripts: control structures and functions

Packages for visualization and machine learning will be covered in other sections of the R concentration.

Overview and History of R
=======================

R is the dialect of the S language

What is S?
----------

* S is a language that was developed by John Chambers and others at Bell labs
* It was rewritten in C in 1988
* S has transferred from Bell (now Lucent) to StatSci (then insightful Corp) to TIBCO
* The fundamentals of S have not changed since 1998

S Philosophy
------------

Enter the language as an interactive environment. Then as their needs became clearer they could slide gradually into programming.

Back to R
---------

* 2000 version 1.0.0 is released
* 2013 v.3.0.2 is release in December

Features of R
-------------

* Syntax is similar to S
* Semantics are superficially to S but are actually different
* Runs on almost any standard computing platform/OS (even PLayStation 3)
* Frequent releases (annual + bugfix releases); active development
* Core is quite lean, functionality is divided into modular packages
* Graphic capabilities very sophisticated
* Useful for interactive work, but contains a powerful programming language for developing tools
* Very active user community
* It's free!

Free Software
-------------

* The freedom to run the program
* Freedom to study how it works and adapt to your needs
* Freedom to redistribute copies
* Freedom to improve and release improvements to the public

Drawbacks of R
--------------

* Essentially based on 40-year old technology
* Little built-in support for dynamic or 3D graphics
* Functionality is based on consumer demand
* Objects must be generally stored in your physically memory
* Not ideal for all possible situations

Design of the R System
----------------------

The R system is divided into 2 conceptual parts:

1. The "base" R system that you download from CRAN
2. Everything else

R functionality is divided into a number of packages:

* The "base" package required to run R
* Other bundled packages include: stats, datasets, graphics, grid, methods, tools, parallel, splines, etc
* "Recommended" packages include: boot, class, cluster, lattice, survival, spatial, Matrix
* 4000 contrib packages on CRAN

Some R Resources
----------------

Available from [CRAN](http://cran.r-project.org):

* An introduction to R
* Writing R extensions
* R data import/export
* R installation and admin (mostly for building R from source)
* R internals (not for the faint of heart)

Getting Help
===============

Finding Answers
---------------

* Search the archives of the forum before you post
* Search the web
* Read the manual
* Read the FAQ
* inspection or experimentation
* Ask a skilled friend
* Read the source code (if you're a programmer)

Asking Questions
----------------

* It's important to let other people know you've done due diligence
* What steps will reproduce the problem?
* What is the expected output?
* What did you see instead?
* What version of the product?
* What OS?
* Additional information

Example
-------

### Error Messages

	> library(datasets)
	> data(airquality)
	> cor(airquality)

	Error in cor(airquality) : missing observations in cov/cor
	
### Google is your Friend

Google: "missing observations in cov/cor"

Subject Headers
---------------

* Stupid: "Help! can't fit linear model!"
* Smart: "R 3.0.2 lm() function produces seg fault with large data frame, Mac OSX 10.9.1"
* Smart: "R 3.0.2 lm() function on Mac OSX 10.9.1 -- segfault on large data frame"

Do These
--------

* Describe the goal, not the step
* Be explicit about your question
* Do provide the minimum amount of info necessary
* Be courteous
* Follow up with the solution (if found)

Don't Do These
--------------

* Claim you've found a bug
* Grovel as a substitute for doing your homework
* Post homework questions on mailing lists
* Email multiple emailing lists at once
* Ask others to debug your code without giving a hist as to what sort of problem they should be searching for
