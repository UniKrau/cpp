[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [AbcFile](CppAbcFile.htm)
==========================================

 

![STL](PicStl.png)![Qt
Creator](PicQtCreator.png)![Windows](PicWindows.png)

 

[AbcFile](CppAbcFile.htm) is a [class](CppClass.htm) for an ABC music
notation file.

Technical facts
---------------

 

 

 

 

 

 

./CppAbcFile/CppAbcFile.pri
---------------------------

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` INCLUDEPATH += \     ../../Classes/CppAbcFile  SOURCES += \     ../../Classes/CppAbcFile/abcfile.cpp  HEADERS  += \     ../../Classes/CppAbcFile/abcfile.h  OTHER_FILES += \     ../../Classes/CppAbcFile/Licence.txt`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppAbcFile/abcfile.h
----------------------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef ABCFILE_H #define ABCFILE_H  #include <iosfwd> #include <string> #include <tuple> #include "musicfwd.h"  struct AbcFile {   AbcFile();    ///Get the composer   const std::string& GetComposer() const { return m_composer; }    ///Get the composer   int GetIndex() const { return m_index; }    ///Get the title   const std::string& GetTitle() const { return m_title; }    ///Set the composer   ///The 'C' field   void SetComposer(const std::string& composer);    ///Set the song index   ///The 'X' field   void SetIndex(const int index);    ///Set the key, e.g. 'C'   ///The 'K' field   void SetKey(const Music::Note& note);    ///Set the note length from a numerator and denominator, e.g. (1,4) becomes 1/4   ///The 'L'   void SetNoteLength(const int n, const int d);    ///Set the tempo from a numerator and denominator and a beats per minute,   ///e.g. (1,4,120) becomes 1/4=120   ///The 'Q'   void SetTempo(const int n, const int d, const int tempo);    ///Set the time signature from a numerator and denominator, e.g. (3,4) becomes 3/4   ///The 'M'   void SetTimeSignature(const int n, const int d);    ///Set the title   ///The 'T' field   void SetTitle(const std::string& title);    ///Convert the ABC file to a text with lines   const std::string ToStr() const;    private:   ///The 'C' field   const std::string m_composer;    ///The 'X' field   const int m_index;    ///The 'K' field   const int m_note; //Use int used by Note its internals    ///The 'L' field   const std::pair<int,int> m_note_length;    ///The 'T' field   const std::tuple<int,int,int> m_tempo;    ///The 'M' field   const std::pair<int,int> m_time_signature;    ///The 'T' field   const std::string m_title; };  std::ostream& operator<<(std::ostream& os, const AbcFile& file);  #endif // ABCFILE_H`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppAbcFile/abcfile.cpp
------------------------

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include "abcfile.h"  #include <sstream>  AbcFile::AbcFile()   : m_composer(""),     m_index(0),     m_note(0),     m_note_length { 1,4 },     m_tempo { 1,4,120 } ,     m_time_signature { 3,4 } ,     m_title("") {  }  const std::string AbcFile::ToStr() const {   std::stringstream s;   s << "X:" << this->GetIndex() << '\n'     << "T:" << this->GetTitle() << '\n'     << "C:" << this->GetComposer() << '\n'     << "L:" << m_note_length.first << "/" << m_note_length.second << '\n'     << "M:" << m_time_signature.first << "/" << m_time_signature.second << '\n'     << "T"  << std::get<0>(m_tempo) << "/" << std::get<1>(m_tempo) << "=" << std::get<2>(m_tempo) << '\n'     << "V:V1 clef=treble" << '\n'     << "V:V2 clef=bass" << '\n';   return s.str(); }   std::ostream& operator<<(std::ostream& os, const AbcFile& file) {   os << file.ToStr();   return os; }  /* [V:V1] [FBd]2 d  B   | [FBd]2 d B   | [GBd]2 B d   | [GBd]2 B d    | w:     dot    se-ven | zip    ~ ex- | tract in the | mor-     ning | [V:V2] B,,4          | B,4          | G,,4         | G,4           | %      B             |              | G#m          |               | % % Verse 1, 13-16 % [V:V1] [GBe]2  e B   | [GBe]2  e B  | [FAc]2 c A  | [FAc]2 c   A  | w:     gotta have my | tools, gotta | have ~ mer- | cu-    ri- al | [V:V2] E,4           | E4           | F,,4        | F,4           | %      E             |              | F#          |               |  */`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)