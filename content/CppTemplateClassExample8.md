
 

 

 

 

 

([C++](Cpp.md)) [TemplateClassExample8](CppTemplateClassExample8.md)
======================================================================

 

Technical facts
---------------

 

[Operating system(s) or programming environment(s)](CppOs.md)

-   ![Lubuntu](PicLubuntu.png) [Lubuntu](CppLubuntu.md) 15.04 (vivid)

[IDE(s)](CppIde.md):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.md) 3.1.1

[Project type](CppQtProjectType.md):

-   ![console](PicConsole.png) [Console
    application](CppConsoleApplication.md)

[C++ standard](CppStandard.md):

-   ![C++98](PicCpp98.png) [C++98](Cpp98.md)

[Compiler(s)](CppCompiler.md):

-   [G++](CppGpp.md) 4.9.2

[Libraries](CppLibrary.md) used:

-   ![STL](PicStl.png) [STL](CppStl.md): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): ./CppTemplateClassExample8/CppTemplateClassExample8.pro
------------------------------------------------------------------------------------------------

 

  -------------------------------------------------------------------------------------------------
  ` include(../../ConsoleApplication.pri) include(../../Libraries/Boost.pri) SOURCES += main.cpp`
  -------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppTemplateClassExample8/main.cpp
-----------------------------------

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //FAILS TO COMPILE  /*  Problem: the two get member functions are overloads  struct MyClass {   double Get() const noexcept;   int Get() const noexcept;    private:   double m_x; };  For template functions, this works:  template <class T> T Get() noexcept; template <> double Get() noexcept { return 12.34; } template <> int Get() noexcept { return 42; } */  #include <cassert>   struct MyClass {   template <class T> T Get() const noexcept;   template <> double Get() const noexcept { return 12.34; } //Does not compile   template <> int Get() const noexcept { return 42; } //Does not compile     private:   double m_x; };   int main() {   MyClass c;   const auto x = c.Get<int>();   const auto y = c.Get<double>();   assert(x == 42);   assert(y == 12.34); }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 

