# const Member Function

## Why need const member function

the member function will never write the member datas.

and the compiler always assume the member function is **non-const**.

the member function should explicitly add **const** keyword.

```cpp
#include <iostream>
using namespace std;

class Complex
{
public:
    int re, im;
    Complex(int re_, int im_) : re(re_), im(im_) {}
    int real() const { return re; } // const member function
    int imag() { return im; }       // non const member function
};

int main()
{
    Complex c1(1, -1);
    cout << c1.real() << endl;
    cout << c1.imag() << endl;

    const Complex c2(2, -2); // this means the member function should be qualified with const keyword
    cout << c2.real() << endl;
    cout << c2.imag() << endl; /* error: 'this' argument to member function 'imag' has type 'const Complex',
                                but function is not marked const */
    return 0;
}
```
