[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [CallStackCounter](CppCallStackCounter.htm)
============================================================

 

![STL](PicStl.png)![Qt
Creator](PicQtCreator.png)![Lubuntu](PicLubuntu.png)

 

[CallStackCounter](CppCallStackCounter.htm) is a [class](CppClass.htm)
to probe the depth of the call stack, for example in a recursive
function.

 

The tool [TestCallStackCounter](ToolTestCallStackCounter.htm) is a
[tool](Tools.htm) to demonstrate its use.

Technical facts
---------------

 

 

 

 

 

 

./CppCallStackCounter/CppCallStackCounter.pri
---------------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` INCLUDEPATH += \     ../../Classes/CppCallStackCounter  SOURCES += \     ../../Classes/CppCallStackCounter/callstackcounter.cpp  HEADERS += \     ../../Classes/CppCallStackCounter/callstackcounter.h  OTHER_FILES += \     ../../Classes/CppCallStackCounter/Licence.txt`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppCallStackCounter/callstackcounter.h
----------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //--------------------------------------------------------------------------- /* CallStackCounter, C++ class to track the size of the call stack Copyright (C) 2009-2015 Richel Bilderbeek  This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.  This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.  You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>. */ //--------------------------------------------------------------------------- //From http://www.richelbilderbeek.nl/CppCallStackCounter.htm //--------------------------------------------------------------------------- #ifndef CALLSTACKCOUNTER_H #define CALLSTACKCOUNTER_H  #include <vector>  struct CallStackCounter {   CallStackCounter()  { ++cnt; }   ~CallStackCounter() { --cnt; }   static int Count() { return cnt; }   private:   static int cnt; };  struct CallStackHistoryCounter {   CallStackHistoryCounter()  { ++cnt; history.push_back(cnt); }   ~CallStackHistoryCounter() { --cnt; history.push_back(cnt); }   static int Count() { return cnt; }   static const std::vector<int>& History() { return history; }   static int Max();   private:   static int cnt;   static std::vector<int> history; };  #endif // CALLSTACKCOUNTER_H`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppCallStackCounter/callstackcounter.cpp
------------------------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //--------------------------------------------------------------------------- /* CallStackCounter, C++ class to track the size of the call stack Copyright (C) 2009-2015 Richel Bilderbeek  This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.  This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.  You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>. */ //--------------------------------------------------------------------------- //From http://www.richelbilderbeek.nl/CppCallStackCounter.htm //--------------------------------------------------------------------------- #include "callstackcounter.h"  #include <algorithm>  #pragma GCC diagnostic push #pragma GCC diagnostic ignored "-Weffc++" #pragma GCC diagnostic ignored "-Wunused-local-typedefs" #pragma GCC diagnostic ignored "-Wunused-but-set-parameter" #include "callstackcounter.h" #pragma GCC diagnostic pop  int CallStackCounter::cnt = 0; int CallStackHistoryCounter::cnt = 0; std::vector<int> CallStackHistoryCounter::history = std::vector<int>();  int CallStackHistoryCounter::Max() {   return *std::max_element(history.begin(),history.end()); }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)