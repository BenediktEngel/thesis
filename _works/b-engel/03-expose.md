# Exposé

## Problemfeld und Kontext

Im Internet lassen sich schnell unzählige Informationen und Inhalte finden und abrufen. Sowohl jurnalistische Texte, Lexikonartikel, als auch Bedienungsanleitung und Stellenanzeigen lassen sich finden. Diese Inhalte werden meist in Form von HTML-Seiten (Hypertext Markup Language) bereitgestellt, wodurch sie sich einfach über ihre URL (Uniform Resource Locator) in einem Browser öffnen, darstellen und daraufhin betrachten lassen. Zusätzlich können die HTML-Seiten durch den Einsatz von CSS (Cascading Style Sheet) in ein gewüschtes Layout gebracht werden.
Ein Problem hierbei ist jedoch, dass die Verfasser*innen, bzw. Betreibenden der Webseiten jederzeit die Inhalte verändern, an einen anderen Ort verschieben oder löschen können. Dies kann dazu führen, dass Informationen verloren gehen oder nicht mehr auffindbar sind. Zusätzlich wird in der Regel für das Abrufen der HTML-Seiten und eingebetteten Dateien, wenn diese nicht lokal auf dem Computer des Nutzenden vorliegen eine aktive Internetverbindung benötigt.
Um die Informationen auch ohne Internetverbindung verfügbar zu machen, können diese beispielsweise in Form von PDF-Dokumenten gespeichert werden. Bei PDF (Portable Document Format) handelt es sich um ein plattformunabhängiges Dateiformat, welches von Adobe entwickelt wurde und als Standard von der PDF Association weiterentwickelt wird <!-- BELEG -->. PDF-Dokumente können auf jedem Endgerät mit einem PDF-Reader geöffnet werden und sehen unabhängig von Endgerät und Betriebssystem immer gleich aus.

Von der Möglichkeit aus Webinhalten PDF-Dokumente zu erstellen profitieren sowohl Betreibende der Webangebote, als auch die Nutzenden. Betreibende können einen Download als PDF anbieten, ohne das sie die Informationen zweimal aufbereiten müssen, da die Informationen bereits in Form von HTML vorliegen woraus das PDF-Dokument generiert wird. Dies kann beispielsweise bei Stellenanzeigen hilfreich sein, da diese eher kurzlebig sind, aber oft sowohl als HTML-Seite als auch als PDF-Download zur Verfügung gestellt werden. Druch eine Generierung dieses Downloads aus dem Webinhalt könenn hier Zeit und dadurch Kosten gespart werden.
Nutzende profitieren von einer als PDF-Dokument gespeicherten Version der Webinhalte unteranderem dadurch, dass sie diese offline nutzen können, aber auch dadurch, dass sie einen Stand der Informationen zum Zeitpunkt des Abrufs besitzen, welcher sich nicht verändert. Dies kann beispielsweise bei der Recherche von Informationen hilfreich sein. Zusätzlich können die Informationen auch auf einem anderen Endgerät betrachtet werden, ohne das die Informationen erneut aus dem Internet geladen werden müssen.
Die Generierung von PDF-Dokumenten anhand von Webseiten im HTML-Format ist aktuell nur möglich wenn man Abstriche in Kauf nimmt.
Eine Möglichkeit ist die Serverseitige Generierung, hierbei wird die Webseite auf einem Server in einem Headless-Browser aufgerufen, anschließend als PDF-Dokument gespeichert und durch den Nutzenden heruntergeladen. Hierbei wird jedoch ein zusätzlicher Server benötigt, welcher durch Anschaffung und Betrieb zusätzliche Kosten verursacht. 
Eine weitere Möglichkeit ist die Clientseitige Generierung durch eine JS-Bibliothek (JavaScript). Hierbei stehen einige verschiedene Bibliotheken bereit welche unteranderem aus dem HTMl-Inhalt ein PDF-Dokument generieren können. Hierbei arbeiten die Bibliotheken meist mit der Methode, dass die Webseite auf die gewünschte Seitenbreite des PDFs skaliert wird und anschließend ein Bild des Inhalts, ähnlich einem Bildschirmfoto, in der Größe einer PDF-Seite erstellt wird. Die daraus entstehnden Bilder werden anschließend in das PDF-Dokument eingefügt. Dadurch kommt es dazu, dass es sich nur noch um ein Bild handelt und jeglicher Text nicht mehr als Text sondern als Teil des Bilds vorliegt. Dies hat zur Folge, dass der Text nicht mehr markiert, kopiert oder durchsucht werden kann. Dadurch verlieren die Inhalte auch ihre Semantik welche sie als Teil der HTML-Seite besitzen.
Eine dritte Möglichkeit ist die Generierung von PDF-Dokumenten durch den Druckdialog des Browsers. Denn statt einen Drucker auszuwählen, steht hier auch die Möglichkeit `Als PDF speichern` zur Verfügung. Im Gegensatz zu der Clientseitigen Generierung durch eine Bibliothek ist hierbei jeglicher Text immernoch Text, welcher markiert, kopiert und durchsucht werden kann. Ein Nachteil dieser Variante ist jedoch das die Browser standardmäßig Hintergrundfarben von Elementen entfernen um im wirklichen Druck Farbe zu sparen. Dadurch sehen die Inhalte jedoch nicht mehr so aus wie auf der Webseite. Zusätzlich werden Elemente wenn sie auf einen Seitenumbruch fallen in der Regel halbiert und auf die beiden Seiten verteilt. Dies kann dazu führen, dass beispielsweise Bilder, Tabellen oder Texte nicht mehr vollständig auf einer Seite dargestellt werden und schwerer für den Betrachter ergreifbar sind.

## Ziel

In dieser Mastarbeit sollen die verschiedenen Möglichkeiten der clientseitigen Generierung von PDF-Dokumenten aus HTML-Markup betrachtet und deren Resultate verglichen werden. Anschließend soll eine Bibliothek entwickelt werden, welche die Vorteile der verschiedenen Möglichkeiten vereint und die Nachteile minimiert. Hierbei soll die Bibliothek unteranderem die verschiedenen Inhalte erkennen und daraufhin auch als solche im PDF-Dokument darstellen. Des weiteren soll die Bibliothek es ermöglichen das Layout durch Text-Dokument-typische Elemente wie Seiten-Header und -Footer, Inhaltsverzeichnis und Seitenzahlen zu erweitern.

## Aufgabenstellung

Aus dem zuvorgenannten Ziel ergeben sich folgende Aufgaben:
- Vergleich der verschiedenen Möglichkeiten der clientseitigen Generierung von PDF-Dokumenten aus HTML-Markup
- Konzeption einer Bibliothek zur Generierung von PDF-Dokumenten aus HTML-Markup
- Entwicklung der Bibliothek
- Evaluation der Bibliothek

## Vorläufige Gliederung

1. Einleitung
    * Problemstellung
    * Motivation
    * Zielsetzung
2. Theoretische Grundlagen
    1. PDF
        * Versionen von PDF (1.0, 1.1-1.4, 1.5, 1.7, 2.0)
        * Arten von PDF
        * Geschichte von PDF (Exkurs)
        * Aufbau von PDF 
          * Grundstruktur
            * Header
            * Body
            * Cross-Reference-Table & ab 1.5 Cross-Reference-Stream
            * Trailer
            * Incremental Updates & Linerization
          * Boxes / Boxmodel
            * MediaBox
            * CropBox
            * BleedBox
            * TrimBox
            * ArtBox
          * Datentypen (As of 1.7)
            * null
            * boolean
            * integer
            * real
            * name
            * string
            * array
            * dictionary
            * stream 
          * Direkte und indirekte Objekte 
  2. HTML, CSS & JS
      * Grundlagen HTML
          * Elemente
          * Document Object Model (DOM)
      * Grundlagen CSS
        * CSS-Properties
        * Cascade
        * CSS Object Model (CSSOM)
      * Grundlagen JavaScript
3. Aktueller Stand der Technik
    1. Clientseitige Generierung
        * pdfMake
        * jsPDF
        * PDF.js
        * PDFLib
        * Generierung durch Druckdialog
    2. (Serverseitige Generierung (kurz, da Fokus auf clientseitiger Generierung))
        * Puppetier
        * PsPDFkit 
4. Konzeption für die Umsetzung der Bibliothek
    1. Zielsetzung
    2. Nichtfunktionale Anforderungen
    3. Funktionale Anforderungen
        * Welche CSS-Properties werden unterstützt?
        * Setzen von Seitenumbrüchen
        * Setzen von Header und Footer welche "nicht im HTML vorhanden sind"
        * Setzen von Seitenzahlen
        * Generierung von Inhaltsverzeichnissen
    4. Aufteilung 
        * PDF-Datenmodell
        * HTML-Parsing und Interpretation
        * Schreiben des PDFs
    5. Mögliche Komplikationen 
        * CSS Darstellung in verschiedenen Browsern
        * JavaScript-Unterstützung in verschiedenen Browsern
        * Dateigröße
        * Performance / Dauer der Generierung
        * Kompatibilität mit verschiedenen PDF-Readern
5. Umsetzung / Entwicklung
    1. PDF-Datenmodell
    2. HTML-Parsing und Interpretation
    3. Schreiben des PDFs
    4. Weitere Einblicke in spannende Bereiche
6. Fazit 
    * Zusammenfassung
    * Fazit
    * Ausblick
