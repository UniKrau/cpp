[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [Get a TForm in a TForm](CppTFormInTForm.htm)
==============================================================

 

[VCL](CppVcl.htm) [graphics](CppVclGraphics.htm) [code
snippet](CppVclCodeSnippets.htm) to get a TForm in a
[TForm](CppTForm.htm). In other words: to use a TForm as a TPanel.

 

View the code below

[Download the code of ProjectTFormInTForm (zip)](CppTFormInTForm.zip)

[View a screenshot of ProjectTFormInTForm (png)](CppTFormInTForm.PNG)

 

Make sure that FormChild is not an auto-created form (do Project |
Options | Forms and put FormChild in the Available forms list).

 

 

 

 

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //UnitFormParent.h  #ifndef UnitFormParentH #define UnitFormParentH  #include <Classes.hpp> #include <Controls.hpp> #include <StdCtrls.hpp> #include <Forms.hpp> #include <ExtCtrls.hpp>  #include <boost/shared_ptr.hpp>  class TFormParent : public TForm {   __published: // IDE-managed Components   TPanel *PanelBottom;   TPanel *PanelTop;   TPanel *PanelTopLeft;   TPanel *PanelBottomLeft;   TPanel *PanelTopRight;   TPanel *PanelBottomRight; private: // User declarations public: // User declarations   __fastcall TFormParent(TComponent* Owner); };  extern PACKAGE TFormParent *FormParent;  #endif     //UnitFormParent.cpp  #include <vcl.h> #pragma hdrstop   #include "UnitFormParent.h" #include "UnitFormChild.h"  #pragma package(smart_init) #pragma resource "*.dfm" TFormParent *FormParent;  __fastcall TFormParent::TFormParent(TComponent* Owner) : TForm(Owner) {   {     TFormChild * child = new TFormChild(this,"1");     assert(child->BorderStyle == bsNone);     child->Parent = PanelTopLeft;     child->Align = alClient;     child->Show();   }   {     TFormChild * child = new TFormChild(this,"2");     assert(child->BorderStyle == bsNone);     child->Parent = PanelTopRight;     child->Align = alClient;     child->Show();   }   {     TFormChild * child = new TFormChild(this,"3");     assert(child->BorderStyle == bsNone);     child->Parent = PanelBottomLeft;     child->Align = alClient;     child->Show();   }   {     TFormChild * child = new TFormChild(this,"4");     assert(child->BorderStyle == bsNone);     child->Parent = PanelBottomRight;     child->Align = alClient;     child->Show();   } }       //UnitFormChild.h   #ifndef UnitFormChildH #define UnitFormChildH  #include <Classes.hpp> #include <Controls.hpp> #include <StdCtrls.hpp> #include <Forms.hpp> #include <ExtCtrls.hpp>  class TFormChild : public TForm { __published: // IDE-managed Components   TPanel *Panel; private: // User declarations public: // User declarations   __fastcall TFormChild(TComponent* Owner, const String& s); };  extern PACKAGE TFormChild *FormChild;  #endif    //UnitFormChild.cpp  #include <vcl.h> #pragma hdrstop   #include "UnitFormChild.h"  #pragma package(smart_init) #pragma resource "*.dfm" TFormChild *FormChild;  __fastcall TFormChild::TFormChild(TComponent* Owner, const String& s) : TForm(Owner) {   Panel->Caption = "Child #" + s; }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)