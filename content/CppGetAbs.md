[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [GetAbs](CppGetAbs.htm)
========================================

 

[GetAbs](CppGetAbs.htm) is a [math](CppMath.htm) [code
snippet](CppCodeSnippets.htm) to create a [container](CppContainer.htm)
with absoluted values of another [container](CppContainer.htm).

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <functional> #include <vector>  //From http://www.richelbilderbeek.nl/CppMakeAbs.htm template <typename T> struct Abs   : public  std::unary_function<T,T> {   const T operator()(const T& x) const     { return (x < static_cast<T>(0.0) ? -x : x); } };  //From http://www.richelbilderbeek.nl/CppMakeAbs.htm template <typename T> void MakeAbs(std::vector<T>& v) {   std::transform(v.begin(),v.end(),v.begin(),Abs<T>()); }  //From http://www.richelbilderbeek.nl/CppGetAbs.htm template <typename T> const std::vector<T> GetAbs(   const std::vector<T>& a) {   std::vector<T> v(a);   MakeAbs(v);   return v; }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)