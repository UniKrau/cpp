[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [Answer of exercise \#9: No for-loops \#19](CppExerciseNoForLoopsAnswer19.htm)
===============================================================================================

 

This is the answer of [Exercise \#9: No
for-loops](CppExerciseNoForLoops.htm).

 

 

 

 

 

Question
--------

 

Replace the **[for](CppFor.htm)**-loop. You will need:

-   [std::bind2nd.htm](CppBind2nd.htm)
-   [std::greater.htm](CppGreater.htm)
-   [std::multiplies.htm](CppMultiplies.htm)
-   A conditional [std::accumulate](CppAccumulate.htm)

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` int ProductNonZeroPositives(const std::vector<int>& v) {   const size_t sz = v.size();   int product = 0;   for (size_t i=0; i!=sz; ++i)   {     if (v[i]>0) product*=v[i];   }   return product; }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Answer
------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //From http://www.richelbilderbeek.nl/CppAccumulate_if.htm template   <   typename InputIterator,   typename ElementType,   typename BinaryOperation,   typename Predicate   > const ElementType std::accumulate_if(   InputIterator first,   const InputIterator last,   ElementType init,   const BinaryOperation binary_op,   const Predicate predicate) {   for (; first != last; ++first)     if (predicate(*first)) init = binary_op(init, *first);   return init; }  #include <vector>  //From http://www.richelbilderbeek.nl/CppProductNonZeroPositives.htm int ProductNonZeroPositives(const std::vector<int>& v) {   return ::std::accumulate_if(     v.begin(),     v.end(),     1,     std::multiplies<int>(),     std::bind2nd(std::greater<int>(),0)); } `
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)