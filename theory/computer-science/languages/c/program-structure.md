# Program structure

A typical program in [C language](https://www.tutorialspoint.com/cprogramming/index.htm) has certain mandatory sections and a few optional sections, depending on the program's logic, complexity, and readability. Normally a C program starts with one or more [preprocessor directives](https://www.tutorialspoint.com/cprogramming/c\_preprocessors.htm) (#include statements) and must have a [main() function](https://www.tutorialspoint.com/cprogramming/c\_main\_function.htm) that serves as the entry point of the program. In addition, there may be global declarations of [variables](https://www.tutorialspoint.com/cprogramming/c\_variables.htm) and [functions](https://www.tutorialspoint.com/cprogramming/c\_functions.htm), macros, other user-defined functions, etc.

### The Preprocessor Section

The [C compiler](https://www.tutorialspoint.com/compile\_c\_online.php) comes with several library files, having ".h" as an extension. A ".h" file (called a "header file") consists of one or more predefined functions (also called "library functions") to be used in the C program.

The library functions must be loaded in any C program. The "#include" statement is used to include a header file. It is a "preprocessor directive".

For example, [printf()](https://www.tutorialspoint.com/c\_standard\_library/c\_function\_printf.htm) and [scanf()](https://www.tutorialspoint.com/c\_standard\_library/c\_function\_scanf.htm) functions are needed to perform console [I/O operations](https://www.tutorialspoint.com/cprogramming/c\_input\_output.htm). They are defined in the [stdio.h file](https://www.tutorialspoint.com/c\_standard\_library/stdio\_h.htm). Hence, you invariably find #include \<stdio.h> statement at the top of any C program. Other important and frequently used header files include [string.h](https://www.tutorialspoint.com/c\_standard\_library/string\_h.htm), [math.h](https://www.tutorialspoint.com/c\_standard\_library/math\_h.htm), [stdlib.h](https://www.tutorialspoint.com/c\_standard\_library/stdlib\_h.htm), etc.

There are other preprocessor directives such as #define which is used to define constants and macros and #ifdef for conditional definitions.

The following statement defines a constant PI −

```
#define PI 3.14159
#define AREA(r) (PI*r*r)
```

You can also define a macro with the "#define" directive. It is similar to a function in C. We can pass one or more arguments to the macro name and perform the actions in the code segment.

### The main() Function

A C program is a collection of one or more functions. There are two types of functions in a C program: library functions and user-defined functions.

There must be at least one user-defined function in a C program, whose name must be main(). The main() function serves as the entry point of the program. When the program is run, the compiler looks for the main() function.

### The Global Declaration Section

This section consists of declaration of variables to be used across all the functions in a program. Forward declarations of user-defined functions defined later in the program as well as user-defined data types are also present in the global section.

Example of global variable declaration −

```
int total = 0;
float average = 0.0;
```

### Subroutines in a C Program

There may be more than one user-defined functions in a C program. Programming best practices require that the programming logic be broken down to independent and reusable functions in a structured manner.

Depending on the requirements, a C program may have one or more user-defined functions, which may be called from the main() function or any other user-defined function as well.

```
float area(float height, float width);
```

### Comments in a C Program

Apart from the programming elements of a C program such as variables, [structures](https://www.tutorialspoint.com/cprogramming/c\_structures.htm), [loops](https://www.tutorialspoint.com/cprogramming/c\_loops.htm), functions, etc., the code may have a certain text inside "/\* .. \*/" recognized as [comments](https://www.tutorialspoint.com/cprogramming/c\_comments.htm). Such comments are ignored by the compiler.

Inserting comments in the code often proves to be helpful in documenting the program, and in understanding as well as debugging the programming logic and errors.

If the /\* symbol doesn’t have a matching \*/ symbol, the compiler reports an error: "Unterminated comment".

A text between /\* and \*/ is called as C-style comment, and is used to insert multi-line comments.



