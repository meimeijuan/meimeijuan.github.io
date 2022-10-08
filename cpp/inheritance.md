# inheritance with virtual function

## what is inheritance

class Rectangle `is a` class Shape, where class Shape is a `base class`, and class Rectangle is a `derived class`.

![class](https://user-images.githubusercontent.com/111368834/194709689-0b5e0cc7-b79c-4508-a9f8-f4df9ef8e02f.png)

### memory model

### constructor and destructor call sequence

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
