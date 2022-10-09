# inheritance with virtual function

## what is inheritance

class Rectangle `is a` class Shape, where class Shape is a `base class`, and class Rectangle is a `derived class`.

![class](https://user-images.githubusercontent.com/111368834/194709689-0b5e0cc7-b79c-4508-a9f8-f4df9ef8e02f.png)

### memory model

TODO

### constructor and destructor call sequence

call constructor from inner to outer;
call destructor from outer to inner;

## what is virtual function

non-virtual function // cannot override in derived class
virtual function  // may override in derived class
pure virtual function  // must override in derived class

```cpp
#include <iostream>
using namespace std;

class Shape {
   public:
    virtual double area() const = 0;
    virtual void print() { cout << "the shape is generated" << endl; }
    void lineColor() { cout << "the color is black" << endl; }
    Shape() { cout << "Shape constructor called" << endl; }
    virtual ~Shape() { cout << "Shape destructor called" << endl; }
};

class Rectangle : public Shape {
   public:
    virtual double area() const { return h * w; }
    virtual void print() { cout << "the Rectangle is generated" << endl; }
    Rectangle(double h1 = 1, double w1 = 1) : h(h1), w(w1) {
        cout << "Rectangle constructor called" << endl;
    }
    ~Rectangle() { cout << "Rectangle destructor called" << endl; }

   private:
    double h, w;
};

int main() {
    Rectangle r(2, 3);
    cout << "area is " << r.area() << endl;
    r.print();
    r.lineColor();
    return 0;
}
```

Output:

```
Shape constructor called
Rectangle constructor called
area is 6
the Rectangle is generated
the color is black
Rectangle destructor called
Shape destructor called
```

## Initialization list

Use the base class to Initialize some datas.

```cpp
#include <iostream>

class Base
{
private: // our member is now private
    int m_id {};

public:
    Base(int id=0)
        : m_id( id )
    {
    }

    int getId() const { return m_id; }
};

class Derived: public Base
{
private: // our member is now private
    double m_cost;

public:
    Derived(double cost=0.0, int id=0)
        : Base(id ) // Call Base(int) constructor with value id!
        , m_cost(cost )
    {
    }

    double getCost() const { return m_cost; }
};

int main()
{
    Derived derived( 1.3, 5 ); // use Derived(double, int) constructor
    std::cout << "Id: " << derived.getId() << '\n';
    std::cout << "Cost: " << derived.getCost() << '\n';

    return 0;
}
```
