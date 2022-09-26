# handle/body, aka, pImpl

## code

```cpp
#include <iostream>
#include <string>

using namespace std;

#include <memory> // PImpl
#include <string>
using namespace std;

class Impl;

class User {
public:
 // Constructor and Destructors

 ~User();
 User(string name);

 // Assignment Operator and Copy Constructor

 User(const User& other);
 User& operator=(User rhs);

 // Getter
 int getSalary();

 // Setter
 void setSalary(int);

private:

 Impl* pimpl;
};

struct Impl {

 Impl(string name)
  : name(move(name)){};

 ~Impl(){};


 void welcomeMessage()
 {
  cout << "Welcome, "
   << name << endl;
 }

 string name;
 int salary = -1;
};

// Constructor connected with our Impl structure
User::User(string name)
 : pimpl(new Impl(move(name)))
{
 pimpl->welcomeMessage();
}

// Default Constructor
User::~User() {}

// Assignment operator and Copy constructor

User::User(const User& other)
 : pimpl(new Impl(*other.pimpl))
{
}

User& User::operator=(User rhs)
{
 swap(pimpl, rhs.pimpl);
 return *this;
}

// Getter and setter
int User::getSalary()
{
 return pimpl->salary;
}

void User::setSalary(int salary)
{
 pimpl->salary = salary;
 cout << "Salary set to "
  << salary << endl;
}

int main()
{
    class User xm(string("xiaoming"));
    xm.setSalary(1000);
    cout<<xm.getSalary()<<endl;
    return 0;
}

```
