[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [HelloBoostRegexQt5QtCreatorLubuntuToWindows](CppHelloBoostRegexQt5QtCreatorLubuntuToWindows.htm)
==================================================================================================================

 

![Boost](PicBoost.png)![Qt5](PicQt5.png)![Qt
Creator](PicQtCreator.png)![Lubuntu](PicLubuntu.png)![To](PicTo.png)![Windows](PicWindows.png)

 

[Hello Boost.Regex using Qt5 under Qt Creator under Lubuntu,
crosscompiled to
Windows](CppHelloBoostRegexQt5QtCreatorLubuntuToWindows.htm) is a [Hello
Boost.Regex](CppHelloBoostRegex.htm) program.

 

-   [Download the Qt Creator project
    'CppHelloBoostRegexQt5QtCreatorLubuntuToWindows' (zip)](CppHelloBoostRegexQt5QtCreatorLubuntuToWindows.zip)

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

-   ![Boost](PicBoost.png) [Boost](CppBoost.htm): version 1.55
-   ![Qt](PicQt.png) [Qt](CppQt.htm): version 5.4.1 (32 bit)
-   ![STL](PicStl.png) [STL](CppStl.htm): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): ./CppHelloBoostRegexQt5QtCreatorLubuntuToWindows/CppHelloBoostRegexQt5QtCreatorLubuntuToWindows.pro
--------------------------------------------------------------------------------------------------------------------------------------------

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` QT       += core QT       -= gui CONFIG   += console CONFIG   -= app_bundle TEMPLATE = app SOURCES += main.cpp  LIBS += -L../../Libraries/mxe/usr/i686-pc-mingw32/lib LIBS += -lboost_regex`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppHelloBoostRegexQt5QtCreatorLubuntuToWindows/main.cpp
---------------------------------------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream> #include <boost/regex.hpp>   int main() {   std::string s = "Hello World";   s = boost::regex_replace(s,boost::regex("World"),std::string("Boost"));   std::cout << s << '\n'; }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppHelloBoostRegexQt5QtCreatorLubuntuToWindows/CppHelloBoostRegexQt5QtCreatorLubuntuToWindows.sh
--------------------------------------------------------------------------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #!/bin/bash myfile="../../Libraries/mxe/usr/i686-pc-mingw32/qt5/bin/qmake" mytarget="CppHelloBoostRegexQt5QtCreatorLubuntuToWindows" myprofile=$mytarget.pro  if [ ! -e $myprofile ] then   echo "FAIL: Qt Creator project '$myprofile' not found"   exit fi  $myfile $myprofile  if [ ! -e Makefile ] then   echo "FAIL: "$myfile" "$myprofile" (makefile not found)"   exit fi  make  if [ -e ./release/$myexe ] then   echo $mytarget": SUCCESS" else   echo $mytarget": FAIL (executable not found)" fi  #Cleaning up rm -r release rm -r debug rm Makefile rm Makefile.*`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)