These are instructions for installing Tesseract from the Subversion repository. You should be ready to face unexpected problems.

# Installing With Autoconf Tools #

In order to do this, you must have aclocal, autoheader, autoconf, automake, libtool and leptonica installed.

On Debian or Ubuntu, you can probably do that with:

```
    apt-get install autoconf automake libtool libleptonica-dev
```

Afterwards, the steps for installing the SVN version of Tesseract, do this:

```
    svn checkout http://tesseract-ocr.googlecode.com/svn/trunk/ tesseract-ocr
    cd tesseract-ocr
    ./autogen.sh
    ./configure
    make
    sudo make install
    sudo make install-langs
    sudo ldconfig
```

On some systems autotools did not create m4 directory  automatically (you got error: "`configure: error: cannot find macro directory 'm4'`"). In this case you must create m4 dicrectory by yourself before running `./configure`:
```
mkdir -p m4
```

If you get error:

```
make  all-recursive
Making all in ccstruct
/bin/sh ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -
I..  -I../ccutil -I../cutil -I../image -I../viewer -I/opt/local/
include -I/usr/local/include/leptonica  -g -O2 -MT blobbox.lo -MD -MP -
MF .deps/blobbox.Tpo -c -o blobbox.lo blobbox.cpp
mv -f .deps/blobbox.Tpo .deps/blobbox.Plo
mv: rename .deps/blobbox.Tpo to .deps/blobbox.Plo: No such file or
directory
make[3]: *** [blobbox.lo] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
```

try to run _autoreconf -i_ after _./autogen.sh_

# Windows Visual Studio build #

Please follow instructions in [Visual Studio 2008 Developer Notes for Tesseract-OCR](http://tesseract-ocr.googlecode.com/svn/trunk/vs2008/doc/index.html)