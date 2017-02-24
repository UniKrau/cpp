[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [Boost.Random example 2: storing and retrieving a normal distribution's state](CppRandomExample2.htm)
======================================================================================================================

 

[Boost.Random example 2: storing and retrieving a normal distribution's
state](CppRandomExample2.htm) is a [Boost.Random](CppRandom.htm)
example.

 

-   [Download the Qt Creator project
    'CppRandomExample2' (zip)](CppRandomExample2.zip)

 

 

 

 

 

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <fstream> #include <iostream> #include <boost/random/normal_distribution.hpp> #include <boost/random/lagged_fibonacci.hpp> //From http://www.richelbilderbeek.nl/CppRandomExample2.htm struct MyRandomNormal {   MyRandomNormal()   {     {       std::ifstream f("engine.txt");       f >> m_engine;     }     {       std::ifstream f("norm_dist.txt");       f >> m_norm_dist;     }   }   MyRandomNormal(const double mean, const double stddev)     : m_norm_dist(mean,stddev)   {   }   ~MyRandomNormal()   {     {       std::ofstream f("engine.txt");       f << m_engine;     }     {       std::ofstream f("norm_dist.txt");       f << m_norm_dist;     }   }   double Get()   {     return m_norm_dist.operator ()<boost::lagged_fibonacci19937>((m_engine));   }   boost::lagged_fibonacci19937 m_engine;   boost::normal_distribution<double> m_norm_dist; }; int main() {   const double mean = 1.1;   const double stddev = 2.2;   {     MyRandomNormal x(mean,stddev);   }   {     MyRandomNormal x;     assert(x.m_norm_dist.mean() == mean);     assert(x.m_norm_dist.sigma() == stddev);   } }  `
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)