**Note:** This wiki expects you to be familiar with compiling software on your operation system.

# Linux / Other Unices #

## Dependencies ##

  * Autotools
  * [Leptonica](http://www.leptonica.org/)

If they are not already installed, you need the following libraries (Ubuntu):
```
sudo apt-get install autoconf automake libtool
sudo apt-get install libpng12-dev
sudo apt-get install libjpeg62-dev
sudo apt-get install libtiff4-dev
sudo apt-get install zlib1g-dev
sudo apt-get install libicu-dev      # (if you plan to make the training tools)
sudo apt-get install libpango1.0-dev # (if you plan to make the training tools)
sudo apt-get install libcairo2-dev   # (if you plan to make the training tools)
```

You also need to install [Leptonica](http://www.leptonica.org/). There is an apt-get package libleptonica-dev, **but if you are using an oldish version of Linux, the Leptonica version may be too old, so you will need to build from source.**

3.01 requires at least v1.67 of Leptonica.<br>
3.02 requires at least v1.69 of Leptonica. (Both available in Ubuntu 12.04 Precise Pangolin.)<br>
3.03 requires at least v1.70 of Leptonica. (Both available in Ubuntu 14.04 Trusty Tahr.)<br>
The sources are at <a href='http://www.leptonica.org/'>http://www.leptonica.org/</a>. The instructions at <a href='http://www.leptonica.org/source/README.html'>Leptonica README</a> are clear, but basically it is as described in <a href='#Compilation.md'>Compilation</a> below.<br>
<br>
Ensure that the development headers for Leptonica are installed before compiling Tesseract. Note that if building Leptonica from source, you may need to ensure that /usr/local/lib is in your library path. This is a standard Linux bug, and the information at <a href='http://stackoverflow.com/questions/4743233/is-usr-local-lib-searched-for-shared-libraries'>Stackoverflow</a> is very helpful.<br>
<br>
<h2>Compilation</h2>

Tesseract uses a standard autotools based build system, so the compilation process should be familiar.<br>
<br>
<pre><code>./autogen.sh<br>
./configure<br>
make<br>
sudo make install<br>
sudo ldconfig<br>
</code></pre>

On some systems autotools does not create m4 directory automatically (giving the error: "configure: error: cannot find macro directory 'm4'"). In this case you must create m4 directory (<code>mkdir m4</code>), and then rerun the above commands starting with ./configure.<br>
<br>
If you want the training tools (3.03), you will also need to run the following commands:<br>
<br>
<pre><code>make training<br>
sudo make training-install<br>
</code></pre>

Build of training tools is not available if you do not have necessary dependencies (pay attention to messages from ./configure script).<br>
<br>
<br>
<h2>Install elsewhere / without root</h2>

Tesseract can be configured to install anywhere, which makes it possible to install it without root access.<br>
<br>
To install it in $HOME/local:<br>
<br>
<pre><code>./autogen.sh<br>
./configure --prefix=$HOME/local/<br>
make install<br>
</code></pre>

To install it in $HOME/local using Leptonica libraries also installed in $HOME/local:<br>
<br>
<pre><code>./autogen.sh<br>
LIBLEPT_HEADERSDIR=$HOME/local/include ./configure \<br>
  --prefix=$HOME/local/ --with-extra-libraries=$HOME/local/lib<br>
make install<br>
</code></pre>


<h2>Language Data</h2>

<ol><li>Download langugage data file (e.g. 'wget <a href='http://tesseract-ocr.googlecode.com/files/tesseract-ocr-3.01.eng.tar.gz'>http://tesseract-ocr.googlecode.com/files/tesseract-ocr-3.01.eng.tar.gz</a>' for 3.01 version)<br>
</li><li>Decompress it ('tar xf tesseract-ocr-3.01.eng.tar.gz')<br>
</li><li>Move it to installation of tessdata (e.g. 'mv tesseract-ocr/tessdata $TESSDATA_PREFIX' if defined TESSDATA_PREFIX)</li></ol>

You can also use:<br>
<pre><code>export TESSDATA_PREFIX=/some/path/to/tessdata<br>
</code></pre>
to point to your tessdata directory (example: if your tessdata path is '/usr/local/share/tessdata' you have to use 'export TESSDATA_PREFIX='/usr/local/share/').<br>
<br>
<br>
<h1>Windows</h1>

<h2>3.02</h2>

For tesseract-ocr 3.02 please follow instruction in <a href='http://tesseract-ocr.googlecode.com/svn/trunk/vs2008/doc/setup.html#using-the-latest-tesseractocr-sources'>Visual Studio 2008 Developer Notes for Tesseract-OCR</a>.<br>
<br>
<h2>3.01</h2>

Download these packages from the <a href='http://code.google.com/p/tesseract-ocr/downloads/list'>Downloads</a> page:<br>
<br>
<ul><li><code>tesseract-&lt;version&gt;.tar.gz</code> - Tesseract source<br>
</li><li><code>tesseract-&lt;version&gt;-win_vs.zip</code> - Visual studio (2008 & 2010) solution with necessary libraries<br>
</li><li><code>tesseract-ocr-&lt;version&gt;.eng.tar.gz</code> - English language file for tesseract (or download other language training file)</li></ul>

Unpack them to one directory (e.g. <code>tesseract-3.01</code>). Note that <code>tesseract-ocr-&lt;version&gt;.eng.tar.gz</code> names the root directory <code>'tesseract-ocr'</code> instead of <code>'tesseract-&lt;version&gt;'</code>.<br>
<br>
Windows relevant files are located in vs2008 directory (e.g. 'tesseract-3.01\vs2008'). The same build process as usual applies: Open tesseract.sln with VC++Express 2008 and build all (or just Tesseract.) It should compile (in at least release mode) without having to install anything further. The dll dependencies and Leptonica are included. Output will be in tesseract-3.01\vs2008\bin (or tesseract-3.01\vs2008\bin.rd or tesseract-3.01\vs2008\bin.dbg based on configuration build).<br>
<br>
<h2>Mingw+Msys</h2>

For Mingw+Msys have a look at blog <a href='http://www.sk-spell.sk.cx/compiling-leptonica-and-tesseract-ocr-with-mingwmsys'>Compiling Leptonica and Tesseract-ocr with Mingw+Msys</a>.