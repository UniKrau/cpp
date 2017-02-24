[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [QwtExample12](CppQwtExample12.htm)
====================================================

 

Technical facts
---------------

 

[Operating system(s) or programming environment(s)](CppOs.htm)

-   ![Lubuntu](PicLubuntu.png) [Lubuntu](CppLubuntu.htm) 15.04 (vivid)

[IDE(s)](CppIde.htm):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.htm) 3.1.1

[Project type](CppQtProjectType.htm):

-   ![console](PicConsole.png) [Console
    application](CppConsoleApplication.htm)

[C++ standard](CppStandard.htm):

-   ![C++98](PicCpp98.png) [C++98](Cpp98.htm)

[Compiler(s)](CppCompiler.htm):

-   [G++](CppGpp.htm) 4.9.2

[Libraries](CppLibrary.htm) used:

-   ![STL](PicStl.png) [STL](CppStl.htm): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): ./CppQwtExample12/CppQwtExample12.pro
------------------------------------------------------------------------------

 

  --------------------------------------------------------------------------------------------------------------------------------------------
  ` #Qwt does not go together with Qwt include(../../DesktopApplicationNoWeffcpp.pri) include(../../Libraries/Qwt.pri)  SOURCES += main.cpp`
  --------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQwtExample12/main.cpp
--------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <cmath> #include <string> #include <string> #include <sstream>  #include <QApplication> #include <QDesktopWidget>  #include <random> #include <boost/math/distributions/exponential.hpp>  #include <qwt_plot.h> #include <qwt_plot_curve.h> #include <qwt_column_symbol.h> #include <qwt_legend.h> #include <qwt_plot_multi_barchart.h> #include <qwt_text.h>  int main(int argc, char *argv[]) {   QApplication a(argc, argv);    const double maxx{10.0};   const double dx{0.01};    QwtPlot * const plot{new QwtPlot};    //dof: degrees of freedom   for (int i=0; i!=3; ++i)   {     const double lambda{static_cast<double>(i+1) * 0.5};     boost::math::exponential_distribution<double> distribution(lambda);      QwtPlotCurve * const curve{new QwtPlotCurve};     QVector<QPointF> v;     for (double x=0.0; x < maxx; x+=dx)     {       const double y{boost::math::pdf(distribution,x)};       v.push_back(QPointF(x,y));     }      const int r{i == 0 ? 255 : 0};     const int g{i == 1 ? 255 : 0};     const int b{i == 2 ? 255 : 0};     curve->setPen(QColor(r,g,b),2.0);     curve->setSamples(v);     curve->setTitle(QwtText(std::to_string(lambda).c_str()));     curve->attach(plot);   }    plot->setTitle("Probability density function of exponential distribution");   plot->setAxisScale(QwtPlot::xBottom,0.0, 5.0);   plot->setAxisScale(QwtPlot::yLeft  ,0.0, 1.5);   plot->setAxisTitle(QwtPlot::xBottom,"x");   plot->setAxisTitle(QwtPlot::yLeft  ,"Density");    {     QwtLegend * const legend = new QwtLegend;     legend->setFrameStyle(QFrame::Box|QFrame::Sunken);     plot->insertLegend(legend, QwtPlot::RightLegend);   }    //Put plot in screen center   {     const QRect screen = QApplication::desktop()->screenGeometry();     plot->setGeometry(0,0,screen.width() * 8 / 10,screen.height() * 8 / 10);     plot->move(screen.center() - plot->geometry().center());   }    plot->show();   plot->replot();   return a.exec(); }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)