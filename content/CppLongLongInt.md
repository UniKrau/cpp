[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [long long int](CppLongLongInt.htm)
====================================================

 

[long long int](CppLongLongInt.htm) is a 64-bit [integer](CppInt.htm)
[data type](CppDataType.htm).

 

An [long long int](CppLongLongInt.htm) is a [keyword](CppKeyword.htm)
that can be used, depending on the [standard](CppStandard.htm) used:

-   ![C++98](PicCpp98.png) [long long int](CppLongLongInt.htm) in the
    [C++98](Cpp98.htm) [standard](CppStandard.htm)
-   ![C++11](PicCpp11.png) [long long int](CppLongLongInt.htm) in the
    [C++11](Cpp11.htm) [standard](CppStandard.htm)

 

 

 

 

 

![C++98](PicCpp98.png) [long long int](CppLongLongInt.htm) in the [C++98](Cpp98.htm) [standard](CppStandard.htm)
----------------------------------------------------------------------------------------------------------------

 

[long long int](CppLongLongInt.htm) is not guaranteed to be 64-bit in
the [C++98](Cpp98.htm) [standard](CppStandard.htm).

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream> #include <boost/static_assert.hpp>  int main() {   BOOST_STATIC_ASSERT(sizeof(int) == 4);   BOOST_STATIC_ASSERT(sizeof(long long int) == 8);   long long int x = 1;   int y = 1;   std::cout << "#: int - long long int\n";   for (int i = 1; i!=64; ++i)   {     x*=2;     y*=2;     std::cout << i << ": " << x << ',' << y << '\n';   } }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` Starting /MyFolder/CppLongLongInt... #: int - long long int 1: 2,2 ... 30: 1073741824,1073741824 31: 2147483648,-2147483648 32: 4294967296,0 ... 62: 4611686018427387904,0 63: -9223372036854775808,0 /MyFolder/CppLongLongInt exited with code 0`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

![C++11](PicCpp11.png) [long long int](CppLongLongInt.htm) in the [C++11](Cpp11.htm) [standard](CppStandard.htm)
----------------------------------------------------------------------------------------------------------------

 

-   [Download the Qt Creator project
    'CppLongLongInt' (zip)](CppLongLongInt.zip)

 

[long long int](CppLongLongInt.htm) is guaranteed to be 64-bit in the
[C++11](Cpp11.htm) [standard](CppStandard.htm).

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream>  int main() {   static_assert(sizeof(int) == 4,     "int has 4 bytes");   static_assert(sizeof(long long int) == 8,     "long long int has 8 bytes");   long long int x = 1;   int y = 1;   std::cout << "#: int - long long int\n";   for (int i = 1; i!=64; ++i)   {     x*=2;     y*=2;     std::cout << i << ": " << x << ',' << y << '\n';   } }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` Starting /MyFolder/CppLongLongInt... #: int - long long int 1: 2,2 ... 30: 1073741824,1073741824 31: 2147483648,-2147483648 32: 4294967296,0 ... 62: 4611686018427387904,0 63: -9223372036854775808,0 /MyFolder/CppLongLongInt exited with code 0`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Technical note: the code shown is [compiled](CppCompile.htm)
successfully using the [G++](CppGpp.htm) 4.4.5
[compiler](CppCompiler.htm), which is supplied with the [Qt
Creator](CppQtCreator.htm) 2.0.0 [IDE](CppIde.htm).

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)