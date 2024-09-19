
### Review C and C++: Basics

#### a. input/output

``` c++
#include <iostream>
using namespace std;

int main (int argc, char **argv)
{
    int i;
    cout << "Please enter an integer value: ";
    cin >> i;
    cout << "The value you entered is " << i << endl;
    return 0;
}
```

#### b. new/delete

The `new` and `delete` keywords are used to allocate and free memory.
They are \"object-aware\" so it may be less confusing to use instead `malloc`and `free`. `delete` does two things: it calls the destructor and deallocates(free) the memory.

``` c++
int *a = new int;
delete a;

int *b = new int[5];
delete [] b;
```

#### c. references

A reference allows to declare an alias to another variable. As long as the aliased variable lives, you can use indifferently the variable or the alias.

``` c++
int x;
int& foo = x;

foo = 42;
cout << x << endl;
```

#### d. parameters

You can specify default values for function parameters. When the function is called with fewer parameters, default values are used.

``` c++
float foo( float a=0, float b=1, float c=2 )
{return a+b+c;}

cout << foo(1) << endl
     << foo(1,2) << endl
     << foo(1,2,3) << endl;
```

You should obtain values 4, 5 and 6.

#### e. namespaces

Namespace allows to group classes, functions and variable under a common scope name that can be referenced elsewhere.

``` c++
namespace first  { int var = 5; }
namespace second { int var = 3; }

cout << first::var << endl << second::var << endl;
```

There exists some standard namespace in the standard template library, e.g.) namespace std.

#### f. overloading

Function overloading refers to the possibility of creating multiple functions with the same name as long as they have different parameters.

``` c++
float add( float a, float b )
{return a+b;}

int add( int a, int b )
{return a+b;}
```

#### g. const 

Defines and macros are bad if NOT used properly.

``` c++
#define SQUARE(x) x*x

int result = SQUARE(3+3);
```

For constant, prefer the const notation:

``` c++
const int two = 2;
```

#### h. mixing C and C++

``` c++
#ifdef __cplusplus
extern "C" {
#endif

#include "some-c-code.h"

#ifdef __cplusplus
}
#endif
```

