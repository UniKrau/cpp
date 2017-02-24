[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) ![Qt](PicQt.png) [QGraphicsProxyWidget example 6](CppQGraphicsProxyWidgetExample6.htm)
=======================================================================================================

 

[QGraphicsProxyWidget example 6](CppQGraphicsProxyWidgetExample6.htm) is
a [QGraphicsProxyWidget](CppQGraphicsProxyWidget.htm) example.

 

This example shows to be able to move the MyItem, even when MyItem has a
focusable QLineEdit.

 

-   ![Lubuntu](PicLubuntu.png) [View a screenshot of
    'CppQGraphicsProxyWidgetExample6' (png)](CppQGraphicsProxyWidgetExample6.png)
-   ![Wine](PicWine.png) [View a screenshot of
    'CppQGraphicsProxyWidgetExample6' (png)](CppQGraphicsProxyWidgetExample6Wine.png)
-   ![Qt Creator](PicQtCreator.png) [Download the Qt Creator project
    'CppQGraphicsProxyWidgetExample6' (zip)](CppQGraphicsProxyWidgetExample6.zip)
-   ![Windows](PicWindows.png) [Download the Windows executable of
    'CppQGraphicsProxyWidgetExample6' (zip)](CppQGraphicsProxyWidgetExample6Exe.zip)

 

 

 

 

 

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

-   ![GUI](PicGui.png) [GUI application](CppGuiApplication.htm)

[C++ standard](CppStandard.htm):

-   ![C++11](PicCpp11.png) [C++11](Cpp11.htm)

[Compiler(s)](CppCompiler.htm):

-   [G++](CppGpp.htm) 4.7.2

[Libraries](CppLibrary.htm) used:

-   ![Qt](PicQt.png) [Qt](CppQt.htm): version 4.8.3 (32 bit)
-   ![STL](PicStl.png) [STL](CppStl.htm): GNU ISO C++ Library, version
    4.7.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm): CppQGraphicsProxyWidgetExample6.pro
----------------------------------------------------------------------------

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` QT       += core QT       += gui QMAKE_CXXFLAGS += -std=c++11 -Wall -Wextra -Werror TARGET = CppQGraphicsProxyWidgetExample6 CONFIG   += console CONFIG   -= app_bundle TEMPLATE = app SOURCES += main.cpp \     myitem.cpp \     myview.cpp  HEADERS += \     myitem.h \     myview.h `
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

main.cpp
--------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifdef _WIN32 //See http://www.richelbilderbeek.nl/CppCompileErrorSwprintfHasNotBeenDeclared.htm #undef __STRICT_ANSI__ #endif  #pragma GCC diagnostic ignored "-Weffc++" #include <QApplication> #include <QDesktopWidget> #pragma GCC diagnostic pop  #include "myview.h"  int main(int argc, char **argv) {   //Create the application   QApplication app(argc, argv);   MyView view;   view.setGeometry(0,0,800,600);   {     //Put the dialog in the screen center     const QRect screen = QApplication::desktop()->screenGeometry();     view.move( screen.center() - view.rect().center() );   }   view.show();   return app.exec(); } `
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

myitem.h
--------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef MYITEM_H #define MYITEM_H  #include <QWidget> #include <boost/signals2.hpp>  struct QLabel; struct QLineEdit;  class MyItem : public QWidget {   Q_OBJECT    public:   explicit MyItem(QWidget *parent = 0, Qt::WindowFlags f = 0);   boost::signals2::signal<void (MyItem*)> m_signal_mouse_press;   boost::signals2::signal<void (MyItem*)> m_signal_lose_focus;   protected:   void mousePressEvent(QMouseEvent * event);   void mouseDoubleClickEvent(QMouseEvent * event);   public slots:   void LoseFocus();    public:   QLineEdit * const m_edit;   QLabel * const m_label; };  #endif // MYITEM_H `
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

myitem.cpp
----------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifdef _WIN32 //See http://www.richelbilderbeek.nl/CppCompileErrorSwprintfHasNotBeenDeclared.htm #undef __STRICT_ANSI__ #endif  //#include own header file as first substantive line of code, from: // * John Lakos. Large-Scale C++ Software Design. 1996. ISBN: 0-201-63362-0. Section 3.2, page 110 #include "myitem.h"  #pragma GCC diagnostic ignored "-Weffc++" #include <QLineEdit> #include <QLabel> #include <QVBoxLayout> #pragma GCC diagnostic pop  #include "myitem.h"  MyItem::MyItem(QWidget *parent, Qt::WindowFlags f)   : QWidget(parent,f),     m_edit(new QLineEdit(this)),     m_label(new QLabel(this)) {   assert(!this->layout());   QVBoxLayout * const layout = new QVBoxLayout(this);   this->setLayout(layout);   layout->addWidget(m_label);   layout->addWidget(m_edit);   QObject::connect(m_edit,SIGNAL(returnPressed()),this,SLOT(LoseFocus())); }  void MyItem::LoseFocus() {   //Really get rid of the focus   this->clearFocus();   this->setEnabled(false);   m_signal_lose_focus(this);   //Enable the item again   this->setEnabled(true); }  void MyItem::mousePressEvent(QMouseEvent * event) {   m_signal_mouse_press(this);   QWidget::mousePressEvent(event); }   void MyItem::mouseDoubleClickEvent(QMouseEvent *) {   LoseFocus(); } `
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

myview.h
--------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef MYVIEW_H #define MYVIEW_H  #include <QGraphicsView>   #include "myitem.h"  struct MyItem; struct QGraphicsScene;  class MyView : public QGraphicsView {   Q_OBJECT    public:   explicit MyView(QWidget *parent = 0);    protected:   void mouseMoveEvent(QMouseEvent *event);   void mouseReleaseEvent(QMouseEvent *);    private:   QGraphicsScene * const m_scene;   MyItem * m_drag_item;   std::map<MyItem *,QGraphicsProxyWidget *> m_m;    //My own added method   void OnMousePress(MyItem * item);   //An item wants to get rid of its focus   void OnItemNoFocus(MyItem * item); };  #endif // MYVIEW_H `
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

myview.cpp
----------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifdef _WIN32 //See http://www.richelbilderbeek.nl/CppCompileErrorSwprintfHasNotBeenDeclared.htm #undef __STRICT_ANSI__ #endif  //#include own header file as first substantive line of code, from: // * John Lakos. Large-Scale C++ Software Design. 1996. ISBN: 0-201-63362-0. Section 3.2, page 110 #include "myview.h"   #include <cassert> #include <cmath>  #pragma GCC diagnostic ignored "-Weffc++" #include <QGraphicsProxyWidget> #include <QGraphicsScene> #include <QLabel> #include <QLineEdit> #include <QDialog> #include <QGraphicsSceneMouseEvent> #pragma GCC diagnostic pop   MyView::MyView(QWidget *parent)   : QGraphicsView(parent),     m_scene(new QGraphicsScene(this)),     m_drag_item(nullptr) {   this->setScene(m_scene);   //Create the QLineEdit instances   const int sz = 10;   std::vector<QGraphicsProxyWidget *> proxies;   for (int i=0; i!=sz; ++i)   {     MyItem * const item = new MyItem;     item->setGeometry(0,0,100,22);     item->m_label->setText(QString("#") + QString::number(i));     item->m_edit->setText(QString("Text ") + QString::number(i));     item->m_signal_mouse_press.connect(       boost::bind(         &MyView::OnMousePress,         this,_1)); //_1 because the signal contains an argument     item->m_signal_lose_focus.connect(       boost::bind(         &MyView::OnItemNoFocus,         this,_1)); //_1 because the signal contains an argument     //Add the QWidget and obtain its proxy     QGraphicsProxyWidget * const proxy = m_scene->addWidget(item);     proxies.push_back(proxy);     m_m[item] = proxy;   }    const double ray = 200.0; //pixels   for (int i=0; i!=sz; ++i)   {     const double angle = 2.0 * M_PI * static_cast<double>(i) / static_cast<double>(sz);     const int x = static_cast<int>(0.0 + (std::sin(angle) * ray));     const int y = static_cast<int>(0.0 - (std::cos(angle) * ray));     QGraphicsProxyWidget * const proxy = proxies[i];     proxy->setRotation(angle * 360.0 / (2.0 * M_PI));     proxy->setPos(x,y);     proxy->setFlag(QGraphicsItem::ItemIsMovable,true); //No need to set this flag   } }  void MyView::OnMousePress(MyItem * item) {   assert(item);   m_drag_item = item;   //item->m_edit->setText("Gotcha!"); }  void MyView::OnItemNoFocus(MyItem * item) {   assert(item);   //item->m_edit->setText("Lost focus");   this->setFocus();   m_drag_item = nullptr;   assert(!m_drag_item); }  void MyView::mouseMoveEvent(QMouseEvent *event) {   if (m_drag_item)   {     //Convert the position clicked to the QGraphicsView coordinat     const QPointF p = this->mapToScene(event->pos());     //Let the item follow the mouse cursor     m_m[m_drag_item]->setPos(p);   } }  void MyView::mouseReleaseEvent(QMouseEvent *) {   m_drag_item = nullptr; } `
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

crosscompiletowindows.sh
------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #!/bin/sh #From http://richelbilderbeek.nl/CppQtCrosscompileToWindowsExample15.htm  echo "Cross compiling to Windows"  echo "1/2: Creating Windows makefile" i686-pc-mingw32-qmake CppQGraphicsProxyWidgetExample6.pro  echo "2/2: making makefile"  make  echo "Done" `
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)