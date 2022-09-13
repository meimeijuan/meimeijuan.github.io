# static

## limit global name's scope to current source file : effect name scope

### main.cpp 

```cpp
#include <iostream>
using namespace std;

extern int s;
extern int sum(int,int);

int main()
{
    cout << s << endl;  // undefined reference to `s'
    cout << sum(1,2) << endl; // undefined reference to `sum(int, int)'
                              // error: linker command failed with exit code 1 
    return 0;
}
```

### sum.cpp

```cpp
static int s=0;

static int sum(int a, int b)
{
    return a + b;
} 
```

## static local object : effect object lifetime 

### record.cpp

```cpp
int record()
{
    static int s=0;  // the function call is finished, the value of s can be remembered
    s++;
    return s;
}
```

### main.cpp

```cpp
#include <iostream>
using namespace std;

extern int record();

int main()
{
    for(int i=0;i<3;i++)
    {
        cout << record() << endl; // output 1, 2, 3
    }
    
    return 0;
}
```
