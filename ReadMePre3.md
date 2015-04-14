## Installation Notes - Tesseract 3.01 ##

### General ###

**IMPORTANT: 3.01 is not backwards compatible with 2.04.** The data files are different. (Single file per language among other things.) You therefore need to make sure you connect your new executable with the new data files.

Another important change is that you should **really** be using TessBaseAPI if you are linking with another program. In Linux (non-Windows) the main library is now libtesseract\_api.a (in case of creating multiplelibs solution) or libtesseract.a (in case of onelib solution) instead of the old libtesseract\_full.a.

The command line is:
```
tesseract <image> <outputbasename> [-l lang] [configs]
```
In the executable, page layout analysis is enabled by default. You may need to turn it off to process small images. No command-line control for this yet. Sorry. See tesseractmain.cpp.

The training process is described on separate [wiki page](http://code.google.com/p/tesseract-ocr/wiki/TrainingTesseract3).

Use the most recently available language files for the languages that you want.

### Linux ###
If they are not already installed, you need the following libraries (Ubuntu):
```
sudo apt-get install autoconf automake libtool
sudo apt-get install libpng12-dev
sudo apt-get install libjpeg62-dev
sudo apt-get install libtiff4-dev
sudo apt-get install zlib1g-dev
```

You also need to install [Leptonica](http://www.leptonica.org/). There is an apt-get package libleptonica-dev, **but if you are using an oldish version of Linux, the Leptonica version may be too old, so you will need to build from source.** 3.01 requires at least v1.67 of Leptonica. The sources are at http://www.leptonica.org/. The instructions at [Leptonica README](http://www.leptonica.org/source/README.html) are clear, but basically it is the usual
```
./autogen.sh
./configure
make
sudo make install
sudo ldconfig
```

Now back to Tesseract. Download the source package [tesseract-3.01.tar.gz](http://tesseract-ocr.googlecode.com/files/tesseract-3.01.tar.gz) from [download page](http://code.google.com/p/tesseract-ocr/downloads/list). If you are developer you can try to [install tesseract from the subversion repository](http://code.google.com/p/tesseract-ocr/wiki/TesseractSvnInstallation).

The same build process as usual applies:
```
./autogen.sh
./configure
make
sudo make install
sudo ldconfig
```

On some systems autotools did not create m4 directory  automatically (you got error: "`configure: error: cannot find macro directory 'm4'`"). In this case you must create m4 dicrectory by yourself before running `./configure`:
```
mkdir -p m4
```

Between configure and make, you can check that everything has worked by looking at config\_auto.h.

You can also use:
```
export TESSDATA_PREFIX=/some/path/to/tessdata
```
to point to your tessdata directory (example: if your tessdata path is '/usr/local/share/tessdata' you have to use 'export TESSDATA\_PREFIX='/usr/local/share/'). The command line for running tesseract is:
```
tesseract <image> <outputbasename> [-l lang] [configs]
```

Install language data:

  1. Download langugage data file (e.g. 'wget http://tesseract-ocr.googlecode.com/files/tesseract-ocr-3.01.eng.tar.gz' for 3.01 version)
  1. Decompress it ('tar xf tesseract-ocr-3.01.eng.tar.gz')
  1. Move it to installation of tessdata (e.g. 'mv tesseract-ocr/tessdata $TESSDATA\_PREFIX' if defined TESSDATA\_PREFIX)


### Windows ###

There is [windows installer](http://code.google.com/p/tesseract-ocr/downloads/detail?name=tesseract-ocr-setup-3.01.exe) for Tesseract-OCR 3.01 including English language data. Other language data can be downloaded and installed from installer. Installer adapt PATH environment of current user (e.g. user that installed tesseract) and setup TESSDATA\_PREFIX environment variable for current user.

If you have problem to run it, please check if you have installed [Microsoft Visual C++ 2008 SP1 Redistributable Package (x86)](http://www.microsoft.com/download/en/details.aspx?id=5582&WT.mc_id=MSCOM_EN_US_DLC_DETAILS_121LSUS007998).

The dll isn't supported in Tesseract-OCR 3.00/3.01.

#### Installation from source ####

Download these packages:
  * [tesseract-3.01.tar.gz](http://tesseract-ocr.googlecode.com/files/tesseract-3.01.tar.gz) - tesseract source
  * [tesseract-3.01-win\_vs.zip](http://tesseract-ocr.googlecode.com/files/tesseract-3.01-win_vs.zip) - Visual studio (2008 & 2010) solution with necessary libraries
  * [tesseract-ocr-3.01.eng.tar.gz](http://tesseract-ocr.googlecode.com/files/tesseract-ocr-3.01.eng.tar.gz) - English language file for tesseract (or download other 3.01 or 3.00 language datafile)

Unpack them to one directory ('tesseract-3.01'). tesseract-ocr-3.01.eng.tar.gz has wrong name of root directory ('tesseract-ocr' instead of 'tesseract-3.01').

Windows relevant files are located in vs2008 directory (e.g. 'tesseract-3.01\vs2008'). The same build process as usual applies:
Open tesseract.sln with VC++Express 2008 and build all (or just Tesseract) It should compile (in at least release mode) without having to install anything further. The dll dependencies and Leptonica are included. Output will be in tesseract-3.01\vs2008\bin (or tesseract-3.01\vs2008\bin.rd or tesseract-3.01\vs2008\bin.dbg based on configuration build).

If you want to use code from svn please check [Visual Studio 2008 Developer Notes for Tesseract-OCR](http://tesseract-ocr.googlecode.com/svn/trunk/vs2008/doc/setup.html#using-the-latest-tesseractocr-sources).

## Support ##

If you need support please try to search and use [tesseract user forum](http://groups.google.com/group/tesseract-ocr) or [tesseract developer forum](http://groups.google.com/group/tesseract-dev). It is good to read [wiki pages](http://code.google.com/p/tesseract-ocr/wiki)  before posting on forum.


## Installation Notes - Tesseract 2.04 ##

### Linux ###

Installation process is the same as for version 3.01 just use correct [source](http://tesseract-ocr.googlecode.com/files/tesseract-2.04.tar.gz) and language data for Tesseract 2.0x.

### Windows ###

**There is no windows installer!** There are windows executables: `tesseract-2.04.exe.tar.gz` (It is not for the 'exe' language.) They are built with VC++ express 2008 and come with absolutely no warranty. If they work for you then great, otherwise get Visual C++ Express 2008 with service pack 1 and build from the source.  You can also try tesseract-2.01.exe.tar.gz, which is built with VC++6, and may work better if your windows is old, but note that this is an older version of Tesseract.

If you are building from the [sources](http://tesseract-ocr.googlecode.com/files/tesseract-2.04.tar.gz), there are still (up to v2.04) `.dsw` and `.dsp` files for vc++6, but the recommended build platform is now VC++ Express 2008. There are also `.sln` and `.vcproj` files for VC++ Express 2008, but these files are not backward compatible with any previous version - not even VC++ Express 2005. Note that the executables produced  with the newer compiler are smaller, faster, and, believe it or not, _more accurate._ (See [TestingTesseract.](http://code.google.com/p/tesseract-ocr/wiki/TestingTesseract))

**New with 2.04:** the executables are built with static linking, so they stand more chance of working out of the box on more windows systems.

The executable must reside in the same directory as the tessdata directory. (The Visual Studio projects build the release executable directly to the correct place!)

The command line is:
```
tesseract <image.tif> <output> [-l <langid>]
```

For interfacing to other applications, there is a DLL included with the executables, but you may be better off building it yourself. The DLL is NOT built for static C-Runtime, so you will probably need VC++ Express 2008 to run it.

The dll has been updated to allow input of non-binary images. (Thanks to Glen of Jetsoft.)


### Non-Windows (or Cygwin) ###

You have to tell Tesseract through a standard unix mechanism where to find
its data directory. You must either:
```
./configure
make
make install
```
to move the data files to the standard place, or:
```
export TESSDATA_PREFIX="directory in which your tessdata resides/"
```

In either case the command line is:
```
tesseract <image.tif> <output> [-l <langid>]
```
**New** there is a tesseract.spec for making rpms. (Thanks to Andrew Ziem for the help.)
It might work with your OS if you know how to do that.

If you are linking to the libraries, as Ocropus does, there is now a single master
library called libtesseract\_full.a.

Libtiff support should now be properly working via configure, but **note that you need libtiff-dev,** as that contains the header files required to compile the code that uses it.


# History: #

The engine was developed at Hewlett Packard Laboratories Bristol and
at Hewlett Packard Co, Greeley Colorado between 1985 and 1994, with some
more changes made in 1996 to port to Windows, and some C++izing in 1998.
A lot of the code was written in C, and then some more was written in C++.
Since then all the code has been converted to at least compile with a C++
compiler. Currently it builds under Linux with gcc4.0, gcc4.1 and under Windows
with VC++2008 Express. The C++ code makes heavy use of a list system using macros.
This predates stl, was portable before stl, and is more efficient than stl
lists, but has the big negative that if you do get a segmentation violation,
it is hard to debug. Another "feature" of the C/C++ split is that the C++
data structures get converted to C data structures to call the low-level C
code. This is ugly, and the C++izing of the C code is a step towards
eliminating the conversion, but it has not happened yet.

The most recent change is that Tesseract can now recognize 33 languages, is fully UTF8 capable, and is fully trainable. See TrainingTesseract for more information on training.

Tesseract was included in UNLV's Fourth Annual Test of OCR Accuracy. See http://www.isri.unlv.edu/downloads/AT-1995.pdf. With Tesseract 2.00, scripts are now included to allow anyone to reproduce some of these tests. See [TestingTesseract](http://code.google.com/p/tesseract-ocr/wiki/TrainingTesseract) for more details.


# About the Engine #

This code is a raw OCR engine. It has **NO OUTPUT FORMATTING, and NO UI.** It can detect fixed pitch vs proportional text.
Having said that, in 1995, this engine was in the top 3 in terms of character accuracy, and it compiles and runs on both Linux and Windows. Training code IS included in the open source release however, and is now included for those willing to try.