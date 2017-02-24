[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [ConvertToGrey](CppConvertToGrey.htm)
======================================================

 

[ConvertToGrey](CppConvertToGrey.htm) is a [graphics](CppGraphics.htm)
[code snippet](CppCodeSnippets.htm) to convert a color [VCL](CppVcl.htm)
[TImage](CppTImage.htm) to a grey [TImage](CppTImage.htm).

 

In [the 'ConvertToGrey' example image](CppConvertToGrey.png) you see an
original color image, this image [converted to
grey](CppConvertToGrey.htm) and the result of [a histogram
equalization](CppDoHistogramEqualization.htm) on the grey image.

 

-   [View an example of an image converted to
    grey (png)](CppConvertToGrey.png)

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //From http://www.richelbilderbeek.nl/CppConvertToGrey.htm void ConvertToGrey(const TImage * const source, TImage * const target) {   assert(source!=0 && "Source image is NULL");   assert(target!=0 && "Target image is NULL");   assert(source->Picture->Bitmap!=0 && "Source bitmap is NULL");   assert(target->Picture->Bitmap!=0 && "Target bitmap is NULL");   assert(source->Picture->Bitmap->PixelFormat == pf24bit && "Source bitmap must be 24 bit");   assert(target->Picture->Bitmap->PixelFormat == pf24bit && "Target bitmap must be 24 bit");   //Get the width and height from the source   const int width  = source->Picture->Bitmap->Width;   const int height = source->Picture->Bitmap->Height;   //Set the target's width and height   target->Picture->Bitmap->Width  = width;   target->Picture->Bitmap->Height = height;    for (int y=0; y!=height; ++y)   {     const unsigned char * lineSource       = static_cast<const unsigned char *>(         source->Picture->Bitmap->ScanLine[y]);     unsigned char * lineTarget       = static_cast<unsigned char *>(         target->Picture->Bitmap->ScanLine[y]);     for (int x=0; x!=width; ++x)     {       const int grey         = (lineSource[x*3+0] + lineSource[x*3+1] + lineSource[x*3+2]) / 3;        lineTarget[x*3+0]=grey; //Blue       lineTarget[x*3+1]=grey; //Green       lineTarget[x*3+2]=grey; //Red     }   } }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)