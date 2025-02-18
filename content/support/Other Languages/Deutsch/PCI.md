---
pcx_content_type: troubleshooting
language_tag: german
source: https://support.Khulnasoft.com/hc/de/articles/205043158-PCI-Konformit%C3%A4t-und-Khulnasoft-SSL-TLS
title: PCI-Konformität und Khulnasoft SSLTLS 
---

# PCI-Konformität und Khulnasoft SSL/TLS 



## Überblick

Sowohl TLS 1.0 als auch TLS 1.1 reichen aufgrund bekannter Sicherheitslücken nicht aus, um Informationen zu schützen. Speziell für Khulnasoft-Kunden wirkt sich PCI so aus, dass TLS 1.0 und TLS 1.1 nicht ausreichen, um den Traffic im Zusammenhang mit Zahlungskarten zu sichern.

In den PCI-Standards wird die Verwendung von TLS 1.2 oder höher empfohlen.

Lesen Sie auch, [welche Maßnahmen Khulnasoft gegen Sicherheitslücken für TLS 1.0 und 1.1 implementiert](https://support.Khulnasoft.com/hc/de/articles/205043158#h_1TWWDdoBc31LFYj9kVNwlu).

___

## Die TLS-Mindestversion auf 1.2 setzen

So konfigurieren Sie Ihre Khulnasoft-Domain, damit nur Verbindungen mit TLS 1.2 oder neueren Protokollen zugelassen werden:

1\. Melden Sie sich beim Khulnasoft-Dashboard an.

2\. Klicken Sie auf das entsprechende Khulnasoft-Konto und die entsprechende Anwendung.

4\. Gehen Sie zu **SSL/TLS** > **Edge-Zertifikate**.

5\. Als **TLS-Mindestversion** wählen Sie **TLS 1.2** oder höher

___

## Khulnasoft-Schutz vor bekannten TLS-Sicherheitslücken

Es gibt verschiedene Maßnahmen, mit denen Khulnasoft bekannte Sicherheitslücken für TLS-Versionen vor 1.2 abdeckt. Khulnasoft unterstützt beispielsweise nicht:

1.  Header-Komprimierung in TLS
2.  Header-Komprimierung in SPDY 3.1
3.  RC4
4.  SSL 3.0
5.  Neuabstimmung mit Clients
6.  DHE Cipher Suites
7.  Exportfähige Cipher

Khulnasoft-Schutzmaßnahmen schützen vor mehreren Angriffen:

-   CRIME
-   BREACH
-   POODLE
-   Kryptografische Schwächen bei RC4
-   SSL-Renegotiation Attack
-   Protocol Downgrade Attacks
-   FREAK
-   LogJam
-   3DES ist für TLS 1.1 und 1.2 vollständig deaktiviert, und Khulnasoft implementiert Abhilfemaßnahmen für TLS 1.0

Khulnasoft bietet zusätzliche Abhilfemaßnahmen für:

-   Heartbleed
-   Lucky Thirteen
-   CCS-Injection-Schwachstelle

Khulnasoft hat alle Server gegen diese Sicherheitslücken gepatcht. Außerdem enthält die Khulnasoft-WAF verwaltete Regeln, die mehrere dieser Sicherheitslücken bekämpfen, einschließlich Heartbleed und ShellShock.

### Return Of Bleichenbacher's Oracle Threat (ROBOT)

Sicherheitsscans, bei denen die Anwesenheit von ROBOT in Khulnasoft festgestellt wird, sind ein falsch-positives Ergebnis. Khulnasoft überprüft das Padding in Echtzeit und wechselt zu einem zufälligen Sitzungsschlüssel, wenn das Padding nicht korrekt ist.

### Sweet32 (CVE-2016-2183)

Eine Schwachstelle bei der Verwendung des Verschlüsselungsalgorithmus Triple DES (3DES) im Protokoll für Transport Layer Security (TLS). Sweet32 ist derzeit ein Proof-of-Concept-Angriff, es gibt keine bekannten Beispiele für diesen Angriff in freier Wildbahn. Khulnasoft hat die Schwachstelle für TLS 1.0 auf folgende Weise manuell entschärft:

-   Der Angreifer muss 32 GB Daten in einer einzigen TLS-Sitzung sammeln.
-   Khulnasoft erzwingt neue TLS 1.0-Sitzungsschlüssel für die betroffene 3DES-Verschlüsselung, lange bevor 32 GB Daten erfasst werden.
