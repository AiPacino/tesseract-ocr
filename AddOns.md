# External Tools, Wrappers And Projects #


## Tesseract box editors and traning tools ##

Platform support depends on used language and experience of user.

### For Tesseract-OCR 3.0x ###


#### Box file editors ####

| **Name** | **Last update** | **Language** | Multipage support |
|:---------|:----------------|:-------------|:------------------|
| [jTessBoxEditor](http://vietocr.sourceforge.net/training.html) | March 2015 | Java | yes |
| [QT Box Editor](http://zdenop.github.com/qt-box-editor/) | July 2013 | C++, Qt4/Qt5 | yes |
| [tesseract-box-editor](http://code.google.com/p/tesseract-box-editor/) | Feb 2013 | .NET 4 | yes |
| [Tesseract-OCR boxfile AJAX editor](http://pp19dd.com/tesseract-ocr-chopper/) | March 2012 | online tool |
| [cowboxer](http://code.google.com/p/cowboxer/) | Jan 2012 | C++, Qt4 | no |
| [moshPyTT ](http://code.google.com/p/moshpytt/) | Feb 2011 | Python, GTK2 | no |
| [pytesseracttrainer](http://code.google.com/p/pytesseracttrainer/) | Jan 2011 | Python, GTK2 | no |


### For Tesseract-OCR 2.0x ###


#### Box file editors ####

| **Name** | **Last update** | **Language** |
|:---------|:----------------|:-------------|
| [Tesseract-OCR boxfile AJAX editor](http://pp19dd.com/tesseract-ocr-chopper/) | March 2012 | online tool |
| [owlboxer](http://code.google.com/p/owlboxer/) | Jul 2010 | C++, Qt4 |
| [Tessboxer](http://sites.google.com/site/spilkaondrej) | Jun 2009 | .NET |
| [boxfilereader.php](http://tesseract-ocr.googlecode.com/files/boxfilereader.php) | Mar 2009 |  php |
| [tessboxes](http://www.lbreyer.com/tessboxes.html) | Nov 2008 | C |
| [JTesseract](http://code.google.com/p/jtesseract/) |  Oct 2008 | C# |
| [wx-tetra](http://code.google.com/p/wx-tetra/) | Sep 2008 | perl, wx  |
| [bbtesseract](http://code.google.com/p/bbtesseract/) | Jul 2008 | VB.NET 2008 |


## Other Training Tools ##

  * [MzTesseract](https://github.com/mazluta/MzTesseract) - MS Windows program that can train new langauge from top to bottom
  * [FrankenPlus](https://github.com/this-is-ari/python-tesseract-3.02-training) - tool for creating font training for Tesseract OCR engine from page images. More information about Franken+ is at at [IT'S ALIVE!](http://emop.tamu.edu/node/54Franken+:) and [Franken+ homepage](http://dh-emopweb.tamu.edu/Franken+/).
  * [python-tesseract-3.02-training](https://github.com/this-is-ari/python-tesseract-3.02-training) - script to automate the generation of Tesseract 3.02 training files
  * [tesseract-box-file](https://code.google.com/p/tesseract-box-file/) - autoit script to make editing the box file easier
  * [Serak Tesseract Trainer for Tesseract 3.02](https://code.google.com/p/serak-tesseract-trainer/) - a front end GUI for training tesseract 3.02
  * [BoxMaker](http://reza1615.github.com/index.html) is online tool for generating image&box pair. Offline version is available in download section of [PersianOCR project](https://github.com/reza1615/PersianOcr/downloads)
  * [boxFactory](http://www.dinosaursandmoustaches.com/boxFactory.php) is a tool for quickly creating box files to train the Tesseract OCR engine. You can identify characters in the image by simply drawing boxes around them..
  * https://github.com/BaltoRouberol/TesseractTrainer - TesseractTrainer is a simple Python API, taking over the tedious process of manually training Tesseract3
  * [tess\_school](https://github.com/ddohler/tess_school) - a set of handy scripts to make the tesseract training process a bit easier
  * [txt2img](http://code.google.com/p/txt2img/): Qt GUI application that generate image and box file based on text imput
  * [DangAmbigs Generator](http://www.cs.toronto.edu/~mreimer/tesseract.html): Creates a DangAmbigs file automatically given a set of OCR text output and correct text. _Requirements:_ Python
  * [train.ps1](http://sourceforge.net/p/vietocr/code/HEAD/tree/jTessBoxEditor/trunk/tools/): Windows powershell script for Automate Tesseract 3.01 language data pack generation process.
  * [Update unicharambigs.exe](http://code.google.com/p/tesseract-ocr/issues/detail?id=544): A small (windows) C# program for editing "lang.unicharambigs" file
  * [train\_tess.pl](http://code.google.com/p/tesseract-ocr/issues/detail?id=640): perl script to facilitate training


## Community training projects ##

  * **tesseract-georgian**: https://github.com/ddohler/tesseract-georgian
  * **Polish Fraktur**: training as [result of the IMPACT project](http://dl.psnc.pl/activities/projekty/impact/results/), [trained dataset](http://dl.psnc.pl/download/tesseract_traineddata.zip)
  * **Ancient Greek**: http://ancientgreekocr.org/
  * **Chinese simplefied**: see issue [296](http://code.google.com/p/tesseract-ocr/issues/detail?id=296); download http://ubuntuone.com/p/3Yw/
  * **Indic**: http://code.google.com/p/tesseractindic/, https://github.com/debayan/Tesseract-Indic-OCR/
  * **Indian and South Asian languages**: http://code.google.com/p/parichit/
  * **Irish uncial**: http://code.google.com/p/tesseract-gle-uncial/
  * **Polish**: http://code.google.com/p/tesseract-polish/
  * **Fraktur** (dan, deu, swe):  https://github.com/paalberti/tesseract-dan-fraktur
  * **Hebrew**: http://roidayan.com/wordpress/?p=26, http://code.google.com/p/tesseract-ocr/issues/detail?id=432
  * **Myanmar**: http://code.google.com/p/myaocr/
  * **Persian (Farsi)**: https://github.com/reza1615/PersianOcr
  * **7 segments font**: https://github.com/arturaugusto/display_ocr/tree/master/letsgodigital

## Commercial Training Services ##

  * http://www.tesseract-training.com/


## Tesseract wrappers ##

### Tesseract 3.0x ###

**C wrapper**:
  * 3.02 includes C API
  * for 3.00 (and 3.01?) see http://code.google.com/p/ocrivist/source/browse/#svn%2Ftessintf where is C wrapper with Freepascal bindings

**.Net**:
  * https://github.com/charlesw/tesseract - project offers also [tesseract-ocr 64bit Windows library](https://github.com/charlesw/tesseract/tree/master/src/lib/TesseractOcr/x64)
  * http://code.google.com/p/tesseractdotnet/

**Python**:
  * http://code.google.com/p/python-tesseract/ is a wrapper class for Tesseract OCR that allows any conventional image files (SWIG based)
  * https://github.com/virtuald/python-tesseract-sip - A python SIP wrapper for libtesseract (Apache license)
  * https://github.com/jflesch/pyocr - A python wrapper for Tesseract and Cuneiform
  * https://github.com/gregjurman/tesserwrap - Python bindings to the Tesseract API
  * http://code.google.com/p/pytess/ - A simple SWIG-based interface to Tesseract

**Ruby**:
  * https://github.com/meh/ruby-tesseract-ocr/ - wrapper for tesseract 3.0x using the C++ API
  * https://github.com/dannnylo/rtesseract

**Clojure**: https://github.com/antoniogarrote/clj-tesseract

**Java**: http://tess4j.sourceforge.net/ (JNA wrapper)

**PHP**: https://code.google.com/p/php-tesseract/

**Objective-C**: https://github.com/ldiqual/tesseract-ios


### Tesseract 2.0x ###

**Python**:
  * https://github.com/hoffstaetter/python-tesseract/wiki
  * http://code.google.com/p/pytesser/
  * http://code.google.com/p/tesseract-python (pytesser clone)
  * https://github.com/hoffstaetter/python-tesseract/wiki
  * http://pokerai.org/pf3/viewtopic.php?f=3&t=2677&start=0&st=0&sk=t&sd=a
  * [patches of SWIG wrapper](http://code.google.com/p/tesseract-ocr/issues/detail?id=77) for python

**.NET**: http://www.pixel-technology.com/freeware/tessnet2/

**Java**:
  * http://code.google.com/p/tesjeract (JNI wrapper)
  * http://tess4j.sourceforge.net/ (JNA wrapper)