[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [StdBitsetExample5](CppStdBitsetExample5.htm)
==============================================================

 

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

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): ./CppStdBitsetExample5/CppStdBitsetExample5.pro
----------------------------------------------------------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------
  ` TEMPLATE = app CONFIG += console CONFIG -= app_bundle CONFIG -= qt  QMAKE_CXXFLAGS += -std=c++1y SOURCES += main.cpp`
  -------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppStdBitsetExample5/main.cpp
-------------------------------

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream> #include <bitset> #include <cassert> #include <fstream> #include <vector>  typedef std::bitset<8> Bitset; const int n_bitsets{2};  //Avoid using globals Bitset v_global[n_bitsets]; Bitset w_global[n_bitsets];  ///Writes v to file void BitsetsToFile(   const std::string& filename) {   std::ofstream f(filename.c_str());   for (int i=0; i!=n_bitsets; ++i) { f << v_global[i] << '\n'; } }  ///Reads w from file void FileToBitsets(const std::string& filename) {   std::ifstream f(filename.c_str());   std::vector<std::bitset<8>> v;   std::ifstream in(filename.c_str());   for (int i=0; !in.eof(); ++i)   {     std::string s;     std::getline(in,s);     std::bitset<8> bitset(s);     v.push_back(bitset);   }   assert(!v.empty());   v.pop_back(); //If this is omitted, a "00000000" is added to back of std::vector    for (int i=0; i!=n_bitsets; ++i) { w_global[i] = v[i]; } }   int main() {   const Bitset b0(std::string("01010101"));   const Bitset b1(std::string("11111111"));   v_global[0] = b0;   v_global[1] = b1;    const std::string filename{"tmp.txt"};    //Write v to file   BitsetsToFile(filename);    //Read w from file   FileToBitsets(filename);   //if (*v_global != *w_global)   {     std::cout << "v:" << '\n';     for (const auto& b: v_global) { std::cout << b << '\n'; }     std::cout << "w:" << '\n';     for (int i=0; i!=n_bitsets; ++i) { std::cout << w_global[i] << '\n'; }   }   //Compare whole array   for (int i=0; i!=n_bitsets; ++i) { assert(v_global[i] == w_global[i]); } }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)