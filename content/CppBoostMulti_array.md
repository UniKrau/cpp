[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [boost::multi\_array](CppMulti_array.htm)
==========================================================

 

[boost::multi\_array](CppMulti_array.htm) is a [Boost](CppBoost.htm)
[container](CppContainer.htm) for storing elements similar to a
multi-dimensional array.

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <boost/multi_array.hpp>  int main () {   //Determine boost::multi_array size   const int maxx = 3;   const int maxy = 4;   const int maxz = 5;   //The '3' determines v being 3-dimensional   boost::multi_array<double, 3> v(boost::extents[maxx][maxy][maxz]);   //Choose a random spot   const int x = std::rand() % maxx;   const int y = std::rand() % maxy;   const int z = std::rand() % maxz;   //Write to a random spot   v[x][y][z] = x + y + z;   //Read from to a random spot   assert(v[x][y][z]==x+y+z); }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)