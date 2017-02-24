[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [Boost.Integer](CppInteger.htm)
================================================

 

[Boost.Integer](CppInteger.htm) is a [Boost](CppBoost.htm)
[library](CppLibrary.htm) for working with [integers](CppInt.htm).

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <limits> #include <iostream> #include <boost/cstdint.hpp>  int main() {   std::cout     << std::numeric_limits<int>::max() << '\n'     << std::numeric_limits<uint_fast64_t>::max() << '\n'; }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  ------------------------------------
  ` 2147483647 18446744073709551615`
  ------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)