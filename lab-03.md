

### g++ compile and run

Try the followings one by one carefully, don't just copy and paste. Type it up and try.

#### a. stupid example

1. open terminal and version check

```
$ g++-14 --version
```

2. let's create hello.cpp

```
$ vim hello.cpp
```

- insert the following and quit:

```c
#include <iostream>
using namespace std;

int main() {
   cout << "Hello CPP" << endl;
   return 0;
}
```

3. let's compile and run it

```
$ g++ -o hello hello.cpp
$ ./hello
```

- again for mac, it could be:

```
$ g++-14 -o hello hello.cpp
$ ./hello
```

- g++ to use other compiler options. e.g.) -Wall for all warnings

```
gcc++-14 -Wall hello.c
```

Question: can we ignore all these warnings at compilation?

Note: Let's not use fancy IDEs yet. 

#### b. preprocessing, macro

```
$ vim pre.cpp
```

- insert the following and quit:

```c
#include <iostream>
using namespace std;

#define PI 3.14

int main(void) {
  int r = 3;
  cout << "Area: " << PI*r*r << endl;
  return 0;
}
```

- what's the output?

```
$ g++-14 -o pre pre.cpp
$ ./pre
```

#### c. another macro

```c
#include <iostream>
using namespace std;
#define EXTRA_HAPPY

int main(void) {
  #ifdef EXTRA_HAPPY
  cout << "I'm happy!\n" << endl;
  #endif
  cout << "OK!\n" << endl;
}
```

#### d. command line arguments

- create the following and run it (argu.cpp)

```c
#include <iostream>
using namespace std;

int main(int argc, char **argv) {
   int n, m;

   cout << argv[0] << endl;
  
   n = atoi(argv[1]);
   m = atoi(argv[2]);

	 cout << "Argument 1: " << n << " Argument 2: " << m << endl;
  
   return 0;
}
```

- what's the output?

```
$ g++-14 -o argu argu.cpp
$ ./argu 2 3
```

