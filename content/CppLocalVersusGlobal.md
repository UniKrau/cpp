[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [LocalVersusGlobal](CppLocalVersusGlobal.htm)
==============================================================

 

A simple [benchmark](CppBenchmark.htm) that tests the speed of
[local](CppLocal.htm) versus [member variables](CppMemberVariable.htm)
versus [global](CppGlobal.htm) [variables](CppVariable.htm).

 

The following tests are performed:

-   A complex calculation on only [local](CppLocal.htm)
    [variables](CppVariable.htm)
-   A complex calculation on only [member
    variables](CppMemberVariable.htm)
-   A complex calculation on only [member
    variables](CppMemberVariable.htm), that are first copied to
    [local](CppLocal.htm) [variables](CppVariable.htm). In the end of
    the calculation, the [local](CppLocal.htm)
    [variables](CppVariable.htm) are written to the [member
    variables](CppMemberVariable.htm) they originated from
-   A complex calculation on only [global](CppGlobal.htm)
    [variables](CppVariable.htm)

 

-   [Download the Qt Creator project 'CppLocalVersusGlobal'
    (version 1.2)(zip)](CppLocalVersusGlobal_1_2.zip)
-   [Download the Windows executable of 'CppLocalVersusGlobal'
    (version 1.0)(zip)](CppLocalVersusGlobalExe_1_0.zip)

 

Avoid using [global](CppGlobal.htm) data \[1-4\].

 

 

 

 

 

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

-   ![C++98](PicCpp98.png) [C++98](Cpp98.htm)

[Compiler(s)](CppCompiler.htm):

-   [G++](CppGpp.htm) 4.7.2

[Libraries](CppLibrary.htm) used:

-   ![STL](PicStl.png) [STL](CppStl.htm): GNU ISO C++ Library, version
    4.7.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): CppLocalVersusGlobal.pro
-----------------------------------------------------------------

 

  --------------------------------------------------------------------------------------------------------
  ` TEMPLATE = app CONFIG += console CONFIG -= qt QMAKE_CXXFLAGS += -Wextra -Werror SOURCES += main.cpp`
  --------------------------------------------------------------------------------------------------------

 

 

 

 

 

main.cpp
--------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //Benchmark to compare the speed of local versus global variables //From http://www.richelbilderbeek.nl/CppLocalVersusGlobal.htm #include <iostream> #include <boost/timer.hpp>  int g_a = 0; int g_b = 0; int g_c = 0; int g_d = 0; int g_e = 0; int g_f = 0; int g_g = 0; int g_h = 0; int g_i = 0; int g_j = 0; int g_k = 0; int g_l = 0; int g_m = 0; int g_n = 0; int g_o = 0; int g_p = 0; int g_q = 0; int g_r = 0; int g_s = 0; int g_t = 0; int g_u = 0; int g_v = 0; int g_w = 0; int g_x = 0; int g_y = 0; int g_z = 0; int g_count = 0;  double TestGlobals() {   boost::timer t;   for (g_a=0; g_a!=32; ++g_a)   for (g_b=0; g_b!=g_a; ++g_b)   for (g_c=0; g_c!=g_b; ++g_c)   for (g_d=0; g_d!=g_c; ++g_d)   for (g_e=0; g_e!=g_d; ++g_e)   for (g_f=0; g_f!=g_e; ++g_f)   for (g_g=0; g_g!=g_f; ++g_g)   for (g_h=0; g_h!=g_g; ++g_h)   for (g_i=0; g_i!=g_h; ++g_i)   for (g_j=0; g_j!=g_i; ++g_j)   for (g_k=0; g_k!=g_j; ++g_k)   for (g_l=0; g_l!=g_k; ++g_l)   for (g_m=0; g_m!=g_l; ++g_m)   for (g_n=0; g_n!=g_m; ++g_n)   for (g_o=0; g_o!=g_n; ++g_o)   for (g_p=0; g_p!=g_o; ++g_p)   for (g_q=0; g_q!=g_p; ++g_q)   for (g_r=0; g_r!=g_q; ++g_r)   for (g_s=0; g_s!=g_r; ++g_s)   for (g_t=0; g_t!=g_s; ++g_t)   for (g_u=0; g_u!=g_t; ++g_u)   for (g_v=0; g_v!=g_u; ++g_v)   for (g_w=0; g_w!=g_v; ++g_w)   for (g_x=0; g_x!=g_w; ++g_x)   for (g_y=0; g_y!=g_x; ++g_y)   for (g_z=0; g_z!=g_y; ++g_z)   ++g_count;    const double time = t.elapsed();   std::cout << g_count << std::endl;   return time; }  struct MembersOnly {   MembersOnly() : m_count(0) {}   double Test()   {     boost::timer t;     for (m_a=0; m_a!=32; ++m_a)     for (m_b=0; m_b!=m_a; ++m_b)     for (m_c=0; m_c!=m_b; ++m_c)     for (m_d=0; m_d!=m_c; ++m_d)     for (m_e=0; m_e!=m_d; ++m_e)     for (m_f=0; m_f!=m_e; ++m_f)     for (m_g=0; m_g!=m_f; ++m_g)     for (m_h=0; m_h!=m_g; ++m_h)     for (m_i=0; m_i!=m_h; ++m_i)     for (m_j=0; m_j!=m_i; ++m_j)     for (m_k=0; m_k!=m_j; ++m_k)     for (m_l=0; m_l!=m_k; ++m_l)     for (m_m=0; m_m!=m_l; ++m_m)     for (m_n=0; m_n!=m_m; ++m_n)     for (m_o=0; m_o!=m_n; ++m_o)     for (m_p=0; m_p!=m_o; ++m_p)     for (m_q=0; m_q!=m_p; ++m_q)     for (m_r=0; m_r!=m_q; ++m_r)     for (m_s=0; m_s!=m_r; ++m_s)     for (m_t=0; m_t!=m_s; ++m_t)     for (m_u=0; m_u!=m_t; ++m_u)     for (m_v=0; m_v!=m_u; ++m_v)     for (m_w=0; m_w!=m_v; ++m_w)     for (m_x=0; m_x!=m_w; ++m_x)     for (m_y=0; m_y!=m_x; ++m_y)     for (m_z=0; m_z!=m_y; ++m_z)     ++m_count;      const double time = t.elapsed();     std::cout << m_count << std::endl;     return time;   }   private:   int m_a;   int m_b;   int m_c;   int m_d;   int m_e;   int m_f;   int m_g;   int m_h;   int m_i;   int m_j;   int m_k;   int m_l;   int m_m;   int m_n;   int m_o;   int m_p;   int m_q;   int m_r;   int m_s;   int m_t;   int m_u;   int m_v;   int m_w;   int m_x;   int m_y;   int m_z;   int m_count; };  struct MembersToLocal {   MembersToLocal() : m_count(0) {}   double Test()   {     int member_count = 0;     int a = m_a;     int b = m_b;     int c = m_c;     int d = m_d;     int e = m_e;     int f = m_f;     int g = m_g;     int h = m_h;     int i = m_i;     int j = m_j;     int k = m_k;     int l = m_l;     int m = m_m;     int n = m_n;     int o = m_o;     int p = m_p;     int q = m_q;     int r = m_r;     int s = m_s;     int t = m_t;     int u = m_u;     int v = m_v;     int w = m_w;     int x = m_x;     int y = m_y;     int z = m_z;     boost::timer timer;      for (int a=0; a!=32; ++a)     for (int b=0; b!=a; ++b)     for (int c=0; c!=b; ++c)     for (int d=0; d!=c; ++d)     for (int e=0; e!=d; ++e)     for (int f=0; f!=e; ++f)     for (int g=0; g!=f; ++g)     for (int h=0; h!=g; ++h)     for (int i=0; i!=h; ++i)     for (int j=0; j!=i; ++j)     for (int k=0; k!=j; ++k)     for (int l=0; l!=k; ++l)     for (int m=0; m!=l; ++m)     for (int n=0; n!=m; ++n)     for (int o=0; o!=n; ++o)     for (int p=0; p!=o; ++p)     for (int q=0; q!=p; ++q)     for (int r=0; r!=q; ++r)     for (int s=0; s!=r; ++s)     for (int t=0; t!=s; ++t)     for (int u=0; u!=t; ++u)     for (int v=0; v!=u; ++v)     for (int w=0; w!=v; ++w)     for (int x=0; x!=w; ++x)     for (int y=0; y!=x; ++y)     for (int z=0; z!=y; ++z)     ++member_count;      m_a = a;     m_b = b;     m_c = c;     m_d = d;     m_e = e;     m_f = f;     m_g = g;     m_h = h;     m_i = i;     m_j = j;     m_k = k;     m_l = l;     m_m = m;     m_n = n;     m_o = o;     m_p = p;     m_q = q;     m_r = r;     m_s = s;     m_t = t;     m_u = u;     m_v = v;     m_w = w;     m_x = x;     m_y = y;     m_z = z;     m_count = member_count;     const double time = timer.elapsed();     std::cout << m_count << std::endl;     return time;   }   private:   int m_a;   int m_b;   int m_c;   int m_d;   int m_e;   int m_f;   int m_g;   int m_h;   int m_i;   int m_j;   int m_k;   int m_l;   int m_m;   int m_n;   int m_o;   int m_p;   int m_q;   int m_r;   int m_s;   int m_t;   int m_u;   int m_v;   int m_w;   int m_x;   int m_y;   int m_z;   int m_count; };  double TestLocals() {   int local_count = 0;   boost::timer t;   for (int a=0; a!=32; ++a)   for (int b=0; b!=a; ++b)   for (int c=0; c!=b; ++c)   for (int d=0; d!=c; ++d)   for (int e=0; e!=d; ++e)   for (int f=0; f!=e; ++f)   for (int g=0; g!=f; ++g)   for (int h=0; h!=g; ++h)   for (int i=0; i!=h; ++i)   for (int j=0; j!=i; ++j)   for (int k=0; k!=j; ++k)   for (int l=0; l!=k; ++l)   for (int m=0; m!=l; ++m)   for (int n=0; n!=m; ++n)   for (int o=0; o!=n; ++o)   for (int p=0; p!=o; ++p)   for (int q=0; q!=p; ++q)   for (int r=0; r!=q; ++r)   for (int s=0; s!=r; ++s)   for (int t=0; t!=s; ++t)   for (int u=0; u!=t; ++u)   for (int v=0; v!=u; ++v)   for (int w=0; w!=v; ++w)   for (int x=0; x!=w; ++x)   for (int y=0; y!=x; ++y)   for (int z=0; z!=y; ++z)   ++local_count;    const double time = t.elapsed();   std::cout << local_count << std::endl;   return time; }  int main() {   const double t_global = TestGlobals();   const double t_local  = TestLocals();   MembersOnly m1;   MembersToLocal m2;   const double t_m1 = m1.Test();   const double t_m2 = m2.Test();    std::cout     << "Globals: " << t_global << " seconds.\n"     << "Members only: " << t_m1 << " seconds.\n"     << "Members with local variables: " << t_m2 << " seconds.\n"     << "Locals : " << t_local  << " seconds.\n";  }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Results
-------

 

On a laptop (built in around 2011) with [Lubuntu](CppLubuntu.htm):

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------
  ` 906192 906192 906192 906192 Globals: 7.84 seconds. Members only: 5.9 seconds. Members with local variables: 5.78 seconds. Locals : 5.8 seconds.`
  ----------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[References](CppReferences.htm)
-------------------------------

 

-   [Andrei Alexandrescu](CppAndreiAlexandrescu.htm). Modern C++ Design.
    2001. ISBN: 0201704315. Item 10: 'Minimize global and shared data'.
-   [Andrei Alexandrescu](CppAndreiAlexandrescu.htm). Modern C++ Design.
    2001. ISBN: 0201704315. Item 18: 'Declare variables as locally
    as possible'.
-   Stephen C. Dewhurst. C++ Gotchas. 2003. ISBN: 0-321-12518-5. Gotcha
    \#3: 'Avoid global variables'.
-   [C++ FAQ Lite](http://www.parashift.com/c++-faq/global-vars.html):
    'The names of global variables should start with //' and 'Instead of
    using a global variable, you should seriously consider if there are
    ways to limit the variable's visibility and/or lifetime'.

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)