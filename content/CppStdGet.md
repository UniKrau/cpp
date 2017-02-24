[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [boost::get](CppGet.htm)
=========================================

 

[boost::get](CppGet.htm) is a [Boost](CppBoost.htm)
[function](CppFunction.htm) to access an element from a
[container](CppContainer.htm), for example a
[boost::tuple](CppTuple.htm).

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream> #include <string> #include <boost/tuple/tuple.hpp> #include <boost/tuple/tuple_io.hpp>  int main() {   boost::tuple<int,double,std::string> t     = boost::make_tuple(123,3.14159,"Bilderbikkel");    const int x1 = t.get<0>();   const double x2 = t.get<1>();   const std::string x3 = t.get<2>();    boost::get<0>(t) = x1 + 1;   boost::get<1>(t) = x2 + 1.0;   boost::get<2>(t) = x3 + " was here";    std::cout << t << '\n'; }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)