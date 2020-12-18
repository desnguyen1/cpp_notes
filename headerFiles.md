YT: https://www.youtube.com/watch?v=9RJTQmK0YPI&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=10

# Header Files

C++ has header files which are seperate from `.cpp` files. `.cpp` files are translation units, what the CPU uses to translate machine code into something the computer can understand.

**Header Files** will contain classes, structs, or function declarations for function definitions that are in seperate `.cpp` files

* This tells our code that the function exists and where its definition is stored
* Also by using header files, we do not need to declare the function before using it every time
* Essentially, it copies and paste the functions we have in the corresponding `.cpp` file into the file where we have included our header

Ideally, our header files should be the same name of our `.cpp` file and in our `main.cpp` we need to add `#include "fileheader.h"`

## Header Guards

These are conditional compilation directives that will prevent accidental duplicate header calls (because it acts as a copy and paste function)

### #pragma once

\# : represents a preprocessor command that means that this will be evaluated by c++ preprocessor before it gets compiled

pragma : instruction that is sent to the compiler or to the processor

pragma once : means to only include the header file once, essentially, only include the header file once in each translation unit (each `.cpp` file)

Much cleaner compared to next one

### ifndef and define

```cpp
#ifndef headerFile
#define headerFile

//fucntion declarations
//classes declaration
//structs declaration

#endif
```



**NOTE**: very useful when we have multiple `.cpp` files that all include the same header and we try to 'copy and paste' into each other. 

(ex at 9:00 on YT video)



## Using #include "" or #include <>

Use " ": when we need to go to a different directory for the file (for everything)

Use <>: when the file is in the same directory (for compiling files in local paths)