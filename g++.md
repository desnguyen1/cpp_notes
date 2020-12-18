# Compiling Multiple C++ Files

Inside terminal in the file directory:

```cpp
g++ main.cpp other.cpp file.cpp
```

this will compile it in individually.

Or we can do either:

```cpp
g++ *.cpp
```

or to be more specific:

```cpp
g++ *.cpp -o output
```

where `ouput` is the name of the ouput specified by `-o`. Without `-o` the default is `a.out`

To run the program, make sure you're in the file directory and run the `output` 

```cpp
//if output is specified
./output
//if by default
./a.out
```



For reference: https://stackoverflow.com/questions/3202136/using-g-to-compile-multiple-cpp-and-h-files