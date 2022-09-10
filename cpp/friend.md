# friend

## friend function can access the private data of the class

```cpp
#include <iostream>
using namespace std;

class Complex
{
public:
    Complex(int re_, int im_) : re(re_), im(im_) {}
    int real() const { return re; }
    int imag() { return im; }
    /* __doAssignmentPlus() is a friend function of class Complex, 
    marked with keyword friend*/
    friend Complex &__doAssignmentPlus(Complex *, const Complex &);
private:
    int re, im;
};

inline Complex &__doAssignmentPlus(Complex *ths, const Complex &c)
{
    ths->re += c.re;  // can access the private data in the Complex class
    ths->im += c.im;
    return *ths;
}

int main()
{
    Complex c1(1, 2);
    Complex c2(2, 3);
    Complex c = __doAssignmentPlus(&c2, c1);
    cout << "the real part of c is " << c.real() << endl;
    cout << "the imag part of c is " << c.imag() << endl;
    return 0;
}
```

## Objects of the same class are mutual friends

```cpp
#include <iostream>
using namespace std;

class Complex
{
public:
    Complex(int re_ = 0, int im_ = 0) : re(re_), im(im_) {}
    int real() const { return re; }
    int imag() { return im; }
    /* &param is a reference of class Complex */
    int func(const Complex &param)
    {
        return param.re + param.im;
    }

private:
    int re, im;
};

int main()
{
    Complex c1(1, 2);
    Complex c2;
    /* c1 and c2 are objects of class Complex, they are mutual friends */
    int sum = c2.func(c1);
    cout << "the sum of real and imag part of c1 is " << sum << endl;
    return 0;
}
```
