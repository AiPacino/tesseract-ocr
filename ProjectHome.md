Tesseract is probably the most accurate open source OCR engine available. Combined with the [Leptonica Image Processing Library](http://leptonica.com) it can read a wide variety of image formats and convert them to text in over 60 languages. It was one of the top 3 engines in the 1995 UNLV Accuracy test. Between 1995 and 2006 it had little work done on it, but since then it has been improved extensively by Google. It is released under the [Apache License 2.0.](http://www.apache.org/licenses/LICENSE-2.0)

<font size='4'>
<ul><li>ReadMe - Installation and usage information.<br>
</li><li><a href='Compiling.md'>Compiling</a> - How to build Tesseract on a variety of platforms.<br>
</li><li><a href='FAQ.md'>FAQ</a> - Common questions and problems. Please check before <a href='http://code.google.com/p/tesseract-ocr/issues/list'>filing a bug</a> or <a href='https://groups.google.com/forum/?fromgroups#!forum/tesseract-ocr'>consulting the forum.</a>
</li><li><a href='ImproveQuality.md'>Too many errors?</a> - See the guidance on getting the best out of Tesseract.<br>
</font></li></ul>

# Supported Platforms #

Tesseract works on Linux, Windows (with VC++ Express or CygWin) and Mac OSX. See the [ReadMe](ReadMe.md) for more details and install instructions. It can also be compiled for other platforms, including Android and the iPhone, though these are not as well tested platforms. See also the [AddOns](AddOns.md) page for other projects using Tesseract on various platforms.

If you're interested in supporting other platforms or languages, please get in touch with Ray Smith or the [Developers](https://groups.google.com/forum/?fromgroups#!forum/tesseract-dev).

# A Note about Downloads #

With the discontinuation of downloads at code.google.com, new source downloads will be posted to [GoogleDrive](https://drive.google.com/folderview?id=0B7l10Bj_LprhQnpSRkpGMGV2eE0&usp=sharing). Other download folders will be setup as new files are uploaded, and the original Downloads page will go away. During the transition, other downloads can still be found at the [Old Downloads](https://code.google.com/p/tesseract-ocr/downloads/list) page.

# Roadmap #

Version 3.03 release candidate is now available (source only so far) for download and contains many new features. (See the ReleaseNotes for a full list.) Please check out the [ReadMe](http://code.google.com/p/tesseract-ocr/wiki/ReadMe) before going to  [Downloads](http://code.google.com/p/tesseract-ocr/downloads/list) as you need more than one file. **Even the windows executables tarball is incomplete as language files are required.** Most notable new features:

  * PDF output.
  * New `Renderer` for extracting detailed recognition information at a document level.

# Core Developers #

The core developer on the project is Ray Smith (theraysmith).

In related work, Thomas Breuel (tmbdev) and Ilya Mezhirov (mezhirov) work on the [OCRopus](http://www.ocropus.org/) project, which also provides layout analysis and statistical language modeling.

Most of the work on Tesseract is sponsored by Google.