---
title: "Portable Dev Env for C&#43;&#43;"
date: 28 Feb 20 05:02 UTC
draft: false
---

A cross-platform method to construct a development environment for developing C++ applications by using several tools such as :

1. Eclipse (IDE)
2. GNU GCC (Compiler)
3. CMake (only for Windows)
4. GNU GDB (Debugger)
5. JDK (Java Runtime)
6. Python (To run scripts and required by SCons)
7. SCons (Build system)
8. Boost (Advanced C++ libraries)

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

    mkdir devenv/gdb-9.1
    cd into your temporary gdb source folder
    mkdir build
    cd build
    ../configure --prefix=/home/devenv/gdb-9.1
    make -j4
    make install

### Pretty-Print for GDB

Install subversion

`sudo apt-get install subversion`

Checkout related packages to enable pretty printing in GDB

    cd /home/devenv/gdb-9.1
    svn co https://gcc.gnu.org/svn/gcc/trunk/libstdc++-v3/python
    touch .gdbinit

Open **.gdbinit** file and copy the following contents

    python
    import sys, os
    sys.path.insert(0, os.getenv('GDB_LOC') + '\\python')
    from libstdcxx.v6.printers import register_libstdcxx_printers
    register_libstdcxx_printers (None)
    end
    set print pretty on
    set print object on
    set print static-members on
    set print vtbl on
    set print demangle on
    set demangle-style gnu-v3
    set print sevenbit-strings off

`os.getenv('GDB_LOC')` gets **GDB_LOC** environment variable which we will set before opening eclipse, thus it will be able to fetch the GDB location

### JDK

Download **Linux Compressed Archive** from [https://www.oracle.com/java/technologies/javase-jdk13-downloads.html](https://www.oracle.com/java/technologies/javase-jdk13-downloads.html)

`mkdir devenv/jdk-13.0.2`

Extract downloaded compressed jdk into **devenv/jdk-x.x.x** folder.

### Python

Download latest linux source files from [https://www.python.org/downloads/](https://www.python.org/downloads/)

Extract downloded compressed file into some temporary location (This will also be compiled)

    mkdir devenv/Python3.8
    cd into temporary python source folder
    ./configure --prefix=/home/devenv/Python3.8
    make -j4
    make install

### SCons

Download latest source files from [https://scons.org/pages/download.html](https://scons.org/pages/download.html)

Extract downloaded compressed file into some temporary location (Will be compiled)

    cd devenv/Python3.8/bin
    #/home/Downloads/scons-3.1.2 is your temporary location
    ./python /home/Downloads/scons-3.1.2/setup.py install

### Boost

Download latest compressed source file from under [https://dl.bintray.com/boostorg/release](https://dl.bintray.com/boostorg/release)

Extract downlodad compressed file into some temp location (Will be compiled)

    mkdir devenv/boost_1_72_0
    cd into your temp source location
    sh bootstrap.sh
    ./b2 install --prefix=/home/devenv/boost_1_72_0

## Windows 10

### Eclipse

Download Eclipse IDE for C/C++ Developers from [https://www.eclipse.org/downloads/packages/](https://www.eclipse.org/downloads/packages/) for Windows 64-bit

Extract compressed **.zip** file into **devenv\eclipse** folder

### GNU GCC

Download MinGW Installation Manager (mingw-get) from [https://osdn.net/projects/mingw/releases/](https://osdn.net/projects/mingw/releases/)

Run mingw-get

Select destination folder location as **devenv\MinGW**

Check all Basic Setup packages (gcc-fortran-bin and gcc-ada-bin are not necessary for us, you can uncheck them)

From All Packages screen, uncheck **mingw32-gdb-bin** and all related gdb packages since we will be installing our own GDB which is the latest one that supports pretty-print with python scripting for C++ STL objects.

Install and exit.

### CMake

It is required to build some programs so it is better to have it inside development environment.

Download Windows win64-x64 ZIP(Binary distributions) from [https://cmake.org/download/](https://cmake.org/download/)

Extract zip into **devenv**

### Python

Download Windows x86 embeddable zip file from [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)

Extract it into **devenv\Python38-32**

### SCons

Download latest source files from [https://scons.org/pages/download.html](https://scons.org/pages/download.html)

Extract downloaded compressed file into some temporary location (Will be compiled)

    cd devenv\Python38-32
    #C:\Downloads\scons-3.1.2 is your temporary location
    python.exe C:\Downloads\scons-3.1.2\setup.py install

### GNU GDB

Download latest source files from [http://ftp.gnu.org/gnu/gdb/](http://ftp.gnu.org/gnu/gdb/)

Extract compressed **.tar** file into **devenv\MinGW\msys\1.0\home\user\gdb-9.1**

Open **devenv\MinGW\msys\1.0\msys.bat**

    #assuming devenv at D:\devenv
    export PATH="/D/devenv/MinGW/bin:/D/devenv/MinGW/msys/1.0/bin:/D/devenv/Python38-32:/D/devenv/cmake-3.17.0-rc1-win64-x64/bin"
    mkdir gdb_export
    cd gdb-9.1
    mkdir build
    cd build
    ../configure --prefix=/home/user/gdb_export
    make -j4
    make install

Copy the contents of **gdb_export** folder into **devenv\gdb-9.1**

### Pretty-Print for GDB

Download and Install subversion from [https://tortoisesvn.net/downloads.html](https://tortoisesvn.net/downloads.html)

Checkout related packages to enable pretty printing in GDB

    cd D:\devenv\gdb-9.1
    svn co https://gcc.gnu.org/svn/gcc/trunk/libstdc++-v3/python

Create a file inside **devenv/gdb-9.1** folder named as **.gdbinit** (It can be done through NotePad++)

Open **.gdbinit** file and copy the following contents

    python
    import sys, os
    sys.path.insert(0, os.getenv('GDB_LOC') + '\\python')
    from libstdcxx.v6.printers import register_libstdcxx_printers
    register_libstdcxx_printers (None)
    end
    set print pretty on
    set print object on
    set print static-members on
    set print vtbl on
    set print demangle on
    set demangle-style gnu-v3
    set print sevenbit-strings off

`os.getenv('GDB_LOC')` gets **GDB_LOC** environment variable which we will set before opening eclipse, thus it will be able to fetch the GDB location

### JDK

Download **Windows x64 Compressed Archive** from [https://www.oracle.com/java/technologies/javase-jdk13-downloads.html](https://www.oracle.com/java/technologies/javase-jdk13-downloads.html)

Extract downloaded compressed jdk into **devenv/jdk-x.x.x** folder.

### Boost

RenderCallout NYI

Download latest compressed source file from under [https://dl.bintray.com/boostorg/release](https://dl.bintray.com/boostorg/release)

Extract downlodad compressed file into some temp location (Will be compiled)

Open **cmd.exe**

    #Clear the PATH variable
    set PATH=
    set PATH=D:\devenv\jdk-13.0.2;D:\devenv\MinGW\bin;D:\devenv\MinGW\msys\1.0\bin;D:\devenv\Python38-32;D:\devenv\cmake-3.17.0-rc1-win64-x64;%SYSTEMROOT%;%SYSTEMROOT%\system32
    cd into your temp source location
    bootstrap.bat gcc
    b2 install --prefix="D:\devenv\boost_1_72_0"