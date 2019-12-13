# Memory Layout of a C Program

In practical words, when we run any C-program, its executable image is loaded into RAM of computer in an organized manner.

This memory layout is organized in following fashion :-

![Image of Yaktocat](https://he-s3.s3.amazonaws.com/media/uploads/383f472.png)

1. Text or Code Segment :-

Text segment contains machine code of the compiled program. Usually, the text segment is sharable so that only a single copy needs to be in memory for frequently executed programs, such as text editors, the C compiler, the shells, and so on. The text segment of an executable object file is often read-only segment that prevents a program from being accidentally modified.

2. Initialized Data Segment :-

Initialized data stores all '<global>', '<static>', '<constant>', and external variables (declared with '<extern>' keyword) that are initialized beforehand. Data segment is not read-only, since the values of the variables can be altered at run time.

This segment can be further classified into initialized read-only area and initialized read-write area.
