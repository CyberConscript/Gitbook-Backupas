# C - Environment Setup

### The C Compiler

The source code written in the source file is the human readable source for your program. It needs to be "compiled", into machine language so that your CPU can actually execute the program as per the instructions given.

There are many C compilers available. Following is a select list of C compilers that are widely used −

GNU Compiler Collection (GCC) − GCC is a popular open-source C compiler. It is available for a wide range of platforms including Windows, macOS, and Linux. GCC is known for its wide range of features and support for a variety of C standards.

Clang: Clang is an open-source C compiler that is part of the LLVM project. It is available for a variety of platforms including Windows, macOS, and Linux. Clang is known for its speed and optimization capabilities.

Microsoft Visual C++ − Microsoft Visual C++ is a proprietary C compiler that is developed by Microsoft. It is available for Windows only. Visual C++ is known for its integration with the Microsoft Visual Studio development environment.

Turbo C − Turbo C is a discontinued C compiler that was developed by Borland. It was popular in the early 1990s, but it is no longer widely used.

The examples in this tutorial are compiled on the GCC compiler. The most frequently used and free available compiler is the GNU C/C++ compiler. The following section explains how to install GNU C/C++ compiler on various operating systems. We keep mentioning C/C++ together because GNU gcc compiler works for both C and [C++ programming languages](https://www.tutorialspoint.com/cplusplus/index.htm).



### Installation on UNIX/Linux

If you are using Linux or UNIX, then check whether GCC is installed on your system by entering the following command from the command line −

```
$ gcc -v
```

If you have GNU compiler installed on your Ubuntu Linux machine, then it should print a message as follows −

```
$ gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/11/lto-wrapper
OFFLOAD_TARGET_NAMES=nvptx-none:amdgcn-amdhsa
OFFLOAD_TARGET_DEFAULT=1
Target: x86_64-linux-gnu
Configured with: ../src/configure -v . . .
Thread model: posix
Supported LTO compression algorithms: zlib zstd
gcc version 11.3.0 (Ubuntu 11.3.0-1ubuntu1~22.04)
```

If GCC is not installed, then you will have to install it yourself using the detailed instructions available at [https://gcc.gnu.org/install/](https://gcc.gnu.org/install/)

[Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.](https://www.tutorialspoint.com/latest/courses?utm\_source=tutorialspoint\&utm\_medium=tutorials\_3p\&utm\_campaign=internal)

### Installation on Mac OS

If you use Mac OS X, the easiest way to obtain GCC is to download the Xcode development environment from Apple's web site and follow the simple installation instructions. Once you have Xcode setup, you will be able to use GNU compiler for C/C++.

Xcode is currently available at developer.apple.com/technologies/tools/

### Installation on Windows

To install GCC on Windows, you need to install MinGW. To install MinGW, go to the MinGW downloads page, [https://www.mingw-w64.org/downloads/](https://www.mingw-w64.org/downloads/), and follow the link to the MinGW download page. Download the latest version of the MinGW installation program, mingw-w64-install.exe from here.

While installing Min GW, at a minimum, you must install gcc-core, gcc-g++, binutils, and the MinGW runtime, but you may wish to install more.

Add the bin subdirectory of your MinGW installation to your PATH environment variable, so that you can specify these tools on the command line by their simple names.

After the installation is complete, you will be able to run gcc, g++, ar, ranlib, dlltool, and several other GNU tools from the Windows command line.

### Text Editor

You will need a Text Editor to type your program. Examples include Windows Notepad, OS Edit command, Brief, Epsilon, EMACS, and vim or vi.

The name and version of the text editors can vary on different operating systems. For example, Notepad will be used on Windows, and vim or vi can be used on windows as well as on Linux or UNIX.

The files you create with your editor are called the source files and they contain the program source codes. The source files for C programs are typically named with the extension ".c".

Before starting your programming, make sure you have one text editor in place and you have enough experience to write a computer program, save it in a file, compile it and finally execute it.

### Using an IDE

Using a general-purpose text editor such as Notepad or vi for program development can be very tedious. You need to enter and save the program with ".c" extension (say "hello.c"), and then compile it with the following command −

```
gcc -c hello.c -o hello.o
gcc -o hello.exe hello.o
```

The executable file is then run from the command prompt to obtain the output. However, if the source code contains errors, the compilation will not be successful. Hence we need to repeatedly switch between the editor program and command terminal. To avoid this tedious process, we should an IDE (Integrated Development Environment).

There are many IDEs available for writing, editing, debugging and executing C programs. Examples are CodeBlocks, NetBeans, VSCode, etc.

CodeBlocks is a popular open-source IDE for C and C++. It is available for installation on various operating system platforms like Windows, Linux, MacOS.

For Windows, download codeblocks-20.03mingw-setup.exe from [https://www.codeblocks.org/downloads/binaries/](https://www.codeblocks.org/downloads/binaries/) URL. This will install CodeBlocks as well as MinGW compiler on your computer. During the installation process, choose MinGW as the compiler to use.





