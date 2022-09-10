# return value vs return reference

## return value

```cpp
int sum(int a, int b)
{
    int sum;
    sum = a + b;
    return sum;  // sum is a return value
}
```

## return reference

```cpp
#include <iostream>
#include <string>
using namespace std;

const string &shorterString(const string &s1, const string &s2) /* return by reference and the parameter is
                                                                defined begond the current function scope */
{
    return s1.size() <= s2.size() ? s1 : s2;
}

int main()
{
    string s1 = "in this";
    string s2 = "in this room 2";
    const string s = shorterString(s1, s2); // ok
    cout << s << endl;                      // output s1
    return 0;
}
```

**never return a reference to a local object.**

```cpp
#include <iostream>
#include <string>
using namespace std;

const string& func()
{
    string ret("xxx"); // warnning: reference to local variable 'ret' returned [-Wreturn-local-addr]
    
    if(!ret.empty())
        return ret; // 
    else
        return "empty"; // warnning: returning reference to temporary [-Wreturn-local-addr]
}

int main()
{

    const string s1 = func(); // Exception has occurred. Segmentation fault
    cout<<s1<<endl;
    return 0;
}
```
