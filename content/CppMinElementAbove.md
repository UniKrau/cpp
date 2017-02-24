[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [MinElementAbove](CppMinElementAbove.htm)
==========================================================

 

[MinElementAbove](CppMinElementAbove.htm) is a [math](CppMath.htm) [code
snippet](CppCodeSnippets.htm) to get the
[std::min\_element](CppMin_element.htm) above a certain value.

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //From http://www.richelbilderbeek.nl/CppMinElementAbove.htm double MinElementAbove(const std::vector<double>& v, const double above) {   const double max = std::numeric_limits<double>::max();   double lowest = max;   const std::vector<double>::const_iterator j = v.end();   std::vector<double>::const_iterator i = v.begin();   for ( ; i!=j; ++i)   {     if (*i > above && *i < lowest)     {       lowest = *i;     }   }   return (lowest != max ? lowest : above); }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)