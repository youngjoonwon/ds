### Others examples

#### data size example

let's create data_size.cpp

```shell
$ vim data_size.cpp
```

insert the following and quit:

```c++
#include <iostream>
using namespace std;

int main() {
     cout << "bool " << sizeof( bool )     << endl;
     cout << "char " << sizeof( char )     << endl;
     cout << "short " << sizeof( short )    << endl;
     cout << "int " << sizeof( int )      << endl;
     cout << "char* " << sizeof( char * )   << endl;
     cout << "int * " << sizeof( int * )    << endl;
     cout << "double " << sizeof( double )   << endl;
     cout << "int[10] " << sizeof( int[10] )  << endl;

     return 0;
}
```

```shell
$ g++-14 -o data_size data_size.cpp
$ ./data_size
```

#### array example

let's create arr.cpp and insert:

```c++
#include <array>
#include <iostream>
using namespace std;

void print(array<int, 4> v, const char msg[])
{
    cout << msg << '\n';
    for (size_t i = 0; i < v.size(); ++i) {
        cout << v[i] << '\n';
    }
    cout << '\n';
}

void set_values_1(array<int, 4> v)
{
    for (size_t i = 0; i < v.size(); ++i) {
        v[i] = 1;
    }
}

void set_values_2(array<int, 4> &v) // use the address-of operator
{
    for (size_t i = 0; i < v.size(); ++i) {
        v[i] = 1;
    }
}

int main(void)
{
    array<int, 4> a = {0};
    print(a, "After initialization"); // all zeros

    set_values_1(a); // pass-by-value: the function gets its own copy of a
    print(a, "After set_values_1");

    set_values_2(a); // pass-by-reference: the function gets a reference to a
    print(a, "After set_values_2");

    return 0;
}
```

```
$ g++-14 -o vec vec.cpp
$ ./vec
```

#### list example

let's create vec.cpp and insert:

```
$ vim vec.cpp
```

```c++
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v( 10, 0 );

    cout << "vector empty?  " << v.empty() << endl;            
    cout << "vector size:  "  << v.size()  << endl;

    v[0] = 42;
    v[9] = 91;

    for ( int k = 0; k < 10; ++k ) {
        cout << "v[" << k << "] = " << v[k] << endl;
    }

    return 0;
}
```

```
$ g++-14 -o vec vec.cpp
$ ./vec
```

