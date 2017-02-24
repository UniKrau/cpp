[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [std::unique\_copy](CppUnique_copy.htm)
========================================================

 

[std::unique\_copy](CppUnique_copy.htm) is an [STL](CppStl.htm)
[algorithm](CppAlgorithm.htm) similar to [std::copy](CppCopy.htm) except
that it copies identical adjacent values once.

 

-   [Download the Qt Creator project
    'CppUnique\_copy' (zip)](CppUnique_copy.zip)

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <algorithm> #include <vector>  int main() {   std::vector<int> v;   v.push_back(0);   v.push_back(1);   v.push_back(1);   v.push_back(2);   v.push_back(2);   v.push_back(2);   v.push_back(3);   v.push_back(3);   v.push_back(3);   v.push_back(3);   std::vector<int> w;   std::unique_copy(v.begin(),v.end(),std::back_inserter(w));   assert(w[0]==0);   assert(w[1]==1);   assert(w[2]==2);   assert(w[3]==3); }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)