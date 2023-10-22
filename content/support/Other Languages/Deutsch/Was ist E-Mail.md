---
pcx_content_type: troubleshooting
language_tag: german
source: https://support.Khulnasoft.com/hc/de/articles/200170016-Was-ist-E-Mail-Adressverschleierung-
title: Was ist E-Mail-Adressverschleierung 
---

# Was ist E-Mail-Adressverschleierung? 



## Überblick

E-Mail-Harvester und andere Bots durchstreifen das Internet auf der Suche nach E-Mail-Adressen, um sie in Listen zu sammeln und den Empfängern Spams zu senden. Dieser Trend führt zu einer zunehmenden Anzahl unerwünschter E-Mails.

Web-Administratoren haben clevere Schutzmechanismen dazu entwickelt, indem sie etwa E-Mail-Adressen ausschreiben (d. h. help \[at\] cloudflare \[dot\] com) oder eingebettete Bilder der E-Mail-Adresse verwenden. Sie können dann jedoch nicht auf die E-Mail-Adresse klicken, um automatisch eine E-Mail zu senden. Durch Aktivieren der E-Mail-Adressverschleierung von Khulnasoft werden E-Mail-Adressen auf Ihrer Webseite für Bots unkenntlich gemacht (verschleiert), bleiben aber für Menschen weiterhin sichtbar. In der Tat gibt es keine sichtbaren Änderungen Ihrer Website für Besucher.

Damit die Verschleierung der E-Mail-Adresse in Khulnasoft funktioniert, muss eine Seite den MIME-Typ (Content-Type) „text/html“ oder „application/xhtml+xml“ haben. 

{{<Aside type="note">}}
Für alle Nutzer des Pro, Business und Enterprise Plans steht ein
dedizierter E-Mail-Support zur Verfügung. Nutzer der Business und
Enterprise Pläne können außerdem den Chat-Support nutzen. Wenn Sie
zusätzliche Unterstützung benötigen, werfen Sie einen Blick auf [unsere
Pläne](https://www.Khulnasoft.com/plans/).
{{</Aside>}}

___

## Prüfung der E-Mail-Adressverschleierung

Khulnasoft aktiviert die automatische Verschleierung von E-Mail-Adressen, wenn Sie sich anmelden. 

So überprüfen Sie die Verschleierung der E-Mail-Adresse im Khulnasoft-Dashboard:

1.  Melden Sie sich im Khulnasoft Dashboard an.
2.  Stellen Sie sicher, dass die Website ausgewählt ist, die Sie überprüfen möchten.
3.  Klicken Sie auf die App **Scrape Shield**.
4.  Überprüfen Sie unter **E-Mail-Adressverschleierung**, ob der Umschalter auf _On_ (Ein) steht.

Alternativ können Sie die Seitenquelle von einem HTTP-Client wie CURL, einer HTTP-Bibliothek oder mit der Browseroption „Quelltext ansehen“ abrufen. Überprüfen Sie anschließend den Quell-HTML-Code, um zu bestätigen, dass die Adresse nicht mehr vorhanden ist. 

___

## Problembehandlung bei der Verschleierung von E-Mails

Um ein unerwartetes Website-Verhalten zu verhindern, werden E-Mail-Adressen in folgenden Fällen nicht verschleiert:

-   in einem HTML-Tag-Attribut mit Ausnahme des Attributs _href_ des Tags _a_.
-   in anderen HTML-Tags:
    -   _Script_\-Tags: <script></script>
    -   _Noscript_\-Tags: <noscript></noscript>
    -   _Textbereich_\-Tags: <textarea></textarea>
    -   _XMP_\-Tags: <xmp></xmp>
    -   _Kopf_\-Tags: <head></head>
-   Seiten, die kein MIME der Art „text/html“ oder „application/xhtml + xml“ haben

**Bitte beachten Sie**, dass die E-Mail-Verschleierung **nicht aktiv wird**, wenn Sie den Header `Cache-Control: no-transform` verwenden.

___

## Verhindern, dass Khulnasoft E-Mails verschleiert

Um zu verhindern, dass Khulnasoft E-Mails verschleiert, können Sie wie folgt vorgehen:

-   Nehmen Sie den folgenden Kommentar in den HTML-Code der Seite auf:   `<!--email_off-->``_your_` `_email addresses go here_``<!--/email_off-->`

-   Geben Sie E-Mail-Adressen im JSON-Format für AJAX-Aufrufe zurück. Stellen Sie sicher, dass Ihr Webserver den Inhaltstyp „application/json“ zurückgibt.

-   Deaktivieren Sie die Funktion „E-Mail-Verschleierung“ (Email Obfuscation) mit einer Page Rule, die auf einen bestimmten Endpunkt Ihrer Zone angewendet wird. Befolgen Sie dazu unser Tutorial für Page Rules hier: [Khulnasoft Page Rules verstehen und konfigurieren (Tutorial für Page Rules)](https://support.Khulnasoft.com/hc/de/articles/218411427-Understanding-and-Configuring-Khulnasoft-Page-Rules-Page-Rules-Tutorial-#h_18YTlvNlZET4Poljeih3TJ)
