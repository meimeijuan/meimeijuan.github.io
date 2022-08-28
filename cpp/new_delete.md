# keyword "new" / "delete"

## How to use new and delete

```cpp
#include <iostream>
using namespace std;

int main() 
{
    int *p = new int;  // new a built-in type
    cout << *p << endl;
    cout << p << endl;
    delete p;  // delete 
    return 0;
}
```

```cpp
#include <iostream>
using namespace std;

int main() 
{
    int *p = new int[2];  // new an array
    cout << p[0] << endl;
    cout << p[1] << endl;
    cout << p << endl;
    delete []p;  // delete the array completely
    return 0;
}
```
```cpp
#include <iostream>
using namespace std;

class Complex
{
    public:
    int real, imag;
};

int main() 
{
    Complex *p = new Complex();  // new an object
    cout << (*p).real << endl;
    cout << (*p).imag << endl;
    cout << p << endl;
    delete p;  // delete
    return 0;
}
```
