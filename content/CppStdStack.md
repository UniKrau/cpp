
 

 

 

 

 

([C++](Cpp.md)) [std::stack](Cppstd::stack.md)
================================================

 

[std::stack](Cppstd::stack.md) is an [STL](CppStl.md)
[container](CppContainer.md) for a stack (that is: First-In-Last-Out
storage).

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <stack>  int main() {   //Create a stack   std::stack<int> s;   //Put three values on stack   s.push(1);   s.push(2);   s.push(3);   //Reading and emptying stack   const int first  = s.top();   s.pop();   const int second = s.top();   s.pop();   const int third  = s.top();   s.pop();    assert(s.empty());   assert(first  == 3);   assert(second == 2);   assert(third  == 1); }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

-   [Download the Qt Creator project 'CppStack' (zip)](CppStack.md)

 

 

 

 

 

 

