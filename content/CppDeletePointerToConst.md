[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [delete a pointer-to-const](CppDeletePointerToConst.htm)
=========================================================================

 

Be aware that you can [delete](CppDelete.htm) a
pointer-to-[const](CppConst.htm):

 

  --------------------------------------------------------------------------------------------------------------------------------------
  ` int main() {   //Create a read-only MyClass   const MyClass * const myClass = new MyClass;    delete myClass; //VALID C++ CODE! }`
  --------------------------------------------------------------------------------------------------------------------------------------

 

See [exercise \#2: a foolproof
function](CppExerciseFoolproofFunction.htm) for the implications and
prevention of this.

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)