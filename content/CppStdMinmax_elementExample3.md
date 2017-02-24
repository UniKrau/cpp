[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [StdMinmax\_elementExample3](CppStdMinmax_elementExample3.htm)
===============================================================================

 

![C++11](PicCpp11.png)![STL](PicStl.png)![Qt
Creator](PicQtCreator.png)![Lubuntu](PicLubuntu.png)![Windows](PicWindows.png)

 

[std::minmax\_element example 3](CppStdMinmax_elementExample3.htm) is an
[example](CppExample.htm) of the
[std::minmax\_element](CppStdMinmax_element.htm)
[algorithm](CppAlgorithm.htm).

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

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): ./CppStdMinmax\_elementExample3/CppStdMinmax\_elementExample3.pro
----------------------------------------------------------------------------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` include(../../ConsoleApplication.pri) #Or use the code below # QT += core # QT += gui # greaterThan(QT_MAJOR_VERSION, 4): QT += widgets # CONFIG   += console # CONFIG   -= app_bundle # TEMPLATE = app # CONFIG(release, debug|release) { #   DEFINES += NDEBUG NTRACE_BILDERBIKKEL # } # QMAKE_CXXFLAGS += -std=c++11 -Wall -Wextra -Weffc++ # unix { #   QMAKE_CXXFLAGS += -Werror # }  SOURCES += main.cpp`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppStdMinmax\_elementExample3/main.cpp
----------------------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <cassert> #include <set>  struct Coordinat {   explicit Coordinat(const double x = 0.0,const double y = 0.0)     : m_x{x}, m_y{y}   {    }   double GetX() const noexcept { return m_x; }   double GetY() const noexcept { return m_y; }    private:   const double m_x;   const double m_y; };  bool operator<(const Coordinat& lhs, const Coordinat& rhs) {   if (lhs.GetX() < rhs.GetX()) return true;   if (lhs.GetX() > rhs.GetX()) return false;   return lhs.GetY() < rhs.GetY(); }  int main() {   std::set<Coordinat> s;   s.insert(s.begin(),Coordinat( 2.0,-5.0));   s.insert(s.begin(),Coordinat(-1.0,-1.0));   s.insert(s.begin(),Coordinat( 0.0, 8.0));   s.insert(s.begin(),Coordinat(-2.0,-4.0));   s.insert(s.begin(),Coordinat( 1.0,-1.0));    const auto xs {     std::minmax_element(s.begin(),s.end(),       [](const Coordinat& lhs, const Coordinat& rhs)       {         return lhs.GetX() < rhs.GetX();       }     )   };   const double minx = (std::get<0>(xs)).GetX();   const double maxx = (*xs.second).GetX();   assert(minx == -2.0);   assert(maxx ==  2.0);    const auto ys {     std::minmax_element(s.begin(),s.end(),       [](const Coordinat& lhs, const Coordinat& rhs)       {         return lhs.GetY() < rhs.GetY();       }     )   };    const double miny = (*ys.first).GetY();   const double maxy = (*ys.second).GetY();   assert(miny == -5.0);   assert(maxy ==  8.0); }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)