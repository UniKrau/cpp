[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [boost::circular\_buffer](CppCircular_buffer.htm)
==================================================================

 

[boost::circular\_buffer](CppCircular_buffer.htm) is an
'[STL](CppStl.htm) compliant [container](CppContainer.htm) also known as
ring or cyclic buffer' \[1\].

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <cassert> #include <iostream> #include <boost/circular_buffer.hpp>  int main() {   const int size = 3;   boost::circular_buffer<int> v(size);    v.push_back(1);   v.push_back(4);   v.push_back(9);    assert(v.size() == 3);   assert(v[0] == 1);   assert(v[1] == 4);   assert(v[2] == 9);    v.push_back(16);    assert(v.size() == 3);   assert(v[0] == 4);   assert(v[1] == 9);   assert(v[2] == 16);    v.push_back(25);    assert(v.size() == 3);   assert(v[0] == 9);   assert(v[1] == 16);   assert(v[2] == 25);    //Screen output: 9 16 25 9 16 25 9 16 25 9   for (int i=0; i!=10; ++i)   {     std::cout << *v.begin() << ' ';     v.rotate(v.begin() + 1);   } } `
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

External links
--------------

 

-   [Boost page about
    boost::circular\_buffer](http://www.boost.org/doc/libs/release/libs/circular_buffer/index.html)

 

 

 

 

 

[References](CppReferences.htm)
-------------------------------

 

1.  [Boost page listing all its
    libraries](http://www.boost.org/doc/libs)

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)