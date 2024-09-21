### Review C and C++: Class

### Class

A class is considered as an extended concept of a data structure: instead of holding only data, it can hold both data and functions. An object is an instantiation of a class. By default, all attributes and functions of a class are private.

``` c++
class Foo {
    int attribute;
    int function( void ) { };
};

struct Bar {
    int attribute;
    int function( void ) { };
};

Foo foo;
foo.attribute = 1; // WRONG

Bar bar;
bar.attribute = 1;  // OK
```

#### a. constructors

It is possible to specify zero, one or more constructors for the class.

``` c++
#include <iostream>
using namespace std;

class Foo {
public:
    Foo( void )
    { cout << "Foo constructor 1 called" << endl; }
    Foo( int value )
    { cout << "Foo constructor 2 called" << endl; }
};

int main( int argc, char **argv )
{
    Foo foo_1, foo_2(2);
    return 0;
}
```

#### b. destructor

There can be only one destructor per class. Note that you generally may not need to explicitly call a destructor.

``` c++
#include <iostream>

class Foo {
public:
    ~Foo( void )
    { cout << "Foo destructor called" << endl; }
}
int main( int argc, char **argv )
{
    Foo foo();
    return 0;
}
```

#### You can have control over who is granted access to a class function or attribute by specifying an explicit access policy:

-   **public**: anyone is granted access
-   **protected**: only derived classes are granted access
-   **private**: no one but friends are granted access

#### c. initialization list

Object\'s member should be initialized using initialization lists

``` c++
class Foo
{
  int _value;

public:
  Foo(int value=0): _value(value) { };
};
```

#### d. operator overloading

``` c++
class Foo {
private:
    int _value;

public:
    Foo( int value ) : _value(value) { };

    Foo operator+ ( const Foo & other )
    {
        return Foo( _value+ other._value );
    }

    Foo operator* ( const Foo & other );
    {
        return Foo( _value * other._value );
    }
}
```

#### e. friends

Friends are functions or other classes that are granted privileged access to a class.

``` c++
#include <iostream>
using namespace std;

class Foo {
public:
    friend ostream& operator<< ( ostream& output, Foo const & that )
    {
        return output << that._value;
    }
private:
    double _value;
};

int main( int argc, char **argv )
{
  Foo foo;
  cout << "Foo object: " << foo << endl;
  return 0
}
```
