# constructor

## Why we need a constructor ?

构造函数执行必要的初始化工作，不用再去写初始化函数，并且避免忘记调用初始化函数😉

## How to write a constructor for a class

```cpp
#include <iostream>
using namespace std;

class Complex
{
    public:
    int real, imag;
    Complex();  // declare but no definition
};
    
int main() 
{
    Complex c;  // undefined reference to `Complex::Complex()'  and collect2.exe: error: ld returned 1 exit status
    cout << "the real part of c is " << c.real << endl;
    cout << "the imag part of c is " << c.imag << endl;
    
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
    Complex();  // declare
};

Complex::Complex()  // definition a none parameter constructor
{

}
 
int main() 
{
    Complex c;  // can work well
    cout << "the imag part of c is " << c.imag << endl;
    cout << "the real part of c is " << c.real << endl;
    
    return 0;
}
```

```cpp
#include <iostream>
using namespace std;

class Complex  // no declaration and no explicit definition about constructor
{
    public:
    int real, imag;
};
 
int main() 
{
    Complex c;  // the compiler will generate a default constructor for class Complex
    cout << "the imag part of c is " << c.imag << endl;
    cout << "the real part of c is " << c.real << endl;
    
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
    Complex(int real, int imag);
};

Complex::Complex(int real_ = 0, int imag_ = 0)  // the parameter name should be different with the built-in type
{
    real = real_;
    imag = imag_;
}
 
int main() 
{
    Complex c = Complex();  // default parameter will pass to the instance variables.
    cout << "the imag part of c is " << c.imag << endl;
    cout << "the real part of c is " << c.real << endl;
    
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
    Complex(int real, int imag);
};

Complex::Complex(int real = 0, int imag = 0)  // real and imag has the same life cycle with parameter in the public part, it's the same variables.
{
    real = real;
    imag = imag;  // this operation is nonsense.
}
 
int main() 
{
    Complex c;
    cout << "the imag part of c is " << c.imag << endl;
    cout << "the real part of c is " << c.real << endl;
    
    return 0;
}

```
### Note

1. name is the same as the class name
2. it may have parameters, but no return
3. it is mainly used for Initialization,
