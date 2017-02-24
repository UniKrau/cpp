[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [DumbNewickToString](CppDumbNewickToString.htm)
================================================================

 

[DumbNewickToString](CppDumbNewickToString.htm) is a
[Newick](CppNewick.htm) [code snippets](CppCodeSnippets.htm) to convert
a -possibly invalid- [Newick](CppNewick.htm) to
[std::string](CppString.htm). [NewickToString](CppNewickToString.htm) is
the checked version of [DumbNewickToString](CppDumbNewickToString.htm).

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` ///DumbNewickToString converts a Newick std::vector<int> to a ///standard-format std::string without error checking. ///From http://www.richelbilderbeek.nl/CppDumbNewickToString.htm const std::string DumbNewickToString(const std::vector<int>& v) {   std::string s;   s.reserve(2 * v.size()); //Just a guess   const int sz = v.size();   for (int i=0; i!=sz; ++i)   {     const int x = v[i];     if (x >= 0)     {       s+=boost::lexical_cast<std::string>(x);       const int next = v[i+1];       if (next > 0 || next == BinaryNewickVector::bracket_open)       {         s+=",";       }     }     else if (x==BinaryNewickVector::bracket_open)     {       s+="(";     }     else if (x==BinaryNewickVector::bracket_close)     {       s+=")";       //Final closing bracket?       if (i+1==sz) break;       const int next = v[i+1];       if (next > 0 || next == BinaryNewickVector::bracket_open)       {         s+=",";       }     }     else     {       s+="x"; //Unknown character     }   }   return s; } `
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)