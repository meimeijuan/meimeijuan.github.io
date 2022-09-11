# temp Ojbect

## What is a temp object of a class

typically is **typename();**

```cpp
#include <iostream>
using namespace std;

class Complex
{
public:
    Complex(int re_ = 0, int im_ = 0) : re(re_), im(im_) 
    {cout << "constructor is called"<< endl;}
    int real() const { return re; }
    int imag() const { return im; }

private:
    int re, im;
};

ostream& operator<<(ostream &os, const Complex &x)  // << is overloading here
{
    return os << '(' << x.real() << ',' << x.imag() << ')';
}

int main()
{
    Complex c1(2,1);
    Complex c2;
    cout << "c2 real part is " << c2.real() << endl;
    cout << "c2 imag part is " << c2.imag() << endl;
    
    Complex();  // Complex() is a temp object;
    Complex(4, 5);  // Complex(4, 5) is a temp object;
    cout << Complex(2);  // Complex(2) is a temp object;  
                         // the << is also overloaded.
    
    return 0;
}
```

**output :**

```
constructor is called
constructor is called
c2 real part is 0
c2 imag part is 0
constructor is called
constructor is called
constructor is called
(2,0)
```

## When the return type is a temp object, the return type can't be a reference

```cpp
#include <iostream>
using namespace std;

class Complex
{
public:
    Complex(int re_ = 0, int im_ = 0) : re(re_), im(im_) 
    {cout << "constructor is called"<< endl;}
    int real() const { return re; }
    int imag() const { return im; }

private:
    int re, im;
};

/* the following three function are non-member function of class Complex */

/* complex + complex */
inline Complex operator + (const Complex x, const Complex& y) // return type is Complex, not ref.
{
    return Complex(x.real() + y.real(), x.imag() + y.imag());  
    // Complex(x.real() + y.real(), x.imag() + y.imag()); will generate a temp object
}

/* complex + real */
inline Complex operator + (const Complex& x, double y)
{
    return Complex(x.real() + y, x.imag());
}

/* real + complex */
inline Complex operator + (double x, const Complex& y)
{
    return Complex(x + y.real(), y.imag());
}

ostream& operator<<(ostream &os, const Complex &x)  // << is overloading here
{
    return os << '(' << x.real() << ',' << x.imag() << ')';
}

int main()
{
    Complex c1(2,1);
    Complex c2;
    c2 = c2 + c1;
    
    return 0;
}
```

**Output :**

```bash
constructor is called
constructor is called
constructor is called
```

## non-const lvalue reference to type 'Complex' cannot bind to a temporary of type 'Complex'

```cpp
#include <iostream>
using namespace std;

class Complex
{
public:
    Complex(int re_ = 0, int im_ = 0) : re(re_), im(im_)
    {
        cout << "constructor is called" << endl;
    }
    int real() const { return re; }
    int imag() const { return im; }

private:
    int re, im;
};

/* the following function are non-member function of class Complex */

/* complex + complex */
inline Complex &operator+(Complex x, Complex &y)
{
    // Complex(); generate a temp object
    /* error: non-const lvalue reference to type 'Complex' cannot bind to 
    a temporary of type 'Complex' */
    return Complex(x.real() + y.real(), x.imag() + y.imag());
}

ostream &operator<<(ostream &os, const Complex &x)
{
    return os << '(' << x.real() << ',' << x.imag() << ')';
}

int main()
{
    Complex c1(2, 1);
    Complex c2;
    c2 = c2 + c1;

    return 0;
}
```

