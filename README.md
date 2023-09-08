# Assignment 3: Basics of Compilation

One of the most essential tools for software development is a compiler. Without a compiler, we
cannot generate an executable from our source code. In this assignment and next, you will learn
various aspects of a compiler and practice them.

Similar to the tutorials that you have done earlier, this assignment consists of reading and
practicing. For the reading part, you need to study it like reading a textbook. It is not a
description of the assignment but a task itself. Make sure you understand what is there before you
proceed.

## Task 0: Understanding the Compilation Steps

(This is a reading task. Make sure you read and understand this before you proceed.)

Conventionally, when we say we "compile" C code, we understand it to mean generating executables
from source files. However, strictly speaking, this is *not* correct because there are multiple
steps involved and compilation is one of the steps. The actual steps are, *preprocessing*,
*compiling*, and *linking*. Well-known compilers for C/C++, such as GCC and Clang, hide these steps
and generate executables directly from source files. However, internally they go through these
steps.

* Preprocessing: This is the first step of generating an executable and the *preprocessor* looks at
  the source code and transforms it for compilation. Generally, this involves two things. First, it
  removes all comments (`/* */`, `//`, etc.) as those are not going to be compiled. Second, it
  processes all *preprocessing directives*, which are the statements that start with `#` in C (e.g.,
  `#include`, `#define`, etc.). The preprocessor looks at these and transforms them appropriately
  according to their purposes. An example would be `#include <stdio.h>`, where the preprocessor
  replaces the statement with the content of a file named `<stdio.h>`. Another example would be
  `#define NUM 10`, where the preprocessor replaces all occurrences of `NUM` with `10` in the code.
* Compiling: Once preprocessing is done, the *compiler* transforms C code into machine code. This is
  done by reading each and every source file (a `.c` file) and transforming the code in it into
  machine-specific instructions. These machine-specific instructions are what a CPU can directly
  execute. The compiler stores these instructions in an *object* file that typically has the
  extension of `.o`. For each `.c` (source) file, the compiler generates a corresponding `.o`
  (object) file. Often times, there are multiple `.c` files in the source and the compiler generates
  multiple `.o` files. We note that there can be other intermediate steps involved such as the
  assembly step, which we do not discuss here. We also note that `.o` files contain more than just
  machine-specific instructions, which again we do not discuss here.
* Linking: This is the final step of generating an executable. In the most basic form, the *linker*
  takes all `.o` files and combines them to generate a single executable.

## Task 1: Using the Compiler

In this task, you will create some `.c` files and compile them. For grading, you need to use
`record` to record what you do.

One thing to note before we proceed is that we have installed a linter and a formatter for
C/C++---[Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/index.html) and
[ClangFormat](https://clang.llvm.org/docs/ClangFormat.html). As you write your C code, you will
notice that our Neovim will provide error messages and suggestions, and also fix the code style. As
mentioned before, these are very common programming tools and we highly encourage you to use these
tools for all your programming tasks, regardless of the language and the editor you use. These tools
teach you how to write clean and reliable code with best practices.

Now, here is the list of things you need to do for this task.

* First, make sure you're recording (using `record`, which will record what you do to in a directory
  named `.record`). Make sure you see `[recording]` in your prompt.
* Create a file named `test.c` that prints out `Hello World!`.
* Enter `clang test.c` and see what it generates. [Clang](https://clang.llvm.org/) is a C/C++
  compiler that we use in this course (an alternative would be [GCC](https://gcc.gnu.org/), which we
  don't use). Execute the generated file and check if it prints out `Hello World!`. (If you are not
  sure about how to run an executable in the current directory, go back to the Linux Tutorial and
  look it up.) The file you see is the default name of the file that Clang or GCC generates.
* Enter `clang -o test test.c`. This generates `test` as the name of the executable, i.e., you can
  provide the name of the executable that you want to generate with the `-o` flag. Run the
  executable and check if it prints out `Hello World!`.
* Create two files, one named `main.c` and the other named `other.c`. In `other.c`, write a function
  that prints out `Other invoked`. In `main.c`, write a main function that calls the function in
  `other.c`. You can create a header file, if you so choose.
* Enter `clang main.c other.c` which generates an executable with the default name. Run it and check
  if it prints out `Other invoked`.
* Enter a command that will generate an executable named `main`. Once generated, run it and check if
  it prints out `Other invoked`.
* Now, when you run `clang main.c other.c`, Clang conveniently combines all the compile steps
  described earlier and generates an executable. However, we can run each step separately.
* Enter `clang -E main.c`. This runs only the preprocessor on `main.c`. Check the output to see how
  it looks like. It should have expanded your source code significantly with the header files and
  macros all replaced and included. You can also try `clang -E other.c`.
* Enter `clang -c main.c`. This runs both the preprocessor and the compiler to generate an object
  file (`.o`) from `main.c`. List the files in the current directory to see what it generates.
* Enter a command that will generate an object file from `other.c`.
* Enter `clang main.o other.o`. This runs the linker that combines both object files to generate an
  executable with the default name. Run the executable and check the output.
* Enter a command that will run the linker that combines `main.o` and `other.o` to generate an
  executable named `main.1`. Run the executable and check the output.
* After you're done with the above, enter `exit` to stop recording. As you know already, you can
  later come back and enter `record` to start recording again.
* Once you're done, push all the files/directories you created, including `.record/` and `.nvim/`,
  for grading.

# Next Steps

You need to accept the invite for the next assignment (A4).

* Go to this URL: [https://classroom.github.com/a/PGPiPLGw](https://classroom.github.com/a/PGPiPLGw)
* Accept the invite for Assignment 4 (A4).
* If you are not in `units/02-tools` directory, go to that directory.
* Clone the assignment repo.
