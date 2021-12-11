# Assignment 3

so in c++ keywords like **const** and **&** have many uses, so we will mention some of there uses in this report,

so we first will talk about **const** keyword.

## 1. Const :

1. the most basic use of **Const** keyword, is to make a variable that's can not be modified through the code, like when you define Pi, it can't be changed because it's a constant value.

   ```c++
   #include <iostream>
   using namespace std;
    
   int main()
   {
       const int Pi = 3.14;
       cout << Pi;
       return 0;
   }
   ```

   here we can't change the variable Pi in this code.

   ```c++
   #include <iostream>
   using namespace std;
    
   int main()
   {
       // we can't use this methode when using const
       const int Pi;
       Pi=3.14;
       // and we can't use this way also
       const int Pi;
       cout << Pi;
       return 0;
   }
   ```

2. We can use **Const**, when the pointer variable point to a const value

   ```c++
   #include <iostream>
   using namespace std;
   int main()
   {
       int x{ 10 };
       char y{ 'M' };
       const int* i = &x;
       const char* j = &y;
       x = 9;
       y = 'A';
       cout << *i << " " << *j;
       // so we can't change the value the pointer point to.
       *i=10;
       *j='S';
       // this code will give an error now.
   }
   ```

3. we can use **Const**, when a const pointer point to the value

   ```c++
   #include <iostream>
   using namespace std;
   int main()
   {
       int x = 5;
       char y = 'A';
       int* const i = &x;
       char* const j = &y;
       *i = 10;
       *j = 'D';
       cout << *i << " and " << *j<< endl;
       cout << i << " and " << j;
       return 0;
       // so we can't change the address of a const pointer
       i=&x+1;
   }
   ```

4. we can use **Const**, when a const pointer point to the const value

   ```c++
   #include <iostream>
   using namespace std;
   int main()
   {
       int x{ 9 };
       const int* const i = &x;
       char y{ 'A' };
       const char* const j = &y;
       cout << *i << " and " << *j;
       return 0;
       // we can't change neither value nor address of the pointer
   }
   ```

5. when passing **Const** variable as an argument to non-const parameter of a function cause error

   ```c++
   #include <iostream>
   using namespace std;
   int foo(int* y)
   {
       return *y;
   }
   int main()
   {
       int z = 8;
       const int* x = &z;
       cout << foo(x);
       return 0;
   }
   ```

   this code will cause compile time error.

6. Using **Const** with classes and functions

   ```c++
   #include <iostream>
   using namespace std;
   class Test {
       int value;
   public:
       Test(int v = 0)
       {
           value = v;
       }
       int getValue() const
       {
           return value;
       }
       void setValue(int val) {
           value = val;
       }
   };
   int main()
   {
       Test t(20);
       cout << t.getValue() << endl;
       const Test t_const(10);
      
       // const object invoking const function, no error
       cout << t_const.getValue() << endl;
       // const object invoking non-const function, CTE
       // t_const.setValue(15);
       // non-const object invoking non-const function, no error
       t.setValue(12); 
       cout << t.getValue() << endl;
       return 0;
   }
   ```

7. we can use **Const**, with const return type or const parameter

   ```c++
   #include <iostream>
   using namespace std;
    
   const int foo(const int y)
   {
       return y;
   }
    
   // Driver code
   int main()
   {
       int x = 9;
       const int z = 10;
       cout << foo(x) << '\n'
            << foo(z);
    
       return 0;
   }
   ```

## 2. & Keyword:

1. we can use **&** in a function to return reference

   ```c++
   class A
   {
     public:
     int bar() const {return someValue;}
     //Big, expensive to copy class
   }
   
   class B
   {
   public:
    A const& getA() { return mA;}
   private:
    A mA;
   }
   void someFunction()
   {
    B b = B();
    //Access A, ability to call const functions on A
    //No need to check for null, since reference is guaranteed to be valid.
    int value = b.getA().bar(); 
   }
   ```

2. we also can use **&** to pass a reference parameter and avoid null reference

   ```c++
   foo(string const& myname) 
   ```

3. also **&** can be used as and operation in bool condition 

   ```
   if(true&&false){
   ...
   }// the condition is false
   ```

4. **&** can be used in bitwise operations

   ```c++
   #include <iostream>
   using namespace std;
   int main() {
         // a = 5(00000101), b = 9(00001001)
       int a = 5, b = 9;
     
       // The result is 00000001
       cout<<"a = " << a <<","<< " b = " << b <<endl;
       cout << "a & b = " << (a & b) << endl;
     
       return 0;
   }
   ```

   