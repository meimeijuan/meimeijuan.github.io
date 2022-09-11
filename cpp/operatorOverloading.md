# operator overloading

## member function operator overloading

```cpp
#include <iostream>
using namespace std;

class Complex
{
public:
    Complex(int re_ = 0, int im_ = 0) : re(re_), im(im_) {}
    int real() const { return re; }
    int imag() const { return im; }
    /* */
    int func(const Complex &param)
    {
        return param.re + param.im;
    }

    inline Complex &operator+=(const Complex &);

private:
    int re, im;
};

inline Complex &Complex::operator+=(const Complex &c)  // define the operator += and the return type is Complex& 
{
    this->re += c.real();
    this->im += c.imag();
    return *this;  // this pointer in class use
}

int main()
{
    Complex c1(2, 1);
    Complex c2(5);

    c2 += c1;
    cout << "c2 real part is " << c2.real() << endl;
    cout << "c2 imag part is " << c2.imag() << endl;
    return 0;
}
```

## another method from Hou Jie slides

```cpp
#include <iostream>
using namespace std;

class Complex
{
public:
    Complex(int re_ = 0, int im_ = 0) : re(re_), im(im_) {}
    int real() const { return re; }
    int imag() const { return im; }
    int func(const Complex &param)
    {
        return param.re + param.im;
    }

    inline Complex &operator+=(const Complex &);  // declare += operator in class type Complex
    friend inline Complex &__doAssignmentPlus(Complex *, const Complex &);

private:
    int re, im;
};

inline Complex &Complex::operator+=(const Complex &c)  // operator += is a member function of class Complex
{
    return __doAssignmentPlus(this, c);
}

inline Complex &__doAssignmentPlus(Complex *ths, const Complex &c)
{
    ths->re += c.re; // can access the private data in the Complex class
    ths->im += c.im;
    return *ths;
}

int main()
{
    Complex c1(2, 1);
    Complex c2(5);

    c2 += c1;
    cout << "c2 real part is " << c2.real() << endl;  // 7
    cout << "c2 imag part is " << c2.imag() << endl;  // 1
    return 0;
}
```

## Note: the return type is Complex&

```cpp
inline Complex &Complex::operator+=(const Complex &c)
{
    this->re += c.real();
    this->im += c.imag();
    return *this;  // this pointer in class use
}

/* other call method */
c3 += c2 += c1;  // there must be a return type with Complex&
```

## non-member function operator overloading

```cpp
/* complex + complex */
#include <iostream>
using namespace std;

class Complex
{
public:
    Complex(int re_ = 0, int im_ = 0) : re(re_), im(im_) {}
    int real() const { return re; }
    int imag() const { return im; }
    /* */
    int func(const Complex &param)
    {
        return param.re + param.im;
    }

private:
    int re, im;
};

/* the following three function are non-member function of class Complex */
/* complex + complex */
inline Complex operator + (const Complex x, const Complex& y)
{
    return Complex(x.real() + y.real(), x.imag() + y.imag());
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

int main()
{
    Complex c1(2,1);
    Complex c2;
    cout << "c2 real part is " << c2.real() << endl;
    cout << "c2 imag part is " << c2.imag() << endl;
    
    c2 = c1 + c2;
    cout << "c2 real part is " << c2.real() << endl;
    cout << "c2 imag part is " << c2.imag() << endl;
    c2 = c1 + 5;
    cout << "c2 real part is " << c2.real() << endl;
    cout << "c2 imag part is " << c2.imag() << endl;
    c2 = 7 + c1;
    cout << "c2 real part is " << c2.real() << endl;
    cout << "c2 imag part is " << c2.imag() << endl;
    
    return 0;
}
```

## ostream << is different

```cpp
#include <iostream>
using namespace std;

class Complex
{
public:
    Complex(int re_ = 0, int im_ = 0) : re(re_), im(im_) {}
    int real() const { return re; }
    int imag() const { return im; }

private:
    int re, im;
};

inline Complex conj(const Complex &x)
{
    return Complex(x.real(), -x.imag());
}

ostream& operator<<(ostream &os, const Complex &x)  // << is overloading here
{
    return os << '(' << x.real() << ',' << x.imag() << ')';
}

int main()
{
    Complex c1(2, 1);
    cout << conj(c1) << endl;
    cout << c1 << conj(c1);  // << operation priority is from left value
                             // this means the return type must be a ostream&
    return 0;
}
```



