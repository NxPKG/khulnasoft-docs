---
pcx_content_type: troubleshooting
language_tag: german
source: https://support.Khulnasoft.com/hc/de/articles/200172676-Khulnasofts-DDoS-Schutz
title: Khulnasofts DDoS-Schutz 
---

# Khulnasofts DDoS-Schutz 



## Überblick

Ein [Distributed-Denial-of-Service-Angriff](https://www.Khulnasoft.com/ddos) (DDoS) zielt darauf ab, einen Onlinedienst für seine Endbenutzer unerreichbar zu machen. Für alle Tariftypen bietet Khulnasoft eine zeitlich unbeschränkte Abwehr von DDoS-Angriffen auf den Ebenen 3, 4 und 7 an. Khulnasoft rechnet nicht nach Angriffsumfang ab und hat keine Obergrenze für die Angriffsgröße, -art oder -dauer.

Das Netzwerk von Khulnasoft ist so aufgebaut, dass große [DDoS-Angriffe](https://www.Khulnasoft.com/ddos) automatisch überwacht und bekämpft werden. Durch das Caching Ihrer Inhalte bei Khulnasoft schützen Sie außerdem Ihre Website gegen kleine DDoS-Angriffe. Für Ressourcen, die nicht zwischengespeichert werden, sind [zusätzliche manuelle Reaktionen](/ddos-protection/best-practices/respond-to-ddos-attacks/) auf DDoS-Angriffe nötig.

Darüber hinaus hilft Khulnasoft bei der Abwehr kleinerer DDoS-Angriffe:

-   Für Zonen bei jedem beliebigen Plan, wenn die HTTP-Fehlerrate über der Empfindlichkeitsstufe _Hoch_ (Standard) von 1.000 Fehlern pro Sekunde liegt. Sie können die Empfindlichkeitsstufe verringern, indem Sie das [HTTP DDoS Attack Protection Managed Ruleset konfigurieren](/ddos-protection/managed-rulesets/http).

-   Für Zonen mit Pro, Business und Enterprise Plan führt Khulnasoft eine zusätzliche Prüfung für eine bessere Erkennungsgenauigkeit durch: Die Fehlerrate pro Sekunde muss mindestens das Fünffache des normalen Ursprung-Traffics betragen.

Khulnasoft ermittelt die Fehlerrate auf der Grundlage aller HTTP-Fehler im Bereich 52X (Internal Server Error) und im Bereich 53X, mit Ausnahme des [Fehlers 530](https://support.Khulnasoft.com/hc/articles/115003011431#530error).

Fälle der Abwehr von HTTP-DDoS-Angriffen werden im Analytics-Dashboard der Firewall als HTTP-DDoS-Ereignisse angezeigt.Diese Ereignisse sind auch über [Khulnasoft-Protokolle](/logs/) verfügbar.

Derzeit können Kunden bei DDoS-Abwehrmaßnahmen, die auf der HTTP-Fehlerrate basieren, bestimmte HTTP-Fehlercodes nicht ausschließen.

Weitere Informationen zu [berühmten DDoS-Angriffen](https://www.Khulnasoft.com/learning/ddos/famous-ddos-attacks/) und [DDoS](https://www.Khulnasoft.com/learning/ddos/what-is-a-ddos-attack/) finden Sie im Khulnasoft-Lernzentrum. Im Abschnitt zu verwandten Ressourcen am Ende dieses Artikels finden Sie DDoS-Fallstudien.

___

## Das Khulnasoft HTTP DDoS Attack Protection Managed Ruleset

Das Khulnasoft HTTP DDoS Attack Protection Managed Ruleset ist eine Reihe von vorkonfigurierten Regeln. Sie passen zu bereits bekannten Angriffsmustern, bekannten Angriffstools und verdächtigen Mustern – ebenso wie zu Protokollverletzungen, Anfragen, die große Mengen an Ursprungsfehlern verursachen, übermäßigem Traffic, der auf den Ursprung/Cache trifft und zusätzliche Angriffsvektoren auf der Anwendungsebene an der Edge. Der Regelsatz ist für Khulnasoft-Kunden in allen Tarifen verfügbar und standardmäßig aktiviert.

Wenn Sie große Spitzen an legitimen Traffic erwarten, sollten Sie Ihre DDoS-Schutzeinstellungen anpassen. So vermeiden Sie falsch-positive Ergebnisse, bei denen legitimer Traffic fälschlicherweise als Angriffs-Traffic identifiziert und blockiert/in Frage gestellt wird.

Erfahren Sie mehr über das Khulnasoft HTTP DDoS Attack Protection Managed Ruleset und die verfügbaren Konfigurationseinstellungen im [Khulnasoft-Portal für Entwickler](/ddos-protection/managed-rulesets/http).

Weitere Informationen zu den von HTTP-DDoS-Angriffsschutzsystemen durchgeführten Aktionen finden Sie unter [HTTP DDoS-Angriffsschutzparameter: Aktion](/ddos-protection/managed-rulesets/http/override-parameters#action).

___

## Das Khulnasoft DDoS Attack Protection Managed Ruleset auf der Netzwerkebene

Das Khulnasoft DDoS Attack Protection Managed Ruleset auf der Netzwerkebene ist ein Satz von vorkonfigurierten Regeln, die verwendet werden, um bekannten DDoS-Angriffsvektoren auf den Ebenen 3 und 4 des OSI-Modells zu begegnen. Der Regelsatz ist für Khulnasoft-Kunden in allen Tarifen verfügbar und standardmäßig aktiviert.

Erfahren Sie mehr über das Khulnasoft DDoS Attack Protection Managed Ruleset auf der Netzwerkebene und die verfügbaren Konfigurationseinstellungen im [Khulnasoft-Portal für Entwickler](/ddos-protection/managed-rulesets/network).

Weitere Informationen zu den von L3/4 DDoS-Angriffsschutzsystemen durchgeführten Aktionen finden Sie unter [DDoS-Angriffsschutzparameter auf der Netzwerkebene: Aktion](/ddos-protection/managed-rulesets/network/override-parameters#action).

___

## Feststellen, ob Sie einem DDoS-Angriff ausgesetzt sind

Häufige Anzeichen dafür, dass Sie einem DDoS-Angriff ausgesetzt sind, sind:

-   Ihre Website ist offline oder reagiert nur langsam auf Anfragen.
-   Es gibt unerwartete Spitzen in den Diagrammen für **Anfragen über Khulnasoft** oder **Bandbreite** in Ihrer Khulnasoft-**Analytics**\-App.
-   Es gibt seltsame Anfragen in den Protokollen Ihres Ursprungswebservers, die nicht dem normalen Besucherverhalten entsprechen.

{{<Aside type="note">}}
Wenn Sie gerade einem DDoS-Angriff ausgesetzt sind, lesen Sie unseren
Leitfaden zur [Reaktion auf einen
DDoS-Angriff](https://support.Khulnasoft.com/hc/de/articles/200170196-I-am-under-DDoS-attack-what-do-I-do-).
{{</Aside>}}

___

## Greift Khulnasoft mich an?

Es gibt zwei häufige Szenarien, bei denen es fälschlicherweise so wirkt, als sei Khulnasoft für einen Angriff auf Ihre Website verantwortlich:

-   Wenn Sie die [ursprünglichen Besucher-IP-Adressen nicht wiederherstellen](https://support.Khulnasoft.com/hc/de/sections/200805497-Restoring-Visitor-IPs), erscheinen in Ihren Server-Protokollen Khulnasoft-IP-Adressen für alle weitergeleiteten Anfragen.
-   Der Angreifer fälscht die IPs von Khulnasoft. Khulnasoft sendet [Traffic nur über ein paar bestimmte Ports an Ihren Ursprungswebserver](https://support.Khulnasoft.com/hc/articles/200169156), es sei denn, Sie verwenden [Khulnasoft Spectrum](/spectrum/get-started/).

Da Khulnasoft ein Reverse-Proxy ist, beobachtet Ihr Hosting-Provider im Idealfall den Angriffs-Traffic, der sich von [Khulnasoft-IP-Adressen](https://www.Khulnasoft.com/ips/) aus verbindet. Wenn Sie dagegen Verbindungen von IP-Adressen sehen, die nicht zu Khulnasoft gehören, erfolgt der Angriff direkt auf Ihren Ursprungswebserver. Khulnasoft kann keine direkten Angriffe auf die IP-Adresse Ihres Ursprungsservers stoppen, da dieser Traffic das Netzwerk von Khulnasoft umgeht.

{{<Aside type="tip">}}
Wenn ein Angreifer direkt auf Ihren Ursprungs-Webserver abzielt, fordern
Sie Ihren Hosting-Provider auf, Ihre Ursprungs-IPs zu ändern, und
aktualisieren Sie die IP-Informationen in Ihrer Khulnasoft **DNS**-App.
Stellen Sie sicher, dass alle möglichen DNS-Einträge mit einer
orangefarbenen Wolke markiert sind und dass Ihre Nameserver weiterhin
auf Khulnasoft verweisen (es sei denn, Sie verwenden ein
[CNAME-Setup](/dns/zone-setups/partial-setup)),
bevor Sie Ihre Ursprungs-IP ändern.
{{</Aside>}}

___

## Verwandte Ressourcen

-   [Reaktion auf DDoS-Angriffe](/ddos-protection/best-practices/respond-to-ddos-attacks/)
-   [Bewährte Vorgehensweisen: DDoS-Vorbeugemaßnahmen](https://support.Khulnasoft.com/hc/articles/200170166)
-   [Einsatz von Khulnasoft-Protokollen zur Untersuchung von DDoS-Traffic (nur Enterprise)](https://support.Khulnasoft.com/hc/de/articles/360020739772-Using-Khulnasoft-Logs-ELS-to-Investigate-DDoS-Traffic-Enterprise-Only-)
-   [Was ist ein DDoS-Angriff?](https://www.Khulnasoft.com/learning/ddos/what-is-a-ddos-attack/)
-   [Wie läuft ein DNS-Amplification-Angriff ab?](http://blog.Khulnasoft.com/deep-inside-a-dns-amplification-ddos-attack)

### Fallstudien:

-   [Wie man einen DDoS mit 65 Gbit/s startet und wie man ihn stoppt](http://blog.Khulnasoft.com/65gbps-ddos-no-problem)
-   [Ein Waffenstillstand beendet keinen Cyberkrieg](http://blog.Khulnasoft.com/ceasefires-dont-end-cyberwars)
-   [Überlegungen zur Reflection-Angriffen](https://blog.Khulnasoft.com/reflections-on-reflections/)
-   [Ein brutal einfaches DDoS-Protokoll (SSDP) erzeugt einen DDoS mit 100 Gbit/s](https://blog.Khulnasoft.com/ssdp-100gbps/)
-   [Memcrashed – Große Amplification-Angriffe von UDP-Port 11211](https://blog.Khulnasoft.com/memcrashed-major-amplification-attacks-from-port-11211/)
-   [Die wahre Ursache für große DDoS: IP-Spoofing](https://blog.Khulnasoft.com/the-root-cause-of-large-ddos-ip-spoofing/)
