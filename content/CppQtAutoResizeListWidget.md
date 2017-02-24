[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [QtAutoResizeListWidget](CppQtAutoResizeListWidget.htm)
========================================================================

 

Technical facts
---------------

 

 

 

 

 

 

./CppQtAutoResizeListWidget/qtautoresizelistwidget.h
----------------------------------------------------

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef QTAUTORESIZELISTWIDGET_H #define QTAUTORESIZELISTWIDGET_H  #include <QListWidget>  struct QtAutoResizeListWidget : public QListWidget {   QtAutoResizeListWidget(QWidget *parent = 0);   void addItem(QListWidgetItem *item);    private:   QTimer * const m_timer;    void OnTimer(); };  #endif // QTAUTORESIZELISTWIDGET_H`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQtAutoResizeListWidget/qtautoresizelistwidget.cpp
------------------------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include "qtautoresizelistwidget.h"  #include <QObject> #include <QScrollBar> #include <QTimer>  QtAutoResizeListWidget::QtAutoResizeListWidget(QWidget *parent)   : QListWidget(parent),     m_timer(new QTimer) {   QObject::connect(m_timer,&QTimer::timeout,this,&QtAutoResizeListWidget::OnTimer);   m_timer->setInterval(1);   m_timer->start(); }  void QtAutoResizeListWidget::addItem(QListWidgetItem *item) {    QListWidget::addItem(item);   this->repaint();   m_timer->start(); }  void QtAutoResizeListWidget::OnTimer() {   if (this->verticalScrollBar()->isVisible())   {     const int height = this->height();     this->setMinimumHeight(height + 1);   }   else   {     m_timer->stop();   } }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)

This page has been created by the [tool](Tools.htm)
[CodeToHtml](ToolCodeToHtml.htm)