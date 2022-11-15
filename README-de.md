<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a> &nbsp; <a href="README-sv.md">Svenska</a></p>

# Edit 0.8.70

Webseite im Webbrowser bearbeiten. [Demo ausprobieren](https://datenstrom.se/de/yellow/demo/).

<p align="center"><img src="edit-screenshot.png?raw=true" alt="Bildschirmfoto"></p>

## Wie man eine Webseite im Webbrowser bearbeitet

Die Anmeldeseite ist auf deiner Webseite vorhanden als `http://website/edit/`. Melde dich mit deinem Benutzerkonto an. Du kannst die normale Navigation benutzen, Änderungen machen und das Ergebnis sofort sehen. Der eingebauten Webeditor gibt dir die Möglichkeit Inhaltsdateien zu bearbeiten, Mediendateien hochzuladen und Systemeinstellungen zu ändern. Es ist eine großartige Art Webseiten zu aktualisieren. Um einen Bearbeitungslink auf deiner Webseite anzuzeigen, benutze eine `[edit]`-Abkürzung.

## Wie man ein Benutzerkonto erstellt

Die erste Möglichkeit besteht darin, ein Benutzerkonto im Webbrowser zu erstellen. Gehe zur Anmeldeseite. Du kannst ein Benutzerkonto erstellen und dein Kennwort ändern. Der Webmaster muss neue Benutzerkonten genehmigen. Die E-Mail des Webmasters wird in der Datei `system/extensions/yellow-system.ini` festgelegt.

Die zweite Möglichkeit besteht darin, ein Benutzerkonto in der [Befehlszeile](https://github.com/annaesvensson/yellow-command/tree/main/README-de.md) zu erstellen. Öffne ein Terminalfenster. Gehe ins Installations-Verzeichnis, dort wo sich die Datei `yellow.php` befindet. Gib ein `php yellow.php user add` gefolgt von E-Mail und Kennwort. Alle Benutzerkonten werden in der Datei `system/extensions/yellow-user.ini` gespeichert.

## Wie man ein Benutzerkonto löscht

Die erste Möglichkeit besteht darin, ein Benutzerkonto im Webbrowser zu löschen. Melde dich mit deinem Benutzerkonto an. Gehe in die Einstellungen. Du kannst dein eigenes Benutzerkonto jederzeit löschen. Nachdem du bestätigt hast dass du dein Benutzerkonto löschen möchtest, erhältst du eine abschließende E-Mail und das Benutzerkonto wird entfernt.

Die zweite Möglichkeit besteht darin, ein Benutzerkonto in der [Befehlszeile](https://github.com/annaesvensson/yellow-command/tree/main/README-de.md) zu löschen. Öffne ein Terminalfenster. Gehe ins Installations-Verzeichnis, dort wo sich die Datei `yellow.php` befindet. Gib ein `php yellow.php user remove` gefolgt von E-Mail. Alle Benutzerkonten werden in der Datei `system/extensions/yellow-user.ini` gespeichert.

## Wie man ein Benutzerkonto beschränkt

Falls du nicht willst dass Seiten im Webbrowser verändert werden, beschränke Benutzerkonten. Öffne die Datei `system/extensions/yellow-user.ini` und ändere `Access` und `Home`. Benutzer dürfen Seiten innerhalb ihrer Startseite bearbeiten, aber nirgendwo sonst. Es gibt verschiedene [Zugriffsrechte](#einstellungen-access), um zu bestimmen was Benutzer machen dürfen.

Falls du nicht willst dass Benutzerkonten erstellt werden, beschränke die Anmeldeseite. Öffne die Datei `system/extensions/yellow-system.ini` und ändere `EditLoginRestriction: 1`. Benutzer dürfen ihr Kennwort zurücksetzen, aber kein neues Benutzerkonto erstellen.

## Beispiele

Bearbeitungslink anzeigen:

    [edit]
    [edit - Anmelden]
    [edit - Du kannst diese Seite bearbeiten]

Inhaltsdatei mit Bearbeitungslink:

    ---
    Title: Beispielseite
    ---
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut 
    labore et dolore magna pizza. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris 
    nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit 
    esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt 
    in culpa qui officia deserunt mollit anim id est laborum.
    
    [edit - Anmelden].

Ein Benutzerkonto mit maximalen Zugriffsrechten ausstatten:

```
Email: anna@svensson.com
Name: Anna Svensson
Description: Designer
Language: de
Access: create, edit, delete, restore, upload, configure, update
Home: /
Hash: $2y$10$j26zDnt/xaWxC/eqGKb9p.d6e3pbVENDfRzauTawNCUHHl3CCOIzG
Stamp: 21196d7e857d541849e4
Pending: none
Failed: 0
Modified: 2000-01-01 13:37:00
Status: active
```

Ein Benutzerkonto mit Standard-Zugriffsrechten ausstatten:

```
Email: niklas@svensson.com
Name: Niklas Svensson
Description: Redakteur
Language: de
Access: create, edit, delete, restore, upload
Home: /
Hash: $2y$10$zG5tycOnAJ5nndGfEQhrBexVxNYIvepSWYd1PdSb1EPJuLHakJ9Ri
Stamp: a81eb147a5dd3384138b
Pending: none
Failed: 0
Modified: 2000-01-01 13:37:00
Status: active
```

Ein Benutzerkonto mit beschränkten Zugriffsrechten ausstatten:

```
Email: deutsch@example.com
Name: Demo
Description: Zum Testen der Webseite
Language: de
Access: edit, upload
Home: /demo/
Hash: $2y$10$zG5tycOnAJ5nndGfEQhrBexVxNYIvepSWYd1PdSb1EPJuLHakJ9Ri
Stamp: 2a2d4ef05dbea5071ba0
Pending: none
Failed: 0
Modified: 2000-01-01 13:37:00
Status: active
```

Verschiedene Symbolleistenschaltflächen in den Einstellungen festlegen:

```
EditToolbarButtons: auto 
EditToolbarButtons: format, bold, italic, strikethrough, code, separator, list, link, file, undo, redo
EditToolbarButtons: bold, italic, h1, h2, h3, code, quote, ul, ol, tl, link, file, preview, help
EditToolbarButtons: format, bold, italic, separator, quote, code, link, file, separator, emoji
```

Verschiedene Orte zum Hochladen in den Einstellungen festlegen:

```
EditUploadNewLocation: /media/@group/@filename
EditUploadNewLocation: /media/@group/@timestamp.@type
EditUploadNewLocation: /media/@group/@folder/@filename
EditUploadNewLocation: /media/uploads/@filename
```

Vorhandene Benutzerkonten in der Befehlszeile anzeigen:

`php yellow.php user`  

Ein Benutzerkonto in der Befehlszeile erstellen:
 
`php yellow.php user add email@example.com password`  

Ein Benutzerkonto in der Befehlszeile ändern:

`php yellow.php user change email@example.com password`  

Ein Benutzerkonto in der Befehlszeile löschen:

`php yellow.php user remove email@example.com`  

## Einstellungen

Die folgenden Einstellungen können in der Datei `system/extensions/yellow-system.ini` vorgenommen werden:

`Author` = Name des Webmasters  
`Email` = E-Mail des Webmasters  
`EditSiteEmail` = E-Mail der Webseite, wird für erstellte Nachrichten angewendet  
`EditLocation` = Ort der Anmeldeseite  
`EditUploadNewLocation` = Ort für hochgeladene Mediendateien, [unterstützte Platzhalter](#einstellungen-placeholders)  
`EditUploadExtensions` = Dateiformate zum Hochladen, `none` um zu deaktivieren  
`EditKeyboardShortcuts` = Tastaturkürzel und Befehle, `none` um zu deaktivieren  
`EditToolbarButtons` = Symbolleistenschaltflächen, `auto` für automatische Erkennung, `none` um zu deaktivieren  
`EditEndOfLine` = Zeilenenden, z.B. `auto`, `lf`, `crlf`  
`EditNewFile` = Inhaltsdatei für neue Seite  
`EditUserPasswordMinLength` = Mindestlänge von Kennwörtern  
`EditUserHashAlgorithm` = Hash-Algorithmus für verschlüsseltes Kennwort  
`EditUserHashCost` = Hash-Kosten für verschlüsseltes Kennwort  
`EditUserAccess` = Standard-Zugriffsrechte für neues Benutzerkonto  
`EditUserHome` = Standard-Startseite für neues Benutzerkonto  
`EditLoginRestriction` = Anmeldebeschränkung aktivieren, 1 oder 0  
`EditLoginSessionTimeout` = Gültigkeit der Anmeldung in Sekunden  
`EditBruteForceProtection` = Anzahl fehlgeschlagener Anmeldeversuche  

<a id="einstellungen-placeholders"></a>Die folgenden Platzhalter für hochgeladene Mediendateien werden unterstützt:

`@filename` = Dateiname  
`@timestamp` = Hochladedatum der Datei als Zeitstempel  
`@date` = Hochladedatum der Datei, JJJJ-MM-TT Format  
`@type` = Dateityp  
`@group` = Dateigruppe  
`@folder` = Ordnername der Urspungsseite

<a id="einstellungen-user"></a>Die folgenden Einstellungen können in der Datei `system/extensions/yellow-user.ini` vorgenommen werden:

`Email` = E-Mail des Benutzers  
`Name` = Name des Benutzers  
`Description` = Beschreibung des Benutzers  
`Language` = Sprache des Benutzers, z.B. `de`  
`Access` = Zugriffsrechte, [unterstützte Zugriffsrechte](#einstellungen-access)  
`Home` = Ort der Startseite  
`Hash` = verschlüsseltes Kennwort  
`Stamp` = eindeutiges Token zur Authentifizierung  
`Pending` = ausstehende Änderungen  
`Failed` = Anzahl fehlgeschlagener Anmeldeversuche  
`Modified` = Änderungsdatum, JJJJ-MM-TT Format  
`Status` = Status des Benutzers, [unterstützte Statuswerte](#einstellungen-status)  

<a id="einstellungen-access"></a>Die folgenden Benutzer-Zugriffsrechte werden unterstützt:

`create` = Benutzer kann Seite erstellen  
`edit` = Benutzer kann Seite bearbeiten  
`delete` = Benutzer kann Seite löschen  
`restore` = Benutzer kann gelöschte Seite wiederherstellen  
`upload` = Benutzer kann Mediendateien hochladen  
`configure` = Benutzer kann Webseite konfigurieren  
`update` = Benutzer kann Webseite aktualisieren  

<a id="einstellungen-status"></a>Die folgenden Benutzer-Statuswerte werden unterstützt:

`active` = Benutzer ist aktiv  
`inactive` = Benutzer wurde vorübergehend deaktiviert  
`unconfirmed` = Benutzer hat Benutzerkonto nicht bestätigt  
`unapproved` = Benutzer wurde vom Webmaster nicht genehmigt  
`unverified` = Benutzer hat neue E-Mail-Adresse nicht bestätigt  
`unchanged` = Benutzer hat ausstehende Änderungen nicht bestätigt  
`removed` = Benutzer hat ausstehende Löschung nicht bestätigt  

<a id="einstellungen-files"></a>Die folgenden Dateien können angepasst werden:

`content/shared/page-new-default.md` = Inhaltsdatei für neue Seite  
`content/shared/page-new-wiki.md` = Inhaltsdatei für neue Wikiseite  
`content/shared/page-new-blog.md` = Inhaltsdatei für neue Blogseite  

## Installation

[Erweiterung herunterladen](https://github.com/annaesvensson/yellow-core/archive/main.zip) und die ZIP-Datei in dein `system/extensions`-Verzeichnis kopieren. [Weitere Informationen zu Erweiterungen](https://github.com/annaesvensson/yellow-update/tree/main/README-de.md).

## Entwickler

Anna Svensson. [Hilfe finden](https://datenstrom.se/de/yellow/help/).
