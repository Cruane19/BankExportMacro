# BankExport – LibreOffice SEPA-XML Export Macro

[Deutsch](#deutsch) | [English](#english)

---

## Deutsch

Einfaches LibreOffice-Calc-Makro zum Erstellen von SEPA-XML-Dateien aus Calc-Tabellen.  
Die erzeugten Dateien können in Banking-Programme wie **Hibiscus** oder die **Raiffeisen-Web-Applikation** importiert werden.

### Kurze Entstehungsgeschichte

Seit vielen Jahren verwaltet meine Frau einen örtlichen Verein. Anfangs ging es nur darum, Mitglieder zu verwalten und Jahresbeiträge einzuziehen. Da wir damals ausschließlich Linux benutzten, wurden die Daten in StarOffice-Calc-Dateien verwaltet.

Damit meine Frau die Lastschriftdaten nicht jedes Jahr manuell ins Banking-Programm eingeben musste, habe ich ein Makro geschrieben, das (damals) eine sogenannte DTAUS-Datei erzeugte. Ich weiß nicht mehr, welches Banking-Programm das war, aber es konnte nur DTAUS-Dateien importieren.

Später sind wir auf Moneyplex umgestiegen und haben mit CSV-Dateien in einem Moneyplex-eigenen Format gearbeitet. In der Zwischenzeit hatte der Verein eine Kita mit Hort und Kindergarten gegründet und viele Angestellte. Deshalb wurde die Funktionalität erweitert: um Überweisungen von Löhnen, Beiträgen an Krankenkassen und monatliche Einzüge (z. B. für Mittagessen usw.).

Irgendwie haben wir den Sprung auf ein professionelles Verwaltungsprogramm nie geschafft und arbeiten bis heute mit Calc-Dateien weiter – zuerst mit OpenOffice und jetzt mit LibreOffice.

Dann wurde Moneyplex auf einmal nicht mehr weiterentwickelt und funktionierte wegen bankseitiger Änderungen immer schlechter, sodass wir uns nach Alternativen umsehen mussten. Unter Linux war das keine leichte Aufgabe. Mit Hibiscus konnte sich meine Frau nicht anfreunden, und das Programm hatte die neuesten bankseitigen Änderungen für Überweisungen noch nicht implementiert. So sind wir bei der Raiffeisenbank-Web-Applikation gelandet.

Hier ist die einzige vernünftige Möglichkeit zum Datenaustausch SEPA-XML. Also habe ich mich daran gemacht, das Makro um einen SEPA-XML-Export zu erweitern.

Ich hatte vorher schon gesucht, ob es etwas Ähnliches für LibreOffice gibt, mit dem wir weiter hätten arbeiten können – aber ich habe nur Microsoft-Excel-basierte Lösungen gefunden. Deshalb habe ich beschlossen, alles noch etwas aufzuräumen und das Makro zur freien Verfügung zu stellen – **ohne jede Gewähr!**

Ich hoffe, irgendjemand kann damit etwas anfangen.

### Features

- Erstellung von SEPA-XML-Dateien (sowie CSV-Dateien im Moneyplex-Format, die von uns für Lastschriften noch verwendet werden)
- Benutzerfreundlicher Dialog
- Fehlerbehandlung mit klaren Meldungen
- Vorlagen für regelmäßige Vorgänge
- Deutsche und englische Oberfläche

### Voraussetzungen

- LibreOffice (getestet mit Version 25.8.x oder neuer)
- Makros müssen in den Sicherheitseinstellungen erlaubt sein

### Installation

#### 1. Zum Ausprobieren

Die Datei `BankExportMacro.ods` dient in erster Linie zum Ausprobieren  
(siehe [Releases](https://github.com/Cruane19/BankExportMacro/releases)).

Hier ist das Makro direkt enthalten. Es gibt Testdaten für Überweisungen und Lastschriften sowie Vorlagenbeispiele.

Die Daten enthalten **keine gültigen IBAN-Nummern** und dienen nur zum Testen des Exports. Die erzeugten XML-Dateien werden beim Import in einem Banking-Programm zu Fehlermeldungen führen.

Um einen echten End-to-End-Test durchzuführen, können echte Daten eingetragen werden.

#### 2. Dauerhafte Installation (empfohlen)

Natürlich können die zu verwendenden Daten auch einfach in diese Datei kopiert werden.

Um das Makro in beliebigen Calc-Dateien zu nutzen, sollte es unter **„Meine Makros“** importiert werden. Dafür dient die ZIP-Datei.

**So importierst du die Bibliothek:**

1. `Extras → Makros → Makros verwalten → Basic…`
2. Links **Meine Makros** auswählen
3. Button **Verwalten…** klicken
4. Zum Reiter **Bibliotheken** wechseln
5. **Meine Makros und Dialoge** auswählen
6. Button **Importieren…** klicken
7. Zum entpackten Ordner navigieren und eine der Dateien `dialog.xlb` oder `script.xlb` auswählen  
   (es reicht, eine der beiden Dateien zu importieren – beide werden automatisch übernommen)

Danach kann das Makro in jeder Calc-Datei aufgerufen werden:

`Extras → Makros → Makro ausführen → Meine Makros → LibBankImport → GenBankImport → genBankImportRun`

**Tipp:** Weise der Funktion `genBankImportRun` einen eigenen Button in der Symbolleiste zu.

Erlaube die Ausführung von Makros, wenn du dazu aufgefordert wirst.

Die meisten Beschriftungen sind selbsterklärend. Bei Unklarheiten einfach nachfragen.  
Wir konnten nur unsere eigenen Szenarien testen – bei Problemen gerne melden.

### Verwendung

1. Spreadsheet öffnen  
2. Makro ausführen  
3. Dialogfelder ausfüllen  
   - **Verwendungszweck (Global):** Wenn alle Zahlungen denselben Verwendungszweck haben  
   - **Von Zeile / Bis Zeile:** Exportbereich  
   - **Spalten:** Name und Vorname werden zu „Nachname, Vorname“ zusammengefasst, wenn beide vorhanden sind  
   - **M-REF:** nur bei Lastschriften erforderlich  
   - **Verwendungszweck (Individuell):** nur nötig, wenn die globalen Felder leer sind; kann mit den globalen Feldern kombiniert werden  
   - **Gläubiger-ID:** bei Lastschriften erforderlich (nicht die IBAN!)  
4. Bei Bedarf Dialoginhalt als Vorlage speichern  
5. **„SEPA Generieren“** klicken  
6. SEPA-XML-Datei in das Banking-Programm importieren  

**Hinweis:** Der CSV-Export (Moneyplex-Format) ist nur in der deutschen Oberfläche verfügbar.

### Spenden

Dieses Projekt ist kostenlos und Open Source.  
Wenn es dir hilft, freue ich mich über eine freiwillige Spende:

- [PayPal](https://paypal.me/conruane)

Vielen Dank!

### Lizenz

Dieses Projekt steht unter der **MIT-Lizenz**.  
Siehe die Datei [LICENSE](LICENSE) für Details.

### Autor

**Conleth Ruane**  
GitHub: [Cruane19](https://github.com/Cruane19)

---

**Hinweis:**  
Dieses Makro wird „as is“ bereitgestellt. Der Autor übernimmt keine Haftung für Schäden, fehlerhafte Dateien oder Probleme mit Banking-Programmen.

---

## English

Simple LibreOffice Calc macro to create SEPA XML files from spreadsheets.  
The generated files can be imported into banking applications such as **Hibiscus** or the **Raiffeisen web application**.

### Brief background

For many years my wife has been managing a local association. At first it was only about membership administration and collecting annual fees. Since we used Linux exclusively at the time, the data was kept in StarOffice Calc files.

To avoid entering direct debit data into the banking program by hand every year, I wrote a macro that generated a so-called DTAUS file. I no longer remember which banking program it was, but it only accepted DTAUS files.

Later we switched to Moneyplex and worked with CSV files in a Moneyplex-specific format. In the meantime the association had founded a daycare centre with after-school care and kindergarten and employed more staff. The macro was extended to handle salary transfers, health insurance contributions and monthly collections (e.g. for school lunches).

We never quite made the jump to professional association software and still work with Calc files today – first OpenOffice, now LibreOffice.

Then Moneyplex was discontinued and became increasingly unreliable due to bank-side changes, so we had to look for alternatives. That was not easy under Linux. My wife did not get on with Hibiscus, and at the time it did not yet support the latest bank-side changes for credit transfers. We ended up with the Raiffeisen bank web application.

There the only practical way to exchange data is SEPA XML. So I extended the macro with a SEPA XML export.

I had looked for something similar for LibreOffice beforehand, but only found Microsoft Excel-based solutions. I therefore decided to clean the macro up a bit and release it freely – **without any warranty**.

I hope someone else can make use of it.

### Features

- Creation of SEPA XML files (and CSV files in Moneyplex format, which we still use for direct debits)
- User-friendly dialog
- Error handling with clear messages
- Templates for recurring transactions
- German and English user interface

### Requirements

- LibreOffice (tested with version 25.8.x or newer)
- Macros must be allowed in the security settings

### Installation

#### 1. Trying it out

The file `BankExportMacro.ods` is mainly intended for testing  
(see [Releases](https://github.com/Cruane19/BankExportMacro/releases)).

It contains the macro, sample data for credit transfers and direct debits, and example templates.

The sample data does **not** contain valid IBANs and is only meant for testing the export. The resulting XML files will produce errors when imported into a banking program.

For a real end-to-end test, enter real data.

#### 2. Permanent installation (recommended)

You can of course also copy your own data into this file.

To use the macro in any Calc file, import it under **“My Macros”**. Use the ZIP file for that.

**How to import the library:**

1. `Tools → Macros → Organize Macros → Basic…`
2. Select **My Macros** on the left
3. Click **Organizer…**
4. Switch to the **Libraries** tab
5. Select **My Macros & Dialogs**
6. Click **Import…**
7. Navigate to the extracted folder and select either `dialog.xlb` or `script.xlb`  
   (importing one of them is enough – both are taken over automatically)

You can then run the macro from any Calc file:

`Tools → Macros → Run Macro → My Macros → LibBankImport → GenBankImport → genBankImportRun`

**Tip:** Assign `genBankImportRun` to a custom toolbar button so you do not have to go through the menu every time.

Allow macro execution when prompted.

Most labels should be self-explanatory. If anything is unclear, just ask.  
We have only tested our own scenarios – please report any problems.

### Usage

1. Open a spreadsheet  
2. Run the macro  
3. Fill in the dialog fields  
   - **Remittance information (Global):** used when all payments share the same purpose  
   - **From row / To row:** data range to export  
   - **Columns:** Name and first name are combined as “Last name, First name” when both are present  
   - **M-REF:** required for direct debits only  
   - **Remittance information (Individual):** only needed if the global fields are empty; can be combined with the global fields  
   - **Creditor ID:** required for direct debits (not the IBAN!)  
4. Optionally save the current dialog contents as a template  
5. Click **“Generate SEPA”**  
6. Import the SEPA XML file into your banking program  

**Note:** CSV export (Moneyplex format) is only available in the German UI.

### Donations

This project is free and open source.  
If it helps you, a voluntary donation is welcome:

- [PayPal](https://paypal.me/conruane)

Thank you!

### License

This project is released under the **MIT License**.  
See the [LICENSE](LICENSE) file for details.

### Author

**Conleth Ruane**  
GitHub: [Cruane19](https://github.com/Cruane19)

---

**Disclaimer:**  
This macro is provided “as is”. The author accepts no liability for damage, incorrect files or problems with banking software.
