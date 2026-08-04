# BankExport – LibreOffice SEPA-XML Export Makro

Einfaches LibreOffice-Calc-Makro zum Erstellen von SEPA-XML-Dateien aus Calc-Tabellen.  
Die erzeugten Dateien können in Banking-Programme wie **Hibiscus** oder die **Raiffeisen-Web-Applikation** importiert werden.

## Kurze Entstehungsgeschichte

Seit vielen Jahren verwaltet meine Frau einen örtlichen Verein. Anfangs ging es nur darum, Mitglieder zu verwalten und Jahresbeiträge einzuziehen. Da wir damals ausschließlich Linux benutzten, wurden die Daten in StarOffice-Calc-Dateien verwaltet.

Damit meine Frau die Lastschriftdaten nicht jedes Jahr manuell ins Banking-Programm eingeben musste, habe ich ein Makro geschrieben, das (damals) eine sogenannte DTAUS-Datei erzeugte. Ich weiß nicht mehr, welches Banking-Programm das war, aber es konnte nur DTAUS-Dateien importieren.

Später sind wir auf Moneyplex umgestiegen und haben mit CSV-Dateien in einem Moneyplex-eigenen Format gearbeitet. In der Zwischenzeit hatte der Verein eine Kita mit Hort und Kindergarten gegründet und viele Angestellte. Deshalb wurde die Funktionalität erweitert: um Überweisungen von Löhnen, Beiträgen an Krankenkassen und monatliche Einzüge (z. B. für Mittagessen usw.).

Irgendwie haben wir den Sprung auf ein professionelles Verwaltungsprogramm nie geschafft und arbeiten bis heute mit Calc-Dateien weiter – zuerst mit OpenOffice und jetzt mit LibreOffice.

Dann wurde Moneyplex auf einmal nicht mehr weiterentwickelt und funktionierte wegen bankseitiger Änderungen immer schlechter, sodass wir uns nach Alternativen umsehen mussten. Unter Linux war das keine leichte Aufgabe. Mit Hibiscus konnte sich meine Frau nicht anfreunden, und das Programm hatte die neuesten bankseitigen Änderungen noch nicht implementiert. So sind wir bei der Raiffeisenbank-Web-Applikation gelandet.

Hier ist die einzige vernünftige Möglichkeit zum Datenaustausch SEPA-XML. Also habe ich mich daran gemacht, das Makro um einen SEPA-XML-Export zu erweitern.

Ich hatte vorher schon gesucht, ob es etwas Ähnliches für LibreOffice gibt, mit dem wir weiter hätten arbeiten können – aber ich habe nur Microsoft-Excel-basierte Lösungen gefunden. Deshalb habe ich beschlossen, alles noch etwas aufzuräumen und das Makro zur freien Verfügung zu stellen – **ohne jede Gewähr!**

Ich hoffe, irgendjemand kann damit etwas anfangen.

## Features

- Erstellung von SEPA-XML-Dateien (sowie CSV-Dateien im Moneyplex-Format, die von uns noch verwendet werden)
- Benutzerfreundlicher Dialog
- Fehlerbehandlung mit klaren Meldungen
- Vorlagen können für regelmäßige Vorgänge gespeichert werden

## Voraussetzungen

- LibreOffice (getestet mit Version 25.8.x oder neuer)
- Makros müssen in den Sicherheitseinstellungen erlaubt sein

## Installation

### 1. Zum Ausprobieren

Die Datei `BankExportMacro.ods` dient in erster Linie zum Ausprobieren  
(siehe [Releases](https://github.com/Cruane19/BankExport/releases)).

Hier ist das Makro direkt enthalten. Es gibt Testdaten für Überweisungen und Lastschriften sowie Vorlagenbeispiele.

Die Daten enthalten **keine gültigen IBAN-Nummern** und dienen nur zum Testen des Exports. Die erzeugten XML-Dateien werden beim Import in einem Banking-Programm zu Fehlermeldungen führen.

Um einen echten End-to-End-Test durchzuführen, können echte Daten eingetragen werden.

### 2. Dauerhafte Installation (empfohlen)

Natürlich können die zu verwendenden Daten auch einfach in diese Datei kopiert werden.

Um das Makro vernünftig und in beliebigen Calc-Dateien zu nutzen, sollte es unter **„Meine Makros“** importiert werden. Dafür dient die ZIP-Datei.

**So importierst du die Bibliothek:**

1. `Extras → Makros → Makros verwalten → Basic…`
2. Links **Meine Makros** auswählen
3. Button **Verwalten…** klicken
4. Zum Reiter **Bibliotheken** wechseln
5. **Meine Makros und Dialoge** auswählen
6. Button **Importieren…** klicken
7. Zum entpackten Ordner navigieren und eine der Dateien `dialog.xlb` oder `script.xlb` auswählen  
   (es reicht, eine der beiden Dateien zu importieren – beide werden automatisch übernommen)

Danach kann das Makro in jeder beliebigen Calc-Datei aufgerufen werden:

`Extras → Makros → Makro ausführen → Meine Makros → LibBankImport → GenBankImport → genBankImportRun`

**Tipp:** Weise der Funktion `genBankImportRun` am besten einen eigenen Button in der Symbolleiste zu, damit du nicht jedes Mal durch das Menü navigieren musst.

Erlaube die Ausführung von Makros, wenn du dazu aufgefordert wirst.

Die meisten Überschriften, Buttons und Feldnamen sind selbsterklärend. Bei Unklarheiten einfach nachfragen.

Wir konnten nur unsere eigenen Szenarien testen – bei Problemen gerne melden.

## Verwendung

1. Spreadsheet öffnen
2. Makro ausführen
3. Dialogfelder ausfüllen  
   Die Feldnamen sollten selbsterklärend sein. Hier trotzdem ein paar Hinweise:
   - **Verwendungszweck (Global):** Wird verwendet, wenn alle Überweisungen/Lastschriften denselben Verwendungszweck haben.
   - **Von Zeile / Bis Zeile:** Bereich der Daten, der exportiert werden soll.
   - **Spalten:** Die angegebenen Spalten werden exportiert. Name und Vorname werden zu „Nachname, Vorname“ zusammengefasst, wenn beide vorhanden sind.
   - Die Spalte **M-REF** muss nur bei Lastschriften befüllt sein.
   - Die Spalten **Verwendungszweck (Individuell)** sind nur erforderlich, wenn alle globalen Verwendungszweck-Felder leer sind.
   - Man kann die Verwendungszweck-Felder auch kombinieren, z. B. Feld 1 und 2 global und Feld 3 und 4 individuell.
4. Button **„SEPA Generieren“** klicken
5. Die erzeugte SEPA-XML-Datei in das Banking-Programm importieren

## Spenden

Dieses Projekt ist kostenlos und Open Source.  
Wenn es dir hilft, freue ich mich über eine freiwillige Spende:

- [PayPal](https://paypal.me/conruane)

Vielen Dank!

## Lizenz

Dieses Projekt steht unter der **MIT-Lizenz**.  
Siehe die Datei [LICENSE](LICENSE) für Details.

## Autor

**Conleth Ruane**  
GitHub: [Cruane19](https://github.com/Cruane19)

---

**Hinweis:**  
Dieses Makro wird „as is“ bereitgestellt. Der Autor übernimmt keine Haftung für Schäden, fehlerhafte Dateien oder Probleme mit Banking-Programmen.
