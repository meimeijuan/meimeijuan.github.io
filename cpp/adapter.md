## Adapter

```cpp
template <class T>
class queue
{
    ...
protected : deque<T> c;

public:
    bool empty() const { return c.empty(); }
    size_type size() const { return c.size(); }
    reference front() { return c.front(); }
    reference back() { return c.back(); }
    void push(const value_type &x) { c.push_back(x); }
    void pop() { c.pop_front(); }
};
```

```cpp
template <class T>
class deque
{
protected:
    Itr<T> start;
    Itr<T> finish;
    T** map;
    unsigned int map_size;
};
```

```cpp
template <class T>
struct Itr
{
    T* cur;
    T* first;
    T* last;
    T** node;
    ...
};
```

sizeof(queue) = 40

sizeof(deque) = 16*2 + 4 + 4

sizeof(Itr) = 4*4
