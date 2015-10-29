##Tutorial

Text can be found here:

Link:   http://www.researchgate.net/publication/273136749_The_Data_Distribution_Service_Tutorial
Source: https://github.com/PrismTech/dds-tutorial

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

##Install OpenSplice

Here's a script for x86_64

```bash
#!/usr/bin/env bash


# http://www.prismtech.com/dds-community/building
# (but you don't need tao and all that stuff)

sudo apt-get install flex bison gawk

git clone https://github.com/PrismTech/opensplice.git

BASE_PATH=$(readlink -f opensplice)

cd $BASE_PATH
mkdir -p submods
cd       submods
git clone https://github.com/OpenSplice/MPC_ROOT.git

cd $BASE_PATH

echo
echo " ####"
echo "When prompted (just now) for target: hit 6   (for x86_64.linux-dev)"
echo "Hit enter to continue..."

read

source ./configure
make
make install

sed -i "s|@@INSTALLDIR@@|$BASE_PATH/install|" $BASE_PATH/install/HDE/x86_64.linux-dev/release.com


# Please select a target number:6

# GCC: OK - using version 5.2.1
# NOTE: enabling link-time optimizations in release build
# GLIBC: version 2.19
# MAKE: OK - using GNU Make 4.0
# Perl: OK - using perl version='5.20.2';
# Qt: Warning - Cannot find Qt libraries. Standalone demo package will not be built.
# Please specifiy QTLIBDIR.
# GAWK: OK - using GNU Awk 4.1.1, API: 1.1 (GNU MPFR 3.1.3, GNU MP 6.0.0)
# BISON: OK - using bison (GNU Bison) 3.0.4
# FLEX: OK - using 2.5.39
# JAVAC: Warning - Java compiler environment not set, building of all Java related features is disabled.
# GMCS: Warning - No gmcs compiler found
# gmcs C# compiler not found, disabling SACS api build.
# TAO: Warning - No TAO found
# TAO environment not set, disabling TAO related features.
# JACORB: Warning - JACORB_HOME not set
# JACORB environment not set, disabling JACORB related features.
# GSOAP: Warning - Not found, cmsoap will not be built
# Doxygen: OK
# Configuration OK

# Variable Setup
# SPLICE_TARGET = x86_64.linux-dev
# SPLICE_HOST = x86_64.linux-dev
# OSPL_HOME = /tmp/opensplice
# SPLICE_ORB =
```

Once you have installed OpenSplice you'll have to configure
the support for C++11 -- by default OpenSplice C++ API is
built for C++98.

To enable C++11 support follow the instructions described
here http://dev.opensplice.org/releases/downloads/docs/isocpp/html/isocpp_customlibs.html

Basically do:
```bash
cd opensplice/install/HDE/x86_64.linux-dev/custom_lib

nano Makefile.Build_DCPS_ISO_Cpp_Lib
## add -std=c++11 to the CPPFLAGS line !!!!!!!!!!

make -f Makefile.Build_DCPS_ISO_Cpp_Lib clean
make -f Makefile.Build_DCPS_ISO_Cpp_Lib
```

## Compiling
To compile simply do:

$ cmake .
$ make


That's it.

-Happy Hacking

