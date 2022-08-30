# inline function

## the effect of the inline function

cut function call time cost by insert function definition into the call place.

But increase the size of the target file. {file.exe : 76484Byte -> 77781Byte}

## How to define a inline function

```cpp
#include <iostream>
using namespace std;

inline int Max(int n1, int n2)
{
    return n1>n2 ? n1 : n2;
}

int main() 
{
    cout << Max(3, 4) << endl;
    cout << Max(-3, -4) << endl;
    return 0;
}
```

### Notes

Complier may ignore the inline request.

TODO: check inline is active or not by disassemble file.
