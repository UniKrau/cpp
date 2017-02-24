[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [Answer of exercise \#9: No for-loops \#13](CppExerciseNoForLoopsAnswer13.htm)
===============================================================================================

 

This is the answer of [Exercise \#9: No
for-loops](CppExerciseNoForLoops.htm).

 

 

 

 

 

Question \#13: [MakeAbs](CppMakeAbs.htm)
----------------------------------------

 

Replace the **[for](CppFor.htm)**-loop. You will need:

-   [std::transform](CppTransform.htm)
-   your own [std::unary\_function](CppUnary_function.htm)

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cmath> #include <vector>   void MakeAbs(std::vector<int>& v) {   const int sz = v.size();   for (int i=0; i!=sz; ++i)   {     v[i] = std::abs(v[i]);   } }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Answer
------

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <cmath> #include <functional> #include <vector>  template <class T> struct Abs : public std::unary_function<T,T> {   const T operator()(const T& x) const { return std::abs(x); } };  void MakeAbs(std::vector<int>& v) {   std::transform(v.begin(),v.end(),v.begin(),Abs<int>()); }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Note: I did not find any way to refrain from writing a
[functor](CppFunctor.htm) (for example, by using
[std::ptr\_fun](CppPtr_fun.htm)) as shown in the lines below...

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` std::transform(v.begin(),v.end(),v.begin(),std::abs); //Does not work std::transform(v.begin(),v.end(),v.begin(),&std::abs); //Does not work std::transform(v.begin(),v.end(),v.begin(),std::ptr_fun(&std::abs)); //Does not work std::transform(v.begin(),v.end(),v.begin(),std::ptr_fun(std::abs)); //Does not work`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)