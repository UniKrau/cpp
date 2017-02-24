[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [EnhanceContrast](CppEnhanceContrast.htm)
==========================================================

 

[Graphics](CppGraphics.htm) [code snippet](CppCodeSnippets.htm) to
enhance the contrast of a [VCL](CppVcl.htm) [TImage](CppTImage.htm).

 

[EnhanceContrast](CppEnhanceContrast.htm) is similar to
[DoHistogramEqualization](CppDoHistogramEqualization.htm), except that
[EnhanceContrast](CppEnhanceContrast.htm) is milder: it tries to
minimally change the average greyness (using
[GetAverageGreyness](CppGetAverageGreyness.htm) to first measure it).

 

[EnhanceContrast](CppEnhanceContrast.htm) assumes that you've already
defined [GetAverageGreyness](CppGetAverageGreyness.htm).

 

-   [View an example of a composition image demonstrating
    EnhanceContrast and
    DoHistogramEqualization](CppEnhanceContrast.png): first, on the
    original (top-left), a [DoFilterOperation](CppDoFilterOperation.htm)
    was performed, resulting in the bottom-left image. On this result,
    both a [DoHistogramEqualization](CppDoHistogramEqualization.htm)
    (top-right) and
    [EnhanceContrast](CppEnhanceContrast.htm) (bottom-right) were
    performed on

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <vcl.h>  //From http://www.richelbilderbeek.nl/CppEnhanceContrast.htm void EnhanceContrast(const TImage * const image) {   //Find lowest and highest value   assert(image!=0 && "image must not be NULL");   assert(image->Picture->Bitmap!=0 && "image bitmap must not be NULL");   assert(image->Picture->Bitmap->PixelFormat == pf24bit && "image bitmap must be 24 bit");    //Get the width and height from the source   const int width  = image->Picture->Bitmap->Width;   const int height = image->Picture->Bitmap->Height;   const double averageGreyness = GetAverageGreyness(image);    double stretch = 1000.0; //Way too much for nearly all images    for (int y=0; y!=height; ++y)   {     const unsigned char * const line       = static_cast<const unsigned char *>(         image->Picture->Bitmap->ScanLine[y]);     for (int x=0; x!=width; ++x)     {       const double grey         = static_cast<double>(line[x*3+0] + line[x*3+1] + line[x*3+2])         / 3.0;       const double diff = grey - averageGreyness;       if (diff < 0.0)       {         //pixel was darker then average         const double newStretch = -averageGreyness / diff;         assert(newStretch >= 0.0);         if (newStretch < stretch) stretch = newStretch;       }       else if (diff > 0.0)       {         //pixel was lighter then average         const double newStretch = (255.9 - averageGreyness)  / diff;         if (newStretch < stretch) stretch = newStretch;       }     }   }    //Enhance the contrast   for (int y=0; y!=height; ++y)   {     unsigned char * const line       = static_cast<unsigned char *>(         image->Picture->Bitmap->ScanLine[y]);     for (int x=0; x!=width; ++x)     {       const double grey         = static_cast<double>(line[x*3+0] + line[x*3+1] + line[x*3+2])         / 3.0;       const double diff = grey - averageGreyness;       const double diffGreyNew = averageGreyness + (static_cast<double>(diff) * stretch);       const int newGrey = static_cast<int>(diffGreyNew);       assert(newGrey >=   0);       assert(newGrey <  256);       line[x*3+2] = newGrey; //Red       line[x*3+1] = newGrey; //Green       line[x*3+0] = newGrey; //Blue     }   } }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)