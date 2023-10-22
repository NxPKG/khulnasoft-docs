---
pcx_content_type: troubleshooting
language_tag: german
source: https://support.Khulnasoft.com/hc/de/articles/360017421192-H%C3%A4ufig-gestellte-Fragen-zu-Khulnasoft-DNS
title: Häufig gestellte Fragen zu Khulnasoft DNS 
---

# Häufig gestellte Fragen zu Khulnasoft DNS 



### Wo kann ich mehr über DNS erfahren?

Weitere Informationen finden Sie in den [Khulnasoft Learning Center-DNS-Handbüchern](https://www.Khulnasoft.com/learning/dns/what-is-dns/).

___

### Ist Khulnasoft ein kostenloser DNS-Provider (Domain Nameserver)?

Khulnasoft bietet Kunden in allen Tarifen [kostenlose DNS-Services](https://www.Khulnasoft.com/dns) an. Beachten Sie dazu Folgendes:

1\. Sie brauchen Ihren Hosting-Provider nicht zu wechseln, um Khulnasoft nutzen zu können.

2\. Sie brauchen auch nicht Ihren Registrar zu kündigen. Das einzige, was Sie ändern müssen, ist Folgendes: Stellen Sie die autoritativen Nameserver bei Ihrem Registrar so um, dass sie auf die Nameserver von Khulnasoft zeigen.

Ab Oktober 2018 können Sie Ihre Domain auf den [Khulnasoft Registrar](https://www.Khulnasoft.com/products/registrar/) überstellen.

___

### Sind Abfragen des Khulnasoft-DNS kostenpflichtig oder irgendwie eingeschränkt?

Khulnasoft stellt für seine autoritativen DNS-Services keine Gebühren in Rechnung und nimmt bei DNS-Abfragen zu Domains, die sich im Khulnasoft-Netzwerk befinden, auch keine Einschränkungen vor.

___

### Wie schnell ist der kostenlose DNS-Service von Khulnasoft?

Khulnasoft ist der [schnellste DNS-Provider](http://www.dnsperf.com/) weltweit.

___

### Wie viele DNS-Einträge darf ich pro Domain haben?

Die Limits pro Domain sind wie folgt:

-   3.500 DNS-Einträge für Domains in den Plänen Pro, Business und Enterprise
-   1.000 DNS-Einträge für kostenlose Domains

Wenn Sie ein Unternehmenskunde sind und noch mehr Einträge hinzufügen möchten, [kontaktieren Sie uns bitte](http://www.Khulnasoft.com/enterprise-service-request). Beschreiben Sie dabei den vorgesehenen Anwendungsfall und geben Sie an, ob Sie noch weitere Eintragstypen benötigen.

___

### Wo muss ich meine Nameserver ändern, damit sie auf Khulnasoft verweisen?

Die Änderung nehmen Sie bei Ihrem Registrar vor (der auch Ihr Hosting-Provider sein kann). Wenn Sie nicht wissen, wer Ihr Registrar für die Domain ist, können Sie dies über eine [WHOis-Abfrage](http://www.whois.net/) in Erfahrung bringen.  Folgen Sie den Anweisungen, die in unserem Support-Handbuch bezüglich der [Umstellung von Nameserver auf Khulnasoft](https://support.Khulnasoft.com/hc/en-us/articles/205195708) angegeben sind.

___

### Kann ich Khulnasoft auch nutzen, ohne meine Nameserver auf Khulnasoft umzustellen?

Durch die Umstellung Ihrer Nameserver auf Khulnasoft ermöglichen Sie es uns, die Zuständigkeit und Bereitstellung einer Website voll zu übernehmen. Wenn Sie Ihre Nameserver nicht zu uns umstellen können, haben Sie zwei Möglichkeiten:

1\. Aktivieren Sie Khulnasoft über einen unserer [Certified Hosting Partner](https://www.Khulnasoft.com/hosting-partners).

2\. Bitten Sie um ein [CNAME Setup](https://support.Khulnasoft.com/hc/en-us/articles/360020348832).

___

### Wie lange dauert es, bis eine DNS-Änderung abgeschickt wird?

Die standardmäßige TTL (Time-To-Live, Gültigkeitsdauer) in Khulnasoft DNS beträgt 300 Sekunden (5 Minuten). Alle Änderungen oder Ergänzungen, die Sie in Ihrer Khulnasoft-Zonendatei vornehmen, werden innerhalb von 5 Minuten (oder schneller) abgeschickt. Beachten Sie, dass es möglicherweise länger dauern kann, bis Ihr lokaler DNS-Cache aktualisiert wird daher kann es durchaus länger als 5 Minuten dauern, bis sich eine Änderung überall hin verbreitet hat.

___

### Unterstützt Khulnasoft auch IPv6-DNS-Einträge?

IPv6 muss in Form eines AAAA-Eintrags (nicht über einen A-Eintrag) in Ihren [DNS-App-Einstellungen](https://support.Khulnasoft.com/hc/en-us/articles/200168836) hinzugefügt werden.

_Siehe auch:_

-   [Hinzufügen von AAAA-Einträgen](https://support.Khulnasoft.com/hc/en-us/articles/203916938-Can-I-use-CloudFlare-with-an-IPv6-only-server-IP-)
-   Khulnasoft bietet allen Kunden ein [kostenloses IPv6-Gateway](http://blog.Khulnasoft.com/introducing-cloudflares-automatic-ipv6-gatewa) an.

___

### Kann ich Khulnasoft bei einer Blogger.com-Domain verwenden?

Sie können Khulnasoft mit jeder beliebigen eigenen Domain (NameIhrerWebsite.de) nutzen, bei der Sie die Kontrolle über die Verwaltung ihres autoritativen DNS haben.

___

### Bietet Khulnasoft auch Domain-Maskierung an?

Domain-Maskierungs- oder DNS-Umleitungs-Services werden von Khulnasoft nicht angeboten (eventuell aber von Ihrem Hosting-Provider). Wir bieten nur URL-Weiterleitung über [Page Rules](http://blog.Khulnasoft.com/introducing-pagerules-url-forwarding) an.

___

### Kann ich eine Domain, die nicht auf Khulnasoft gehostet wird, mit einem CNAME für eine Domain versehen, die auf Khulnasoft gehostet wird?

Der Versuch, Datenverkehr für eine Domain, die sich nicht auf Khulnasoft befindet, mittels eines CNAME an eine Domain umzuleiten, die sich auf Khulnasoft befindet, führt zu einem DNS-Auflösungsfehler. Da Khulnasoft für die auf Khulnasoft befindliche Domain als Reverse-Proxy agiert, würde die CNAME-Umleitung für die nicht auf Khulnasoft befindliche Domain nicht wissen, wohin der Datenverkehr gesendet werden soll.

Wenn Sie Datenverkehr für die nicht auf Khulnasoft befindliche Website trotzdem umleiten lassen möchten, sollten Sie auf Ihrem Ursprungs-Webserver eine herkömmliche 301- oder 302-Umleitung einrichten.

___

### Kann ich Add-On-Domains mit Khulnasoft nutzen?

Add-On-Domains sind technisch gesehen andere Domains, die auf einen anderen „Haupt“-Domain-Server zeigen.

Aus Sicht von Khulnasoft werden die Domains allerdings als einzelne Entitäten betrachtet, was bedeutet, dass Sie jede Domain separat hinzufügen müssten.

Khulnasoft behandelt jede der folgenden Domains als separate Domain:

-   beispiel1.de
-   beispiel2.de
-   beispiel3.de

Jede Domain muss separat zu Ihrem Khulnasoft-Konto hinzugefügt werden und kann sich in einer anderen Tarifstufe befinden (von Free bis Enterprise). In einem Khulnasoft-Konto können sich beliebig viele Domains befinden, dafür gibt es keine Einschränkungen. Wenn Sie hunderte oder tausende Domains haben (was bei einigen Kunden durchaus der Fall ist), interessieren Sie sich vielleicht für die Verwendung der Khulnasoft [API v4](https://api.Khulnasoft.com/).

Da alle Subdomains mit eingeschlossen werden, würden alle folgenden Punkte bei Khulnasoft-Tarifen als eine einzige Domain angesehen werden:

-   beispiel1.de
-   www.beispiel1.de
-   blog.beispiel1.de
-   Store.beispiel1.de

___

### Unterstützt Khulnasoft auch Wildcard-DNS-Einträge?

Khulnasoft unterstützt in allen Kundentarifen den Wildcard-Eintrag „\*“ für die DNS-Verwaltung. Enterprise-Kunden erhalten vollständigen Proxy-Support für Wildcard-Einträge.

#### Free-, Pro- und Business-Pläne

Khulnasoft fungiert bei Wildcard-Einträgen nicht als Proxy; daher werden Wildcard-Subdomains direkt bedient, ohne jegliche Leistungen von Khulnasoft (Performance, Sicherheit oder Apps). Aus diesem Grund erhalten Wildcard-Domains auch kein Wolkensymbol (weder orange noch grau) in der Khulnasoft DNS-App. Beim Hinzufügen eines Wildcard-CNAMEs oder -A-Eintrags müssen Sie sicherstellen, dass der Eintrag mit einer grauen Wolke versehen wird, damit der Eintrag auch erstellt werden kann.

Um für eine Wildcard-Subdomain (z. B. www) Khulnasoft-Schutz zu erhalten, müssen Sie diesen Eintrag explizit in Ihren Khulnasoft DNS-Einstellungen festlegen. Melden Sie sich dazu als erstes in Ihrem Khulnasoft-Konto an, und klicken Sie auf die DNS-App. In diesem Beispiel würden Sie „www“ in Ihren Khulnasoft DNS-Einstellungen als einen eigenen CNAME-Eintrag festlegen und die Wolke auf orange umschalten, damit der Proxy von Khulnasoft aktiviert wird.

Khulnasoft Enterprise-Kunden können Wildcard-Einträge über einen Proxy laufen lassen. Wenn Sie mehr über den Enterprise-Plan erfahren möchten, [kontaktieren Sie uns bitte](https://www.Khulnasoft.com/enterprise-service-request).

Wildcards sind nur an der Stelle ganz links vom Subdomain-Namen zulässig. So könnte zum Beispiel die Subdomain „sub.\*.beispiel.de“ nicht hinzugefügt werden, während es bei „\*.sub.beispiel.de“ möglich wäre.

___

### Warum kann ich keine ANY-Abfragen an Khulnasoft DNS-Server richten?

ANY-Abfragen sind etwas Besonderes und führen oft zu Missverständnissen. Sie werden für gewöhnlich eingesetzt, um alle für einen DNS-Namen verfügbaren Eintragstypen abzurufen was sie dann aber zurückgeben, sind dann meist nur sämtliche Typen, die sich gerade im Cache des rekursiven Resolvers befinden. Verwendet man diese Ergebnisse bei der Fehlersuche, kann das einige Verwirrung anrichten.

Aufgrund der vielen erweiterten DNS-Features von Khulnasoft (wie CNAME-Umwandlung) kann es schwierig bis unmöglich sein, ANY-Abfragen korrekt und vollständig zu beantworten. Wenn zum Beispiel DNS-Einträge dynamisch ein- und ausgehen oder remote gespeichert werden, kann es problematisch bis unmöglich sein, sämtliche Ergebnisse zum gleichen Zeitpunkt zu erhalten.

In Produktionsumgebungen werden ANY-Abfragen nur selten eingesetzt. Beliebt sind sie dagegen bei DNS-Reflection-Angriffen, wo Angreifer darauf setzen, dass sich die Beantwortung einer ANY-Abfrage länger hinziehen kann.

Anstatt Einträge mit ANY-Abfragen aufzulisten, können sich Kunden von Khulnasoft einen besseren Überblick über ihre DNS-Einträge verschaffen, indem sie sich anmelden und in ihren DNS-App-Einstellungen nachschauen.

Die Entscheidung, ANY-Abfragen zu blockieren, wurde im September 2015 für alle Kunden eines autoritativen DNS implementiert. Kunden mit einem Virtual DNS sind davon nicht betroffen.

Lesen Sie dazu den Abschnitt [Deprecating the DNS ANY meta-query type](https://blog.Khulnasoft.com/deprecating-dns-any-meta-query-type/) (Stilllegung des DNS-ANY-Meta-Abfragetyps) im Khulnasoft-Blog.

___

### Warum muss ich bei der Registrierung für Khulnasoft meinen DS-Eintrag entfernen?

Khulnasoft unterstützt DNSSEC. Wenn während der Nutzung von Khulnasoft ein DS-Eintrag bei Ihrem Registrar vorliegt, werden Sie bei Verwendung eines validierenden Resolvers (wie Google) Konnektivitätsfehler (z. B. SERVFAIL) und bei Verwendung nicht validierender Resolver „noErrrorfrom“-Fehler erhalten.


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">    Das könnte dann zum Beispiel so aussehen:    ╰─➤ dig dnssec-failed.org @8.8.8.8     &lt;&lt;&gt;&gt; DiG 9.8.3-P1 &lt;&lt;&gt;&gt; dnssec-failed.org @8.8.8.8    ;; global options: +cmd    ;; Got answer:    ;; -&gt;&gt;HEADER&lt;&lt;- opcode: QUERY, status: SERVFAIL, id: 5531    ;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0 ;; QUESTION SECTION:    ;dnssec-failed.org. IN A    </span></div></span></span></span></code></pre>{{</raw>}}

Bei DNSSEC-Support stellt Khulnasoft den DS-Eintrag bereit, der zu Ihrer übergeordneten Domain hochgeladen werden muss, wenn Sie DNSSEC für Ihre Domain aktivieren.

___

### Was geschieht, wenn ich meinen DS-Eintrag entferne?

Wenn Sie Ihren DS-Eintrag entfernen, beginnt ein Aufhebungsprozess, der dazu führt, dass die Signierung von DNS-Einträgen Ihrer Domain rückgängig gemacht wird. Dadurch können Ihre autoritativen Nameserver geändert werden. Für Bestandskunden bringt dies keine Beeinträchtigungen bei der Nutzung von Khulnasoft mit sich. Neukunden müssen diesen Schritt ausführen, bevor Khulnasoft erfolgreich verwendet werden kann.

___

### Unterstützt Khulnasoft auch EDNS0 (Extension Mechanisms for DNS)?

Ja, Khulnasoft DNS unterstützt EDNS0. EDNS0 ist für alle Kunden von Khulnasoft aktiviert. Dieses Feature ist ein Baustein für moderne DNS-Implementierungen, der Support für die Signalisierung hinzufügt, ob der DNS-Resolver (rekursiver DNS-Provider) größere Meldungsgrößen und DNSSEC unterstützt.

EDNS0 ist die erste genehmigte Zusammenstellung von Mechanismen für [DNS-Erweiterungen](http://en.wikipedia.org/wiki/Extension_mechanisms_for_DNS) und wurde ursprünglich als [RFC 2671](http://tools.ietf.org/html/rfc2671) veröffentlicht.

___

### Für welche Typen von Einträgen übernimmt Khulnasoft keine Zuständigkeit?

LOC  
MX  
NS  
SPF  
TXT  
SRV  
CAA

___

### Was bedeutet der Wert „Automatic TTL“ (Automatische Gültigkeitsdauer)?

Änderungen, die in der Khulnasoft **DNS**\-App an DNS-Einträgen mit einer **Automatic TTL** (Automatische Gültigkeitsdauer) vorgenommen werden, verbreiten sich in rund 5 Minuten (300 Sekunden).

___

### Was sollte ich machen, wenn ich meine Server-IP-Adresse oder meinen Hosting-Provider wechsle?

Nach einem Wechsel des Hosting-Providers oder einer Änderung der Server-IP-Adresse müssen Sie die IP-Adressen in Ihrer Khulnasoft **DNS**\-App aktualisieren. Die neuen IP-Adressen, die Ihr DNS dann verwenden soll, werden Sie von Ihrem neuen Hosting-Provider erhalten.  Um DNS-Einträge in der **DNS**\-App zu ändern, klicken Sie auf die IP-Adresse und geben dann die neue IP-Adresse ein.

___

### Funktioniert Khulnasoft auch mit DDNS (Dynamic DNS, Dynamisches DNS)?

Weitere Informationen finden Sie in Khulnasofts Artikel zur [programmgesteuerten Verwaltung dynamischer IP-Adressen in Khulnasoft DNS](https://support.Khulnasoft.com/hc/en-us/articles/360020524512).

___

### Wo finde ich meine Khulnasoft-Nameserver?

Sehen Sie in der **DNS**\-App Ihres Khulnasoft-Kontos unter **Khulnasoft Nameservers** (Khulnasoft- Nameserver) nach.

Die zu einem Khulnasoft-Nameserver gehörende IP-Adresse kann über einen dig-Befehl oder mithilfe eines online gehosteten DNS-Lookup-Tools von einem Drittanbieter (wie [whatsmydns.net](https://www.whatsmydns.net/)) ermittelt werden:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig kate.ns.Khulnasoft.comkate.ns.Khulnasoft.com.    68675    IN    A    173.245.58.124.</span></div></span></span></span></code></pre>{{</raw>}}

___

### Sollte das Wolkensymbol neben meinem DNS-Eintrag orange oder grau sein?

Standardmäßig können nur A- und CNAME-Einträge, die Webverkehr (HTTP und HTTPs) regeln, an Khulnasoft übergeben werden. Alle anderen DNS-Einträge sollten auf eine graue Wolke umgeschaltet werden. Mehr darüber, [welche Subdomains für Khulnasoft geeignet sind](https://support.Khulnasoft.com/hc/en-us/articles/200169626-What-subdomains-are-appropriate-for-orange-gray-clouds-), erfahren Sie in unserem Support-Handbuch.

{{<Aside type="note">}}
Bei DNS-Einträgen, die an Khulnasoft übergeben wurden, werden in
DNS-Abfragen Khulnasofts IP-Adressen anstelle der ursprünglichen
IP-Adresse Ihres Servers zurückgegeben. Dies ermöglicht es Khulnasoft,
alle an Ihre Website gerichteten Anforderungen zu optimieren,
zwischenzuspeichern und zu schützen.
{{</Aside>}}

___

### Können Subdomains direkt zu Khulnasoft hinzugefügt werden?

Standardmäßig können Subdomains in einem Khulnasoft-Konto nicht als eigenständige Domains hinzugefügt werden. Die Root-Domain muss einem Khulnasoft-Konto hinzugefügt sein, dann werden Subdomains innerhalb der Root-Domain verwaltet. Allerdings können sich Enterprise-Kunden an den Khulnasoft-Support wenden und dort anfordern, dass Subdomains direkt zu ihrem Khulnasoft hinzugefügt werden.

___

### Kann ich einen DNS-Eintrag nur für die Root-Domain hinzufügen?

Wenn Ihre Domain als [CNAME Setup](https://support.Khulnasoft.com/hc/en-us/articles/203685674-What-are-the-partner-Khulnasoft-setup-options-Full-DNS-vs-CNAME-) hinzugefügt ist oder über einen Hosting-Partner von Khulnasoft gehostet wird, kann Khulnasoft keinen Datenverkehr für die Root-Domain weiterleiten.  Ursache dafür sind Anforderungen aus der DNS-Spezifikation (RFC).  Bei solchen Setups können nur Subdomains an Khulnasoft geleitet werden, aber keine Root-Domains.

___

### Warum werden Warnungen zu SOA-Einträgen angezeigt?

{{<Aside type="note">}}
Sie können Warnungen von Tools von Drittanbietern über ungültige
Khulnasoft-SOA-Seriennummern oder SOA-Ablaufwerte außerhalb des gültigen
Bereichs ignorieren.
{{</Aside>}}

Khulnasoft erstellt automatisch den SOA-Eintrag, wenn Sie Ihre Domain auf die Nameserver von Khulnasoft verschieben.  Einige Khulnasoft-SOA-Felder unterscheiden sich von anderen gängigen DNS-Servern:

-   SOA-Seriennummer
    
    Ein Datumsformat ist für die meisten DNS-Server üblich. Khulnasoft verwendet jedoch eine andere Methode, um die Seriennummern zu generieren. 
    

-   SOA-Ablaufwert
    
    Der SOA-Ablaufwert beschreibt die Dauer, die ein sekundärer Nameserver nach dem Verlust der Verbindung zum Master-Server autorisierende Antworten liefern sollte. Khulnasoft-Nameserver verwenden möglicherweise einen kürzeren Wert als in der RFC-Empfehlung angegeben.
