[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [std::scientific](CppScientific.htm)
=====================================================

 

[std::scientific](CppScientific.htm) is a [stream](CppStream.htm)
manipulator for real numbers to be displayed in the scientific notation.

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream>  int main() {   const double x = 123.456;   std::cout            << x << '\n'     << std::fixed      << x << '\n'     << std::scientific << x << '\n'; } `
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  ------------------------------------
  ` 123.456 123.456000 1.234560e+02`
  ------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)