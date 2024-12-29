# A tour of computer systems 
## 1.1 information is Bits
A simple hello world program is at the end of the day series of bits organized into bytes which the computer can understand. In the case of the hello world program the individual characters are translated into ascii characters. How the OS and the compilers will run such program is beyond this section but it is important to understand that you programs are not some hovering abstraction detached of your computers.

## 1.2 Programs are Translated by other programs into different from's
You simple hello.c file needs to be converted into something you os can run via the compiler. The compiler is a program that can do just that, the steps of which are the following.

1. preprocessor
    - This part is where you program reads the original source file and looks for place like the `#include <stdio.h>` the proceeds to include stdio header file into your source code. The output of this is: `hello.i`
2. compiler 
    - the compiler the takes this preprocessed file then changes it into an assembly file which the assembler can your can convert into machine instructions. The output of this is: `hello.s`
3. Assembler
    - The assembler takes you assembly file then turns into machine code then packages in to a form known as **relocatable object program** and stores the result in `hello.o` which is a binary file that is executable.
4. Linker
    - The linker takes your `hello.o` file then calls other linked library files like print that you may have included in you source code. Basically handles the merging various relocatable object programs that call on each other.


## 1.3 It pays to understand how compilation systems work

Often times compiler produce good code that runs efficiently but sometimes your code may run slower than you would like and a knowledge of how compilers work would server you well. 
- Are if statements faster than switches
- why are local variables faster the argument variables to a function
- why are some sequence of operations faster than others 
Are examples of some question that would be impossible to answer fully without knowledge of how compilers work.
other problems are linking errors and avoiding security holes like buffer overflow.