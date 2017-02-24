[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [std::nth\_element](CppNth_element.htm)
========================================================

 

[std::nth\_element](CppNth_element.htm) is an [STL](CppStl.htm)
[sorting](CppSort.htm) [algorithm](CppAlgorithm.htm) that
[sorts](CppSort.htm) a [container](CppContainer.htm) up until the nth
element and leaves the rest unsorted.

 

The example below shows how to obtain the top-three lowest elements.

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <cassert> #include <iostream> #include <vector>  int main() {   //Create a random-shuffled std::vector with the   //elements [0,size>   const int size = 100;   std::vector<int> v;   for (int i=0; i!=size; ++i) v.push_back(i);   std::random_shuffle(v.begin(),v.end());    //Only sort the top three   const int top_x = 3;   std::nth_element(v.begin(),v.begin() + top_x,v.end());    //Assume the top three are properly sorted   assert(v[0] == 0);   assert(v[1] == 1);   assert(v[2] == 2);    //Count non-sorted non-top-three   int n_non_sorted = 0;   for (int i=top_x; i!=size; ++i)   {     if (v[i]!=i) ++n_non_sorted;   }   //Display the number of non-sorted elements   //(my screen output: 86)   std::cout << n_non_sorted << '\n'; }`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)