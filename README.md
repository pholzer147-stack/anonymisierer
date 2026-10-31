# Anonymisierer

Ein einfaches Werkzeug, um Vereinslisten zu **pseudonymisieren**, bevor man sie z. B. in Claude einfügt: Namen werden durch Kürzel (K01, K02 …) ersetzt, sensible Spalten (Adresse, Telefon, E-Mail …) entfernt. Die Antwort lässt sich anschließend wieder mit den echten Namen versehen.

**Datenschutz:** Alles läuft nur im Browser. Die Seite lädt nichts nach, sendet nichts und speichert nichts (der Browser blockiert per Content-Security-Policy sogar jede Netzwerkverbindung). Nach dem Schließen oder Neuladen ist alles weg – außer der Schlüsseldatei, die man selbst herunterlädt.

## Starten

`index.html` herunterladen und im Browser öffnen (Doppelklick genügt, auch am Handy). Es ist keine Installation und keine Internetverbindung nötig.

## Bedienung

### Verschlüsseln

1. **Liste einfügen:** In Excel den Bereich mit Kopfzeile markieren, kopieren und in das Feld einfügen. Das Format wird automatisch erkannt (Tabulator aus Excel, Semikolon-CSV oder einfacher Text).
2. **Spalten auswählen:** Für jede Spalte gibt es zwei Häkchen:
   - **Name** – wird durch ein Kürzel ersetzt. „Vorname“ und „Nachname“ werden zu *einem* Kürzel pro Person zusammengefasst.
   - **Entfernen** – die Spalte fällt komplett weg.

   Anhand der Überschriften ist schon eine Auswahl getroffen – bitte prüfen.
3. **Weitere Namen** (optional): Namen, die nur im Freitext vorkommen (z. B. „Petra Lindner“), einen pro Zeile eintragen. Namen aus den Namensspalten werden ohnehin auch im Freitext ersetzt – auch einzeln („Weber“) oder als „Weber, Jonas“.
4. **Verschlüsseln** tippen, Ergebnis kurz durchlesen und mit **Kopieren** in Claude einfügen.
   Tipp: Dazuschreiben „Bitte verwende die Kürzel (K01, K02 …) unverändert in deiner Antwort.“

E-Mail-Adressen, Telefonnummern und IBANs im Freitext werden zusätzlich entfernt (abschaltbar).

### Schlüssel

Der Schlüssel (K01 = Anna Schmidt …) wird unten angezeigt.

- **Schlüssel herunterladen** speichert ihn als JSON-Datei. **Unbedingt tun**, sonst kann später nicht entschlüsselt werden.
- **Schlüssel laden** holt eine gespeicherte Datei zurück. Wer danach eine neue Liste verschlüsselt, behält dieselben Kürzel für bekannte Personen; neue Personen bekommen die nächste Nummer.
- Die Schlüsseldatei enthält die echten Namen: sicher aufbewahren und **nicht** an Claude weitergeben.

### Entschlüsseln

1. Reiter **Entschlüsseln** öffnen (ggf. vorher den Schlüssel laden).
2. Text mit Kürzeln einfügen, z. B. Claudes Antwort.
3. **Echte Namen einsetzen** tippen und das Ergebnis kopieren. Kürzel, die nicht im Schlüssel stehen, werden gemeldet.

## Grenzen – bitte beachten

- Ersetzt werden nur Namen, die das Werkzeug **kennt** (aus Namensspalten, „Weitere Namen“ oder dem geladenen Schlüssel). Ein unbekannter Name im Freitext bleibt stehen – deshalb das Ergebnis vor dem Kopieren kurz durchlesen.
- Kommt ein Namensteil bei mehreren Personen vor (z. B. Geschwister „Schmidt“), wird er im Freitext durch beide Kürzel ersetzt: „K01/K02“.
- Einzelne Namensteile werden nur großgeschrieben ersetzt („Lange bittet …“ ja, „dauerte zu lange“ nein). Nachnamen, die auch Hauptwörter sind (Koch, Bauer), können trotzdem an unpassender Stelle ersetzt werden.
- Pseudonymisierte Daten sind nicht völlig anonym: Funktionen oder Details im Freitext können Rückschlüsse erlauben. Im Zweifel solche Spalten ebenfalls entfernen.

## Beispieldaten

Im Ordner `beispiel/` liegen eine erfundene Mitgliederliste (`mitgliederliste.tsv`) und eine erfundene Antwort mit Kürzeln (`claude-antwort.txt`) zum Ausprobieren.
