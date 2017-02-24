[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [std::find\_end](CppFind_end.htm)
==================================================

 

[std::find\_end](CppFind_end.htm) is an [STL](CppStl.htm)
[algorithm](CppAlgorithm.htm) to find the last occurrence of a sequence
in a [container](CppContainer.htm).

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <cassert> #include <vector>  int main() {   std::vector<int> v;   v.push_back(1);   v.push_back(0);   v.push_back(0);   v.push_back(2);   v.push_back(0);   v.push_back(0);   v.push_back(3);    std::vector<int> sequence;   sequence.push_back(0);   sequence.push_back(0);    assert(std::find_end(     v.begin(),v.end(),     sequence.begin(),sequence.end())     != v.end()     && "Assume sequence is found");    assert(std::find_end(     v.begin(),v.end(),     sequence.begin(),sequence.end())     != v.begin()     && "Assume sequence is not found at the beginning");    assert(* (std::find_end(     v.begin(),v.end(),     sequence.begin(),sequence.end()) - 1 )     == 2     && "Assume there is a 2 before the found sequence"); }`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

External links
--------------

 

-   [Cplusplus.com page about
    std::find\_end](http://www.cplusplus.com/reference/algorithm/find_end)

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)