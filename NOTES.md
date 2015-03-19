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
