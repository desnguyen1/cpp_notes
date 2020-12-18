YT: https://www.youtube.com/watch?v=3tIqpEmWMLI&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=6&t=1s

# How Compilers Work

**Def**: A compiler translates the source code that is writting in a high-level language, e.g., c++, into a machine-language instructions that the CPU understands

This will ouput an **object file** where it will does all the things below:

**Abstract Syntax Tree**: a tree representation of the structure of the source code where each node of the tree denotes a construct occurring in the source code

> * Tree is abstract so it doesnt represent every detail but instead its structural or content-related details, e.g., grouping parentheses do not need to be represented while a loop would be
> * AST is created during compiling 
> * ![img](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c7/Abstract_syntax_tree_for_Euclidean_algorithm.svg/400px-Abstract_syntax_tree_for_Euclidean_algorithm.svg.png)

Machine Code will be created from this AST where the CPU will execute



## In-Depth

After compiling our program we should see in the 'debug' folder a `.obj` file for each c++ file which is the object file

* If each file is seperate, and not included (doesnt have `#include "header.h"`) in other c++ files, each file will turn into a translation unit -> turn into a `.obj` file

	

During preprocessing stage, compiler will go through each preprocessing statements like `#include` or `pragma` statements

```cpp
//inside a file called 'endBrace.h' 
}

//inside a file called 'math.cpp'
int multiply(int a, int b){
    return a*b;
}
```

Equivically we can do:

```cpp
int multiply(int a, int b){
	return a*b;
#include "endBrace.h"
```

This will work as well. 



NOTE: Really, the `.cpp` is a translation file

### Properties Settings

Right click on project -> c/c++ -> preprocessor -> preprocess to a file -> 'yes'

This will create a `.i` file when compiled

> this will show an in depth view of preprocessor statements



## Change to Assembly code

go to YT video at 12:00



## Building vs Compiling

Building will get all the files and linkers and put it into an executable while Compiling will turn the code into machine code