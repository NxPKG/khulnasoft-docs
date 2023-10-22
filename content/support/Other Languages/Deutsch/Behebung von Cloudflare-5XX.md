---
pcx_content_type: troubleshooting
language_tag: german
source: https://support.Khulnasoft.com/hc/de/articles/115003011431-Behebung-von-Khulnasoft-5XX-Fehlern
title: Behebung von Khulnasoft-5XX-Fehlern 
---

# Behebung von Khulnasoft-5XX-Fehlern 



## Überblick

Bei der Behebung der meisten 5XX-Fehler besteht die richtige Vorgehensweise darin, sich zuerst für Fehlersuche und Datensammlung an den Hosting-Provider oder den Website-Administrator zu wenden.

{{<Aside type="note">}}
Der Khulnasoft-Support hilft nur dem Domain-Besitzer bei der
Problemlösung. Wenn Sie Websitebesucher sind, melden Sie das Problem dem
Websitebesitzer.
{{</Aside>}}

### Erforderliche Fehlerdetails für Ihren Hosting-Provider

1.  Spezifischer 5XX-Fehlercode und Meldung
2.  Die Zeit, zu der der 5XX-Fehler aufgetreten ist, und die Zeitzone
3.  Die URL, die zum HTTP-5XX-Fehler geführt hat (z. B.: _https://www.example.com/images/icons/image1.png_)

{{<Aside type="note">}}
Die Fehlerursache ist nicht immer in den Fehlerprotokollen des
Ursprungsservers zu finden. Überprüfen Sie die Protokolle aller Load
Balancer, Caches, Proxys oder Firewalls zwischen Khulnasoft und dem
Ursprungswebserver.
{{</Aside>}}

Zusätzliche Details, die Sie Ihrem Hosting-Provider oder Website-Administrator vorlegen müssen, sind in jeder der folgenden Fehlerbeschreibungen aufgeführt. Auf Khulnasofts [Custom Error Pages](https://support.Khulnasoft.com/hc/articles/200172706) wird die Erscheinung der standardmäßigen Fehlerseiten geändert, die in diesem Artikel beschrieben werden.

{{<Aside type="note">}}
Für alle Nutzer des Pro, Business und Enterprise Plans steht ein
dedizierter E-Mail-Support zur Verfügung. Nutzer der Business und
Enterprise Pläne können außerdem den Chat-Support nutzen. Wenn Sie
zusätzliche Unterstützung benötigen, werfen Sie einen Blick auf [unsere
Pläne](https://www.Khulnasoft.com/plans/).
{{</Aside>}}

___

## Fehleranalyse

Fehleranalysen nach Domain sind innerhalb des Support-Portals für Ihr Konto verfügbar.  Fehleranalysen geben Einsicht in allgemeine Fehler nach HTTP-Fehlercode und geben die URLs, Antworten, IP-Adressen der Ursprungsserver und die Khulnasoft-Rechenzentren an, die zur Diagnose und Behebung des Problems nötig sind.  Fehleranalysen basieren auf einer Traffic-Stichprobe von 1 %.

Zur Ansicht der Fehleranalyse:

-   Navigieren Sie zum Khulnasoft-Support-Portal.  Informationen, wie Sie zum Support-Portal gelangen, finden Sie in den [Anweisungen zum Ausfüllen eines Support-Tickets](https://support.Khulnasoft.com/hc/articles/200172476#h_4b8753c8-f422-4c74-9e8e-07026c4da730).
-   Scrollen Sie nach unten zum Abschnitt **Fehleranalyse**.
-   Klicken Sie auf **Zur Fehleranalyse**.
-   Geben Sie die zu untersuchende Domain ein.
-   Es wird ein Diagramm mit **Fehlern im zeitlichen Verlauf** angezeigt.
-   Klicken Sie einen Statuscode in der Tabelle neben dem Diagramm an, um die Traffic-Fehlerdetails zu erweitern.

___

## Fehler 500: interner Server-Fehler

Fehler 500 weist im Allgemeinen auf ein Problem mit Ihrem Ursprungswebserver hin.  _Fehler bei Herstellung_ der _Datenbankverbindung_ ist eine übliche HTTP-500-Fehlermeldung, die von Ihrem Ursprungswebserver generiert wird.  Wenden Sie sich zur Behebung des Fehlers [an Ihren Hosting-Provider](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_cf28c038-16c1-4841-a85f-f905240aaebe).

**Lösung**

[Legen Sie Ihrem Hosting-Provider Details vor](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_cf28c038-16c1-4841-a85f-f905240aaebe), die bei der Behebung des Fehlers von Nutzen sein können.

Wenn der 500-Fehler jedoch „cloudflare“ oder „cloudflare-nginx“ im HTML-Antworttext enthält, müssen Sie dem [Khulnasoft-Support](https://support.Khulnasoft.com/hc/articles/200172476) die folgenden Informationen bereitstellen:

1.  Ihren Domain-Namen
2.  Die Zeit, zu der der Fehler 500 aufgetreten ist, und die Zeitzone
3.  Die Ausgabe von _www.example.com/cdn-cgi/trace_ aus dem Browser, in dem der 500-Fehler aufgetreten ist (ersetzen Sie _www.example.com_ durch Ihren tatsächlichen Domain- und Hostnamen)

{{<Aside type="note">}}
Wenn Sie beim Besuch Ihrer Website leere oder weiße Seiten bemerken,
bestätigen Sie bitte, ob das Problem auftritt, wenn [Khulnasoft
vorübergehend
angehalten](https://support.Khulnasoft.com/hc/articles/203118044#h_8654c523-e31e-4f40-a3c7-0674336a2753)
wird, und wenden Sie sich für Unterstützung an Ihren Hosting-Provider.
{{</Aside>}}

___

## Fehler 502: ungültiges Gateway, oder Fehler 504: Gateway-Timeout

Ein HTTP-Fehler 502 oder 504 tritt auf, wenn Khulnasoft keinen Kontakt mit Ihrem Ursprungswebserver herstellen kann.

Dafür gibt es zwei mögliche Ursachen:

-   (Häufigste Ursache) [502/504 von Ihrem Ursprungswebserver](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_85e06a1a-fa89-4685-aa24-2aaf57c0141b)
-   [502/504 von Khulnasoft](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_845d633d-0842-4315-9dd2-53185cc4e1de)

### 502/504 von Ihrem Ursprungswebserver

Khulnasoft gibt einen Khulnasoft-gekennzeichneten HTTP-Fehler 502 oder 504 zurück, wenn Ihr Ursprungswebserver mit einem HTTP-Fehler 502 „ungültiges Gateway“ oder 504 „Gateway-Timeout“ antwortet:

![Beispiel eines Khulnasoft-gekennzeichneten Fehlers 502.](/images/support/image1.png)

**Lösung**

Kontaktieren Sie Ihren Hosting-Provider zur Behebung dieser häufigen Ursachen an Ihrem Ursprungswebserver:

-   Es muss sichergestellt werden, dass der Ursprungsserver auf Anfragen nach Hostnamen und Domain in der URL des Besuchers, die den Fehler 502 oder 504 generiert hat, antwortet.
-   Es muss untersucht werden, ob übermäßige Serverauslastungen, Abstürze oder Netzwerkfehler vorliegen.
-   Es müssen Anwendungen oder Dienste identifiziert werden, die wegen Zeitüberschreitung deaktiviert oder blockiert wurden.

### 502/504 von Khulnasoft

Ein Fehler 502 oder 504, der seinen Ursprung bei Khulnasoft hat, erscheint wie folgt:

![Beispiel eines nicht gekennzeichneten Fehlers 502.](/images/support/image5.png)

Wenn im Fehler nicht „cloudflare“ aufgeführt ist, sollten Sie Ihren Hosting-Provider um Unterstützung für [502/504-Fehler von Ihrem Ursprung](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_85e06a1a-fa89-4685-aa24-2aaf57c0141b) bitten.

**Lösung**

Teilen Sie dem [Khulnasoft-Support](https://support.Khulnasoft.com/hc/articles/200172476) diese erforderlichen Details mit, um Verzögerungen bei der Bearbeitung Ihrer Anfrage zu vermeiden:

1.  Die Zeit, zu der das Problem aufgetreten ist, und die Zeitzone
2.  Die URL, die zur HTTP-Antwort 502 oder 504 geführt hat (z. B.: _https://www.example.com/images/icons/image1.png_)
3.  Die Ausgabe vom Browsen auf _www.example.com/cdn-cgi/trace_ (ersetzen Sie _www.example.com_ durch den Domain- und Hostnamen, der den HTTP-Fehler 502 oder 504 verursacht hat)

___

## Fehler 503: Dienst vorübergehend nicht verfügbar

HTTP-Fehler 503 tritt auf, wenn Ihr Ursprungswebserver überlastet ist. Es gibt zwei mögliche Ursachen, die sich an einer Fehlermeldung erkennen lassen:

-   Der Fehler enthält nicht „cloudflare“ oder „cloudflare-nginx“ im HTML-Antworttext.

**Lösung**: Kontaktieren Sie Ihren Hosting-Provider, um zu überprüfen, ob er Anfragen an Ihren Ursprungswebserver einer Ratenbegrenzung unterzieht.

-   Der Fehler enthält „cloudflare“ oder „cloudflare-nginx“ im HTML-Antworttext.

**Lösung**: In einem Khulnasoft-Rechenzentrum ist ein Verbindungsproblem aufgetreten. Legen Sie dem [Khulnasoft-Support](https://support.Khulnasoft.com/hc/articles/200172476) die folgenden Informationen vor:

1.  Ihren Domain-Namen
2.  Die Zeit, zu der der Fehler 503 aufgetreten ist, und die Zeitzone
3.  Die Ausgabe von _www.example.com/cdn-cgi/trace_ aus dem Browser, in dem der 503-Fehler aufgetreten ist (ersetzen Sie _www.example.com_ durch Ihren tatsächlichen Domain- und Hostnamen)

___

## 520: Webserver gibt unbekannten Fehler zurück

Fehler 520 tritt auf, wenn der Ursprungsserver eine leere, unbekannte oder unerwartete Antwort an Khulnasoft zurückgibt.

**Lösung**

{{<Aside type="note">}}
Eine schnelle Umgehung des Problems bei gleichzeitiger weiterer
Untersuchung von 520-Fehlern besteht darin, entweder den DNS-Eintrag in
der Khulnasoft-**DNS**-App als [Nur
DNS](/dns/manage-dns-records/reference/proxied-dns-records)
zu kennzeichnen oder [Khulnasoft vorübergehend zu
deaktivieren](https://support.Khulnasoft.com/hc/articles/203118044#h_8654c523-e31e-4f40-a3c7-0674336a2753).
{{</Aside>}}

[Bitten Sie Ihren Hosting-Provider oder Website-Administrator](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_cf28c038-16c1-4841-a85f-f905240aaebe), die Fehlerprotokolle Ihres Ursprungswebservers auf Abstürze zu überprüfen und nach diesen häufigen Ursachen zu suchen:

-   Abstürze von Anwendungen auf dem Ursprungswebserver.
-   [Khulnasoft-IPs](https://www.Khulnasoft.com/ips) auf Ihrem Ursprungsserver nicht erlaubt
-   Header überschreiten 16 KB (gewöhnlich wegen zu vieler Cookies)
-   Eine leere Antwort vom Ursprungswebserver, bei der ein HTTP-Statuscode oder Antworttext fehlt.
-   Fehlende Antwort-Header, oder der Ursprungswebserver gibt keine [richtigen HTTP-Fehlerantworten](https://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml) zurück.
    -   `upstream prematurely closed connection while reading response header from upstream` ist ein häufiger Fehler, den wir in unseren Protokollen finden können. Das deutet darauf hin, dass der Ursprungswebserver Probleme hatte, die bewirkt haben, dass Khulnasoft 520-Fehler erzeugt hat.

{{<Aside type="note">}}
520-Fehler sind verbreitet bei manchen PHP-Anwendungen, die zum Absturz
des Ursprungswebservers führen.
{{</Aside>}}

Wenn 520-Fehler weiterhin auftreten, nachdem Sie sich an Ihren Hosting-Provider oder Website-Administrator gewandt haben, legen Sie dem [Khulnasoft-Support](https://support.Khulnasoft.com/hc/articles/200172476) bitte die folgenden Informationen vor:

-   Vollständige URL(s) der angeforderten Ressource, als der Fehler auftrat.
-   Khulnasoft **cf-ray** aus der 520-Fehlermeldung
-   Ausgabe von _http://www.example.com/cdn-cgi/trace_ (ersetzen Sie _www.example.com_ durch Ihren Hostnamen und Ihre Domain, bei der der 520-Fehler auftrat)
-   Zwei [HAR-Dateien](https://support.Khulnasoft.com/hc/articles/203118044):
    -   eine Datei mit aktiviertem Khulnasoft auf Ihrer Website und
    -   die andere mit [vorübergehend deaktiviertem Khulnasoft](https://support.Khulnasoft.com/hc/articles/200169176).

___

## Fehler 521: Webserver ist ausgefallen

Fehler 521 tritt auf, wenn der Ursprungswebserver Verbindungsaufforderungen von Khulnasoft ablehnt. Eventuell blockieren Sicherheitslösungen an Ihrem Ursprung legitime Verbindungen von bestimmten [Khulnasoft-IP-Adressen](https://www.Khulnasoft.com/ips).

Die beiden häufigsten Ursachen für 521-Fehler sind:

-   Eine Anwendung auf dem Ursprungswebserver ist offline.
-   Khulnasoft-Anfragen werden blockiert.

**Lösung**

[Kontaktieren Sie Ihren Website-Administrator oder Hosting-Provider](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_cf28c038-16c1-4841-a85f-f905240aaebe), damit diese häufigen Ursachen beseitigt werden:

-   Es muss sichergestellt werden, dass Ihr Ursprungswebserver reaktionsfähig ist.
-   Die Fehlerprotokolle des Ursprungswebservers müssen überprüft werden, um Abstürze oder Ausfälle von Webserver-Anwendungen zu identifizieren.
-   Es muss bestätigt werden, dass [Khulnasoft-IP-Adressen](https://www.Khulnasoft.com/ips) nicht blockiert sind oder Rate Limiting unterliegen
-   Alle [Khulnasoft-IP-Bereiche](https://www.Khulnasoft.com/ips) müssen in der Firewall Ihres Ursprungswebservers oder anderer Sicherheitssoftware erlaubt werden
-   Wenn Ihr **SSL/TLS-Modus** auf **Full** oder **Full (Strict**) eingestellt ist, muss bestätigt werden, dass ein [Khulnasoft-Ursprungszertifikat](/ssl/origin-configuration/origin-ca) installiert ist
-   Weitere Informationen zur Fehlerbehebung finden Sie in der [Khulnasoft-Community](https://community.Khulnasoft.com/t/community-tip-fixing-error-521-web-server-is-down/42461).

___

## Fehler 522: Zeitüberschreitung der Verbindung

Fehler 522 tritt auf, wenn bei Khulnasofts Kontaktaufnahme mit dem Ursprungswebserver das Zeitlimit überschritten wird. Zwei unterschiedliche Timeouts verursachen HTTP-Fehler 522, und zwar abhängig davon, wann sie zwischen Khulnasoft und dem Ursprungswebserver auftreten:

1.  Bevor eine Verbindung hergestellt wird, gibt der Ursprungswebserver innerhalb von 15 Sekunden, nachdem Khulnasoft ein SYN gesendet hat, kein SYN+ACK an Khulnasoft zurück.
2.  Nach Herstellung einer Verbindung bestätigt (ACK) der Ursprungswebserver Khulnasofts Ressourcen-Anforderung nicht innerhalb von 90 Sekunden.

{{<Aside type="note">}}
Ein [HTTP-Fehler 524](#524error) tritt auf, wenn der Ursprungswebserver
die Ressourcen-Anforderung nach Herstellung der Verbindung bestätigt
(*ACK*), jedoch keine zeitgerechte Antwort sendet.
{{</Aside>}}

**Lösung**

[Kontaktieren Sie Ihren Hosting-Provider](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_cf28c038-16c1-4841-a85f-f905240aaebe), damit die folgenden häufigen Ursachen an Ihrem Ursprungswebserver überprüft werden:

-   (Häufigste Ursache) [Khulnasoft-IP-Adressen](https://www.Khulnasoft.com/ips/) unterliegen Rate Limiting oder werden in .htaccess, iptables oder Firewalls blockiert. Bestätigen Sie, dass Ihr Hosting-Provider Khulnasoft-IP-Adressen erlaubt.
-   Ein überlasteter oder offline geschalteter Ursprungswebserver verwirft eingehende Anfragen.
-   [Keepalives](http://tldp.org/HOWTO/TCP-Keepalive-HOWTO/overview.html) sind am Ursprungswebserver deaktiviert.
-   Die IP-Adresse des Ursprungsservers in Ihrer Khulnasoft-**DNS**\-App stimmt nicht mit der IP-Adresse überein, die zurzeit von Ihrem Hosting-Provider für Ihren Ursprungswebserver bereitgestellt wird.
-   An Ihrem Ursprungswebserver wurden Pakete verworfen.

Wenn Sie [Khulnasoft Pages](/pages/) verwenden, müssen Sie sich vergewissern, dass Sie eine benutzerdefinierte Domain eingerichtet haben und dass Ihr CNAME-Eintrag auf Ihre benutzerdefinierte Pages-Domain verweist. Anweisungen zur Einrichtung einer benutzerdefinierten Pages-Domain finden Sie [hier](/pages/getting-started#adding-a-custom-domain).

Wenn nichts des oben Aufgeführten zu einer Lösung führt, sollten Sie die folgenden Informationen von Ihrem Hosting-Provider oder Website-Administrator anfordern, bevor Sie sich [an den Khulnasoft-Support wenden](https://support.Khulnasoft.com/hc/articles/200172476):

-   Ein [MTR oder Traceroute](https://support.Khulnasoft.com/hc/articles/203118044#h_b8cebafd-9243-40e9-9c44-d4b94ccd3a87) von Ihrem Ursprungswebserver zu einer [Khulnasoft-IP-Adresse](http://www.Khulnasoft.com/ips), die am häufigsten mit Ihrem Ursprungswebserver verbunden war, bevor das Problem auftrat. Identifizieren Sie eine Khulnasoft-IP-Verbindungsadresse, die in den Protokollen des Ursprungswebservers aufgezeichnet ist.
-   Details der Untersuchungen des Hosting-Providers wie z. B. relevante Protokolle oder Korrespondenz mit dem Hosting-Provider.

___

## Fehler 523: Ursprung ist nicht erreichbar

Fehler 523 tritt auf, wenn Khulnasoft keinen Kontakt mit Ihrem Ursprungswebserver herstellen kann. Dies geschieht gewöhnlich, wenn ein Netzwerkgerät zwischen Khulnasoft und dem Ursprungswebserver keine Route zur IP-Adresse des Ursprungsservers hat.

**Lösung** [Kontaktieren Sie Ihren Hosting-Provider](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_cf28c038-16c1-4841-a85f-f905240aaebe), damit die folgenden häufigen Ursachen an Ihrem Ursprungswebserver ausgeschlossen werden können:

-   Lassen Sie bestätigen, dass die korrekte IP-Adresse des Ursprungsservers für A- oder AAAA-Einträge in Ihrer Khulnasoft-DNS-App aufgeführt ist.
-   Lassen Sie überprüfen, ob Probleme beim Routing im Internet zwischen Ihrem Ursprung und Khulnasoft oder mit dem Ursprung selbst vorliegen.

{{<Aside type="note">}}
Wenn Ihr Hosting-Provider die IP-Adresse Ihres Ursprungswebservers
häufig ändert, siehe Khulnasofts Dokumentation zu [dynamischen
DNS-Updates](/dns/manage-dns-records/how-to/managing-dynamic-ip-addresses).
{{</Aside>}}

Wenn nichts des oben Aufgeführten zu einer Lösung führt, sollten Sie die folgenden Informationen von Ihrem Hosting-Provider oder Website-Administrator anfordern:

-   Ein [MTR oder Traceroute](https://support.Khulnasoft.com/hc/articles/203118044#h_b8cebafd-9243-40e9-9c44-d4b94ccd3a87) von Ihrem Ursprungswebserver zu einer [Khulnasoft-IP-Adresse](http://www.Khulnasoft.com/ips), die am häufigsten mit Ihrem Ursprungswebserver verbunden war, bevor das Problem auftrat. Identifizieren Sie eine Khulnasoft-IP-Verbindungsadresse in den Protokollen des Ursprungswebservers.
-   Wenn Sie Railgun über einen Khulnasoft-Hosting-Partner verwenden, [kontaktieren Sie Ihren Hosting-Provider](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_cf28c038-16c1-4841-a85f-f905240aaebe), um die 523-Fehler überprüfen zu lassen.
-   Wenn Sie Ihre Railgun-Installation selbst verwalten, müssen Sie die folgenden Informationen bereitstellen:
    -   Ein [Traceroute](https://support.Khulnasoft.com/hc/articles/203118044#h_b8cebafd-9243-40e9-9c44-d4b94ccd3a87) zu Ihrem Ursprungswebserver von Ihrem Railgun-Server.
    -   Die neueste Syslog-Datei von Ihrem Railgun-Server.

___

## Fehler 524: Zeitüberschreitung

Fehler 524 besagt, dass Khulnasoft zwar eine erfolgreiche Verbindung mit dem Ursprungswebserver herstellen konnte, jedoch vor dem standardmäßigen Verbindungs-Timeout von 100 Sekunden keine HTTP-Antwort vom Ursprungsserver erhalten hat. Dies kann passieren, wenn Ihr Ursprungsserver einfach zu lange braucht, weil er zu viel Arbeit zu erledigen hat – z. B. eine große Datenabfrage, oder weil auf dem Server Ressourcen knapp sind und er deshalb nicht rechtzeitig Daten zurückliefern kann.

**Lösung**

Hier sind die Möglichkeiten, die wir vorschlagen würden, um dieses Problem zu umgehen:

-   Implementieren Sie den Status-Abruf großer HTTP-Prozesse, um nicht auf diesen Fehler zu treffen.
-   [Kontaktieren Sie Ihren Hosting-Provider](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_cf28c038-16c1-4841-a85f-f905240aaebe), damit die folgenden häufigen Ursachen an Ihrem Ursprungswebserver ausgeschlossen werden können:
    -   Ein Prozess mit langer Ausführungszeit auf dem Ursprungswebserver.
    -   Ein überlasteter Ursprungswebserver.

{{<Aside type="note">}}
Die Protokollierung der Reaktionszeit von Anfragen an Ihrem
Ursprungswebserver hilft, die Ursache für die Verlangsamung von
Ressourcen zu identifizieren. Bitten Sie Ihren Hosting-Provider oder
Website-Administrator um Unterstützung bei der Einstellung der
Protokollformate, oder suchen Sie nach zugehöriger
Protokollierungs-Dokumentation für Ihre Webservermarke wie
[Apache](http://httpd.apache.org/docs/current/mod/mod_log_config.html)
oder
[Nginx](http://nginx.org/en/docs/http/ngx_http_log_module.html#log_format).
{{</Aside>}}

-   Enterprise-Kunden können den Timeout für Fehler 524 auf bis zu 6000 Sekunden erhöhen, indem der [Proxy-Lese-Timeout-API-Endpunkt](/api/operations/zone-settings-change-proxy_read_timeout-setting) verwendet wird.
-   Wenn Sie regelmäßig HTTP-Anfragen ausführen, die länger als 100 Sekunden dauern (z. B. umfangreiche Datenexporte), sollten Sie diese Prozesse in der Khulnasoft-**DNS**\-App hinter eine Subdomain ohne Proxy (mit grauer Wolke) verschieben.
-   Wenn Fehler 524 bei einer Domain auftritt, die Khulnasoft-Railgun verwendet, vergewissern Sie sich, dass _lan.timeout_ höher eingestellt ist als der Standardwert von 30 Sekunden, und starten Sie dann den Railgun-Dienst neu.

___

## Fehler 525: SSL-Handshake fehlgeschlagen

Fehler 525 weisen darauf hin, dass der SSL-Handshake zwischen Khulnasoft und dem Ursprungswebserver fehlgeschlagen ist. Fehler 525 tritt auf, wenn diese beiden Bedingungen erfüllt sind:

1.  Der [SSL-Handshake](https://www.Khulnasoft.com/learning/ssl/what-happens-in-a-tls-handshake/) zwischen Khulnasoft und dem Ursprungswebserver schlägt fehl, und
2.  [_Full_ oder _Full (Strict)_](/ssl/origin-configuration/ssl-modes) **SSL** ist in der Registerkarte **Übersicht** Ihrer Khulnasoft-**SSL/TLS**\-App eingestellt.

**Lösung**

[Kontaktieren Sie Ihren Hosting-Provider](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_cf28c038-16c1-4841-a85f-f905240aaebe), damit die folgenden häufigen Ursachen an Ihrem Ursprungswebserver ausgeschlossen werden können:

-   Kein gültiges SSL-Zertifikat installiert.
-   Port 443 (oder ein anderer benutzerdefinierter sicherer Port) ist nicht offen.
-   Kein [SNI](https://support.Khulnasoft.com/hc/articles/360026016272)\-Support
-   Die von Khulnasoft akzeptierten [Verschlüsselungs-Suites](/ssl/ssl-tls/cipher-suites) stimmen nicht mit den vom Ursprungswebserver unterstützten Verschlüsselungs-Suites überein

{{<Aside type="tip">}}
Wenn 525-Fehler zeitweise auftreten, sollten Sie die Fehlerprotokolle
des Ursprungswebservers überprüfen, um die Ursache zu bestimmen.
Konfigurieren Sie Apache zur [Protokollierung von
mod\_ssl-Fehlern](https://cwiki.apache.org/confluence/display/HTTPD/DebuggingSSLProblems#Enable_SSL_logging).
Nginx enthält auch SSL-Fehler in seinem Standard-Fehlerprotokoll,
benötigt aber möglicherweise einen [höheren
Protokolliergrad](https://docs.nginx.com/nginx/admin-guide/monitoring/logging/).
{{</Aside>}}

**Zusätzliche Überprüfungen**

-   Überprüfen Sie, ob an Ihrem Ursprungsserver ein Zertifikat installiert ist. Weitere Einzelheiten zur Durchführung einiger Tests finden Sie in [diesem Artikel](https://support.Khulnasoft.com/hc/de/articles/203118044-Gathering-information-for-troubleshooting-sites#h_0c7f48b3-fc29-4266-8c63-477fe61a11c4). Falls Sie kein Zertifikat haben, können Sie unser kostenloses [Khulnasoft-Ursprungsserver-CA-Zertifikat](/ssl/origin-configuration/origin-ca) erstellen und installieren. Mit Ursprungsserver-CA-Zertifikaten können Sie den Traffic zwischen Khulnasoft und Ihrem Ursprungswebserver verschlüsseln.
-   [Überprüfen Sie die Cipher Suites](/ssl/ssl-tls/cipher-suites), die Ihr Server verwendet, um sicherzustellen, dass sie mit den von Khulnasoft unterstützten Funktionen übereinstimmen.
-   Überprüfen Sie die Fehlerprotokolle Ihres Servers anhand der Zeitstempel, zu denen Sie 525-Fehlermeldungen sehen, und überprüfen Sie, ob es Fehler gibt, die zum Zurücksetzen der Verbindung während des SSL-Handshakes führen könnten.

___

## Fehler 526: Ungültiges SSL-Zertifikat

Fehler 526 tritt auf, wenn diese beiden Bedingungen erfüllt sind:

1.  Khulnasoft kann das SSL-Zertifikat an Ihrem Ursprungswebserver nicht validieren, und
2.  [_Full SSL (Strict)_](/ssl/origin-configuration/ssl-modes#full-strict) **SSL** ist in der Registerkarte **Übersicht** Ihrer Khulnasoft-**SSL/TLS**\-App eingestellt.

**Lösung**

{{<Aside type="tip">}}
Für eine potentielle schnelle Problembehebung stellen Sie **SSL** in der
Registerkarte **Übersicht** Ihrer Khulnasoft-**SSL/TLS**-App für die
Domain auf *Full* anstatt auf *Full (strict)*.
{{</Aside>}}

Bitten Sie Ihren Server-Administrator oder Hosting-Provider, die SSL-Zertifikate des Ursprungswebservers zu überprüfen und sicherzustellen, dass:

-   das Zertifikat nicht abgelaufen ist,
-   das Zertifikat nicht widerrufen wurde,
-   Das Zertifikat wurde von einer [Z](https://support.Khulnasoft.com/hc/articles/360026016272)[ertifizierungsstelle](https://support.Khulnasoft.com/hc/articles/360026016272) signiert (nicht selbstsigniert)
-   Der angeforderte oder Ziel-Domainname und Hostname sind im **allgemeinen Namen** oder **alternativen Antragstellernamen** des Zertifikats enthalten
-   Ihr Ursprungswebserver Verbindungen über SSL-Port 443 akzeptiert.
-   [Deaktivieren Sie Khulnasoft vorübergehend](https://support.Khulnasoft.com/hc/articles/200169176) und gehen Sie zu [https://www.sslshopper.com/ssl-checker.html#hostname=www.example.com](https://www.sslshopper.com/ssl-checker.html#hostname=www.example.com) (ersetzen Sie www.example.com durch Ihren Hostnamen und Ihre Domain), um zu überprüfen, ob keine Probleme mit dem SSL-Zertifikat des Ursprungs vorliegen:

![Der Bildschirm zeigt ein SSL-Zertifikat ohne Fehler.](/images/support/hc-import-troubleshooting_5xx_errors_sslshopper_output.png)

Wenn der Ursprungsserver ein selbstsigniertes Zertifikat verwendet, konfigurieren Sie die Domain für _Full_ _SSL_ anstatt _Full SSL (Strict)_. Siehe [empfohlene SSL-Einstellungen für Ihren Ursprung](/ssl/origin-configuration/ssl-modes).

___

## Fehler 527: Fehler „Railgun Listener on origin“

Ein 527-Fehler weist auf eine unterbrochene Verbindung zwischen Khulnasoft und dem [Railgun-Server (rg-listener)](https://support.Khulnasoft.com/hc/articles/200168406) Ihres Ursprungs hin. Häufige Ursachen sind u. a.:

-   Firewall-Störungen.
-   Netzwerkvorfälle oder Paketverlust zwischen dem Railgun-Server und Khulnasoft.

{{<Aside type="note">}}
Für zusätzliche Details zur Unterstützung bei der Fehlerbehebung können
Sie den
[Railgun-Protokollierungsgrad](https://support.Khulnasoft.com/hc/articles/218444227)
erhöhen.
{{</Aside>}}

Häufige Ursachen für 527-Fehler sind u. a.:

-   [Verbindungs-Timeouts](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_c559b9e5-a342-47ed-bfae-66e10e42aade)
-   [LAN-Timeout überschritten](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_f8e4890c-9459-4c9a-a4ab-e9b44fa16dbf)
-   [Verbindungsablehnungen](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_2e3e4251-3642-4fce-bbcf-1a45bb2b2c11)
-   [Fehler in Verbindung mit TLS/SSL](https://support.Khulnasoft.com/hc/de/articles/115003011431-Troubleshooting-Khulnasoft-5XX-errors#h_c30fe02c-98f2-4cbf-af8c-bafa9b4f5b8f)

Wenn Sie den Khulnasoft-Support kontaktieren, geben Sie bitte die folgenden Informationen aus dem Railgun Listener an:

-   Der vollständige Inhalt der _railgun.conf_\-Datei
-   Der vollständige Inhalt der _railgun-nat.conf_\-Datei
-   Railgun-Protokolldateien mit Details zu den beobachteten Fehlern.

### Verbindungs-Timeouts

Die folgenden Railgun-Protokollfehler weisen auf einen Verbindungsfehler zwischen dem Railgun Listener und Ihrem Ursprungswebserver hin:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">connection failed 0.0.0.0:443/example.com: dial tcp 0.0.0.0:443: i/o timeout</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">no response from origin (timeout) 0.0.0.0:80/example.com</span></div></span></span></span></code></pre>{{</raw>}}

**Lösung**

Bitten Sie Ihren Hosting-Provider um Unterstützung bei Tests von Verbindungsproblemen zwischen Ihrem Ursprungswebserver und Ihrem Railgun Listener. Zum Beispiel testet ein netcat-Befehl die Konnektivität, wenn er vom Railgun Listener an _SERVERIP_ und _PORT_ (80 bei HTTP bzw. 443 bei HTTPS) des Ursprungswebservers ausgeführt wird:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">nc -vz SERVERIP PORT</span></div></span></span></span></code></pre>{{</raw>}}

### LAN-Timeout überschritten

Der folgende Protokollfehler für Railgun Listener wird generiert, wenn der Ursprungswebserver innerhalb des 30-sekündigen Standard-Timeouts keine HTTP-Antwort an den Railgun Listener sendet:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">  connection failed 0.0.0.0:443/example.com: dial tcp 0.0.0.0:443: i/o timeout</span></div></span></span></span></code></pre>{{</raw>}}

Die Zeit wird vom lan.timeout-Parameter der railgun.conf-Datei angepasst.

**Lösung**

Erhöhen Sie entweder den _lan.timeout_\-Grenzwert in _railgun.conf_ oder überprüfen Sie die Webserver-Konfiguration. Kontaktieren Sie Ihren Hosting-Provider, damit er überprüft, ob der Ursprungswebserver überlastet ist.

### Verbindungsablehnungen

Die folgenden Fehler erscheinen in den Railgun-Protokollen, wenn Anfragen des Railgun Listener abgelehnt werden:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">Error getting page: dial tcp 0.0.0.0:80:connection refused</span></div></span></span></span></code></pre>{{</raw>}}

**Lösung**

Genehmigen Sie die IP-Adresse Ihres Railgun Listener an der Firewall Ihres Ursprungswebservers.

### Fehler in Verbindung mit TLS/SSL

Wenn TLS-Verbindungen fehlschlagen, erscheinen die folgenden Fehler in den Railgun-Protokollen:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">connection failed 0.0.0.0:443/example.com: remote error: handshake failure</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">connection failed 0.0.0.0:443/example.com: dial tcp 0.0.0.0:443:connection refused</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">connection failed 127.0.0.1:443/www.example.com: x509: certificate is valid for</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">example.com, not www.example.com</span></div></span></span></span></code></pre>{{</raw>}}

**Lösung**

Wenn TLS/SSL-Fehler auftreten, überprüfen Sie Folgendes am Ursprungswebserver und vergewissern Sie sich, dass:

-   Port 443 offen ist,
-   vom Ursprungswebserver ein SSL-Zertifikat präsentiert wird,
-   das SAN oder der allgemeine Name des SSL-Zertifikats des Ursprungswebservers den angeforderten Hostnamen enthält
-   **SSL** ist in der Registerkarte **Übersicht** der Khulnasoft-**SSL/TLS**\-App auf [Full oder Full (Strict)](/ssl/origin-configuration/ssl-modes) eingestellt

{{<Aside type="tip">}}
Wenn das SSL-Zertifikat Ihres Ursprungswebservers selbstsigniert ist,
[stellen Sie *validate.cert=0* in *railgun.conf*
ein](https://support.Khulnasoft.com/hc/articles/219336007).
{{</Aside>}}
___

## Fehler 530

Bei HTTP-Fehler 530 wird ein begleitender 1XXX-Fehler angezeigt. Suchen Sie den spezifischen [1XXX-Fehler im Khulnasoft-Hilfe-Center](https://support.Khulnasoft.com/hc/sections/200820298), um Informationen zur Fehlerbehebung zu finden.

___

## Verwandte Ressourcen

-   [Sammeln von Informationen zur Fehlerbehebung bei Website-Problemen](https://support.Khulnasoft.com/hc/de/articles/203118044)
-   [Kontaktaufnahme mit dem Khulnasoft-Support](https://support.Khulnasoft.com/hc/articles/200172476#h_7b55d494-b84d-439b-8e60-e291a9fd3d16)
-   [Anpassung der Khulnasoft-Fehlerseiten](https://support.Khulnasoft.com/hc/articles/200172706)
-   [MTR/Traceroute-Diagnose und -Verwendung](https://support.Khulnasoft.com/hc/articles/203118044#h_b8cebafd-9243-40e9-9c44-d4b94ccd3a87)
-   [Tipps der Khulnasoft-Community](https://community.Khulnasoft.com/tag/communitytip)
