[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) ![Ubuntu](PicUbuntu.png)![VirtualBox](PicVirtualBox.png)![Windows](PicWindows.png) [::nrand48](CppNrand48.htm)
===============================================================================================================================

 

[::nrand48](CppNrand48.htm) is a [function](CppFunction.htm) in the
[global](CppGlobal.htm) [namespace](CppNamespace.htm) supplied with some
[STL](CppStl.htm)'s to draw a positive (that is: non-negative) [random
number](CppRandom.htm) uniformly distributed between 0 and 2\^31.

 

[::nrand48](CppNrand48.htm) needs to have a buffer supplied.
[Nrand48](CppNrand48.htm) is identical to [::nrand48](CppNrand48.htm).

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <cstdlib> #include <iostream> #include <stdint.h>  //From http://www.richelbilderbeek.nl/CppNrand48.htm long int Nrand48(unsigned short int xsubi[3]) {   //Factor in congruential formula   static unsigned long long int a = 0x5deece66dull;   // Additive constant in congruential formula   static unsigned short int c = 0xb;   const uint64_t x     = static_cast<uint64_t>(xsubi[2]) << 32     | static_cast<uint32_t>(xsubi[1]) << 16     | xsubi[0];   const uint64_t y = x * a + c;    xsubi[0] = y & 0xffff;   xsubi[1] = (y >> 16) & 0xffff;   xsubi[2] = (y >> 32) & 0xffff;    if (sizeof(unsigned short int) == 2)   {     return xsubi[2] << 15 | xsubi[1] >> 1;   }   else   {     return xsubi[2] >> 1;   } }  int main() {   unsigned short int buffer1[3] = {0,0,0};   unsigned short int buffer2[3] = {0,0,0};    for (int i=0; i!=10; ++i)   {     const long int a = ::nrand48(buffer1);     const long int b = Nrand48(buffer2);     assert(a==b);     assert(buffer1[0]==buffer2[0]);     assert(buffer1[1]==buffer2[1]);     assert(buffer1[2]==buffer2[2]);     std::cout       << a << '\t'       << buffer1[0] << '\t'       << buffer1[1] << '\t'       << buffer1[2] << '\t'       << '\n';   } }`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` 0       0       11  0   0    2116118     2116118     59066   37933   64   89401895    89401895    22845   21582   2728     379337186   379337186   52484   29636   11576    782977366   782977366   58047   37548   23894    196130996   196130996   9566    29032   5985     198207689   198207689   23825   53650   6048     1046291021  1046291021  58952   17562   31930    1131187612  1131187612  48307   6968    34521    975888346   975888346   10818   49077   29781   `
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Technical facts about source code above
---------------------------------------

 

-   [Download the Qt Creator project 'CppNrand48' (zip)](CppNrand48.zip)

 

[Application type(s)](CppApplication.htm)

-   ![Desktop](PicDesktop.png) [Desktop
    application](CppDesktopApplication.htm)
-   ![Mobile](PicMobile.png) [Mobile
    application](CppMobileApplication.htm)

[Operating system(s) or programming environment(s)](CppOs.htm)

-   ![Ubuntu](PicUbuntu.png) [Ubuntu](CppUbuntu.htm) 10.10 (maverick)
-   ![VirtualBox](PicVirtualBox.png) [VirtualBox](CppVirtualBox.htm)
    3.2.8\_OSEr64453
-   ![Windows](PicWindows.png) [Windows](CppWindows.htm) XP

[IDE(s)](CppIde.htm):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.htm) 2.0.1

[Project type](CppQtProjectType.htm):

-   ![console](PicConsole.png) [Console
    application](CppConsoleApplication.htm)
-   ![GUI](PicGui.png) [GUI application](CppGuiApplication.htm)

[C++ standard](CppStandard.htm):

-   ![C++98](PicCpp98.png) [C++98](Cpp98.htm)

[Compiler(s)](CppCompiler.htm):

-   [G++](CppGpp.htm) 4.4.5

[Libraries](CppLibrary.htm) used:

-   ![STL](PicStl.png) [STL](CppStl.htm): GNU ISO C++ Library, version
    4.4.5

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)