# Introduction #

Tesseract is an Open Source OCR engine, available under the [Apache 2.0 license.](http://www.apache.org/licenses/LICENSE-2.0) It can be used directly, or (for programmers) using an [API](http://code.google.com/p/tesseract-ocr/source/browse/trunk/api/baseapi.h). It supports a wide variety of languages.

Tesseract doesn't have a built-in GUI, but there are several available from the [3rdParty](3rdParty.md) page.

# Installation #

There are two parts to install, the engine itself, and the training data for a language.

## Linux ##

Tesseract is available directly from many Linux distributions. The package is generally called 'tesseract' or 'tesseract-ocr' - search your distribution's repositories to find it. Packages are also generally available for language training data (search the repositories,) but if not you will need to [download the appropriate training data](http://code.google.com/p/tesseract-ocr/downloads/list), unpack it, and copy the .traineddata file into the 'tessdata' directory, probably `/usr/share/tesseract-ocr/tessdata` or `/usr/share/tessdata`.

If Tesseract isn't available for your distribution, or you want to use a newer version than they offer, you can [compile your own](Compiling.md). Note that older versions of Tesseract only supported processing .tiff files.

## Mac OS X ##

The easiest way to install Tesseract is with [MacPorts](https://www.macports.org/). Once it is installed, you can install Tesseract by running the command `sudo port install tesseract`, and any language with `sudo port install tesseract-<langcode>`. List of available langcodes can be found on [MacPorts tesseract page](https://www.macports.org/ports.php?by=name&substr=tesseract-).

## Windows ##

An installer is available for Windows from our [download](Downloads.md) page. This includes the English training data.

If you want to use another language, [download the appropriate training data](http://code.google.com/p/tesseract-ocr/downloads/list), unpack it using [7-zip](http://www.7-zip.org), and copy the .traineddata file into the 'tessdata' directory, probably `C:\Program Files\Tesseract OCR\tessdata`.

## Other Platforms ##

Tesseract may work on more exotic platforms too. You can either try [compiling it yourself](Compiling.md), or take a look at the list of [other projects using Tesseract](3rdParty.md).

# Running Tesseract #

Tesseract is a command-line program, so first open a terminal or command prompt. The command is used like this:

```
  tesseract imagename outputbase [-l lang] [-psm pagesegmode] [configfile...]
```

So basic usage to do OCR on an image called 'myscan.png' and save the result to 'out.txt' would be:

```
  tesseract myscan.png out
```

Or to do the same with German:

```
  tesseract myscan.png out -l deu
```

Tesseract also includes a hOCR mode, which produces a special HTML file with the coordinates of each word. This can be used to create a searchable pdf, using a tool such as [Hocr2PDF](http://exactcode.de/site/open_source/exactimage/hocr2pdf). To use it, use the 'hocr' config option, like this:

```
  tesseract myscan.png out hocr
```

More information about the various options is available in the [Tesseract manpage](http://tesseract-ocr.googlecode.com/svn/trunk/doc/tesseract.1.html).

# Other Languages #

Tesseract has been trained for many languages, check for your language on the [Downloads](http://code.google.com/p/tesseract-ocr/downloads/list) page. It can also be trained to support other languages and scripts; for more details see [TrainingTesseract3](TrainingTesseract3.md).

# Development #

Tesseract can also be used in your own project, under the terms of the [Apache License 2.0.](http://www.apache.org/licenses/LICENSE-2.0) It has a fully featured API, and can be compiled for a variety of targets including Android and the iPhone. See the [3rdParty](3rdParty.md) page for a sample of what has been done with it.

Also, it's free software, so if you want to pitch in and help, please do!
If you find a bug and fix it yourself, the best thing to do is to attach the patch to your bug report in the [Issues List](http://code.google.com/p/tesseract-ocr/issues/list)

# Support #

First read the [Wiki](http://code.google.com/p/tesseract-ocr/w/list), particularly the [FAQ](FAQ.md) to see if your problem is addressed there. If not, search the the [Tesseract user forum](http://groups.google.com/group/tesseract-ocr) or the [Tesseract developer forum](http://groups.google.com/group/tesseract-dev), and if you still can't find what you need, please ask us there.

Installation notes for earlier versions have been relocated to a [separate page](http://code.google.com/p/tesseract-ocr/wiki/ReadMePre3)