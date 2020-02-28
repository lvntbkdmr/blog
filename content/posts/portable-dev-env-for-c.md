---
title: "Portable Dev Env for C&#43;&#43;"
date: 28 Feb 20 05:02 UTC
draft: false
---

A cross-platform method to construct a development environment for developing C++ applications by using several tools such as :

1. Eclipse (IDE)
2. GNU GCC (Compiler)
3. GNU GDB (Debugger)
4. JDK (Java Runtime)
5. Python (To run scripts and required by SCons)
6. SCons (Build system)
7. Boost (Advanced C++ libraries)

First of all create a folder named as **devenv** at any location.

## Ubuntu 18.04

### Eclipse

Download Eclipse IDE for C/C++ Developers from [https://www.eclipse.org/downloads/packages/](https://www.eclipse.org/downloads/packages/) for Linux 64-bit

Extract compressed **.tar.gz** file into **devenv/eclipse** folder

### GNU GCC

`sudo apt install build-essential` is sufficient for now

### GNU GDB

Download latest source files from [http://ftp.gnu.org/gnu/gdb/](http://ftp.gnu.org/gnu/gdb/)

Extract compressed **.tar** file into some temporary location (for only building purposes, source files of gdb will not be a part of our development environment)

### Pretty-Print for GDB

Install subversion

`sudo apt-get install subversion`

Checkout related packages to enable pretty printing in GDB

Open **.gdbinit** file and copy the following contents

`os.getenv('GDB_LOC')` gets **GDB_LOC** environment variable which we will set before opening eclipse, thus it will be able to fetch the GDB location

### JDK

Download **Linux Compressed Archive** from [https://www.oracle.com/java/technologies/javase-jdk13-downloads.html](https://www.oracle.com/java/technologies/javase-jdk13-downloads.html)

`mkdir devenv/jdk-13.0.2`

Extract downloaded compressed jdk into **devenv/jdk-x.x.x** folder.

### Python

Download latest linux source files from [https://www.python.org/downloads/](https://www.python.org/downloads/)

Extract downloded compressed file into some temporary location (This will also be compiled)

### SCons

Download latest source files from [https://scons.org/pages/download.html](https://scons.org/pages/download.html)

Extract downloaded compressed file into some temporary location (Will be compiled)

### Boost

Download latest compressed source file from under [https://dl.bintray.com/boostorg/release](https://dl.bintray.com/boostorg/release)

Extract downlodad compressed file into some temp location (Will be compiled)

## Windows 10

### Eclipse

Download Eclipse IDE for C/C++ Developers from [https://www.eclipse.org/downloads/packages/](https://www.eclipse.org/downloads/packages/) for Windows 64-bit

Extract compressed **.zip** file into **devenv/eclipse** folder

### GNU GCC

Download MinGW Installation Manager (mingw-get) from [https://osdn.net/projects/mingw/releases/](https://osdn.net/projects/mingw/releases/)

Run mingw-get

Select destination folder location as **devenv/MinGW**

Check all Basic Setup packages (gcc-fortran-bin and gcc-ada-bin are not necessary for us, you can uncheck them)

From All Packages screen, uncheck **mingw32-gdb-bin** and all related gdb packages since we will be installing our own GDB which is the latest one that supports pretty-print with python scripting for C++ STL objects.

Install and exit.

### CMake

It is required to build some programs so it is better to have it inside development environment.

Download Windows win64-x64 ZIP(Binary distributions) from [https://cmake.org/download/](https://cmake.org/download/)

Extract zip into **devenv**

### Python

Download Windows x86 embeddable zip file from [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)

Install it into 

### GNU GDB

Download latest source files from [http://ftp.gnu.org/gnu/gdb/](http://ftp.gnu.org/gnu/gdb/)

Extract compressed **.tar** file into some temporary location (for only building purposes, source files of gdb will not be a part of our development environment)

### Pretty-Print for GDB

### JDK

### SCons

### Boost