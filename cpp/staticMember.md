# static member in class

## static data member & static member function

```cpp
#include <iostream>

using namespace std;

class account
{
  private:
  static double rate_5_years;
  
  public:
  static void setRate(double new_rate){ rate_5_years = new_rate ; }  // no this pointer in static member function
  
  double money(double investment){ return investment*(1+rate_5_years/100);}  // non-static member function have this pointer
};

double account::rate_5_years = 3.0;

int main() {
  account::setRate(3.1);
  account meiJuan;
  meiJuan.setRate(5.1);
  cout<<meiJuan.money(10000.0)<<endl; 
  return 0;
}
```

