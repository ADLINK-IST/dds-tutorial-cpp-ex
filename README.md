#Overview

This repository contains the code C++ examples for the 
DDS Tutorial.

To make to code more compact and clear I take deliberately
advantage of some of the features introduced by C++11. 
Considered the widely spread availability of C++11 compilers
this should not pose a problem.


#Getting Started

To try out the examples you need to have:

  - OpenSplice DDS (http://opensplice.org | http://prismtech.com)
  - g++ or clang with support for C+0x
  - cmake 2.8 or higher

Once you have installed OpenSplice you'll have to configure
the support for C++11 -- by default OpenSplice C++ API is
built for C++98.

To enable C++11 support follow the instructions described
here http://dev.opensplice.org/releases/downloads/docs/isocpp/html/isocpp_customlibs.html


## Compiling
To compile simply do:

$ cmake .
$ make


That's it.

-Happy Hacking

