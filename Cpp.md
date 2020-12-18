

# C++

Simple c++ code:

```cpp
#include <iostream> //includes cin and cout
using namespace std; //standard namespace
int main(){
    cout<<"Hello World";
    return 0;
}
```

`#include <iostream>` 

> Include is a directory that allows the iostream library to become available to use. Contains the routines that handles input and output (cin, cout)

`using namespace std` 

> "names defined in iostream are to be interepreted in the standard (std) way"
>
> Essentially, the names that are used will have the meaning defined for them in the std namespace 

## User Input and Output

```cpp
std::cout<<"Enter your name: ";
std::cin>>name;
std::cout<<"Hello Agent "<<name;
```



## Data Types and Variables

* Character - char

	* uses single ' ' quotes

* String - string

  * uses double " " quotes
  * must use `using namespace std` or `std::string` 
  * will read until it hits whitespace characters
  * stores each character in a string in an arra
  * `.length()` will print out length of string
  * `.find()` to find info about the string

* Long - long

	* like an int
	* use when you need a type that takes a lot of bits

* Integer - int

	* use when we need a type that is fast and only take a few bits

* Float - float

	* Supports `e` notation, e.g., 2.36 e 2 = 2.36 x 10² 
	* float allows decimal point to float to a new position

* Double - double
	
	* Can store more decimal points than a float
	
* Boolean - bool

	* returns `True`(nonzero value)  or `False` (0)

		```c++
		bool time = 36; //sets time to True
		std::cout<<time; //prints out True
		time = !time; //becomes False
		```

		

### Constant Data Type

Syntax: const typeName varName = value

Keeps a value constant and cannot be changed

```c++
const pi = 3.14; //or
const pi(3.14);
```

#### Global_Const

Global constant that has global scope; typically placed outside of the main function

```cpp
GLOBAL_CONST = 1.0;
```



### Number of Decimal Points

```cpp
//for two decimal places
cout.setf(ios::fixed); 
cout.setf(ios::showpoint); //sets flag so it will show decimal point
cout.precision(2);
```

setf: set flags; flag is an instruction to do something in one of two possible ways

> `setf(ios::fixed)`: all floating point numbers that are output to that stream will be written normally rather in `e`notation (6.27e2)
>
> `Setf(ios::scientific)`: will set floating point numbers to e-notation
>
> `Setf(ios::showpoint)`: a decimal point and trailing zeros will always be show for floating numbers, otherwise a decimal point might not be show (6.00 vs 6)
>
> `Setf(ios::right)`: it is already set so if we don’t want this feature then we must disable the flag (by enabling ios::left); basically prints things on the right and to the set width
>
> `Sef(ios::left)`: the next item will be printed to the LEFT of the previous value at the set width that user specifies
>
> Width is set by `cout.width(#);` before printing value
>
> `Setf(ios::showpos)`: shows plus signs in front of positive integers
>
> To unset a flag we do: `cout.unsetf(ios::…);`

Another way of using `precision()`

> Manipulator: a function that is called in an untraditional way
>
> Must `#include <iomanip>`
>
> ```cpp
> cout.setf(ios::fixed);
> cout.setf(ios::showpoint);
> cout<<"$"<<setprecision(2)<<10.3<<endl;
> ```

### Declaring a Variable

Syntax: typeName varName = value or 

typeName varName (value)

```cpp
int value = 5;
int sameValue(5);
float valueTwo = 3.5;
char charVal = 'c';
string sVal = "string";

```

## TypeCasting

Converts one type to another, e.g., turning an int to a double

Syntax: static_cast<type>(expression)

```cpp
int num = 2;
total = static_cast<double>(num) / 3;
//turns num to a double
```

### Automatic Type Conversion

If a function requires an argument of type double and it has been assigned as an integer, then c++ will automatically convert the int to a type double

## Operators

* +
* -
* *
* /
* %

## Escape Sequence

* New line \n

* Horizontal tab \t

* Alert \a

* Backslash \\ 

*  Double quote \”

* Raw string literal
	* If there are too many escape characters used then we can use ‘R’ followed by quotes
	* Ex: cout << R”(c:\files\)”;

## Scope and Block

A **block** is code that is enclosed in { }

**Scope** of a variable is within the block if it only has local scope

> For global scope, declare variable outside of main where function prototypes are

Note: this applies to #include directives and using namespace std as well

```cpp
void printMenu(){
    using namespace std; //only has scope within the function
    cout<<"Print";
}
```



## ++var vs var++

++var will first increment then use the incremented value

var++ will use the value then increment

```cpp
int num = 2;
value = 2 * (num++); //2 * 2 = 4 then num increments to 3
```

```c++
int num = 2;
value = 2 * (++num); //2 * 3 = 6
```

--var and var-- works the same way

## cmath Library

`#include <cmath>` must also `#include <cstdlib>` 

Must use `using namespace std` or `std::` 

Some functions of cmath: 

* `pow(2, 5)` -> 2^5^ 
* `sqrt(36)` -> √36
* `round(4.3)` -> rounds the number 
* `ceil(4.1)` -> rounds number up
* `floor(4.8)` -> rounds number down
* `fmax(3, 10)` -> returns bigger number (10)
* `fmin(3,10)` -> returns smallest number (3)

### Pseudorandom

Number that appears ot be random but is actually determined by a predictable formula

```cpp
srand(35) //where 35 is initial seed value
```

```cpp
#include <ctime>
srand(time(0));
//uses the initial seed value of time where it returns the number of seconds that have elapsed
```

`RAND_MAX` is a constant defined in <cstdlib> 

Ex: for a random side on a six sided die

```cpp
int die = (rand()%6) + 1;
```

> `rand() % 6` will return a number between 0 and 5, therefore the + 1 will return a number between 1 and 6

## Functions

Syntax: `returnType funcName(parameters)`

If returnType != void then when calling the function, we must store it in a variable

```cpp
int addNum(int a, int b){
    return a+b;
}
int main(){
    int sum, num1, num2;
    sum = addNum(num1, num2);
    return 0;
}
```

### Parameters and Arguments

Formal parameters: blank placeholders that will be filled with something when function is called

Argument: will fill the parameters and is used in function calls

### Function Declaration/Prototype

Equivalent to declaring a variable, we must declare a function before usage; typically declared near the top 

```cpp
void printMenu(); #function declaration
```

### Overloading a Funciton Name

Overloading occurs when there are two functions with the same name

```cpp
int funcName(int var, double anotherVar);
int funcName(double test, double end);
```

When calling the function, the compiler will check the number of arguments then the types of arguments in the function call. This will determine what function to use

```cpp
double var1, var2;
int total;
total = funcName(var1, var2);
//will use the second function because both var1 and var2 are doubles
```

**CANNOT** overload a funciton by giving two definitions that differ the return type

```cpp
//DONT DO THIS
int funcName(int start, int end);
double funcName(int start, int end);
```

### Void Functions

Doesnt contain a return statement

Syntax: void funcName(parameters);

If a void function contains a `return` statement then it will terminate the function call

```cpp
void divide(int a, int b){
    int ans;
    if(b == 0)
        return; //cannot divide by 0
    else
        ans = a/b;
}
```

### Call-by-Reference and Call-by-Value

In a **call-by-value**, the function will take the value of the variable but doesnt have the power to change the variable itself

```cpp
void changeNum(int a){
    a += 1; //attempts to change the parameter
}
int main(){
    int num = 0;
    changeNum(num);
    std::cout<<num; //will print out 0
}
```

In **call-by-reference** the value can be changed by the function by accessing the memory location of the variable and altering it

Syntax: returnType funcName(int& first, int& second);

```cpp
void changeNum(int& a){
    a += 1; //attempts to change the parameter
}
int main(){
    int num = 0;
    changeNum(num);
    std::cout<<num; //will print out 1
}
```

Essentially, the function will go to the memory location associated with the variable (hence the &) and manipulates the value at the location

### Default Arguments for Functions

```cpp
void test(int arg1, double arg2 = 5.3);
//call by
test(1); //second argument is already set
```



## Assert Macro

A tool to ensure that the expected conditions are true at the location of the assert statement. If conditions are not met, it will display an error message and abort

Must have `#include <cassert>` 

Syntax: assert(boolExpression);

```cpp
assert(num>0); //will display error if num < 0
```

## Input and Output Files

Must `#include <fstream>` and `using namespace std`

ifstream -> input file

ofstream -> output file

Open a file by using method `.open("fileName.txt")` 

Close a file when finished using method `.close()` 

```cpp
#include <fstream>
int main(){
    //declaring I/O variables
    ifstream instreamVar;
    ofstream outstreamVar;
    //opening
    instreamVar.open("inputFile.txt");
    outstreamVar.ope("outputFile.txt");
    
    //closing files when done
    instreamVar.close();
    outstreamVar.close();
    return 0;
}
```

Reading from a file and storing into a variable by using >> 

Write to a fill by using <<

```cpp
instreamVar >> someVar;
outstreamVar << "Writing to file and adding a variable: "<< someVar;
```

### Appending to a File (ios::app)

Must have `#include <iostream>` , `using namespace std`, and `#include <fstream>`  to be able to use the appending feature `(ios::app)` 

If the file that is specified already exists then the preexisting contents will be deleted. Appending will avoid deletion. 

If the file doesnt exist then it will create an empty file with that name to receive the output

```cpp
ofstream outstream;
outsream.open("important.txt", ios::app);
```

This will either create a file named 'important.txt' and add the contents (if it doesnt exist yet) or append the contents to the end of a file named 'important.txt'

### Letting User Choose what File to Use

Store the file name into an array of characters 

```cpp
#include <iostream>
#incldue <fstream>
using namespace std;
int main(){
    char filename[16]; //char array
    cout<<"Enter a filename";
    cin>>filename;
    ifstream instreamVar;
    instreamVar.open(filename); //gets the file the user wants to use
    return 0;
}
```

### Fail Function

A boolean expression that can be used to control a loop

If a file does not open or it fails then this returns true

```cpp
if(instreamVar.fail())
    cout<<"Error";
```

### Exit Function

Causes the program to end immediately

Must have `#include <cstdlib>` and `using namespace std` 

Exit(1) is used if there is an error, otherwise exit(0) is used

### Using Streams as Arguments in Functions

Must be used like a call-by-reference

```cpp
void make_neat(ifstream& messyFile, ofstream& neat_file);
```

#### isstream

find stuff

### .next

Similar to `.eof` and checks to see if there is more values

```cpp
ifstream in_stream;
while(instream >> next){
    //do this
}
```

General rule: use this when processing numeric data

### .eof Member Function

End of file: tells the user when they have reach the end of the file

Can be used as a boolean expression, e.g., 

```cpp
ifstream fin;
while(!fin.eof()){
    //as long as it is not the end of file
    //do this
}
```

There is a special end of file marker that eof will detect

> Note: do not write out the marker again because it may cause errors

General Rule: use this when processing input as text and reading the input with the `get` member function

### Get and Put

Both must have `using namespace std`

**get** allows the program to read in one character of input and store it in a variable of type char

> syntax: input_stream.get(char_variable);
>
> takes in an argument of type char
>
> ```cpp
> //this will read in the next input character from the keyboard and stores it in the variable next_symbol
> char next_symbol;
> cin.get(next_symbol);
> ```
>
> This doesnt skip over blanks or new lines therefore, it will even store '\n' in the variable; this is the main difference between `cin` and `get`
>
> Can use this function to detect a new line
>
> ```cpp
> cin.get(next_symbol);
> while(next_symbol != '\n'){
>     //do this
> }
> ```

**put** the value of its argument becomes the output to the output stream

> syntax: output_stream.put(char_expression);
>
> ```cpp
> cout.put(next_symbol);
> //or
> cout.put('a');
> //or
> out_stream.put('Z');
> ```



### Getline

```cpp
std::string name;
std::cout << "Please, enter your full name: ";
  std::getline (std::cin,name);
```

This will get everything and store it in a string including spaces



### Putback

Puts back a character we dont want or need

```cpp
file.putback(next); //will not include the char next held
```

Mainly for input streams



## cin.get()

This will acces character arrays and includes whitespace.

If we use `cin>>` this will terminate and ignore all whitespace found

```cpp
//lets assume we do not know about strings
char* message;
//get message from user and store it in message
//this example will take up to 50 characters
cin.get(message, 50);

//print message
cout<<message;
```



## cctype Library

`#include <cctype>` 

* `Toupper(char)`: returns uppercase version

* `Tolower(char)`: returns lowercase version

* `Isupper(char)`: will return true if the char is uppercase; otherwise false

* `Islower(char)`: same as above except with lowercase

* `Isalpha(char)`: returns true if the char is a letter of the alphabet

* `Isdigit(char)`: returns true if it is a digit between 0-9

* `Isspace(char)`: returns true if this is a whitespace char like a blank or newline (\n)

## Arrays

Syntax: type arrayName[size];

Initialization:

```cpp
int c[3] = {2, 3, 4};
//or
c[0] = 2;
c[1] = 3;
c[2] = 4;
```

If no initialization is done then the index values will be set to 0; however, it is better to manually set it

#### How Arrays are stored

> When an array is declared, the computer will reserve enought memory to hold the size of the array of that type
>
> The computer doesnt remember the address of each value, instead it will remember the address of the first index and calculate the address of the desired memory from there

### Using Arrays as Parameters and Arguments

Array parameter is a function parameter that is an array, e.g., void func(int a[]);

Array parameters are not exactly call-by-references but will act like one, therefore, any action in a function that an array has been passed to can change the array

Because the function can change the array, to avoid array changes use `const` in the parameters

```cpp
void func(const int a[]);
```

This will keep the array the same and just use the values that it contains

The base type of array that is getting passed to the function must be the same base type of the array parameter

When passing the array, we must also keep in mind to pass a parameter to inform the function about the size of the array passed



## Conditional/Ternary Operator (?:)

Equivalent to an if-else statement

Essentially given `variable = expression1 ? expression2 : expression3`

represents:

```cpp
//if expression1 is true
if(expression1)
    variable = expression2;
else
    variable = expression3;
```



 ## Loops

### For-Loops

Syntax: for(dataType varName : array){

​		//varName is successively set to each element in the array

}

```cpp
int arr = [2, 3, 4, 5, 6];
for(int x:arr)
    cout<<x; //prints arr -> 23456
```

We can even define x as a pass-by-reference using & and then changes to x will be made in the array

Or

A more popular syntax ex:

`for(int i = 0; i<5; i++)`



### While Loops

a conditional loop 

```cpp
while(True){
    //do this
}
```



### Do-While Loop

Similar to a while loop except the loop will run at least once and more if condition is met

```cpp
do{
    //do this
}while(True)
```



### Continue, Break, Return

`continue;` 

> when the loop runs into a continue, it will skip the rest of the loop and go to the next iteration
>
> ```cpp
> for(int i = 0; i<5; i++){
>     if(i % 2 == 0)
>         continue;
>     std::cout<<"\nHello World";
> }
> ```
>
> This will skip all even iterations

`break;`

> this will exit the loop completely 
>
> ```cpp
> for(int i = 0; i<5; i++){
>     if(i % 2 == 0)
>         break;
>     std::cout<<"\nHello World";
> }
> ```
>
> Now, when i is 2, this will exit the loop completely

`return;`

> ```cpp
> for(int i = 0; i<5; i++){
>     if(i % 2 == 0)
>         return 0;
>     std::cout<<"\nHello World";
> }
> ```
>
> will return the value when the condition is met



## Built-In Reverse

There is a built-in reverse function `reverse()`

```cpp
using namespace std;
int main(){
	string str = "random string";
	reverse(str.begin(), str.end());
    return 0;
}
```



## Pointers

def: a pointer is an integer that stores a memory address

if a pointer is given a data type then that translates to "the data at the address is assumed to be this type", it will also tell how much memory should be saved 

**Initialization** 

```cpp
//dont care about data type of pointer
//only want it to hold an address
void* ptr = nullptr; //null pointer
```

```cpp
int var = 8;
//getting memory address of var
void* ptr = &var;
```

**Accessing** (dereferencing)

is essentially changing the value that is at that memory address

```cpp
//dereferencing
int* ptr = &var;
*ptr = 10;
//this will make var = 10 instead of the initial 8
```

**Levels of Pointers**

These pointers also have a place in memory (this allows us to have layers of pointers)

so `int** ptr` is a double pointer that holds an address to another pointer which holds an address to a variable that holds a value

## References

Very similar to pointers, but is considered an **alias** to another variable (another name for a variable)

* not new variables
* do not take place in memory
* has the same memory address as the variable it is referencing to
* can help change the value in the variable it is an alias to, however, we cannot change the variable we are aliasing once it has been assigned

```cpp
int main(){
    int a = 5;
    
    //initializing a reference
    int& ref = a; //now a can be called with either a or ref
}
```



## Pass-by Types (reference, pointer, value)



## Structs

Similar to classes but all its data members and functions are public

```cpp
struct p{
  int x;
  int y;
};

//initialize in main
p var;
var.x = 8;
var.y = 9;
//or
p var = {8, 9};
```



## Classes (OOP)

Note: structs and classes are almost the same, except with classes, we can declare private and public variables (members) and/or methods (functions in a lcass). (regular c does not have classes, only structs)



Also, by default, all members of a class is private unless specified

```cpp
class Player{
  public:
    int x,y;
    int speed;
    void Move(int xa, int ya){
        x += xa * speed;
        y = ya * speed;
    }
};

int main(){
    Player player; //instantiated(created) an object
    //created an object named player of type Player
    
    //getting access
    player.Move(1,1-);
}
```





### Struct vs Class

* structs do not have the option to say if a variable or function is private or public, it is only public
* Class is defaulted at private, but we can control if variables or functions are private or not

**When to use**

> Mostly this is personal preference, but if we want a class with all public variables then we use a struct



### Example

```cpp
class Log{
    
    public: //for variables 
    	const int logLevelError = 0;
        const int logLevelWarning = 1;
        const int logLevelInfo = 2;
    
    private:
    	int m_logLevel = logLevelInfo;//the m_ means it is a priv var
    
    public: //for functions
    	void setLevel(int level){
            m_logLevel = level;
        }
    
         //char* is an alt to string
         void warn(const char* message){
			std::cout<<"[Warning]: "<<message<<std::endl;
         }
};

int main(){
    
    Log log; //instantiate an object (creating an object)
    log.setLevel(1);
    log.Warn("Hello!");
    std::cin.get();
}
```



### Constructor 

This will immediately run when we istantiate (create) and object, essentially, a basic setup function

* we could use it to initialize variables

```cpp
class Entity{
public:
    float X, Y;
    
    //constructor
    Entity(){
        X =0.0f;
        Y=0.0f;
    }
    
    void print(){
        std::cout<<X<<", "<<Y<<std::endl;
    }
    
};

int main(){
    Entity e;
    e.print();
    
}
```

In the above example, we created a constructor which will immediately initialize X and Y to 0.0f. 

By default, there is a constructor but it is empty and looks like this:

```cpp
Entity(){
    
}
```

Now,  lets look at constructor with parameters

```cpp
class Entity{
public:
    float X, Y;
    
    // default constructor
    Entity(){
     
    }
    
   	// constructor with parameters
    Entity(float x, float y){
        X = x;
        Y = y;
    }
    
    void print(){
        std::cout<<X<<", "<<Y<<std::endl;
    }
    
};

int main(){
    Entity e(10.0f, 5.0f);
    e.print();
    
}
```

This will allow us to immediately initialize an object upon creation to certain values

Now lets say we have a class where we do not want the user to use, it is mainly used for keeping code organize, we can do:

```cpp
class Log{
private:
    Log(){};
public:
    static void Write(){
        //something
    }
};
```

This will hide the constructor under a private name so instantiating an object type Log is impossible

OR

```cpp
class Log{
public:
    
    Log() = delete;
    
    static void Write(){
        //something
    }
};
```

Delete the default constructor

### Destructor

Opposite of constructor, so this will run when an object is destroyed and will do any **uninitialization** of variables when object is `deleted` 

```cpp
class Entity{
public:
    float X, Y;
    
    Entity(){ 
        X = 0.0f;
        Y = 0.0f;
        std::cout<<"\nCreated Entity";
    }
    
    //destructor
    ~Entity(){
        std::cout<<"\nDestroyed Entity";
    }
    
    void print(){
        std::cout<<X<<", "<<Y<<std::endl;
    }
    
};

void Function(){
    Entity e; //will print out 'created Entity'
    e.print(); //print out 0.0f, 0.0f
}

int main(){
    Function();
    //after leaving Function, the destructor will be called
    //because it is now outside scope of Entity e
    std::cin.get();
}
```

Why use? when we need to uninitialize or destroy values after destroying the variable, that were created in the constructor. This is done to avoid memory leaks. 

To manually call the destructor (not recommended)

```cpp
e.~Entity();
```



## Inheritance

This allows us to have a heiararchy of classes which relate to each other

(Essentialy, creating  a parent class and then creating children classes from that parent class -> subclasses)

This will help avoid code duplication (def: almost the same thing but maybe new tweaks here and there)

* Make a base class then add subclasses to add new functionality on top of base class

Ex of where inheritance would be helpful

```cpp
class Entity{
public:
    float X,Y;
    
    void Move(float xa, float ya){
        X += xa;
        Y += ya;
    }
};

class Player{
public:
    float X,Y;
    const char* Name;// the only difference between Player and Entity
    
    void Move(float xa, float ya){
        X += xa;
        Y += ya;
    }   
};

int main(){
    
    std::cin.get();
}
```



Same concept as above but uses inheritance

```cpp
class Entity{
public:
    float X,Y;
    
    void Move(float xa, float ya){
        X += xa;
        Y += ya;
    }
};

//inheritance
//Player is now a subclass of Entity
//now Player has all of Entity plus new functionality
class Player : public Entity
{
public:
    const char* Name;
    
    void PrintName(){
        std::cout<<Name<<std::endl;
    }
 
};

int main(){
    Player player;
    //normal
    player.PrintName();
    //inheritance
    player.Move(5,5);
    std::cin.get();
}
```

Essentially, the `Player` type is a superset of `Entity `meaning, it has everything Entity has and more. With this in mind, Player can also have access to all **PUBLIC** functions and variables in `Entity`. `Player` does NOT have access to private members of `Entity`. To give subclasses access to private members, put those members as `protected` and that will give all subclasses access to those members.

Protected vs Public

> public members can be accessed everywhere, even in main
>
> protected members only subclass have access to



### Virtual Functions

This will allow us to override methods in subclasses (inheritance classes)

We need to mark the base function as our virtual function by adding `virtual` and add `override` after function name for the new function that we are trying to override

Ex:

```cpp
class Entity
{
public:
    //virtual function -> base function
    virtual std::string GetName(){ return "Entity";}
};

class Player : public Entity
{
private:
	std::string m_Name;
public:
    //constructor to specify a name
    Player(const std::string& name) : m_Name(name){}
    
    //overriden from base class Entity
    std::string GetName() override { return m_Name;}
};

int main(){
    //creating new entity
   	Entity* e = new Entity();
    //print "Entity"
    std::cout<<e->GetName()<<std::endl;
    
    Player* p = new Player("Cherno");
    //print "Cherno"
    std::cout<<p->GetName()<<std::endl;
    
}
```

Note: we do use additional memory due to the V-table (get more info) and then it takes longer to run because we have to go through V-table to find the right function



### Pure Virtual Functions





## Static

* Two situations: using a static outside a class/struct and using a static inside a class/struct



### Outside the class/struct

This means the static variable will be linked internally inside that translation unit (that .cpp file)

```cpp
//example 1

//defining a static variable
static int s_variable = 5;

//inside another .cpp file
int s_variable = 10;
cout<<s_variable; //this will print 10

//example 2
int s_variable = 5;

//inside another .cpp file
int s_variable = 10;
cout<<s_variable; //will produce an error for having multiple same variables

//to fix this issue we do this

extern s_variable;
cout<<s_variable;//prints out 5

```

The `extern` will tell the compiler to externally link and look for this variable that is located elsewhere

We can think of `static` as a `private` feature where with a static variable, the variable remains local to that .cpp file (translation unit)

```cpp
//example with functions
static void func{
    
}

//inside another .cpp file
void func{
    
}
```

During compilation, this will not produce an error because one func is static. If the `static` keyword was not there then this will cause an error

### Inside a Class/Struct

```cpp
struct ent{
    static x;
    static y;
};

//inside main
//we cant do this
ent e;
e.x = 8;
e.y = 9;
//^^ This will cause errors because struct vars are static so it is only local to ent

//do this
ent::x = 8;
ent::y = 9;
//but this is not assigned to the object 'e'
```

for more info: https://www.youtube.com/watch?v=V-BFlMrBtqQ&list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb&index=22

## The #define

Ex: `#define struct class` will turn all keywords of `struct` into `class`

> essentially, we are saying 'define all our struct keywords as class'



## Enums

Enums = enumeration = a set of a values grouped together

Enums are by default 32 bit integers and MUST be integers

```cpp
enum ex{
    //A=5, B=6, C=7
    A = 5, B, c
        
   	//or we can assign individually
    A = 1, B = 3, C = 9
};
```

```cpp
//Changing the data type of enum
//we can use char, but not float
enum ex : char{
    //values
};
```

Example of usage

```cpp
class Log{
public:
    enum Level{
        //0,1,2
        LevelError = 0, LevelWarning, LevelInfo;
    }
private:
    Level m_LogLevel = LevelInfo;
    
public: 
    void SetLevel(Level level){
        m_LogLevel = level;
    }
    void Error(const char* message){
        if(m_LogLevel >= LevelError)
            std::cout<<"[ERROR]: "<<message<<std::endl;
    }
    void Warn(const char* message){
        if(m_LogLevel >= LevelWarning)
            std::cout<<"[WARNING]: "<<message<<std::endl;
    }
    void Info(const char* message){
        if(m_LogLevel >= LevelInfo)
            std::cout<<"[INFO]: "<<message<<std::endl;
    }
};

int main(){
    Log log;
    log.SetLevel(Log::LevelError); //setting 0
    log.Warn("Hello");
    log.Error("Hello");
    log.Info("Hello");
    std::cin.get();
}
```

Really, they are just integers but it makes our code neater

