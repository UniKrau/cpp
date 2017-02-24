[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [std::noshowbase](CppNoshowbase.htm)
=====================================================

 

[std::noshowbase](CppNoshowbase.htm) is a [stream](CppStream.htm)
manipulator to not show the number system base. For example, the
(hexidecimal) value of '0x11' will be displayed as '11'.

 

The example below shows how to display an [integer](CppInt.htm) in
hexadecimal, octal and decimal with or without showing the number system
base.

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream>  int main () {   const int x = 100;   std::cout     << "The value of x in hex: "     << std::hex     << std::showbase     << x << '\n';   std::cout     << "The value of x in oct: "     << std::oct     << std::showbase     << x << '\n';   std::cout     << "The value of x in dec: "     << std::dec     << std::noshowbase     << x << '\n'; }`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  ---------------------------------------------------------------------------------------
  ` The value of x in hex: 0x64 The value of x in oct: 0144 The value of x in dec: 100`
  ---------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)