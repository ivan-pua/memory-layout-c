# Memory Layout of a C Program

In practical words, when we run any C-program, its executable image is loaded into RAM of computer in an organized manner.

This memory layout is organized in following fashion :-

![Image of Yaktocat](https://he-s3.s3.amazonaws.com/media/uploads/383f472.png)

1. Text or Code Segment :-

Text segment contains machine code of the compiled program. Usually, the text segment is sharable so that only a single copy needs to be in memory for frequently executed programs, such as text editors, the C compiler, the shells, and so on. The text segment of an executable object file is often read-only segment that prevents a program from being accidentally modified.

2. Initialized Data Segment :-

Initialized data stores all `global`, `static`, `constant`, and external variables (declared with `extern` keyword) that are initialized beforehand. Data segment is not read-only, since the values of the variables can be altered at run time.

This segment can be further classified into initialized read-only area and initialized read-write area.

```
#include <stdio.h>

char c[]="rishabh tripathi";     /*  global variable stored in Initialized Data Segment in read-write area*/
const char s[]="HackerEarth";    /* global variable stored in Initialized Data Segment in read-only area*/

int main()
{
    static int i=11;          /* static variable stored in Initialized Data Segment*/
    return 0;
}
```

3. Uninitialized Data Segment (bss) :-

Data in this segment is initialized to arithmetic 0 before the program starts executing. Uninitialized data starts at the end of the data segment and contains all `global` variables and `static` variables that are initialized to 0 or do not have explicit initialization in source code.

```
#include <stdio.h>

char c;               /* Uninitialized variable stored in bss*/

int main()
{
    static int i;     /* Uninitialized static variable stored in bss */
    return 0;
}
```

4. Heap :-

Heap is the segment where dynamic memory allocation usually takes place. When some more memory need to be allocated using `malloc` and `calloc` function, heap grows upward. The Heap area is shared by all shared libraries and dynamically loaded modules in a process.

```
#include <stdio.h>
int main()
{
    char *p=(char*)malloc(sizeof(char));    /* memory allocating in heap segment */
    return 0;
}
```

5. Stack :-

Stack segment is used to store all local variables and is used for passing arguments to the functions along with the return address of the instruction which is to be executed after the function call is over. Local variables have a scope to the block which they are defined in, they are created when control enters into the block. All recursive function calls are added to stack.

The stack and heap are traditionally located at opposite ends of the process's virtual address space.
