[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [XmlToPretty](CppXmlToPretty.htm)
==================================================

 

[XmlToPretty](CppXmlToPretty.htm) is an [XML](CppXml.htm) [code
snippet](CppCodeSnippets.htm).

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <cassert> #include <iostream> #include <iterator> #include <string> #include <vector>  ///Split an XML std::string into its parts //From http://www.richelbilderbeek.nl/CppSplitXml.htm const std::vector<std::string> SplitXml(const std::string& s) {   std::vector<std::string> v;   std::string::const_iterator i = s.begin();   std::string::const_iterator j = s.begin();   const std::string::const_iterator end = s.end();   while (j!=end)   {     ++j;     if ((*j=='>' || *j == '<') && std::distance(i,j) > 1)     {       std::string t;       std::copy(         *i=='<' ? i   : i+1,         *j=='>' ? j+1 : j,         std::back_inserter(t));       v.push_back(t);       i = j;     }   }   return v; }  ///Pretty-print an XML std::string by indenting its elements //From http://www.richelbilderbeek.nl/CppXmlToPretty.htm const std::vector<std::string> XmlToPretty(const std::string& s) {   std::vector<std::string> v = SplitXml(s);   int n = -2;   std::for_each(v.begin(),v.end(),     [&n](std::string& s)     {       assert(!s.empty());       if (s[0] == '<' && s[1] != '/')       {         n+=2;       }       s = std::string(n,' ') + s;       if (s[n+0] == '<' && s[n+1] == '/')       {         n-=2;       }     }   );   return v; }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Testing code
------------

 

[XmlToPretty](CppXmlToPretty.htm) is tested with the code below.

 

-   [Download the Qt Creator project
    'CppXmlToPretty' (zip)](CppXmlToPretty.zip)

 

 

 

 

 

Technical facts
---------------

 

[Application type(s)](CppApplication.htm)

-   ![Desktop](PicDesktop.png) [Desktop
    application](CppDesktopApplication.htm)

[Operating system(s) or programming environment(s)](CppOs.htm)

-   ![Lubuntu](PicLubuntu.png) [Lubuntu](CppLubuntu.htm) 12.10 (quantal)

[IDE(s)](CppIde.htm):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.htm) 2.5.2

[Project type](CppQtProjectType.htm):

-   ![console](PicConsole.png) [Console
    application](CppConsoleApplication.htm)

[C++ standard](CppStandard.htm):

-   ![C++11](PicCpp11.png) [C++11](Cpp11.htm)

[Compiler(s)](CppCompiler.htm):

-   [G++](CppGpp.htm) 4.7.2

[Libraries](CppLibrary.htm) used:

-   ![STL](PicStl.png) [STL](CppStl.htm): GNU ISO C++ Library, version
    4.7.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): CppXmlToPretty.pro
-----------------------------------------------------------

 

  ------------------------------------------------------------------------------------------------------
  ` TEMPLATE = app QMAKE_CXXFLAGS += -std=c++11 CONFIG += console CONFIG -= qt  SOURCES += main.cpp  `
  ------------------------------------------------------------------------------------------------------

 

 

 

 

 

main.cpp
--------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <cassert> #include <iostream> #include <iterator> #include <string> #include <vector>  ///Split an XML std::string into its parts //From http://www.richelbilderbeek.nl/CppSplitXml.htm const std::vector<std::string> SplitXml(const std::string& s) {   std::vector<std::string> v;   std::string::const_iterator i = s.begin();   std::string::const_iterator j = s.begin();   const std::string::const_iterator end = s.end();   while (j!=end)   {     ++j;     if ((*j=='>' || *j == '<') && std::distance(i,j) > 1)     {       std::string t;       std::copy(         *i=='<' ? i   : i+1,         *j=='>' ? j+1 : j,         std::back_inserter(t));       v.push_back(t);       i = j;     }   }   return v; }  ///Pretty-print an XML std::string by indenting its elements //From http://www.richelbilderbeek.nl/CppXmlToPretty.htm const std::vector<std::string> XmlToPretty(const std::string& s) {   std::vector<std::string> v = SplitXml(s);   int n = -2;   std::for_each(v.begin(),v.end(),     [&n](std::string& s)     {       assert(!s.empty());       if (s[0] == '<' && s[1] != '/')       {         n+=2;       }       s = std::string(n,' ') + s;       if (s[n+0] == '<' && s[n+1] == '/')       {         n-=2;       }     }   );   return v; }  int main() {   {     const std::string s = "<a>A</a>";     const std::vector<std::string> split = SplitXml(s);     const std::vector<std::string> split_expected       =       {         "<a>",         "A",         "</a>"       };     assert(split == split_expected);     const std::vector<std::string> pretty = XmlToPretty(s);     const std::vector<std::string> pretty_expected       =       {         "<a>",         "A",         "</a>"       };     assert(pretty == pretty_expected);   }   {     const std::string s = "<a>A<b>B</b></a>";     const std::vector<std::string> split = SplitXml(s);     const std::vector<std::string> split_expected       =       {         "<a>",         "A",         "<b>",         "B",         "</b>",         "</a>"       };     assert(split == split_expected);     const std::vector<std::string> pretty = XmlToPretty(s);     const std::vector<std::string> pretty_expected       =       {         "<a>",         "A",         "  <b>",         "  B",         "  </b>",         "</a>"       };     assert(pretty == pretty_expected);   }     {     const std::string s = "<a>A<b>B1</b><b>B2</b></a>";     const std::vector<std::string> split = SplitXml(s);     const std::vector<std::string> split_expected       =       {         "<a>",         "A",         "<b>",         "B1",         "</b>",         "<b>",         "B2",         "</b>",         "</a>"       };     assert(split == split_expected);     const std::vector<std::string> pretty = XmlToPretty(s);     const std::vector<std::string> pretty_expected       =       {         "<a>",         "A",         "  <b>",         "  B1",         "  </b>",         "  <b>",         "  B2",         "  </b>",         "</a>"       };     assert(pretty == pretty_expected);   } } `
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)