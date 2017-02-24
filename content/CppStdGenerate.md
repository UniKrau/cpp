[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [std::generate](CppGenerate.htm)
=================================================

 

[Algorithm](CppAlgorithm.htm).

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorith> #include <iostream> #include <iterator> #include <vector>   int main() {   const int size = 20;   std::vector<int> v(size);     //Generate the random numbers   std::generate(v.begin(), v.end(), std::rand);     //Output on screen   std::copy(v.begin(),v.end(), std::ostream_iterator<int>(std::cout, "\n")); }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)