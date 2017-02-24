[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [QtExample23](CppQtExample23.htm)
==================================================

 

![Qt](PicQt.png)![Qt
Creator](PicQtCreator.png)![Lubuntu](PicLubuntu.png)![Ubuntu](PicUbuntu.png)

 

This [Qt example](CppQtExample.htm) shows a way to grab a widget as an
image.

 

-   [Download the 'CppQtExample23' source
    code (zip)](CppQtExample23.zip)
-   [View a screenshot of 'CppQtExample23' (png)](CppQtExample23.png)

Technical facts
---------------

 

[Application type(s)](CppApplication.htm)

-   ![Desktop](PicDesktop.png) [Desktop
    application](CppDesktopApplication.htm)

[Operating system(s) or programming environment(s)](CppOs.htm)

-   ![Lubuntu](PicLubuntu.png) [Lubuntu](CppLubuntu.htm) 15.04 (vivid)

[IDE(s)](CppIde.htm):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.htm) 3.1.1

[Project type](CppQtProjectType.htm):

-   ![GUI](PicGui.png) [GUI application](CppGuiApplication.htm)

[C++ standard](CppStandard.htm):

-   ![C++11](PicCpp11.png) [C++11](Cpp11.htm)

[Compiler(s)](CppCompiler.htm):

-   [G++](CppGpp.htm) 4.9.2

[Libraries](CppLibrary.htm) used:

-   ![Qt](PicQt.png) [Qt](CppQt.htm): version 5.4.1 (32 bit)
-   ![STL](PicStl.png) [STL](CppStl.htm): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): ./CppQtExample23/CppQtExample23.pro
----------------------------------------------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` exists(../../DesktopApplication.pri) {   include(../../DesktopApplication.pri) } !exists(../../DesktopApplication.pri) {   QT += core gui   greaterThan(QT_MAJOR_VERSION, 4): QT += widgets   TEMPLATE = app    CONFIG(debug, debug|release) {     message(Debug mode)   }    CONFIG(release, debug|release) {     message(Release mode)     DEFINES += NDEBUG NTRACE_BILDERBIKKEL   }    QMAKE_CXXFLAGS += -std=c++11 -Wall -Wextra    unix {     QMAKE_CXXFLAGS += -Werror   } }  exists(../../Libraries/Boost.pri) {   include(../../Libraries/Boost.pri) } !exists(../../Libraries/Boost.pri) {   win32 {     INCLUDEPATH += \       ../../../Projects/Libraries/boost_1_55_0   } }  SOURCES += \   main.cpp \   grabmedialog.cpp HEADERS  += grabmedialog.h FORMS    += grabmedialog.ui  #CONFIG += mobility #MOBILITY = #symbian { #    TARGET.UID3 = 0xe7eb3159 #    # TARGET.CAPABILITY += #    TARGET.EPOCSTACKSIZE = 0x14000 #    TARGET.EPOCHEAPSIZE = 0x020000 0x800000 #}`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQtExample23/grabmedialog.h
-------------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef GRABMEDIALOG_H #define GRABMEDIALOG_H  #pragma GCC diagnostic push #pragma GCC diagnostic ignored "-Weffc++" #pragma GCC diagnostic ignored "-Wunused-local-typedefs" #include <QDialog> #pragma GCC diagnostic pop  namespace Ui {   class GrabMeDialog; }  class GrabMeDialog : public QDialog {   Q_OBJECT  public:   explicit GrabMeDialog(QWidget *parent = 0);   GrabMeDialog(const GrabMeDialog&) = delete;   GrabMeDialog& operator=(const GrabMeDialog&) = delete;   ~GrabMeDialog();  private:   Ui::GrabMeDialog *ui;  private slots:   void on_button_grab_clicked(); };  #endif // GRABMEDIALOG_H`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQtExample23/grabmedialog.cpp
---------------------------------

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include "grabmedialog.h"  #pragma GCC diagnostic push #pragma GCC diagnostic ignored "-Weffc++" #pragma GCC diagnostic ignored "-Wunused-local-typedefs" #include "ui_grabmedialog.h" #pragma GCC diagnostic pop  GrabMeDialog::GrabMeDialog(QWidget *parent) :     QDialog(parent),     ui(new Ui::GrabMeDialog) {   ui->setupUi(this); }  GrabMeDialog::~GrabMeDialog() {   delete ui; }  void GrabMeDialog::on_button_grab_clicked() {   ui->label_image->setPixmap(       QPixmap::grabWindow(this->winId()));    //Other way:   //QImage copy = QPixmap::grabWindow(this->winId()).toImage();   //copy.save("temp.png");   //ui->label_image->setPixmap(QPixmap("temp.png")); }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQtExample23/main.cpp
-------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #pragma GCC diagnostic push #pragma GCC diagnostic ignored "-Weffc++" #pragma GCC diagnostic ignored "-Wunused-local-typedefs" #include <QApplication> #include "grabmedialog.h"  int main(int argc, char *argv[]) {   QApplication a(argc, argv);   GrabMeDialog w;   w.show();   return a.exec(); }`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)