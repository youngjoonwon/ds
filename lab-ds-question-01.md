### Trying simple C++ basics

#### Read carefully!

#### Question 1. Modify the following program.

```c++
#include <array>
#include <iostream>

using namespace std;

void show(array<int, 10> ar, const char msg[])
{
    cout << msg << endl;
    for (int i = 0; i < ar.size(); ++i) {
        cout << ar[i] << endl;
    }
}

// Read carefully:
// Modify the function "update_array" changing the values of array properly.
// ar should be updated from all 0 to [0,1,2,3,4,5,6,7,8,9].
// Do not use additional cout.
void update_array(array<int, 10> ar)
{
    for (int i = 0; i < ar.size(); ++i) {
        ar[i] = 0;
    }
}

int main(void)
{
  array<int, 10> ar = {0};
  //change it to your name below
  cout << "Young" << endl;
  
  show(ar, "initializing all 0");
  
  //call your new update_array below
  
  show(ar, "after update");
  cout << endl;
  
  return 0;
}
```

- Submit it to LMS, **cpp** file only (**lab-01-1**). Check the deadline!
- DO NOT put any space in your submit file name. e.g.) 'young  ds-lab01 .cpp' (X). 0 will be given.
- If not compiling correctly (or compiling with warning), 0 will be given.

#### Question 2. Modify the following program.

```c++
#include <iostream>

using namespace std;

struct A { A() {  cout << "class" << endl; } };
struct A1 : public A { };
struct A2 : public A { };
struct A3 : public A { };
struct A4 : public A { };
struct B : public A1, public A2, public A3, public A4 { };

int main()
{
  //the following will print "class" 4 times.
  /*
  B b;
  */
  
  // Modify the code to print "class" 9 times without changing struct A,A1,A2,A3,and A4.
  // You can add new struct. Do not use addtional cout.
  
  return 0
}
```

- Submit it to LMS, **cpp** file only (**lab-01-2**). Check the deadline!
- DO NOT put any space in your submit file name. 0 will be given.
- If not compiling correctly (or compiling with warning), 0 will be given.