# Notes

## utnik on scribus-users-de/forum

transparenzen reduzieren kann scribus bisher nicht, also musst du diese entweder durch workarounds (z.b. vorgängiges flachrechnen in gimp) vermeiden, mit höheren .pdf-versionen als 1.3 leben oder die transparenzen nachträglich mit werkzeugen wie 'acrobat' reduzieren – ein gratis-tool kenne ich dafür nicht.

## antonio_mo on scribus-users-de/forum

Das Reduzieren/Verflachen von Transparenz besteht darin, dass betreffende Bereiche des Dokuments von der Anwendung in kleine Teilbereiche gesplittet werden die den ursprünglichen Eindruck wiedergeben

Daher ist die Auflösung, genauso wie der Farbraum bei der PDF-Ausgabe wichtig, weil bei der Transparenzreduzierung alles in Pixelbilder umgewandelt wird.

Es gibt native (Live-) Transparenz, oder verflachte/reduzierte Transparenz.

native (Live-) Transparenz: Darunter versteht man nicht verflachte Transparenzen. deren Parametrierung im Nachhinein im Ursprungsprogramm noch möglich ist!

Live-Transparenzen können dabei in den nativen Formaten von Photoshop (.psd), Illustrator (.ai), in Dateien der PDF-Versionen 1.4 und höher sowie auch in TIFF enthalten sein.

Verflachte/reduzierte Transaprenz:

also jedes transparente Objekt sowie Objekte wie Text, Grafik, oder Bild die mit einer Transparenz in Berührung kommen, werden verflacht, wenn sie ausgegeben werden oder in einem Dateiformat abgespeichert werden das keine Live-Transparenz speichern kann!

Zu diesen Dateiformaten gehören u.a. EPS, jpeg, GIF, BMP und die PDF-Versionen 1.3 und niedriger.

EPS/PostScript unterstützt keine Transparenz (und wird auch nie welche unterstützen, da Adobe seit mehr als 10 Jahren EPS/PostScript nicht weiter entwickelt) ausser ein Illustrator-EPS, weil in dieser Datei 2 Versionen gespeichert werden, öffnet man das Illu.-EPS nicht in Illu. hat man verflachte Transparenz, öffnet man es in Illustrator wird die Live-Transparenz dargestellt!


## julius on scribus-user.de/forum3

mit Ghostscript erzeugt folgender Befehl eine PDF1.3-Datei:

    gs -o output.pdf -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 Test.pdf

Die Transparenzen werden reduziert, Hyperlinks bleiben bestehen, dummerweise rastert Ghostscript aber den Text (vielleicht gibt’s dafür ja eine Lösung), grrr... Meinem Verständnis nach würde es ja reichen, wenn Ghostscript alle Objekte, die Transparenzen verwenden oder mit solchen Überschneidungen besitzen, rastert.

## ale on scribus/forum

there are reasons, both practical and theoretical, that have lead me to push for the opposite way of doing: scribus should not be able to *directly* print at all!

why?

on the one side, printing is a difficult job and you have to deal with many differences both on the side of the OS (linux, bsd, os x, windows, os 2, haiku...), the printer drivers and the printer.
i believe that a specialized tool like a pdf viewerwill always do a better job. trying to manage the printing from scribus only diverts from the real goal of scribus: letting the user creating amazing layouts!

on the theoretical side, from the beginning scribus has chosen to target PDFs. it'a software geared towards creation of a PDF to be sent to a print shop and get professionally printed.
if you use a different subset to print to your home printer before you send your job to the print shop, you might get a wrong preview!
being forced to produce a PDF, display on your monitor and then print it, might help you catch some glitches, since your feeding your home printer with the same data you will send to the print shop.

and for the lazy guys among us, i personally, would prefer a "print command" that creates a PDF in the background and then launches your preferred PDF viewer and print it... but since on some systems the print function does indeed work as intended, the team sticks with the current situation.
and lets us explain all this to the many people that are deceived by scribus not being able to print...

## nermander on the mailing list

Bleed is tha area outside the page edge where Scribus will crop content,
however the PDF size may be larger to accomodate crop marks etc (they have
to be outside the bleed area to prevent them from being covered by bleed
content).

Good PDF tools will be aware of the different PDF boxes (trim, bleed, media
etc) and a PDF "larger than necessary" won't be a problem. Unfortunately
most free PDF tools don't handle the PDF boxes well.

## william bader on the mailing list

(not free content, but posted by jluc on the wiki as cc-by-sa and the original author has been notified about it)

An EPS has only a single BoundingBox but a PDF contains a MediaBox, CropBox, BleedBox, TrimBox and ArtBox.
For a description, see http://www.prepressure.com/pdf/basics/page-boxes

For an advertisement, ArtBox is the content of the ad; TrimBox is the size that an application like Scribus should use to place the ad; BleedBox is the size that applications like Scribus should clip to; CropBox is the size for proofing the ad for viewers but is not supposed to be used by applications like Scribus; MediaBox is for complete pages including items that will be physically trimmed from the final product like crop marks, registration marks, slugs, etc.

Some viewers like "gv" have an option to let you override the displayed area.
The poppler package has the capability also, for example, pdftops crops to the CropBox by default but has a -nocrop option to use the MediaBox instead.

On Linux, you can check the values with pdfinfo in the poppler package with the -box option.

~~~
$ pdfinfo -box 20185846-crop.pdf 
Producer:       Acrobat Distiller 3.0 for Power Macintosh
CreationDate:   Thu Dec 11 16:40:22 2003
ModDate:        Fri Dec 12 13:09:10 2003
...
Page size:      415.79 x 1009.81 pts
Page rot:       0
MediaBox:           0.00     0.00   432.00  1152.00
CropBox:            7.89    16.19   423.68  1026.00
BleedBox:           7.89    16.19   423.68  1026.00
TrimBox:            7.89    16.19   423.68  1026.00
ArtBox:             7.89    16.19   423.68  1026.00
File size:      464073 bytes
Optimized:      yes
PDF version:    1.4
~~~

jluc says on the mailing list:

Here are a few links to pages illustrating the boxes with images.

- http://www.plda.net/en/Examples/UserGuide/PageBoxes.aspx
- https://acrobatusers.com/tutorials/finding-page-boundaries
- http://stackoverflow.com/questions/13236370/pdf-bleed-detection

(I just did an image search on google for "PDF boxes" and picked the good
images)

The relevant Adobe PDF specification:   <http://www.adobe.com/content/dam/Adobe/en/devnet/acrobat/pdfs/PDF32000_2008.pdf>, section 14.11.2.2 "Display of Page Boundaries" on page 630.

## Pdf and size

utnik says in the forum:

Images can be part of the problem:  
afaik scribus doesn't crop images to the visible part when they overlap the frame.  
if your layout contains large images with edges overlapping the frame, you should crop them with an image processor like 'gimp'…


Nermander say in the forum:

Fonts and placement of text are the most common ploblems.

When it comes to fonts, a unicode Open Type font may be as big as 10-15 MB. Embed several fonts and your PDF becomes very big.

Scribus usually places each glyph individually. This means Scribus will "relocate the cursor" for each glyph in the text.

Most other programs just "place the cursor" at the start of the line and then put a string of glyphs starting at that point. 

# imposition

j'essaye d'être bref pour être plus clair :-)

- ce n'est pas conseillé d'imprimer directement depuis scribus. c'est mieux de créer un pdf et de l'impimer par la suite.
- adobe reader a une fonction livret: c'est la meilleure solution pour imprimer un livret sur une imprimante de bureau. il n'y a rien de spécial à faire dans scribus. c'est possible que d'autres lecteurs de pdf aient cette fonctionalité.
- c'est aussi possible de définir une suite de pages dans scribus et ensuite utiliser pdfnup pour créer un livret. ici https://github.com/CoderDojoZH/resources/tree/master/cards#producing-the-a4-pdf-and-its-png-preview tu peuv voir comment j'ai placé 4 pages créées dans scribus sur une feuille A4 (la suite et les commandes pour un livret sont légerement différentes mais pas trop :-)
- ce n'est pas une bonne idée d'avoir du texte qui passe à travers le pli: il y a peu de chances que ça soit lisible à l'impression. sur des imprimantes de bureau j'éviterais aussi tout fond perdu (et si c'est un imprimeur qui va imprimer ton PDF ça sera sa tâche de trier les pages et de faire les découpages)


## ink coverage

kaspar and jghali in the bug tracker

I have a problem with "total ink density" parameter Scribus 1.4.5 generated PDF file.

### Question
Case A:  
I use Scribus for making a cover for a book. Design is tiff file made with Gimp. I converted RGB file to CMYK file. The result of the command "identify -verbose cover-CMYK.tiff" is: "Total ink density: 270%" and "Profiles: Profile-icc: 1829087 bytes SC paper (ECI)". That is ok. If I add this file to Scribus and export to PDF/X-1a file, the result of "identify -verbose cover.pdf" is: "Total ink density: 400%" and "Profiles:" rows is not existing.

Case B:  
I use Scribus for making the content of the book in grayscale. If I export this to PDF1.3 file the result of "identify -verbose book.pdf" is: "Total ink density: 400%" but should be "Total ink density: 270%".

The problem seems to be Scribus, not ICC profile. When I use ImageMagick (convert cover-RGB.tiff +profile icm -profile /usr/share/color/icc/AdobeRGB1998.icc -profile /usr/share/color/icc/SC_paper_eci.icc cover-CMYK.pdf) to make a PDF file, I get the result: "Total ink density: 296%".

### Answer

There is no issue. The issue comes from an ImageMagick limitation vs prepress requirements. The 400% ink limit found by ImageMagick identify comes from PDF marks located outside of bleed zones, noticeably registration marks. Those marks use a special colors called registration color which by definition and for technical reason use 100% for each ink. In production, those 400% are not a problem because those marks are thin and outside the page.

PDF has a concept of page zones. The most important are the TrimBox and BleedBox which defines zones where elements which should be found in the final product appear. Those boxes are all defined by in PDF exported by Scribus. The area located between TrimBox and BleedBox is cut during the production process (with a small margin of error). The various marks are located outside these zones. ImageMagick "identify" scan also those elements while they could be avoided.

Fyi, Acrobat shows that the max ink coverage inside bleed box is 270% in both cases A and B.

	Additional info: professional preflight checkers such as Pitstop Pro consider elements position when checking for ink coverage. They are able to detect in which PDF page zone each element is located and are able to skip elements which are outside a specific page zone.

Kriks:	Just a note: you can add "-define pdf:use-trimbox=true" to your identify command (before the filename), but it still doesn't gives the 270% (my result is 295.686%).  
I don't know where the difference comes from. 

## Fonts emebdding, subsetting, and outlining

Starting with 1.5.1:

"in font subsetting done by Andreas, the subset options now
does exactly what it says: with most of today fonts a real subset will be produced, the
Type3 subset option being now mostly used by old Postscript Type 1 fonts. Same the outline
mode will do what it says, the font will be really vectorized in order to respond to the
need of print shops which do not want to see any trace of font, even Type 3, in the files
they receive. [...]
True vectorization can be achieved with the "Outline all fonts" mode. But that will affect
all fonts. [...]
In "Dont Embed" mode Fonts are not embedded at all in any kind of form. So that's a mode which you should use
only at your own risk. Mostly suited for simple forms. I would not mind completely removing that mode btw." (jean, ML, 14.1.2016)

The meaning of "outline" is different in 1.5.0 and 1.5.1. In 1.5.0, "outline" was really meaning "subset as a Type 3 font". 1.5.1 can now export true CFF and TrueType subsets so using Type 3 subsets is not desirable anymore. The uses of Type 3 subsets also did not provide what some users wanted ie true conversion of text to paths. So in 1.5.1, "outline" means just that, full conversion of text to paths without any use of font in the final PDF. This way of exporting text respond to use case where you do not want any font to be present in the final PDF while being able to print reliably. Hence the different behavior in 1.5.1.  (jean, bug tracker, 2016-03-03 02:08)

## All letter "l"s bold in *.pdf file

Nermander in the forum on 28.1.2016:

"The problem is when the content (in this case the glyph) is sized och positioned with a higher resolution than the output device (in this case the monitor).

Just rounding the numbers does not work, that's why fonts include "hinting" information. That information tells how the numbers should be rounded so that the glyph is not distorted to much.

When a font is converted to outlines, it is no longer a font, thus there is no hinting information available. So what you see is "rounding errors".

<https://www.typotheque.com/articles/hinting>
<http://alistapart.com/column/font-hinting-and-the-future-of-responsive-typography>" 

# Why are the PDFs created by OS X much smaller?

you mostly can sefely distribute the "os x" pdfs... it's probably the better choice if your goal is to get the people to view the pdf on their monitor or print on their home printer.

for the pdf you're sending to the print shop, you'd probably want to use the scribus own pdf engine: it gives you a finer control and more options.

## ale on irc

Why can Scribus create good PDFs but it does not reliably print?

PDF is a clear defined target that scribus supports correctly (for the things it supports).
Printing depends on your specific printer, on the driver you've installed, on the printing subsystem (postscript, hp, ...)...

This beeing said, printing should work correctly on windows.  
On mac and linux scribus can be configured to work correctly. And, then, it will work as you would expect.

but, if it does not work correctly with the default settings, the effort you'll need to get it to work is way too big and you'd better create
a pdf and use a pdf viewer to print your pdf.

- btw, printing a normal b/w a4 document should work correctly.
- landscape is hard
- colors might be hard.

