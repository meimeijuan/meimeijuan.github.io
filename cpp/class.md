## problem 

We already have learned the process based programming, why we introduce in OOP?
The old fashion{struct program) has the following problem:

    1. difficult to understanding
    2. hard to modify on the exist program
    3. hard to handle or look into error
    4. hard to reuse

## object oriented programming

Class is absract + wrap from the real world things. 

Class (data + function) the data type define which function can be act on it.

```cpp
class Rectangle
{
    public:
    int w, h;
    void Init(int w_, int h_)
    {
        w = w_;
        h = h_;
    }
    int Area()         // 1st define method of the member function in class
    {
        return w*h;
    }
    int Perimeter()
    {
        return 2*(w + h);
    }
};             // define a Rectangle class

Rectangle r;  // r is an object, it is an instance of class Rectangle

// 1st access method to the member variables
// instance
r.w = 5;
r.Init(3, 4);

// 2nd access method
// instance pointer
Rectangle *p1 = r;
p1->w = 5;

// 3rd access method
//instance reference
Rectangle & rr = r;
rr.w = 5;

// 2nd define method of the member function
int Rectangle::Aera()
{
    return w*h;
}
```
