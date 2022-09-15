# class template

## original template

```cpp
#include <iostream>
using namespace std;

template<typename T>  // typename is a keyword, keep it
class complex
{
  public:
  T real(){return re;}
  T imag(){return im;}
  
  complex(T re_, T im_):re(re_),im(im_){}
  
  private:
  T re, im;
};

int main() 
{
  complex<int> c(2,1);
  cout << c.real()<<endl;
  cout << c.imag()<<endl;
  return 0;
}
```

## compiler view

```cpp
#include <iostream>
using namespace std;

template<typename T>
class complex
{
  
  public: 
  inline T real()
  {
    return this->re;
  }
  
  inline T imag()
  {
    return this->im;
  }
  
  inline complex(T re_, T im_)
  : re{re_}
  , im{im_}
  {
  }
  
  
  private: 
  T re;
  T im;
};

/* First instantiated from: insights.cpp:19 */
#ifdef INSIGHTS_USE_TEMPLATE
template<>
class complex<int>
{
  
  public: 
  inline int real()
  {
    return this->re;
  }
  
  inline int imag()
  {
    return this->im;
  }
  
  inline complex(int re_, int im_)
  : re{re_}
  , im{im_}
  {
  }
  
  
  private: 
  int re;
  int im;
  public: 
};

#endif


int main()
{
  complex<int> c = complex<int>(2, 1);
  std::cout.operator<<(c.real()).operator<<(std::endl);
  std::cout.operator<<(c.imag()).operator<<(std::endl);
  return 0;
}

```
