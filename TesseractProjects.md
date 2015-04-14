# Introduction #

Interested in contributing to Tesseract? Then read on. Here we will gather a list of projects that have been suggested, but nobody is currently working on.


# List of Projects #

## Easy starter project ##
1. Convert old variables to new. There are 2 implementations of tunable parameters (called "variables"), an old C relic, and a new C++ implementation. It would be nice to get all the old C-style variables (variables.h) converted to new C++ style (varable.h). This would enable a tidying up of config files, and a tidying up of the initialization process.

## Bigger, but still fairly basic ##
~~2. Thread safety. It would be useful to gather all the nasty globals together into a Tesseract class, and make the TessBaseAPI instance-based, with a view to making it possible to have two instances of Tesseract running together in the same process. This might be a lot harder than it looks on the surface, but does involve a lot of fairly basic grind.~~ Fixed in 3.01

## Standard output for access to Bounding Boxes ##
~~3. An hOCR output converter might be useful to many people. A lot of people ask for bounding box information, and that might be a good standard way of doing it.~~ Fixed in 3.00

## Useful preprocessing for handwriting ##
4.De-slant for Handwriting (and applicable to italics in machine print). It is common for handwriting to be written with an italic-like slant. The angle of the slant varies with the writer and fashion, but a lot of handwriting, especially older handwriting, is slanted. Italic fonts in machine print duplicate the style to some extent. It is common in handwriting recognition to transform images to straighten-up the writing before recogntion, as this makes it somewhat easier to segment words into characters. This project would apply a de-italicizing normalization to the input, either at the image level or outline level.

## Longer term, harder & requiring deeper knowledge ##
5. Get rid of the polygonal approximation. Recognition accuracy could be more accurate, probably with virtually no loss of speed, by getting rid of the polygonal approximation. It would be relatively easy to convert the character classifier, but we need a new chopper that works directly on the C\_OUTLINEs. Inter-dependent with:

6. Cut the crap. The top-level code uses C++ classes to describe the outlines, blobs, words, etc, but the lower-level classifier code, and the top-level word classifier both use older C-style structs for the same purpose. While it would be nice to get rid of the old completely and use only the new, it would not really be desirable to do it, until we have a chopper that uses the un-approximated edge-step outlines, as then we could eliminate the polygonal approximation step, and the data structures that support them, completely.

7. More integration with ocropus would be useful. Allowing tesseract and ocropus to share the same training data is one possibility.


# Things I would NOT recommend working on #
1. Someone suggested the macro-based list stuff as a candidate for replacement with stl. I will not be incorporating any such changes into the main codebase for 2 reasons:
a. We have been trying to keep stl out of tesseract for a specific reason that I probably shouldn't comment on.
b. Compared to the macro-based lists in tesseract, stl lists are very different, very incompatitble, and IMHO a poor abstraction designed to make them as like vectors as possible, and if you use them the way they are used in tesseract, it would be very slow. Although the rest of stl is very useful, reason (a) still keeps it out of the codebase. It might be possible to sensibly convert the macro-based lists to (mostly) use templates though.

2. Although it is very tempting to try to expand tesseract to new languages, if you did so, you would be overlapping significantly with the work going on at Google. Of course that leaves anyone that wants a different language in the difficult position of either waiting for it to be available, or trying to train it themselves. I will be in a much better position to discuss language compatibility after the next release, by which time there will be much more language support.