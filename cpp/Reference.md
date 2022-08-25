# define
  类型名 & 引用名 = 某变量名;
  
  int n = 4;
  int &r = n; 初始化变量n


## 从一而终

## 值交换😊
    void swap(int a, int b)
    {
      int tmp;
      tmp = a;
      a = b;
      b = tmp;
    }
    
    int n1,n2;
    swap(n1, n2);//值没有实现交换
    
    void swap(int* a, int* b)
    {
      int tmp;
      tmp = *a;
      *a = *b;
      *b = tmp;
    }
    int n1, n2;
    swap(&n1, &n2);
    
       void swap(int &a, int &b)
    {
      int tmp;
      tmp = a;
      a = b;
      b = tmp;
    }
    
    int n1,n2;
    swap(n1, n2);//值实现交换 
 
 # Reference as the return of a function
 int n = 4;
 int & SetValue() {return n;}
 int main()
 {
    SetValue() = 40;
    cout<<n;
    return 0;
 }
 
 # 常引用
 int n;
 const int & r = n;
 
