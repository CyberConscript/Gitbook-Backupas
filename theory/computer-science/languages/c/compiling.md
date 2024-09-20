# Compiling

Next, we need to compile and build the executable from the source code ("hello.c").

If you are using Windows, open the command prompt in the folder in which "hello.c" has been saved. The following command compiles the source code −

```
gcc -c hello.c -o hello.o
```

The -c option specifies the source code file to be compiled. This will result in an object file with the name hello.o if the C program doesn’t have any errors. If it contains errors, they will be displayed.

To build an executable from the compiled object file, use the following command −

```
gcc  -o hello.exe hello.o
```

The hello.exe is now ready to be run from the command prompt that displays the Hello World message in the terminal.



On Ubuntu Linux, the object file is first given executable permission before running it by prefixing "./" to it.

```
$ chmod a+x a.o
$ ./a.o
```

You can also use an IDE such as CodeBlocks to enter the code, edit, debug and run the Hello World program more conveniently.





### Compiling a C Program

A sequence of binary instructions consisting of 1 and 0 bits is called as machine code. High-level programming languages such as C, C++, Java, etc. consist of keywords that are closer to human languages such as English. Hence, a program written in C (or any other high-level language) needs to be converted to its equivalent machine code. This process is called compilation.

Note that the machine code is specific to the hardware architecture and the operating system. In other words, the machine code of a certain C program compiled on a computer with Windows OS will not be compatible with another computer using Linux OS. Hence, we must use the compiler suitable for the target OS.

![Compilation](https://www.tutorialspoint.com/cprogramming/images/compilation.jpg)

### C Compilation Process Steps

In this tutorial, we will be using the gcc (which stands for GNU Compiler Collection). The GNU project is a free-software project by Richard Stallman that allows developers to have access to powerful tools for free.

The gcc compiler supports various programming languages, including C. In order to use it, we should install its version compatible with the target computer.

The compilation process has four different steps −

* Preprocessing
* Compiling
* Assembling
* Linking

The following diagram illustrates the compilation process.

![Compilation Process](https://www.tutorialspoint.com/cprogramming/images/compilation-process.jpg)
