[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [operator|](CppOperatorBitwiseOr.htm)
======================================================

 

[operator|](CppOperatorBitwiseOr.htm) (pronounces as 'bitwise or
[operator](CppOperator.htm)') is an [operator](CppOperator.htm) to
perform bitwise or operations. The example below shows how to
reconstruct a truth table:

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream>  int main() {   const bool f = false;   const bool t = true;    std::cout     << (f | f) << '\n'  //0     << (f | t) << '\n'  //1     << (t | f) << '\n'  //1     << (t | t) << '\n'; //1 }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)