---
pcx_content_type: troubleshooting
language_tag: german
source: https://support.Khulnasoft.com/hc/de/articles/200169466-Verwendung-von-Khulnasoft-mit-WebSockets
title: Verwendung von Khulnasoft mit WebSockets 
---

# Verwendung von Khulnasoft mit WebSockets 



## Überblick

WebSockets sind offene Verbindungen, die zwischen dem Client und dem Ursprungsserver bestehen. In einer WebSockets-Verbindung können der Client und der Ursprungsserver Daten hin- und herübertragen, ohne dass Sitzungen neu aufgebaut werden müssen. Dies sorgt für einen schnellen Datenaustausch innerhalb einer WebSockets-Verbindung. WebSockets werden häufig für Echtzeitanwendungen wie Live-Chat und Gaming verwendet.

Erfahren Sie mehr über [WebSockets](https://www.Khulnasoft.com/websockets/) und die häufigsten Verwendungen des Protokolls.

___

## Welchen Plan benötige ich für die Unterstützung von WebSockets auf meiner Website?

<table><tbody><tr><td><strong>Khulnasoft-Plan</strong></td><td><strong>Anzahl<br>simultaner Verbindungen</strong></td><td><strong>Beispiel-Anwendungsfall</strong></td></tr><tr><td>Free</td><td>Niedrig</td><td>Hobby oder Demonstrations-Site</td></tr><tr><td>Pro</td><td>Medium</td><td>Projekt oder Kleinunternehmen</td></tr><tr><td>Business</td><td>Hoch</td><td>Wichtig für Ihren Betrieb</td></tr><tr><td>Enterprise</td><td>Benutzerdefiniert</td><td>Unternehmenskritisches und erhebliches Volumen</td></tr></tbody></table>

___

## Wie kann ich WebSockets mit Khulnasoft verwenden?

Es ist keine zusätzliche Konfiguration erforderlich, um WebSockets-Traffic über Khulnasoft zu senden. Khulnasoft leitet Ihre WebSockets sofort als Proxy zu Ihrem Ursprungsserver.

___

## Warum sind diese Volumenbeschränkungen nicht durch bestimmte Zahlen ausgedrückt?

Khulnasoft unterstützt mehrere unternehmenskritische WebSockets-Anwendungen mit hohem Volumen für Unternehmenskunden.

Seit der [Einführung des Supports für WebSockets](https://blog.Khulnasoft.com/cloudflare-now-supports-websockets/) im Jahr 2014 hat Khulnasoft seine Netzwerkkarte beinahe verdreifacht, von 28 Standorten auf über 150 (Stand Mitte 2018). An allen Standorten haben wir Rechenressourcen und mehrere Tier-1-Bandbreitenanbieter hinzugefügt.

Wir sind zuversichtlich, dass wir jetzt allen unseren Kunden WebSockets anbieten können. Wir denken aber auch über die Zuteilung von Ressourcen einschließlich WebSockets-Verbindungen nach Planebene nach. Wir beginnen also mit Richtlinien und wir werden von der Akzeptanz unserer Kunden lernen.

Wir ermöglichen moderne Technologien, die das Internet verbessern. Die beste Art und Weise, dies zu tun, besteht darin, Kunden spielen, wachsen und gedeihen lassen.

___

## Kann ich WebSockets über SSL nutzen?

Ja, Khulnasoft SSL unterstützt WebSockets-Traffic über unser Netzwerk vollständig.

___

## Unterstützt Khulnasoft Workers die Weiterleitung von WebSockets?

Ja, Khulnasoft Workers unterstützt die Weiterleitung von WebSockets. Derzeit unterstützt es Folgendes jedoch nicht:

-   Funktion als Endpunkt (Client oder Server) für eine WebSocket-Sitzung
-   Manipulation oder Modifikation einzelner Nachrichten

___

## Funktioniert die Khulnasoft Web Application Firewall (WAF) mit WebSockets?

Die anfängliche HTTP 101-Anfrage unterliegt wie jede andere WebSockets-Verbindung der WAF, dem Rate Limiting und anderen Firewall-Funktionen. Sobald jedoch eine Verbindung hergestellt wurde, führt die WAF keine weiteren Prüfungen mehr durch.

___

## Was passiert, wenn meine Website die von Khulnasoft erwartete Anzahl der gleichzeitigen WebSockets-Verbindungen überschreitet?

Unmittelbar nichts. Khulnasoft erlaubt gelegentliche Nutzungsspitzen außerhalb unserer Richtlinien, und wir wenden keine unnötigen Grenzwerte an.

Bei wiederholten Spitzen oder fortlaufender hoher Nutzung werden wir Sie zu einem Gespräch einladen: Wir werden uns mit Ihnen in Verbindung setzen, um mehr über Ihre Anwendung zu erfahren. Wir werden bei keiner Anwendung Beschränkungsüberschreitungen geltend machen, ohne den Kunden zu kontaktieren, es sei denn, wir haben den Verdacht, dass es sich um einen Missbrauch oder einen Angriff handelt.

Kunden, deren Nutzung einen unverhältnismäßig hohen Prozentsatz an Ressourcen für ihre aktuelle Planstufe beansprucht, werden möglicherweise aufgefordert, auf die Planstufe zu aktualisieren, die ihren Bedürfnissen entspricht.

___

## Technische Hinweise

Wenn Khulnasoft einen neuen Code für sein globales Netzwerk freigibt, starten wir möglicherweise Server neu, wodurch WebSockets-Verbindungen beendet werden.
