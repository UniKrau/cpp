[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [Wait](CppWait.htm)
====================================

 

Technical facts
---------------

 

[Operating system(s) or programming environment(s)](CppOs.htm)

-   ![Lubuntu](PicLubuntu.png) [Lubuntu](CppLubuntu.htm) 15.04 (vivid)

[IDE(s)](CppIde.htm):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.htm) 3.1.1

[Project type](CppQtProjectType.htm):

-   ![console](PicConsole.png) [Console
    application](CppConsoleApplication.htm)

[C++ standard](CppStandard.htm):

-   ![C++98](PicCpp98.png) [C++98](Cpp98.htm)

[Compiler(s)](CppCompiler.htm):

-   [G++](CppGpp.htm) 4.9.2

[Libraries](CppLibrary.htm) used:

-   ![STL](PicStl.png) [STL](CppStl.htm): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): ./CppWait/CppWait.pro
--------------------------------------------------------------

 

  --------------------------------------------------------------------------------------------------
  ` include(../../ConsoleApplication.pri) include(../../Libraries/Boost.pri)  SOURCES += main.cpp`
  --------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppWait/main.cpp
------------------

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <chrono>  void WaitStl(const double n_secs) noexcept {   const std::chrono::system_clock::time_point t = std::chrono::system_clock::now();   while (1)   {     const std::chrono::system_clock::duration d = std::chrono::system_clock::now() - t;     const long long int n_msecs_passed{std::chrono::duration_cast<std::chrono::milliseconds>(d).count()};     const double secs_passed{static_cast<double>(n_msecs_passed) / 1000.0};     if (secs_passed > n_secs) return;   } }   #include <boost/timer.hpp>  void WaitBoost(const double n_secs) noexcept {   boost::timer t;   while (t.elapsed() < n_secs) {} }  #include <iostream>  int main() {   for (int i=0; i!=10; ++i)   {     std::cout << "Waiting 100 msecs using STL" << std::endl;     WaitStl(0.1);   }   for (int i=0; i!=10; ++i)   {     std::cout << "Waiting 100 msecs using Boost" << std::endl;     WaitBoost(0.1);   } }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)