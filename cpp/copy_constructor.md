# Copy Constructor in class

## Problem

### Why we need a new type constructor? though we have learned constructor.

    There are some circumstances that need to create a new object fron an existing object.

    1.
```cpp
Complex c2(c1);  // Instance c2 with c1

Complex c2 = c1; // is different from "=" operation
```
    2.
```cpp
void Func(Complex c1){}  // where object c1 is parameter

int main()
{
    Complex c2;
    Func(c2);  // Complex c1 = c2; see 1
    return 0;
}
```
    3.
```cpp
Complex Func()
{
    Complex c(4);
    return c;  // return Complex xxx = c;
}
```
### How to add a copy constructor to a class?

```cpp
class Complex
{
    private:
    int real, imag;
    public:
    setValue(int real_, int imag_)
    {
        real = real_;
        imag = imag_;
    }
    Complex(const Complex &c); // declare a const type
    Complex(Complex &c);  // declare a copy constructor
};
Complex::Complex(const Complex &c){}  // definition
Complex::Complex(Complex &c){}  // define the copy constructor out the class
```


### Note

```cpp
Complex c1, c2;
c2 = c1;  // won't call the copy constructor
```

