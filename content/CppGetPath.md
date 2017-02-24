[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [GetPath](CppGetPath.htm)
==========================================

 

![STL](PicStl.png)![Qt
Creator](PicQtCreator.png)![Lubuntu](PicLubuntu.png)

 

[GetPath](CppGetPath.htm) is a [file I/O](CppFileIo.htm)
[std::string](CppStdString.htm) [code snippet](CppCodeSnippets.htm) to
get a filename's path.

 

-   [Download the Qt Creator project 'CppGetPath' (zip)](CppGetPath.zip)

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

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): ./CppGetPath/CppGetPath.pro
--------------------------------------------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` include(../../ConsoleApplication.pri) #Or use the code below # QT += core # QT += gui # greaterThan(QT_MAJOR_VERSION, 4): QT += widgets # CONFIG   += console # CONFIG   -= app_bundle # TEMPLATE = app # CONFIG(release, debug|release) { #   DEFINES += NDEBUG NTRACE_BILDERBIKKEL # } # QMAKE_CXXFLAGS += -std=c++11 -Wall -Wextra -Weffc++ # unix { #   QMAKE_CXXFLAGS += -Werror # }  include(../../Libraries/BoostAll.pri)  SOURCES += main.cpp`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppGetPath/main.cpp
---------------------

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <string>  #pragma GCC diagnostic push #pragma GCC diagnostic ignored "-Weffc++" #pragma GCC diagnostic ignored "-Wunused-local-typedefs" #include <boost/filesystem.hpp> #include <boost/xpressive/xpressive.hpp> #pragma GCC diagnostic pop  ///Returns the path of a filename ///From http://www.richelbilderbeek.nl/CppGetPath.htm const std::string GetPathStl(const std::string& filename) {   const int a = filename.rfind("\\",filename.size());   const int b = filename.rfind("/",filename.size());   const int i = std::max(a,b);   assert(i < static_cast<int>(filename.size()));   return filename.substr(0,i); }  ///Returns the path of a filename //From http://www.richelbilderbeek.nl/CppGetPath.htm const std::string GetPathBoostFilesystem(const std::string& filename) {   return boost::filesystem::path(filename).parent_path().string(); }  ///Returns the path of a filename ///From http://www.richelbilderbeek.nl/CppGetPath.htm const std::string GetPathBoostXpressive(const std::string& filename) {   const boost::xpressive::sregex rex     = boost::xpressive::sregex::compile(       "(.*)(\\\\|/)([A-Za-z\\._]*)" );   boost::xpressive::smatch what;    if( boost::xpressive::regex_match( filename, what, rex ) )   {     return what[1];   }    return ""; }  #include <iostream>  int main() {   #ifdef _WIN32   assert(GetPathBoostFilesystem("C:\\any_path\\any_file.cpp")=="C:\\any_path");   #else   assert(GetPathBoostFilesystem("/any_path/any_file.cpp")=="/any_path");   #endif    assert(GetPathBoostXpressive("C:\\any_path\\any_file.cpp")=="C:\\any_path");   assert(GetPathStl("C:\\any_path\\any_file.cpp")=="C:\\any_path");    assert(GetPathBoostXpressive("/any_path/any_file.cpp")=="/any_path");   assert(GetPathStl("/any_path/any_file.cpp")=="/any_path");    for (const auto f: { GetPathStl, GetPathBoostFilesystem, GetPathBoostXpressive} )   {     #ifdef _WIN32     assert(f("C:\\any_path\\any_file.cpp")=="C:\\any_path");     assert(f("any_path\\any_file.cpp")=="any_path");     #else     assert(f("/any_path/any_file.cpp")=="/any_path");     #endif   } }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)