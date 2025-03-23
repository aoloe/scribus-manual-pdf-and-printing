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

## erfahrungsberichte über transparenzen in pdf aus scribus-user.de/forum

http://www.scribus-user.de/forum/viewtopic.php?f=5&t=319&p=2193

- carlos:  Ich habe jetzt einen Testflyer mit Transparenzen bei http://www.online-druck.biz in Auftrag gegeben, denn die bieten als einzige Online-Druckerei PDF/X-4 an. Und siehe da, der Druck war perfekt, der Preis sowieso.
- tipper: für Ceweprint kann ich noch melden: Transparenzen wurden bei mir (2015) ordentlich verarbeitet aus einem PDF 1.4 aus Scribus 1.4.5. Ich hatte einen PDF-Proof bestellt, der war nur noch PDF 1.3 und die Transparenzen waren ordentlich reduziert, sah gut aus.

laser antowrtet darauf: Das würde mich auch interessieren - denn in dem von Scribus erzeugten pdf 1.4 ist ja keine Transparenz mehr vorhanden.  
Cewe schreibt auch ausdrücklich, daß keine Transparenzen erlaubt sind. (Ich laß da auch öfter drucken.)

Wir müssen uns aber noch darauf einigen, daß mit Transparenz diese in Prozent gemeint ist. 100% Transparenz bereitet keine Probleme!  
Keine Hintergrundfarbe bei einem Textrahmen z.B., oder Transparenz bei einem png.  
Aber legt mal über ein Bild einen weißen Rahmen mit 60% Transparenz (40% Deckkraft), um das Bild an der Stelle heller zu machen - der wird im pdf komplett weiß. Schlagschatten arbeiten auch mit prozentualen Transparenzen und tauchen deshalb im pdf gar nicht auf. (Alle Angaben für pdf, die keine Transparenz können.)

tipper: Doch! Die von Scribus 1.4.5 erzeugte 1.4-PDF-Datei enthält echte Transparenzen. Das ist ein Feature von PDF 1.4. Für den PDF-Proof hat Ceweprint in der eigenen Engine die Transparenzen reduziert und mir zur Kontrolle ein PDF 1.3 geschickt (das keine echten Transparenzen mehr enthalten kann).  
Das war das Zeichen dafür, daß sie die echten Transparenzen aus meiner Datei verstanden haben. Weil ich das auf der Ceweprint-Webseite auch gelesen hatte ("keine Transparenzen"), hab ich angerufen und den Tip mit dem Softproof bekommen. Genauer: ich sollte die Bestellung abschicken mit bestelltem Softproof, eine halbe Stunde nach Datenübermittlung anrufen und zum bestehenden Auftrag mitteilen, daß die Transparenzen ernst gemeint sind. Hab ich dann auch so gemacht, hat geklappt. 
[...]  
Eine PDF/X-3 ist technisch eine PDF 1.3 mit zusätzlichen Anforderungen* und kann keine Transparenzen enthalten (per Definition nicht, kein Manko von Scribus).  
Eine PDF/X-4 ist technisch mindestens eine PDF 1.4 (oder 1.6) mit zusätzlichen Anforderungen* und kann echte Transparenzen enthalten


## julius on scribus-user.de/forum

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

## page and paper size

### nermander on the mailing list

Bleed is tha area outside the page edge where Scribus will crop content,
however the PDF size may be larger to accomodate crop marks etc (they have
to be outside the bleed area to prevent them from being covered by bleed
content).

Good PDF tools will be aware of the different PDF boxes (trim, bleed, media
etc) and a PDF "larger than necessary" won't be a problem. Unfortunately
most free PDF tools don't handle the PDF boxes well.

### william bader on the mailing list

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

### Getting the right page size according to the printer's specification

http://forums.scribus.net/index.php/topic,2243.msg10260.htm

TSRAlex asks: The print-company wants to have the PDF in a size of 89x59mm (see here their example here: http://www.saxoprint.de/Librarys/global/saxoprint/docs/templates/de/pdf/85x55mm_landscape_2s.pdf) and I made - for my understanding  :-\  - everything right for, but the result is a size of 91x61mm!  

"Der Sicherheitsbereich von 3 mm wird mitgedruckt. Das Endformat Ihrer Visitenkarte beträgt 85 x 55 mm - mit Randanschnitt (welcher weggeschnitten wird) sollte die Datei 89 x 59 mm groß sein. Alle Schriften/Logos etc. sollten sich innerhalb des Bereiches 79 x 49 mm befinden um bei Ausreizen der Toleranzen nicht in den Beschnitt zu gelangen."

utnik answers: the following settings will lead to your desired .pdf file:

- document size: 85×55 mm
- bleeds: 2 mm
- margins: 3 mm (just to keep your content within the safe zone of 79×49 mm)

utnik says:

here’s my assumption: if you change the document size after its creation, you have to manually apply the change to the existing page(s) and master pages (if you want to apply the change to all existing and future pages).  
go to `file > document setup` again, make sure that the settings are correct and under `apply settings to:` check ` all document pages` and `all master pages`.

Nermander explains: "Individual pages in a document can have completely different sizes, that is why a change to the document setup does not automatically change the size of all pages. You need to explicitly tell Scribus that you want the change to affect pages that have already been created."

## Pdf and file size

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
- Bookblet:
  - https://github.com/HornPenguin/Booklet
  - https://www.reddit.com/r/bookbinding/comments/xmesw2/my_own_imposition_software/
- https://github.com/pdfjam/pdfjam
- https://github.com/momijizukamori/bookbinder-js / https://momijizukamori.github.io/bookbinder-js/

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

## Why are the PDFs created by OS X much smaller?

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

## Pdfs and fonts

jean says: honnêtement, je ne sais combien de fois j'ai déja mentionné que les polices OTF ne peuvent être incorporées dans les fichiers PDF <= 1.5. Elles sont subset: dans ce cas les polices OTF sont incorporées sous forme de jeux partiels en tant que police PostScript CFF


## ll letter "l"s bold in pdf file

Dave Barber in the forums: Best solution I have found is open Adobe Reader - Edit - Preference - select page display - uncheck Enhance Thin Line.

mnawij in the forums: It happens with Adobe Illustrator and InDesign outlined fonts as well as CorelDraw fonts converted to curves.  I believe that it is a problem with "hinting" after the font is converted to a vector object.  As long as it prints to a postscript printer and looks correct there should be no problem.

Since 1.5.2 it should be not so much of a problem anymore, since Scribus normally converts the font to a Type 1 one, instead of a real outlining (except when asked to do so).

## color management for beginners

in the bug tracker jean [says](https://bugs.scribus.net/view.php?id=13069#c39808):

When exporting to print PDF, I recommend to users who are not color management aware to not enable any of the "use profile" options in PDF export dialog. However color management should be enabled in the color management options of document setup. In those options I recommend to enable the black point compensation. As a generic CMYK profile, the ISOCoated v2 300 (bas) gives god results, it can be downloaded from here:
http://colormanagement.org/de/isoprofile2009.html#ISOcoated_v2_300_bas [^]

The "use profile" options should be enabled when working in a color managed workflow. In the case of digital presses there are also benefits in doing so. Two cases here:
- press/rip are configured so as to simulate a traditional press: leaving images as RGB will avoid a CMYK -> CMYK conversion, better to avoid that when possible as any further processing might affect image quality
- press/rip are configured to use press full gamut: digital presses can indeed often reproduce a wider range of colors than traditional presses. In such condition, unless the press profile is at disposal, preconverting RGB image to CMYK will produce suboptimal results. Letting the RIP do so will produce more colorful results. 

## avox on irc on fonts embedding

9.2016: Scribus creates Type3 fonts for embedding which look heavier than properly subsetted or embedded fonts.

## PDF Versions

The most common PDF versions in use are 1.4, 1.5 and X/1-a.

Depending on the device/printer you're targetting, you will choose a different version. Be aware, that the different versions also have different requirements and you have to fullfill some of them before being able to select that PDF version.

You should also select the matching pdf version in the preflight verifier, so that you get meaningful warnings. and then squash all the warnings before producing the PDF.

- If your targetting a print shop you should use the PDF version the print shop is expecting. If you don't know about such a requirement, you should target PDF 1.4 but avoid using transparencies and gradients.
- If your targetting a home / office printer, you should use PDF 1.4. Transparencies and gradients are ok.
- If you want to distribute the PDF on the web you should use PDF 1.4 and use the "size reduction script" to improve the internal structure of the PDF.

Of course you have multiple targets, you can create multiple PDFs and use each one in the right context.


## ale on facebook

afaict in scribus there is no such thing as an export to cmyk...

of course, this does not mean that you cannot export to cmyk.

there are two ways of achieving this:

- you can use only CMYK resources (pictures and colors!) and export with "screen/web" as a target. but this is risky
- or you can add the correct CMYK profile (it should match the printer being used to give you the expected results) and then export with "printer" as a target. you should probably not check any other option.

## Exporting shows different/dull colours to those in scribus

some (many) RGB colors aren't printable in a regular cmyk process.  
either you work wit spot colors (expensive), or you live with the limitations of process colors. (utnik)

the only way for a good approximation of the colors that will be printed, is to (correctly) enable the color management.

using CMYK colors in scribus will only help, if your goal is to avoid using colors that are not printable at all (except if your picking the cmyk colors from a printed catalog or from the corporate identity guidelines).
but on the monitor you will always see an RGB representation of the CMYK color. and without CMS that will or not reliably match what you will get from the printer.
simply using CMYK colors probably will not really help if you want to avoid dull colors...

and if you really want a good matching, you'll probably also need to calibrate the monitor...

## hints from libregrahpics production

http://libregraphicsproduction.com/workflow/print-preparation


## doubts about scribus' outputs details

```
joesber> Hi! I'm using Scribus-svn (1.5.4), trying to create a table of content. But I can't select any destination frame or paragraph style on: file/document setup/table of contents
<joesber> could it be a bug?
<joesber> I had created before one item called "Index" on: File/document setup/document items se
<joesber> And I tried also to add the atribute on a text frame, but it doens't show up on the list
<a-l-e> the solution is (imo) not to use the table of contents...
<joesber> Nice ;P
<a-l-e> seriously, with the current way the toc is implemented you'd better type your titles and page numbers by hand.
<joesber> I'm layouting a book with 150 tales and 150 autors, and it would be hard to type that amount of names
* yvan has quit (Remote host closed the connection)
* yvan (~yvan@2a01:e35:2ef8:a3d0:e494:e048:debb:708e) has joined
<a-l-e> do the list outside of scribus...
<a-l-e> you have to type the titles in the properties again...
<a-l-e> a solution might be to open the pdf with libreoffice, create a toc in there and then import he toc in scribus... it might or not work correctly.
* joesber_ (~joesber@20.red-79-151-78.dynamicip.rima-tde.net) has joined
* estan (~astan@kde/developer/astan) has joined
<estan> hi folks. when checking "Crop Marks" during PDF export, it seems they are always placed 1 mm in from the bleed (?). how do i control this?
* yvan has quit (Remote host closed the connection)
* yvan (~yvan@2a01:e35:2ef8:a3d0:e494:e048:debb:708e) has joined
<estan> e.g. this shows both the bleed marks and crop marks in the exported PDF: https://imgur.com/a/KLQlx , how can i control the distance between them?
<estan> i'd like it to be zero, i want my crop marks to be exactly at the bleed/non-bleed boundary.
<a-l-e> estan, when exporting to pdf, in the pre-press tab, you can set an offset... is this what you are looking for?
<estan> a-l-e: i tried that, but it seems to have no effect (it's also set to 0 by default).
<estan> what i did was: create a document, give it a 3 mm bleed, export to pdf and check "Crop Marks". i had expected the crop marks to be at the bleed/non-bleed boundary (3 mm from the edge of the exported pdf). but it was an additional 2 mm in.
<estan> (i said wrong when i said 1 mm, it's actually 2)
<a-l-e> mmm... i would say that having the marks on the bleed will give you a risk that they get printed...
<estan> also, how can i control the length of the crop marks? 3 mm is too long, since i have a 3 mm bleed. the ends of the crop marks meet exactly, which is not good.
<estan> get printed? i want them to get printed, how else would the printer see them when he/she is to cut?
<a-l-e> printed in the uncut area...
<a-l-e> anyway, if you think that the way scribus renders the crop marks does not meet the needs of your print shop, please report a ticket in https://bugs.scribus.net with a description of the printer needs that justify your request...
<estan> but that's impossible, the crop marks normally don't meet at their inner ends (though in my case they do, since the default length of them is too long for me).
<estan> alright hm. well i need to get this done today. it's this art print i'm helping my wife with.
<estan> but i'll try to work around it somehow.
<estan> in my case, i just want a pdf with crop marks 3 mm from the edge of the exported pdf. i thought i would get that if i create a document with 3 mm bleed and check "Crop Marks".
<a-l-e> well, what counts is what your print shop wants...
<estan> they want 3 mm bleed and crop marks.
<a-l-e> i cannot judge if what you want is the right thing or not, sorry.
<a-l-e> well, i have no evidence that scribus does snot provide 3mm bleed and crop marks in a way that your printshop cannot use them.
<a-l-e> can use them...
<estan> hm okay. well i entered 3 mm bleed when i created the document, and the bleed margins in the document shows that, it's just that when i check "Crop Marks" and export, the crop marks are an additional 2 mm in from the bleed area, which seems arbitrary, and i can't find a way to change that.
<a-l-e> estan, do you know what you are doing or do you think it does not look correct?
<a-l-e> i really don't know what your skills are in print matters... all i know is that many people tend not to trust what scribus does...
<a-l-e> ... and suppose that things are not right when they are.
<a-l-e> normally, the scribus marks can be used by print shop.
<a-l-e> s
<a-l-e> as said, if you *know* that what scribus is doing is wrong, please please fill a ticket and explain it.
<a-l-e> it will be fixed!
<a-l-e> but if you think that it does not look right or it does not look nice... just trust scribus.
<a-l-e> other people have used the feature and it did work.
<estan> well it's not wrong per se, and i do know what bleed and crop marks are. i know in many cases you do want bleed and then the crop marks a bit inward from that. but in my case i'm only interested in getting the crop marks 3 mm in from the (PDF page) edge.
<a-l-e> as said, what matters is what your print shop needs, not what you want.
<estan> also, no matter what workaround i come up with (i can increase my page size to account for the 2 mm offset scribus seems to have hardcoded), the crop marks are too big. they are 3 mm long.
<a-l-e> it might sound hard, but you're not the first one who argues about things scribsu is doing right.
<estan> if i export a PDF and want the crop marks 3 mm from the edge, 3 mm long crop marks is too long since they will meet exactly, which makes me run the risk of them being printed.
<a-l-e> estan, i really don't understand why you don't trust scribus to do the right thing.
<estan> a-l-e: it's not about right or wrong. do you disagree that scribus has hardcoded the length of the crop marks to 3 mm? what should i do if i need to create a pdf with a 3 mm bleed area?
<a-l-e> i don't disagree with anything, but i think that you're misunderstooding what crop marks are.
<a-l-e> it's just about the print shop being able to correctly cut the paper.
<a-l-e> if they can do it with what scribus provides, it's fine. if they cannot, it's a bug.
<a-l-e> scribus and the print shop don't really care what you think about it. it might sound hard, but it's about what counts...
<estan> i know perfectly well what crop marks are. instructions from my printer are clear: they want a 3 mm bleed, and crop marks 3 mm in from the PDF document edge.
<estan> but because scribus gives me no way of controlling the length of the crop marks (they are 3 mm long), this is what i end up with: https://imgur.com/a/swwvf
<estan> and that's no good, it means the crop marks meet eachother at their inner end.
<a-l-e> if you know that this is wrong, please fill a ticket!
<a-l-e> if you're correct it will be changed.
<a-l-e> i cannot do magic nor tell you more.
<a-l-e> to me those crop marks look fine. but i'm not a big expert in the topic.
<estan> fine? if they meet like that, the printer will run the risk of getting some of the vertical mark on the printed page when doing the horizontal cut and vice versa.
<a-l-e> estan, what do you want me to do?
<estan> crop marks need to be separated by some distance at their inner end.
<a-l-e> i cannot tell you more than: if you know you're right, please fill a ticket: https://bugs.scribus.net
<estan> i will file a ticket unless one has already been filed.
<a-l-e> thanks!
<estan> you said you thought the crop marks looked fine, so i just tried to explain why they are not in this case, no harm meant!
<estan> i did find https://bugs.scribus.net/view.php?id=7793 which sounds like it's about precisely this.
<estan> but i can't find the setting they speak of. i think it's that offset setting you mentioned, but that seems to have no effect on the length of the crop mark here.
<jghali> estan, 1in 1.5.x there is both an offset option + mark length option in prepress tab of pdf export dialog
<jghali> 1.4.x miss the length option iirc
```

## checking that the scribus pdf only contains cmyk resources

- make sure that you are exporting with the "printer" target
- if you have activated the color management, make sure that you have a profile for the printer that is for cmyk (the default one should be ok, if you have not activated it)
- open the created pdf with scribus:
  - make sure that the color editor only shows cmyk colors
  - use the `extra > images" manager to check that all iamges are cmyk

Warning: images that contain transparences are delivered by poppler as RGB images plus the _alpha_ information and Scribus will import them as PNGs. In such cases, on Linux can use `pdfimages` (with Tiff as a target) to extract the images and check that the PDF indeed contains CMYK images.

## Exporting to CMYK images

[undertaker](http://www.linuxgraphic.org/forums/viewtopic.php?f=20&t=8323):

En continuant mes recherches, j'ai appris qu'il existe un greffon pour GIMP qui permet de créer un TIFF avec séparation quadrichromique (qui crée 1 calque pour chacune des couleurs CMJ et N) : "Separate+". 
Le fichier est alors très bien traité chez l'imprimeur. Pour l'envoyer, et selon les directives de l'imprimeur, il est parfois conseillé de l'inclure dans une archive .zip pour gagner un peu de place.
