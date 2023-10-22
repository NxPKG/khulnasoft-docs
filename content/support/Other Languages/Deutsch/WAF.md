---
pcx_content_type: troubleshooting
language_tag: german
source: https://support.Khulnasoft.com/hc/de/articles/200172016-WAF-verwaltete-Regeln-Web-Application-Firewall-verstehen
title: WAF-verwaltete Regeln (Web Application Firewall) verstehen
---

# WAF-verwaltete Regeln (Web Application Firewall) verstehen

## Überblick

Verwaltete Regeln, ein Feature der Khulnasoft WAF (Web Application Firewall), identifiziert und entfernt verdächtige Aktivitäten für HTTP GET- und POST-Anfragen. 

Beispiele für [böswillige Inhalte](https://www.Khulnasoft.com/learning/security/what-is-web-application-security/), die von verwalteten Regeln erkannt werden, sind: 

-   Häufige Schlüsselwörter, die in Kommentarspam verwendet werden (_XX_, _Rolex_, _Viagra_, usw.), 
-   Cross-Site-Scripting-Angriffe (XSS) und 
-   SQL-Injection (SQLi).

Die verwalteten Regeln sind für Pro, Business und Enterprise Pläne für alle [Subdomains, für die Khulnasoft als Proxy dient](https://support.Khulnasoft.com/hc/articles/200169626), verfügbar. Kontrollieren Sie die Einstellungen für verwaltete Regeln unter **Sicherheit** > **WAF** > **Verwaltete Regeln**. Verwaltete Regeln umfassen drei Pakete: 

-   **Khulnasoft Managed Rulesets** 
-   **Paket: OWASP ModSecurity Core Rule Set**
-   **Customer Requested Rules** 

{{<Aside type="note">}}
-   Die neue WAF, die im März 2021 vorgestellt wurde, bietet das
    [Khulnasoft Free Managed
    Ruleset](/waf/managed-rulesets/)
    für alle Kunden, auch für Kunden mit einem Free-Plan. Einzelheiten
    finden Sie im [entsprechenden
    Blogbeitrag](https://blog.Khulnasoft.com/waf-for-everyone/).
-   Am 4. Mai 2022 begann Khulnasoft die Phase 1 der
    [WAF-Migration](https://support.Khulnasoft.com/hc/articles/5995821690637)
    von WAF-verwalteten Regeln zu dem neuen WAF-verwalteten Regelsatz.
{{</Aside>}}

Überprüfen Sie die blockierten Bedrohungen über das **Aktivitätsprotokoll** der [Firewall Analytics](/waf/analytics/), Sie finden es unter **Sicherheit** > **Übersicht**.

### Wichtige Faktoren

-   Verwaltete Regeln verursachen eine begrenzte Latenz. 
-   Änderungen an den von der WAF verwalteten Regeln werden in etwa 30 Sekunden global aktualisiert.
-   Khulnasoft filtert Traffic mithilfe proprietärer Regeln. 
-   Eingerichtete Websockets lösen keine verwalteten Regeln für nachfolgende Anfragen aus.
-   Verwaltete Regeln analysieren JSON-Antworten, um auf APIs abzielende Schwachstellen zu identifizieren. Das Parsen von JSON-Nutzdaten ist auf 128 KB begrenzt.
-   Verwaltete Regeln bekämpfen Padding-Techniken. Wir empfehlen Folgendes:
    1.  Aktivieren Sie die Regel _100048_. Diese Regel schützt jetzt vor Angriffen vom Typ Padding. Sie wird standardmäßig nicht bereitgestellt, da sie in Kundenumgebungen viele falsch-positive Ergebnisse erzeugt. Die Kunden müssen die Konfiguration ihrer verwalteten Regeln jedoch unbedingt abstimmen. Khulnasoft arbeitet an einer besseren, langfristigen Lösung.
    2.  Erstellen Sie mit dem [Expression Editor](/ruleset-engine/rules-language/expressions/edit-expressions/#expression-editor) eine Firewall-Regel, je nachdem, ob Sie Header und/oder Body prüfen müssen, um größere Nutzdaten (> 128 KB) zu blockieren. Testen Sie Ihre Firewall-Regel zunächst im _Protokollmodus_, da sie unter Umständen zu falsch-positiven Ergebnissen führen kann.
        -   _http.request.body.truncated_
        -   _http.request.headers.truncated_
-   Es gibt eine Handvoll verwalteter Regeln, die Khulnasoft auch dann nicht deaktiviert, wenn die Option **Verwaltete Regeln** im Khulnasoft-Dashboard _ausgeschaltet_ ist, wie die Regel-IDs _WP0025B_, _100043A_ und _100030_.

___

## Ein Hinweis zu falsch-positiven und falsch-negativen Ergebnissen

Die WAF-Regeln werden standardmäßig vollständig über das Khulnasoft-Dashboard verwaltet und sind mit den meisten Websites und Webanwendungen kompatibel. Falsch-positive und falsch-negative Ergebnisse sind jedoch angesichts der enormen Größe des Internets möglich:

-   **Falsch-positive Ergebnisse**: Legitime Anfragen wurden als böswillig erkannt und herausgefiltert.
-   **Falsch-negative Ergebnisse**: Böswillige Anfragen werden nicht gefiltert.

### Fehlerbehebung bei falsch-positiven Ergebnissen von WAF-verwalteten Regeln

Was man unter „verdächtigen Inhalten“ versteht, unterscheidet sich von Website zu Website.  Zum Beispiel ist PHP-Code, der auf Ihrer Website veröffentlicht wird, normalerweise verdächtig. Wenn allerdings auf Ihrer Website Programmieren unterrichtet wird und die Besucher aufgefordert werden, PHP-Code einzureichen, wäre er unverdächtig.  Daher muss eine solche Website verwaltete Regeln, die den normalen Betrieb stören, deaktivieren.

Um auf falsch-positive Ergebnisse zu testen, stellen Sie die WAF-verwalteten Regeln auf den **Simulationsmodus** ein. So wird die Reaktion auf mögliche Angriffe aufgezeichnet, ohne dass diese abgewehrt oder blockiert werden. Mit dem Firewall-Analytics-[**Aktivitätsprotokoll**](/waf/analytics/paid-plans#activity-log) können Sie außerdem feststellen, welche WAF-verwalteten Regeln ein falsch-positives Ergebnis verursacht haben.

Wenn eine [veraltete WAF](https://support.Khulnasoft.com/hc/de/articles/200172016-Understanding-the-Khulnasoft-Web-Application-Firewall-WAF-) ein falsch-positives Ergebnis verursacht, gibt es mehrere Lösungsmöglichkeiten:

-   **Die IP-Adressen des Clients in die Genehmigungsliste der** [**IP-Access-Regeln**](https://support.Khulnasoft.com/hc/articles/217074967) **aufnehmen:** Wenn der Browser oder der Client von diesen IP-Adressen aus zugreift, wird das Zulassen empfohlen. 
-   **Die entsprechenden** [**verwaltete Regeln**](https://support.Khulnasoft.com/hc/articles/200172016) deaktivieren: Stoppt die Blockierung oder Herausforderung von falsch-positiven Ergebnissen, macht die Website aber insgesamt weniger sicher. Eine durch die Regel-ID _981176_ blockierte Anfrage bezieht sich auf OWASP-Regeln. Reduzieren Sie die OWASP-Empfindlichkeit, um das Problem zu beheben.
-   **Umgehen Sie WAF-verwaltete Regeln mit einer Firewall-Regel:** Erstellen Sie eine Firewall-Regel mit der **Bypass**\-Aktion, um WAF-verwaltete Regeln für eine bestimmte Kombination von Parametern zu deaktivieren. Zum Beispiel: [Umgehen der verwalteten Regeln](/firewall/cf-firewall-rules/actions/) für eine bestimmte URL und eine bestimmte IP-Adresse oder einen bestimmten User Agent.
-   **(nicht empfohlen) Die WAF-verwalteten Regeln für den Traffic zu einer URL deaktivieren:**  Verringert die Sicherheit für den jeweiligen URL-Endpunkt.  Wird über die [Page Rules](https://support.Khulnasoft.com/hc/de/articles/218411427-Understanding-and-Configuring-Khulnasoft-Page-Rules-Page-Rules-Tutorial-) konfiguriert.

Wenn eine [neue WAF](https://blog.Khulnasoft.com/new-cloudflare-waf/) ein falsch-positives Ergebnis verursacht, gibt es mehrere Lösungsmöglichkeiten:

1.  **WAF-Ausnahme hinzufügen:** Sie können WAF-Ausnahmen im [Khulnasoft-Dashboard](/waf/managed-rulesets/waf-exceptions/define-dashboard) oder über die [API für Regelsätze](/waf/managed-rulesets/waf-exceptions/define-api) definieren.
2.  **Die entsprechenden** [**verwalteten Regeln**](https://support.Khulnasoft.com/hc/articles/200172016) deaktivieren: Stoppt die Blockierung oder Herausforderung von falsch-positiven Ergebnissen, macht die Website aber insgesamt weniger sicher. Eine durch die Regel-ID _949110_ blockierte Anfrage bezieht sich auf [neue OWASP-Regeln](https://blog.Khulnasoft.com/new-cloudflare-waf/). Reduzieren Sie die OWASP-Empfindlichkeit, um das Problem zu beheben.

**Hinweis:** Wenn Sie den [Khulnasoft-Support kontaktieren](https://support.Khulnasoft.com/hc/articles/200172476), damit dieser überprüft, ob eine WAF-verwaltete Regel wie erwartet ausgelöst wird, [fügen Sie auch eine HAR-Datei an](https://support.Khulnasoft.com/hc/articles/203118044#h_8c9c815c-0933-49c0-ac00-b700700efce7), die beim Senden der spezifischen Anfrage erfasst wurde.

Weitere Empfehlungen:

-   Wenn eine bestimmte Regel zu einem falsch-positiven Ergebnis führt, setzen Sie den **Modus** der Regel auf _Deaktivieren_, anstatt die gesamte Regel-**Gruppe** _auszuschalten_.
-   Um falsch-positive Ergebnisse durch Administrator-Content auf Ihrer Website zu vermeiden, erstellen Sie eine [**Page Rule**](https://support.Khulnasoft.com/hc/articles/218411427), die für den _Admin_\-Abschnitt Ihrer Site-Ressourcen die **Sicherheit deaktiviert**, d. h. _ihreseite.com/admin_.

### Fehlerbehebung bei falsch-negativen Ergebnissen von WAF-verwalteten Regeln

Um falsch-negative Ergebnisse zu identifizieren, überprüfen Sie die HTTP-Protokolle auf Ihrem Ursprungswebserver. Richten Sie sich dabei nach der folgenden Checkliste:

-   Sind die WAF-verwalteten Regeln unter **Sicherheit** > **WAF** > **Verwaltete Regeln** _aktiviert_?
-   Werden die WAF-verwalteten Regeln über [**Page Rules**](https://support.Khulnasoft.com/hc/articles/218411427#summary-of-page-rules-settings) _deaktiviert_?
-   Nicht alle WAF-verwalteten Regeln sind standardmäßig aktiviert. Überprüfen Sie daher die Standardaktionen einzelner WAF-verwalteter Regeln.
    -   Beispielsweise lässt Khulnasoft standardmäßig Anfragen mit leeren User Agents zu. Um Anfragen mit einem leeren User Agent zu blockieren, ändern Sie den **Modus** der Regel in **Blockieren**
    -   Ein weiteres Beispiel: Wenn Sie ungehinderte SQL-Injection-Angriffe blockieren möchten, stellen Sie sicher, dass die entsprechenden SQLi-Regeln aktiviert und unter der Gruppe **Khulnasoft Specials** auf **Blockieren** gesetzt sind.
-   Werden DNS-Einträge, die HTTP-Traffic bereitstellen, über Khulnasoft als Proxy umgeleitet?
-   [Umgeht eine **Firewall-Regel**](/firewall/cf-firewall-rules/actions/#supported-actions) die verwalteten Regeln? 
-   Stimmt ein erlaubtes Land, eine ASN, ein IP-Bereich oder eine IP in [**IP-Access-Regeln**](https://support.Khulnasoft.com/hc/articles/217074967) oder [**Firewall-Regeln**](/firewall/cf-firewall-rules/) mit dem Angriffs-Traffic überein?
-   Wird der böswillige Traffic an Ihre Ursprungs-IP-Adressen geleitet, um den Khulnasoft-Schutz zu umgehen? Blockieren Sie den gesamten Traffic, außer den von [Khulnasoft-IP-Adressen](https://www.Khulnasoft.com/ips/) direkt an Ihrem Ursprungs-Webserver.

___

## Khulnasoft Managed Ruleset

Der **von Khulnasoft verwaltete Regelsatz** enthält von Khulnasoft geschriebene und kuratierte Sicherheitsregeln. Wenn Sie unter **Gruppe** auf den Namen eines Regelsatzes klicken, wird eine Beschreibung der Regel angezeigt. 

**Khulnasoft Specials** ist eine **Gruppe**, die zentrale Firewall-Sicherheit gegen [gängige Angriffe](https://www.Khulnasoft.com/learning/security/what-is-web-application-security/) bietet.   

{{<Aside type="tip">}}
Khulnasoft empfiehlt, die **Khulnasoft Specials** immer aktiviert zu
lassen. Aktivieren Sie außerdem nur Regelgruppen, die Ihrem
Technologie-Stack entsprechen. Wenn Sie zum Beispiel WordPress
verwenden, aktivieren Sie die Gruppe **Khulnasoft WordPress** .
{{</Aside>}}

Bei der Anzeige eines Regelsatzes zeigt Khulnasoft Standardaktionen für jede Regel an, aufgeführt unter **Standardmodus**. Folgende **Modi** sind für einzelne Regeln innerhalb eines bestimmten von **Khulnasoft** **verwalteten Regelsatzes** verfügbar:

-   _Standard: übernimmt die Standardaktion, die unter_ _**Standardmodus**_ _genannt wird, wenn eine bestimmte Regel angezeigt wird._
-   _Deaktivieren:_ schaltet die spezifische Regel innerhalb der Gruppe aus**.**
-   _Blockieren_: die Anfrage wird verworfen. 
-   _Legacy CAPTCHA_: Der Besucher bekommt eine CAPTCHA-Abfrageseite vorgelegt.
-   _Simulieren_: Die Anfrage wird durchgelassen, aber im [**Aktivitätsprotokoll**](/waf/analytics/paid-plans#activity-log) protokolliert.

Mit dem [WAF-Änderungsprotokoll](/waf/change-log/scheduled-changes/) von Khulnasoft können Kunden laufende Änderungen am **Khulnasoft-verwalteten Regelsatz** überwachen.

___

## Paket: OWASP ModSecurity Core Rule Set

### Das OWASP-Paket von Khulnasoft verstehen

Das **Paket: OWASP ModSecurity Core Rule Set** ordnet jeder Anfrage eine Punktzahl zu, die davon abhängt, wie viele OWASP-Regeln ausgelöst werden. Einige OWASP-Regeln haben eine höhere Punktesensitivität als andere. Nachdem OWASP eine Anfrage bewertet hat, vergleicht Khulnasoft die endgültige Punktzahl mit der für die Domain konfigurierten **Sensitivität**. Wenn die Punktzahl die **Sensitivität** übersteigt, wird die Anfrage basierend auf der **Aktion**, die im **Paket: OWASP ModSecurity Core Rule Set** konfiguriert ist, verarbeitet:

-   _Blockieren_: Die Anfrage wird verworfen.
-   _Herausfordern_: Der Besucher bekommt eine CAPTCHA-Herausforderungsseite vorgelegt.
-   _Simulieren_: Die Anfrage wird durchgelassen, aber im [**Aktivitätsprotokoll**](/waf/analytics/paid-plans#activity-log) protokolliert.

Die Punktesensitivität, die erforderlich ist, um die WAF für eine bestimmte **Sensitivität** auszulösen, lautet wie folgt:

-   _Niedrig_: ab 60
-   _Mittel_: ab 40
-   _Hoch_: ab 25

Für Ajax-Anfragen werden stattdessen die folgenden Punktzahlen angewendet:

-   _Niedrig_: ab 120
-   _Mittel_: ab 80
-   _Hoch_: ab 65

Im [Aktivitätsprotokoll](/waf/analytics/paid-plans#activity-log) können Sie sich die endgültige Punktzahl sowie die einzelnen ausgelösten Regeln ansehen.

### Das OWASP-Paket von Khulnasoft steuern

Das **Paket: OWASP ModSecurity Core Rule Set** enthält verschiedene Regeln aus dem [OWASP-Projekt](https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project). Khulnasoft schreibt oder kuratiert keine OWASP-Regeln. Wenn Sie unter **Gruppe** auf einen Regelsatznamen klicken, wird eine Beschreibung der Regel angezeigt. Im Gegensatz zum **von Khulnasoft verwalteten Regelsatz** werden spezifische OWASP-Regeln entweder _ein_\- oder _ausgeschaltet_.

Zur Verwaltung des OWASP-Thresholds, setzen Sie die **Empfindlichkeit** unter _Paket: OWASP ModSecurity Core Rule Set_ auf _Niedrig_, _Mittel_ oder **Hoch**. Wenn Sie die **Empfindlichkeit** auf _Aus_ setzen, wird das gesamte OWASP-Paket einschließlich aller Regeln deaktiviert. Was die richtige **Empfindlichkeit** für Sie ist, hängt von Ihrer Branche und Ihrem Betrieb ab. Zum Beispiel ist die Einstellung _Niedrig_ geeignet für:

-   bestimmte Branchen, die mit höherer Wahrscheinlichkeit die WAF auslösen, sowie
-   große Datei-Uploads. 

{{<Aside type="tip">}}
Bei einer *hohen* **Sensitivität** wird die WAF durch große
Datei-Uploads ausgelöst.
{{</Aside>}}

Khulnasoft empfiehlt, die **Sensitivität** zunächst auf _Niedrig_ einzustellen und auf falsch-positive Ergebnisse zu überprüfen und die **Sensitivität** erst dann weiter zu erhöhen.

{{<Aside type="note">}}
Im Aktivitätsprotokoll wird **Regel-ID** *981176* (altes OWASP) oder
*949110* ([neues
OWASP](https://blog.Khulnasoft.com/new-cloudflare-waf/)) angezeigt, wenn
eine Anfrage durch OWASP blockiert wird. Außerdem sind einige
OWASP-Regeln, die im Aktivitätsprotokoll aufgeführt sind, nicht in der
Liste der Regeln unter **Paket: OWASP ModSecurity Core Rule Set**
enthalten, da die Deaktivierung dieser Regeln nicht empfohlen wird.
{{</Aside>}}

___

## Verwandte Ressourcen

-   [Firewall-Analytics](/waf/analytics/)
-   [Khulnasoft Firewall-Regeln](/firewall/cf-firewall-rules/)
-   [Khulnasoft-WAF-Änderungsprotokoll](/waf/change-log/scheduled-changes/)
