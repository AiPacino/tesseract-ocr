# Introduction #

Tesseract 2.0 provides scripts that make it possible to run some of the UNLV tests published in the Fourth Annual Test of OCR Accuracy.
See [AT-1995.pdf](http://stephenvrice.com/images/AT-1995.pdf) (originally available at http://www.isri.unlv.edu/). The main purpose of providing these test scripts is to enable Tesseract users to verify that their installation is correct, and that no architecture-specific problems are causing bad recognition accuracy. It also serves as a benchmark to demonstrate accuracy improvements of each version. Developers working on Tesseract may find the benchmarking tools useful for measuring experimental new modules.

Note that **some** architecture-specific variation is bound to occur. Most of these should be caused by varying treatment and optimization of floating-point arithmetic between compilers. It is also possible of course that there are memory initialization errors that show up as differences between architectures, but we claim to have found most of these already in the unicodeization process.

# Caveat #

You **must** include libtiff in your build to be able to run these tests, as the UNLV images are G4 compressed. Linux users have libtiff included automatically in the build if it is installed. (sudo apt-get install libtiff4-dev is a possible incantation to install it.) On windows, follow the instructions in the ReleaseNotes wiki. Another alternative would be to hack the reorgdata.sh script to convert all the images to uncompressed as it copies them, but that will take significantly more disk space.

Windows users also have to have some unix shell script capability, perhaps via cygwin or equivalent.

# Downloading the images #

The current scripts only cover tests of the 3b, Bb, Mb and Nb test sets. The adaptive thresholding in the open-source Tesseract is not the same as in the original as the original adaptive thresholding was not included in the open source release, so the 8 bit grey image tests would not compare correctly, and the other resolutions, while interesting, do not really serve a useful regression testing purpose.

  1. Goto http://isri-ocr-evaluation-tools.googlecode.com and get 3b.tgz, Bb.tgz, Mb.tgz and Nb.tgz.
  1. Extract the files. It doesn't really matter where in your filesystem you put them, but they must go under a common root so you have directories 3, B, M and N in, for example, `/users/me/ISRI-OCRtk` It is probably better to put them outside of your main tesseract-ocr directory, so that they will not have to move when you get the next version.
  1. Reorganize the files. The lack of tif extensions on the images is inconvenient, so there is a script to reorganize the data to match the rest of the test scripts. cd to `/users/me/ISRI-OCRtk` or wherever 3, B, M and N ended up and run
```
/blah/blah/tesseract-ocr/testing/reorgdata.sh 3B
```
(Substitute your own path to your tesseract root directory.) This makes directories doe3.3B, bus.3B, mag.3B and news.3B.
You can now get rid of 3, B, M, and N unless you want to get some of the
other scanning resolutions out of them.

# Downloading the tools from UNLV #

Download the ISRI toolkit from http://isri-ocr-evaluation-tools.googlecode.com/files/ftk-1.0.tar.gz

If they work for you, use the binaries directly from the bin
directory and put them in tesseract-ocr/testing/unlv
otherwise build the tools for yourself and put them there.

# Running tests #

  1. cd to your main tesseract-ocr dir and Build tesseract.
  1. Run `testing/runalltests.sh` with the root data dir and testname:
```
testing/runalltests.sh /users/me/ISRI-OCRtk tess2.0
```
and go to the gym, have lunch etc.

When complete, there should be a file `testing/reports/tess2.0.summary` that contains the final summarized accuracy report and comparison with the 1995 results.

# Example Results #

Here are some of the results of the 1995 test, taken from [AT-1995.pdf](http://stephenvrice.com/images/AT-1995.pdf) and reformatted to match the output of the Tesseract test tools:

```
Testid  Testset Character               Word                    Non-stopword
                Errors  Acc     Change  Errors  Acc     Change  Errors  Acc     Change
1995    bus.3B  5959    98.14%  0.00%   1631    96.83%  0.00%   1293    95.73%  0.00%
1995    doe3.3B 36349   97.52%  0.00%   7826    96.34%  0.00%   7042    94.87%  0.00%
1995    mag.3B  15043   97.74%  0.00%   4566    96.01%  0.00%   3379    94.99%  0.00%
1995    news.3B 6432    98.69%  0.00%   1946    97.68%  0.00%   1502    96.94%  0.00%
```

(The change column is for the recent tests, and measures the change over these 1995 results.)

The results of Tesseract 2.00 compiled with gcc 4.0.3-1ubuntu5 are:

```
Testid  Testset Character               Word                    Non-stopword
                Errors  Acc     Change  Errors  Acc     Change  Errors  Acc     Change
gcc4.0  bus.3B  6259    98.04%  5.03%   1691    96.71%  3.68%   1313    95.66   1.55%
gcc4.0  doe3.3B 28850   98.03%  -20.63% 7863    96.32%  0.47%   6688    95.13   -5.03%
gcc4.0  mag.3B  14815   97.78%  -1.52%  4396    96.16%  -3.72%  3124    95.37   -7.55%
gcc4.0  news.3B 7533    98.47%  17.12%  1758    97.91%  -9.66%  1220    97.51   -18.77%
gcc4.0  Total   57457   -       -9.92%  15708   -       -1.63%  12345   -       -6.59%
```

The change column shows wild variation in accuracy over the 1995 results, with a 20% reduction in character errors on the doe3.3B test set, but a 17% increase in character errors on the news.3B test set. Since the engine has been completely retrained since the 1995 tests, and it is now running on a different processor with a different compiler, it is difficult to pin down the cause of this wild variation. (It may also be partly due to the absence of the Aspirin package.)

To illustrate what a difference the compiler makes, here are the results from the same code compiled with gcc 4.1.1:

```
Testid  Testset Character               Word                    Non-stopword
                Errors  Acc     Change  Errors  Acc     Change  Errors  Acc     Change
gcc4.1  bus.3B  6258    98.04%  5.02%   1690    96.72%  3.62%   1312    95.67   1.47%
gcc4.1  doe3.3B 28589   98.05%  -21.35% 7864    96.32%  0.49%   6692    95.12   -4.97%
gcc4.1  mag.3B  14800   97.78%  -1.62%  4394    96.16%  -3.77%  3123    95.37   -7.58%
gcc4.1  news.3B 7524    98.47%  16.98%  1759    97.91%  -9.61%  1220    97.51   -18.77%
gcc4.1  Total   57171   -       -10.37% 15707   -       -1.64%  12347   -       -6.58%
```

The error rates are not that different, but there is a slight difference. In contrast, the same code built with VisualC++ Express gives this:

```
Testid  Testset Character               Word                    Non-stopword
                Errors  Acc     Change  Errors  Acc     Change  Errors  Acc     Change
vc++exp bus.3B  6270    98.04%  5.22%   1695    96.71%  3.92%   1315    95.66   1.70%
vc++exp doe3.3B 29098   98.01%  -19.95% 8246    96.14%  5.37%   7038    94.87   -0.06%
vc++exp mag.3B  14981   97.75%  -0.41%  4435    96.12%  -2.87%  3157    95.32   -6.57%
vc++exp news.3B 7548    98.47%  17.35%  1763    97.90%  -9.40%  1224    97.51   -18.51%
vc++exp Total   57897   -       -9.23%  16139   -       1.06%   12734   -       -3.65%
```

This shows a fairly large increase in error rate, and this is after eliminating some use of floating point arithmetic from the code. More dramatically different though, is Visual C++6, which measures up with slightly better word accuracy, but worse character accuracy:

```
Testid  Testset Character               Word                    Non-stopword
                Errors  Acc     Change  Errors  Acc     Change  Errors  Acc     Change
vc6     bus.3B  6298    98.03%  5.69%   1696    96.70%  3.99%   1317    95.65   1.86%
vc6     doe3.3B 29745   97.97%  -18.17% 8105    96.20%  3.57%   6894    94.98   -2.10%
vc6     mag.3B  15036   97.74%  -0.05%  4448    96.11%  -2.58%  3165    95.31   -6.33%
vc6     news.3B 7531    98.47%  17.09%  1745    97.92%  -10.33% 1210    97.53   -19.44%
vc6     Total   58610   -       -8.11%  15994   -       0.16%   12586   -       -4.77%
```

Future work may be directed at making these discrepancies smaller, if not eliminating them completely, on the grounds that where there is variation, there is room for improvement...