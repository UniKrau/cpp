[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [SumFirst](CppSumFirst.htm)
============================================

 

[SumFirst](CppSumFirst.htm) is the answer of question \#21 of [Exercise
\#9: No for-loops](CppExerciseNoForLoops.htm).

 

 

 

 

 

![STL](PicStl.png) [STL](CppStl.htm) [SumFirst](CppSumFirst.htm)
----------------------------------------------------------------

 

You may [contact me](Contact.htm) if you have an [STL](CppStl.htm)
solution...

 

 

 

 

 

![Boost](PicBoost.png) [Boost](CppBoost.htm).Bind [SumFirst](CppSumFirst.htm)
-----------------------------------------------------------------------------

 

Thanks to 'ofwolfandman':

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <functional> #include <numeric> #include <utility> #include <vector> #include <boost/bind.hpp>  int SumFirst(const std::vector<std::pair<int,int> >& v) {   return std::accumulate(     v.begin(),     v.end(),     static_cast<int>(0),     boost::bind(       std::plus<int>(),       _1,       boost::bind<int>(&std::pair<int,int>::first, _2)       )     ); }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

![Boost](PicBoost.png) [Boost](CppBoost.htm).Lambda [SumFirst](CppSumFirst.htm)
-------------------------------------------------------------------------------

 

Thanks to 'ofwolfandman':

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <functional> #include <numeric> #include <utility> #include <vector> #include <boost/lambda/lambda.hpp> #include <boost/lambda/bind.hpp>  int SumFirst(const std::vector<std::pair<int,int> >& v) {   return std::accumulate(     v.begin(),     v.end(),     static_cast<int>(0),     boost::lambda::_1     + boost::lambda::bind(       &std::pair<int, int>::first, boost::lambda::_2       )   ); }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)