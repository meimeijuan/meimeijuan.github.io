## Inline function

1、inline + function
2、function define is in the class

ex:
void B::func1() {}


## function reload
### parameter table is different but the name is the same
### function parameter keep default need to Ambiguity 😃
void valueX(int val = 0) {x = val;}
int valueX() (return x;}

A.valueX(); //build error 

correct ex:
void valueX(int val) {x = val;}
int valueX() (return x;}
