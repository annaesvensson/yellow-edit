<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a> &nbsp; <a href="README-sv.md">Svenska</a></p>

# Edit 0.8.71

Redigera din webbplats i en webbläsare. [Prova demon](https://datenstrom.se/sv/yellow/demo/).

<p align="center"><img src="edit-screenshot.png?raw=true" alt="Skärmdump"></p>

## Hur man installerar ett tillägg

[Ladda ner ZIP-filen](https://github.com/annaesvensson/yellow-core/archive/main.zip) och kopiera den till din `system/extensions` mapp. [Läs mer om tillägg](https://github.com/annaesvensson/yellow-update/tree/main/README-sv.md).

## Hur man redigerar en webbplats i en webbläsare

Inloggningssidan är tillgänglig på din webbplats som `http://website/edit/`. Logga in med ditt användarkonto. Du kan använda vanliga navigeringen, göra ändringar och se resultatet omedelbart. Inbyggda webbredigeraren ger dig möjlighet att redigera innehållsfiler, ladda upp mediefiler och ändra inställningar. Det är ett utmärkt sätt att uppdatera webbsidor. För att visa en redigeringslänk på din webbplats, använd en `[edit]` förkortning.

## Hur man skapar ett användarkonto

Det första alternativet är att skapa ett användarkonto i en webbläsare. Gå till inloggningssidan. Du kan skapa ett användarkonto och ändra ditt lösenord. Webmastern måste godkänna nya användarkonton. Webmastarens email definieras i filen `system/extensions/yellow-system.ini`.

Det andra alternativet är att skapa ett användarkonto på [kommandoraden](https://github.com/annaesvensson/yellow-core/tree/main/README-sv.md). Öppna ett terminalfönster. Gå till installationsmappen där filen `yellow.php` finns. Skriv `php yellow.php user add` följt av email och lösenord. Alla användarkonton lagras i filen `system/extensions/yellow-user.ini`.

## Hur man tar bort ett användarkonto

Det första alternativet är att ta bort ett användarkonto i en webbläsare. Logga in med ditt användarkonto. Gå till inställningarna. Du kan ta bort ditt eget användarkonto när som helst. Efter att du har bekräftat att du vill ta bort ditt användarkonto, får du ett sista meddelande och användarkontot kommer att raderas.

Det andra alternativet är att ta bort ett användarkonto på [kommandoraden](https://github.com/annaesvensson/yellow-core/tree/main/README-sv.md). Öppna ett terminalfönster. Gå till installationsmappen där filen `yellow.php` finns. Skriv `php yellow.php user remove` följt av email. Alla användarkonton lagras i filen `system/extensions/yellow-user.ini`.

## Hur man begränsar ett användarkonto

Om du inte vill att sidorna ska ändras i en webbläsare begränsar du användarkonton. Öppna filen `system/extensions/yellow-user.ini` och ändra `Access` och `Home`. Användare får redigera sidor på sin hemsida, men inte någon annanstans. Det finns olika [rättigheter](#inställningar-access) för att bestämma vad användare får göra.

Om du inte vill att användarkonton ska skapas begränsar du inloggningssidan. Öppna filen `system/extensions/yellow-system.ini` och ändra `EditLoginRestriction: 1`. Användare får återställa sitt lösenord, men kan inte skapa ett nytt användarkonto.

## Exempel

Innehållsfil med redigerings-förkortning:

    ---
    Title: Exempelsida
    ---
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut 
    labore et dolore magna pizza. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris 
    nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit 
    esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt 
    in culpa qui officia deserunt mollit anim id est laborum.
    
    [edit - Logga in].

Konfigurera ett användarkonto med maximala användarrättigheter:

```
Email: anna@svensson.com
Name: Anna Svensson
Description: Formgivare
Language: sv
Access: create, edit, delete, restore, upload, configure, update
Home: /
Hash: $2y$10$j26zDnt/xaWxC/eqGKb9p.d6e3pbVENDfRzauTawNCUHHl3CCOIzG
Stamp: 21196d7e857d541849e4
Pending: none
Failed: 0
Modified: 2000-01-01 13:37:00
Status: active
```

Konfigurera ett användarkonto med standard användarrättigheter:

```
Email: niklas@svensson.com
Name: Niklas Svensson
Description: Redaktör
Language: sv
Access: create, edit, delete, restore, upload
Home: /
Hash: $2y$10$zG5tycOnAJ5nndGfEQhrBexVxNYIvepSWYd1PdSb1EPJuLHakJ9Ri
Stamp: e4138bbd338881147a5d
Pending: none
Failed: 0
Modified: 2000-01-01 13:37:00
Status: active
```

Konfigurera ett användarkonto med begränsade användarrättigheter:

```
Email: svenska@example.com
Name: Demo
Description: För att testa webbplatsen
Language: sv
Access: edit, upload
Home: /demo/
Hash: $2y$10$zG5tycOnAJ5nndGfEQhrBexVxNYIvepSWYd1PdSb1EPJuLHakJ9Ri
Stamp: 3a3d21197d54186d7e85
Pending: none
Failed: 0
Modified: 2000-01-01 13:37:00
Status: active
```

Konfigurera olika uppladdningsplatser i inställningar:

```
EditUploadNewLocation: /media/@group/@filename
EditUploadNewLocation: /media/@group/@timestamp.@type
EditUploadNewLocation: /media/@group/@folder/@filename
EditUploadNewLocation: /media/uploads/@filename
```

Konfigurera olika verktygsfältknappar i inställningar:

```
EditToolbarButtons: auto 
EditToolbarButtons: format, bold, italic, strikethrough, code, separator, list, link, file, undo, redo
EditToolbarButtons: format, bold, italic, separator, quote, code, link, file, emoji, separator, help
EditToolbarButtons: bold, italic, h1, h2, h3, code, quote, ul, ol, tl, link, file, preview, help
```

Visa tillgängliga användarkonton på kommandoraden:

`php yellow.php user`  

Skapa ett användarkonto på kommandoraden:
 
`php yellow.php user add email@example.com password`  

Ändra ett användarkonto på kommandoraden:

`php yellow.php user change email@example.com password`  

Ta bort ett användarkonto på kommandoraden:

`php yellow.php user remove email@example.com`  

## Inställningar

Följande inställningar kan konfigureras i filen `system/extensions/yellow-system.ini`:

`Author` = webmasterns namn  
`Email` = webmasterns email  
`EditSiteEmail` = webbplatsens email, som används för genererade meddelanden  
`EditLocation` = plats för inloggningssidan  
`EditUploadNewLocation` = plats för uppladdade mediefiler, [stödda platshållare](#inställningar-placeholders)  
`EditUploadExtensions` = filformat för uppladdning, `none` för att inaktivera  
`EditKeyboardShortcuts` = tangentbordsgenvägar och kommandon, `none` för att inaktivera  
`EditToolbarButtons` = verktygsfältknappar, `auto` för automatisk detektering, [stödda knappar](#inställningar-toolbar)  
`EditEndOfLine` = linjeändar, t.ex. `auto`, `lf`, `crlf`  
`EditNewFile` = innehållsfil för ny sida  
`EditUserPasswordMinLength` = minsta längd på lösenord  
`EditUserHashAlgorithm` = hash-algoritm som används för krypterat lösenord  
`EditUserHashCost` = hash-kostnad som används för krypterat lösenord  
`EditUserAccess` = standard användarrättigheter för nytt användarkonto  
`EditUserHome` = standardplats för hemsidan för nytt användarkonto  
`EditLoginRestriction` = aktivera inloggningsbegränsning, 1 eller 0  
`EditLoginSessionTimeout` = giltighet av inloggning i sekunder  
`EditBruteForceProtection` = antal misslyckade inloggningsförsök  

<a id="inställningar-placeholders"></a>Följande platshållare för uppladdade mediefiler stöds:

`@filename` = filnamn  
`@timestamp` = filöverföringsdatum som tidsstämpel  
`@date` = filöverföringsdatum, ÅÅÅÅ-MM-DD format  
`@type` = filtyp  
`@group` = filgrupp  
`@folder` = mappnamn på originalsidan  

<a id="inställningar-toolbar"></a>Följande verktygsfältknappar stöds:

`format` = format-rullgardinsmenyn  
`heading` = rubrik-rullgardinsmenyn  
`h1` = rubrik 1  
`h2` = rubrik 2  
`h3` = rubrik 3  
`paragraph` = normal text  
`pre` = källkod  
`notice` = indikation  
`quote` = citat  
`bold` = fet  
`italic` = kursiv  
`strikethrough` = struken  
`code` = code  
`list` = lista-rullgardinsmenyn  
`ul` = osorterad lista  
`ol` = sorterad lista  
`tl` = uppgiftslista  
`link` = länk  
`file` = fil-dialog för att ladda upp mediafiler  
`emoji` = emoji-dialog, [kräver emoji-tillägg](https://github.com/annaesvensson/yellow-emoji/tree/main/README-sv.md)  
`icon` = ikon-dialog, [kräver icon-tillägg](https://github.com/annaesvensson/yellow-icon/tree/main/README-sv.md)  
`status` = sidans status  
`undo` = ångra  
`redo` = gör om  
`separator` = avgränsare  
`preview` = förhandsvisning  
`help` = hjälp  

<a id="inställningar-user"></a>Följande inställningar kan konfigureras i filen `system/extensions/yellow-user.ini`:

`Email` = användarens email  
`Name` = användarens namn  
`Description` = beskrivning av användaren  
`Language` = språket av användaren, t.ex. `sv`  
`Access` = användarrättigheter, [stödda rättigheter](#inställningar-access)  
`Home` = plats för hemsidan  
`Hash` = krypterat lösenord  
`Stamp` = unik token för autentisering  
`Pending` = väntande ändringar  
`Failed` = antal misslyckade inloggningsförsök  
`Modified` = ändringsdatum, ÅÅÅÅ-MM-DD format  
`Status` = användarstatus, [stödda statusvärden](#inställningar-status)  

<a id="inställningar-access"></a>Följande användarrättigheter stöds:

`create` = användaren kan skapa en sida  
`edit` = användaren kan redigera sidan  
`delete` = användaren kan radera sidan  
`restore` = användaren kan återställa raderad sida  
`upload` = användaren kan ladda upp mediefiler  
`configure` = användaren kan konfigurera inställningar  
`update` = användaren kan uppdatera webbplatsen  

<a id="inställningar-status"></a>Följande användarstatusvärden stöds:

`active` = användaren är aktiv  
`inactive` = användaren har inaktiverats tillfälligt  
`unconfirmed` = användaren har inte bekräftat användarkontot  
`unapproved` = användaren har inte godkänts av webmastern  
`unverified` = användaren har inte bekräftat ny email  
`unchanged` = användaren har inte bekräftat väntande ändringar  
`removed` = användaren har inte bekräftat väntande radering  

<a id="inställningar-files"></a>Följande filer kan anpassas:

`content/shared/page-new-default.md` = innehållsfil för ny sida  
`content/shared/page-new-wiki.md` = innehållsfil för ny wikisida  
`content/shared/page-new-blog.md` = innehållsfil för ny bloggsida  

## Utvecklare

Anna Svensson. [Få hjälp](https://datenstrom.se/sv/yellow/help/).
