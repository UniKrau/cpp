[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [PaperRockScissors](CppPaperRockScissors.htm)
==============================================================

 

Technical facts
---------------

 

 

 

 

 

 

./CppPaperRockScissors/CppPaperRockScissors.pri
-----------------------------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` INCLUDEPATH += \     ../../Classes/CppPaperRockScissors  SOURCES += \     ../../Classes/CppPaperRockScissors/paperrockscissors.cpp \     ../../Classes/CppPaperRockScissors/paperrockscissorstest.cpp  HEADERS  += \     ../../Classes/CppPaperRockScissors/paperrockscissors.h  OTHER_FILES += \     ../../Classes/CppPaperRockScissors/Licence.txt`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppPaperRockScissors/paperrockscissors.h
------------------------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef PAPER_ROCK_SCISSORS_H #define PAPER_ROCK_SCISSORS_H  namespace ribi {  enum class PaperRockScissors {   paper,   rock,   scissors };  bool DoesBeat(const PaperRockScissors lhs, const PaperRockScissors rhs);  #ifndef NDEBUG void TestPaperRockScissors() noexcept; #endif //~NDEBUG  } //~namespace ribi  #endif // PAPER_ROCK_SCISSORS_H`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppPaperRockScissors/paperrockscissors.cpp
--------------------------------------------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include "paperrockscissors.h"  bool ribi::DoesBeat(const PaperRockScissors lhs, const PaperRockScissors rhs) {   const int a{static_cast<int>(lhs)};   const int b{static_cast<int>(rhs)};   return (a + 1) % 3 == b; }`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppPaperRockScissors/paperrockscissorstest.cpp
------------------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef NDEBUG #include "paperrockscissors.h"  #include <cassert>  void ribi::TestPaperRockScissors() noexcept {   {     static bool is_tested{false};     if (is_tested) return;     is_tested = true;   }   const PaperRockScissors paper{PaperRockScissors::paper};   const PaperRockScissors rock{PaperRockScissors::rock};   const PaperRockScissors scissors{PaperRockScissors::scissors};   assert(DoesBeat(paper,rock));   assert(DoesBeat(rock,scissors));   assert(DoesBeat(scissors,paper));    assert(!DoesBeat(rock,paper));   assert(!DoesBeat(scissors,rock));   assert(!DoesBeat(paper,scissors));    assert(!DoesBeat(paper,paper));   assert(!DoesBeat(rock,rock));   assert(!DoesBeat(scissors,scissors)); } #endif`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)