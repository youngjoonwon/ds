### Review C and C++: Inheritance and others

### Inheritance

#### a. basics

Inheritance is done at the class definition level by specifying the base class and the type of inheritance.

``` c++
class Foo                            { /* ... */ };
class Bar_public : public Foo        { /* ... */ };
class Bar_private : private Foo      { /* ... */ };
class Bar_protected : protected Foo  { /* ... */ };
```

`Bar_public`, `Bar_private` and `Bar_protected` are derived from `Foo`.
`Foo` is the base class of `Bar_public`, `Bar_private` and`Bar_protected`.

-   In `Bar_public`, public parts of `Foo` are public, protected parts of `Foo` are protected
-   In `Bar_private`, public and protected parts of `Foo` are private
-   In `Bar_protected`, public and protected parts of `Foo` are protected

#### b. multiple inheritance

``` c++
class Foo               { protected: int data; };
class Bar1 : public Foo { /* ... */ };
class Bar2 : public Foo { /* ... */ };
class Bar3 : public Bar1, public Bar2 {
    void method( void )
    {
       data = 1; //not good
    }
};
```

### Streams

#### a. iostream and ios

Screen outputs and keyboard inputs may be handled using the iostream header file:

``` c++
#include <iostream>
using namespace std;

int main( int argc, char **argv )
{

    unsigned char age = 65;
    cout << static_cast<unsigned>(age)     << endl;
    cout << static_cast<void const*>(&age) << endl;

    double f = 3.14159;
    cout.unsetf(ios::floatfield);
    cout.precision(5);
    cout << f << endl;
    cout.precision(10);
    cout << f << endl;
    cout.setf(ios::fixed,ios::floatfield);
    cout << f << endl;

    cout << "Enter a number, or -1 to quit: ";
    int i = 0;
    while( cin >> i )
    {
        if (i == -1) break;
        cout << "You entered " << i << '\n';
    }
    return 0;
}
```

#### b. class input/output

``` c++
#include <iostream>
using namespace std;

class Foo {
public:
    friend ostream& operator<< ( ostream & output, Foo const & that )
    { 
      return output << that._value; 
    }
    friend istream& operator>> ( istream & input, Foo& foo )
    { 
      return input >> fred._value;
    }
private:
    double _value;
};
```

#### c. working with strings

``` c++
#include <sstream>
using namespace std;

int main( int argc, char **argv )
{
    const char *svalue = "42.0";
    int ivalue;
    istringstream istream;
    ostringstream ostream;

    istream.str(svalue);
    istream >> ivalue;
    cout << svalue << " = " << ivalue << endl;

    ostream.clear();
    ostream << ivalue;
    cout << ivalue << " = " << ostream.str() << endl;

    return 0;
}
```

### Templates

#### a. basics

Templates are special operators that specify that a class or a function is written for one or several generic types that are not yet known. The format for declaring function templates is:

-   template \<typename identifier\> function_declaration;
-   template \<typename identifier\> class_declaration;

``` c++
template<typename T1>
T1 foo1( void ) { /* ... */ };

template<typename T1, typename T2>
T1 foo2( void ) { /* ... */ };

template<typename T1>
class Foo3 { /* ... */ };


int a = foo1<int>();
float b = foo2<int,float>();
Foo<int> c;
```


#### b. template function

``` c++
template <class T>
T max( T a, T b)
{
    return( a > b ? a : b );
}

#include <sstream>

int main( int argc, char **argv )
{
    cout << max<int>( 2.2, 2.5 ) << endl;
    cout << max<float>( 2.2, 2.5 ) << endl;
}
```

#### c. template class

``` c++
template <class T>
class Foo {
    T _value;

public:
    Foo( T value ) : _value(value) { };
}

int main( int argc, char **argv )
{
    Foo<int> foo_int;
    Foo<float> foo_float;
}
```

#### d. template specialization

``` c++
#include <iostream>
using namespace std;

template <class T>
class Foo {
    T _value;
public:
    Foo( T value ) : _value(value)
    {
        cout << "Generic constructor called" << endl;
    };
}

template <>
class Foo<float> {
    float _value;
public:
    Foo( float value ) : _value(value)
    {
        cout << "Specialized constructor called" << endl;
    };
}

int main( int argc, char **argv )
{
    Foo<int> foo_int;
    Foo<float> foo_float;
}
```

### Standard template library

STL containers are template classes that implement various ways of storing ancd accessing data structures.

**sequence containers**:

-   vector
-   deque
-   list

**container adaptors**:

-   stack
-   queue
-   priority_queue

**others**:

-   set
-   map
-   multimap

``` c++
#include <vector>
#include <map>
#include <string>
using namespace std;

int main( int argc, char **argv )
{
    vector<int> v;
    v.push_back(1);
    v.push_back(2);
    v.push_back(3);

    map<string,int> m;
    m["one"] = 1;
    m["two"] = 2;
    m["three"] = 3;

    return 0;
}
```

Iterators are a convenient tool to iterate over a container:

``` c++
#include <map>
#include <string>
#include <iostream>
using namespace std;

int main( int argc, char **argv )
{
    map<string,int> m;
    m["one"] = 1;
    m["two"] = 2;
    m["three"] = 3;

    map<string,int>::iterator iter;
    for( iter=m.begin(); iter != m.end(); ++iter )
    {
        cout << "map[" << iter->first << "] = "
                  << iter->second << endl;
    }
    return 0;
}
```

### References

-   STL reference <http://www.cplusplus.com/reference/stl/> 
-   Boost free peer-reviewed portable C++ source libraries <http://www.boost.org/>
-   C++ guide <http://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list>
