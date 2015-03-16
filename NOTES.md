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
