[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [BoostFormatExample1](CppBoostFormatExample1.htm)
==================================================================

 

![Boost](PicBoost.png)![Qt
Creator](PicQtCreator.png)![Lubuntu](PicLubuntu.png)

 

[Boost.Format example 1](CppBoostFormatExample1.htm) is a
[Boost.Format](CppBoostFormat.htm) [example](CppExample.htm).

 

-   [Download the Qt Creator project
    'CppBoostFormatExample1' (zip)](CppBoostFormatExample1.zip)

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

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): ./CppBoostFormatExample1/CppBoostFormatExample1.pro
--------------------------------------------------------------------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` include(../../ConsoleApplication.pri) #Or use the code below # QT += core # QT += gui # greaterThan(QT_MAJOR_VERSION, 4): QT += widgets # CONFIG   += console # CONFIG   -= app_bundle # TEMPLATE = app # CONFIG(release, debug|release) { #   DEFINES += NDEBUG NTRACE_BILDERBIKKEL # } # QMAKE_CXXFLAGS += -std=c++11 -Wall -Wextra -Weffc++ # unix { #   QMAKE_CXXFLAGS += -Werror # }  include(../../Libraries/Boost.pri) #Or use the code below # win32 { #   INCLUDEPATH += \ #     ../../Libraries/boost_1_54_0 # }  SOURCES += main.cpp`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppBoostFormatExample1/main.cpp
---------------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cstdio> #include <iostream>  #pragma GCC diagnostic push #pragma GCC diagnostic ignored "-Weffc++" #pragma GCC diagnostic ignored "-Wunused-local-typedefs" #include <boost/format.hpp> #pragma GCC diagnostic pop  int main() {   //Display integers, default   std::cout << boost::format("%1%\n") % 1;   std::cout << boost::format("%1%\n") % 12;   std::cout << boost::format("%1%\n") % 123;   std::cout << boost::format("%1%\n") % 1234;   std::cout << boost::format("%1%\n") % 12345;   std::cout << boost::format("%1%\n") % 123456;    //Display doubles, default   std::cout << boost::format("%1%\n") % 1.2345678;   std::cout << boost::format("%1%\n") % 12.345678;   std::cout << boost::format("%1%\n") % 123.45678;   std::cout << boost::format("%1%\n") % 1234.5678;   std::cout << boost::format("%1%\n") % 12345.678;   std::cout << boost::format("%1%\n") % 123456.78;    //Display doubles with two significant digits   std::cout << boost::format("%1$.2d\n") % 1.2345678;   std::cout << boost::format("%1$.2d\n") % 12.345678;   std::cout << boost::format("%1$.2d\n") % 123.45678;   std::cout << boost::format("%1$.2d\n") % 1234.5678;   std::cout << boost::format("%1$.2d\n") % 12345.678;   std::cout << boost::format("%1$.2d\n") % 123456.78;    //Display sign   //Pad to 5 digits   std::cout << boost::format("%1$+5d\n") % 1;   std::cout << boost::format("%1$+5d\n") % 12;   std::cout << boost::format("%1$+5d\n") % 123;   std::cout << boost::format("%1$+5d\n") % 1234;   std::cout << boost::format("%1$+5d\n") % 12345;   std::cout << boost::format("%1$+5d\n") % 123456; }  /* Screen output  1 12 123 1234 12345 123456 1.23457 12.3457 123.457 1234.57 12345.7 123457 1.2 12 1.2e+002 1.2e+003 1.2e+004 1.2e+005    +1   +12  +123 +1234 +12345 +123456  */`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)