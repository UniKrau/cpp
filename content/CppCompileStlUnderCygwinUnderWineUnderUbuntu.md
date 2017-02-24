s

[Go back to Richel Bilderbeek's homepage](index.htm).

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

 

 

 

 

 

([C++](Cpp.htm)) [Compiling STL code under Cygwin under Wine under Ubuntu](CppCompileStlUnderCygwinUnderWineUnderUbuntu.htm)
============================================================================================================================

 

[Compiling STL code under Cygwin under Wine under
Ubuntu](CppCompileStlUnderCygwinUnderWineUnderUbuntu.htm) is expected to
be the simplest example of [compiling under Cygwin under Wine under
Ubuntu](CppCompilingUnderCygwinUnderWineUnderUbuntu.htm), while [running
Cygwin under Wine](CppCygwinUnderWine.htm) under Ubuntu. The goal of
[compiling under Cygwin under Wine under
Ubuntu](CppCompileUnderCygwinUnderWineUnderUbuntu.htm) is to
[port](CppPort.htm) code from Linux to Windows.

 

 

 

 

 

Environment
-----------

 

Operating system: [Ubuntu](http://www.ubuntu.com) 10.04 LTS Lucid Lynx

[IDE](CppIde.htm): [Qt Creator](CppQtCreator.htm) 2.0.0

[Project type](CppQtProjectType.htm): console application

[Compiler](CppCompiler.htm): [G++](CppGpp.htm) 4.4.1

[Libraries](CppLibrary.htm) used:

-   [STL](CppStl.htm): from [GCC](CppGcc.htm), shipped with [Qt
    Creator](CppQt.htm) 2.0.0

Project options:

-   Unchecked 'Projects -&gt; Build settings -&gt; General -&gt; Shadow
    build' (so code and makefile are in the same folder)

 

 

 

 

 

[Qt project file](CppQtProjectFile.htm)
---------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #------------------------------------------------- # # Project created by QtCreator 2010-09-29T10:39:29 # #------------------------------------------------- QT       += core QT       -= gui TARGET = CppCompileStlUnderCygwin CONFIG   += console CONFIG   -= app_bundle TEMPLATE = app SOURCES += main.cpp `
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

main.cpp
--------

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream>  int main() {   std::cout     << "I am\n"     << "* written using Qt Creator under Ubuntu\n"     << "* tested to compile under Ubuntu\n"     << "* tested to create an Ubuntu binary\n"     << "* tested to compile under Cygwin under Wine under Ubuntu\n"     << "* tested to create a Windows executable\n"; }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Process
-------

 

I wrote and compiled the code above, zipped entire folder with code and
makefile, unpacked at
'\~/.wine/drive\_c/cygwin/home/richel/CppCompileStlUnderCygwin'.

 

Trying to make the project (as the makefile is made by Qt Creator)

 

  -----------
  ` $ make`
  -----------

 

Screen output:

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` /usr/bin/qmake-qt4 -spec /usr/share/qt4/mkspecs/linux-g++ -unix CONFIG+=debug -o Makefile CppCompileStlUnderCygwin.pro /usr/bin/qmake-qt4: /usr/bin/qmake-qt4: cannot execute binary file make: *** [Makefile] Error 126`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Examining the makefile:

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ``  ############################################################################# # Makefile for building: CppCompileStlUnderCygwin # Generated by qmake (2.01a) (Qt 4.6.2) on: Wed Sep 29 10:43:01 2010 # Project:  CppCompileStlUnderCygwin.pro # Template: app # Command: /usr/bin/qmake-qt4 -spec /usr/share/qt4/mkspecs/linux-g++ -unix CONFIG+=debug -o Makefile CppCompileStlUnderCygwin.pro #############################################################################  ####### Compiler, tools and options  CC            = gcc CXX           = g++ DEFINES       = -DQT_CORE_LIB -DQT_SHARED CFLAGS        = -pipe -g -Wall -W -D_REENTRANT $(DEFINES) CXXFLAGS      = -pipe -g -Wall -W -D_REENTRANT $(DEFINES) INCPATH       = -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4 -I. LINK          = g++ LFLAGS        =  LIBS          = $(SUBLIBS)  -L/usr/lib -lQtCore -lpthread  AR            = ar cqs RANLIB        =  QMAKE         = /usr/bin/qmake-qt4 TAR           = tar -cf COMPRESS      = gzip -9f COPY          = cp -f SED           = sed COPY_FILE     = $(COPY) COPY_DIR      = $(COPY) -r STRIP         = strip INSTALL_FILE  = install -m 644 -p INSTALL_DIR   = $(COPY_DIR) INSTALL_PROGRAM = install -m 755 -p DEL_FILE      = rm -f SYMLINK       = ln -f -s DEL_DIR       = rmdir MOVE          = mv -f CHK_DIR_EXISTS= test -d MKDIR         = mkdir -p  ####### Output directory  OBJECTS_DIR   = ./  ####### Files  SOURCES       = main.cpp  OBJECTS       = main.o DIST          = /usr/share/qt4/mkspecs/common/g++.conf \         /usr/share/qt4/mkspecs/common/unix.conf \         /usr/share/qt4/mkspecs/common/linux.conf \         /usr/share/qt4/mkspecs/qconfig.pri \         /usr/share/qt4/mkspecs/features/qt_functions.prf \         /usr/share/qt4/mkspecs/features/qt_config.prf \         /usr/share/qt4/mkspecs/features/exclusive_builds.prf \         /usr/share/qt4/mkspecs/features/default_pre.prf \         /usr/share/qt4/mkspecs/features/debug.prf \         /usr/share/qt4/mkspecs/features/default_post.prf \         /usr/share/qt4/mkspecs/features/warn_on.prf \         /usr/share/qt4/mkspecs/features/qt.prf \         /usr/share/qt4/mkspecs/features/unix/thread.prf \         /usr/share/qt4/mkspecs/features/moc.prf \         /usr/share/qt4/mkspecs/features/resources.prf \         /usr/share/qt4/mkspecs/features/uic.prf \         /usr/share/qt4/mkspecs/features/yacc.prf \         /usr/share/qt4/mkspecs/features/lex.prf \         /usr/share/qt4/mkspecs/features/include_source_dir.prf \         CppCompileStlUnderCygwin.pro QMAKE_TARGET  = CppCompileStlUnderCygwin DESTDIR       =  TARGET        = CppCompileStlUnderCygwin  first: all ####### Implicit rules  .SUFFIXES: .o .c .cpp .cc .cxx .C  .cpp.o:     $(CXX) -c $(CXXFLAGS) $(INCPATH) -o "$@" "$<"  .cc.o:     $(CXX) -c $(CXXFLAGS) $(INCPATH) -o "$@" "$<"  .cxx.o:     $(CXX) -c $(CXXFLAGS) $(INCPATH) -o "$@" "$<"  .C.o:     $(CXX) -c $(CXXFLAGS) $(INCPATH) -o "$@" "$<"  .c.o:     $(CC) -c $(CFLAGS) $(INCPATH) -o "$@" "$<"  ####### Build rules  all: Makefile $(TARGET)  $(TARGET):  $(OBJECTS)       $(LINK) $(LFLAGS) -o $(TARGET) $(OBJECTS) $(OBJCOMP) $(LIBS)  Makefile: CppCompileStlUnderCygwin.pro  /usr/share/qt4/mkspecs/linux-g++/qmake.conf /usr/share/qt4/mkspecs/common/g++.conf \         /usr/share/qt4/mkspecs/common/unix.conf \         /usr/share/qt4/mkspecs/common/linux.conf \         /usr/share/qt4/mkspecs/qconfig.pri \         /usr/share/qt4/mkspecs/features/qt_functions.prf \         /usr/share/qt4/mkspecs/features/qt_config.prf \         /usr/share/qt4/mkspecs/features/exclusive_builds.prf \         /usr/share/qt4/mkspecs/features/default_pre.prf \         /usr/share/qt4/mkspecs/features/debug.prf \         /usr/share/qt4/mkspecs/features/default_post.prf \         /usr/share/qt4/mkspecs/features/warn_on.prf \         /usr/share/qt4/mkspecs/features/qt.prf \         /usr/share/qt4/mkspecs/features/unix/thread.prf \         /usr/share/qt4/mkspecs/features/moc.prf \         /usr/share/qt4/mkspecs/features/resources.prf \         /usr/share/qt4/mkspecs/features/uic.prf \         /usr/share/qt4/mkspecs/features/yacc.prf \         /usr/share/qt4/mkspecs/features/lex.prf \         /usr/share/qt4/mkspecs/features/include_source_dir.prf \         /usr/lib/libQtCore.prl     $(QMAKE) -spec /usr/share/qt4/mkspecs/linux-g++ -unix CONFIG+=debug -o Makefile CppCompileStlUnderCygwin.pro /usr/share/qt4/mkspecs/common/g++.conf: /usr/share/qt4/mkspecs/common/unix.conf: /usr/share/qt4/mkspecs/common/linux.conf: /usr/share/qt4/mkspecs/qconfig.pri: /usr/share/qt4/mkspecs/features/qt_functions.prf: /usr/share/qt4/mkspecs/features/qt_config.prf: /usr/share/qt4/mkspecs/features/exclusive_builds.prf: /usr/share/qt4/mkspecs/features/default_pre.prf: /usr/share/qt4/mkspecs/features/debug.prf: /usr/share/qt4/mkspecs/features/default_post.prf: /usr/share/qt4/mkspecs/features/warn_on.prf: /usr/share/qt4/mkspecs/features/qt.prf: /usr/share/qt4/mkspecs/features/unix/thread.prf: /usr/share/qt4/mkspecs/features/moc.prf: /usr/share/qt4/mkspecs/features/resources.prf: /usr/share/qt4/mkspecs/features/uic.prf: /usr/share/qt4/mkspecs/features/yacc.prf: /usr/share/qt4/mkspecs/features/lex.prf: /usr/share/qt4/mkspecs/features/include_source_dir.prf: /usr/lib/libQtCore.prl: qmake:  FORCE     @$(QMAKE) -spec /usr/share/qt4/mkspecs/linux-g++ -unix CONFIG+=debug -o Makefile CppCompileStlUnderCygwin.pro  dist:      @$(CHK_DIR_EXISTS) .tmp/CppCompileStlUnderCygwin1.0.0 || $(MKDIR) .tmp/CppCompileStlUnderCygwin1.0.0      $(COPY_FILE) --parents $(SOURCES) $(DIST) .tmp/CppCompileStlUnderCygwin1.0.0/ && $(COPY_FILE) --parents main.cpp .tmp/CppCompileStlUnderCygwin1.0.0/ && (cd `dirname .tmp/CppCompileStlUnderCygwin1.0.0` && $(TAR) CppCompileStlUnderCygwin1.0.0.tar CppCompileStlUnderCygwin1.0.0 && $(COMPRESS) CppCompileStlUnderCygwin1.0.0.tar) && $(MOVE) `dirname .tmp/CppCompileStlUnderCygwin1.0.0`/CppCompileStlUnderCygwin1.0.0.tar.gz . && $(DEL_FILE) -r .tmp/CppCompileStlUnderCygwin1.0.0   clean:compiler_clean      -$(DEL_FILE) $(OBJECTS)     -$(DEL_FILE) *~ core *.core   ####### Sub-libraries  distclean: clean     -$(DEL_FILE) $(TARGET)      -$(DEL_FILE) Makefile   mocclean: compiler_moc_header_clean compiler_moc_source_clean  mocables: compiler_moc_header_make_all compiler_moc_source_make_all  compiler_moc_header_make_all: compiler_moc_header_clean: compiler_rcc_make_all: compiler_rcc_clean: compiler_image_collection_make_all: qmake_image_collection.cpp compiler_image_collection_clean:     -$(DEL_FILE) qmake_image_collection.cpp compiler_moc_source_make_all: compiler_moc_source_clean: compiler_uic_make_all: compiler_uic_clean: compiler_yacc_decl_make_all: compiler_yacc_decl_clean: compiler_yacc_impl_make_all: compiler_yacc_impl_clean: compiler_lex_make_all: compiler_lex_clean: compiler_clean:   ####### Compile  main.o: main.cpp      $(CXX) -c $(CXXFLAGS) $(INCPATH) -o main.o main.cpp  ####### Install  install:   FORCE  uninstall:   FORCE  FORCE:  ``
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

My guess would be to add '-spec win32-g++' as an additional qmake
argument in Qt Creator.

 

  -----------
  ` $ make`
  -----------

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ``  make -f Makefile.Debug make[1]: Entering directory `/home/richel/CppCompileStlUnderCygwin' g++ -c -g -Wall -DUNICODE -DQT_LARGEFILE_SUPPORT -DQT_CORE_LIB -I"/usr/include/qt4/QtCore" -I"/usr/include/qt4" -I"debug" -I"/usr/share/qt4/mkspecs/win32-g++" -o debug/main.o main.cpp /bin/sh: g++: command not found make[1]: *** [debug/main.o] Error 127 make[1]: Leaving directory `/home/richel/CppCompileStlUnderCygwin' make: *** [debug] Error 2 ``
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Changing 'g++' to 'g++-4', changed the error, but did not result in an
executable.

 

Try to compile by hand:

 

  ------------------------------
  ` $ g++-4 -o MyWin main.cpp`
  ------------------------------

 

Screen output:

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` /usr/lib/gcc/i686-pc-cygwin/4.3.4/../../../../i686-pc-cygwin/bin/as.exe: /usr/lib/gcc/i686-pc-cygwin/4.3.4/../../../../i686-pc-cygwin/bin/as.exe: cannot execute binary file`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Follow the approach described in \[1\]:

 

\[not yet done\]

 

 

 

 

 

[References](CppReferences.htm)
-------------------------------

 

1.  [Michal Cihar's
    blog](http://blog.cihar.com/archives/2009/01/12/cygwin_in_wine):\
      ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      `     So let's try to compile Gammu in it. First attempt fails, because Cygwin symlinks do not work in Wine. But there is an easy workaround - just copy as.exe and ld.exe instead of symlinks and now even the compiler works.     `
      ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[Go back to Richel Bilderbeek's C++ page](Cpp.htm).

[Go back to Richel Bilderbeek's homepage](index.htm).

 

[![Valid XHTML 1.0 Strict](valid-xhtml10.png){width="88"
height="31"}](http://validator.w3.org/check?uri=referer)