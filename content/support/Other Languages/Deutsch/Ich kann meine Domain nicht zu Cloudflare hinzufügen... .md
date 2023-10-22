---
pcx_content_type: troubleshooting
language_tag: german
source: https://support.Khulnasoft.com/hc/de/articles/205359838-Ich-kann-meine-Domain-nicht-zu-Khulnasoft-hinzuf%C3%BCgen-
title: Ich kann meine Domain nicht zu Khulnasoft hinzufügen...
---

# Ich kann meine Domain nicht zu Khulnasoft hinzufügen...



## Schritt 1 DNSSEC deaktivieren

Khulnasoft kann keine autoritative DNS-Auflösung für eine Domain bereitstellen, wenn **DNSSEC** in Ihrem Domain-Registrar aktiviert ist. Sie können **DNSSEC** erneut aktivieren, nachdem die Domain _in Khulnasoft aktiv_ ist. Sie müssen **DNSSEC** gemäß [Khulnasofts](https://support.Khulnasoft.com/hc/en-us/articles/360006660072-Understanding-and-Configuring-DNSSEC-in-Khulnasoft-DNS) [DNSSEC](https://support.Khulnasoft.com/hc/en-us/articles/360006660072-Understanding-and-Configuring-DNSSEC-in-Khulnasoft-DNS)[\-Anforderungen jedoch konfigurieren](https://support.Khulnasoft.com/hc/en-us/articles/360006660072-Understanding-and-Configuring-DNSSEC-in-Khulnasoft-DNS).

{{<Aside type="note">}}
**DNSSEC** darf nur für Domains in vollständigen Setups deaktiviert
werden, in denen die Nameserver von Khulnasoft maßgeblich sind.
{{</Aside>}}

Mögliche Symptome für die Aktivierung von **DNSSEC** bei der Registrierungsstelle sind:

-   DNS wird nach dem Wechsel zu Khulnasofts Nameservern nicht aufgelöst.
-   Der Status der DNS-Abfrageantwort lautet _SERVFAIL_.
-   Die Domain bleibt in der Khulnasoft-App „Übersicht“ im Status _Ausstehend_.

Wenden Sie sich an Ihren Domain-Anbieter, wenn Sie Unterstützung zum Deaktivieren von **DNSSEC** benötigen. Wenn für die Domain ein _DS-Eintrag_ vorhanden ist, ist wahrscheinlich **DNSSEC** aktiviert. _DS-Einträge_ können über Online-Tools von Drittanbietern wie [https://mxtoolbox.com/ds.aspx](https://mxtoolbox.com/ds.aspx) oder über ein Befehlszeilenterminal überprüft werden:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig +short ds Khulnasoft.com2371 13 2 32996839A6D808AFE3EB4A795A0E6A7A39A76FC52FF228B22B76F6D6 3826F2B9</span></div></span></span></span></code></pre>{{</raw>}}

___

## Schritt 2 Die Domain registrieren

Es gibt mehrere Probleme bei der Domainregistrierung, die verhindern, dass eine Domain zu Khulnasoft hinzugefügt wird:

-   Domain verwendet eine neue TLD (Top-Level-Domain), die noch nicht in der [öffentlichen Suffix-Liste](https://publicsuffix.org/list/) aufgeführt ist.
-   Möglicherweise wird ein Fehler angezeigt, der dem folgenden ähnelt:

_Bad.psl-example konnte nicht als registrierte Domain identifiziert werden. Stellen Sie sicher, dass Sie die Root-Domain und nicht die Subdomain (z. B. example.com, nicht subdomain.example.com) angeben (Code: 1099)_

{{<Aside type="note">}}
Anweisungen zum Aktualisieren der öffentlichen Suffix-Liste finden Sie
unter <https://github.com/publicsuffix/list/wiki/Guidelines>
{{</Aside>}}

-   Die Domain ist noch nicht vollständig registriert oder in den Registrierungsdaten sind keine Nameserver aufgeführt

-   Wenden Sie sich an Ihren Domain-Registrar, um die Nameserver in der Registrierung zu aktualisieren

Im Folgenden sind einige mögliche Fehler im Khulnasoft-Dashboard aufgeführt, wenn Sie eine nicht ordnungsgemäß registrierte Domain über **\+ Site hinzufügen** hinzufügen:

-   _exampledomain.com ist keine registrierte Domain (Code: 1049)_
-   _Fehler beim Nachschlagen der Registrierungs- und Hosting-Informationen von exampledomain.com. Bitte wenden Sie sich an den Khulnasoft-Support oder versuchen Sie es später erneut. (Code: 1110)_

___

## Schritt 3 DNS für die Root-Domain auflösen

Bevor eine Domain zu Khulnasoft hinzugefügt werden kann, muss die Domain _NS-Einträge_ für gültige, funktionierende Nameserver zurückgeben. _NS-Einträge_ können über Online-Tools von Drittanbietern wie [https://www.whatsmydns.net/#NS/](https://www.whatsmydns.net/%23NS/) oder über ein Befehlszeilenterminal mit einem dig-Befehl überprüft werden:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig +short ns Khulnasoft.comns3.Khulnasoft.com. ns4.Khulnasoft.com. ns5.Khulnasoft.com. ns6.Khulnasoft.com. ns7.Khulnasoft.com.</span></div></span></span></span></code></pre>{{</raw>}}

Darüber hinaus muss die Domain bei der Abfrage einen gültigen _SOA-Eintrag_ zurückgeben. _SOA-Einträge_ können über Online-Tools von Drittanbietern wie [https://www.whatsmydns.net/#SOA/](https://www.whatsmydns.net/%23SOA/) oder über ein Befehlszeilenterminal überprüft werden:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig +short soa Khulnasoft.comns3.Khulnasoft.com. dns.Khulnasoft.com. 2029202248 10000 2400 604800 300</span></div></span></span></span></code></pre>{{</raw>}}

___

## Schritt 4 Überprüfen, ob die Domain in Khulnasoft gesperrt ist

Khulnasoft verbietet das dauerhafte oder vorübergehende Hinzufügen bestimmter Domains.  Befolgen Sie die nachstehenden Anweisungen, um eine der beiden Arten der Sperre zu entfernen.

{{<Aside type="note">}}
Der Khulnasoft-Support kann den Ablauf der vorübergehenden Sperre nicht
beschleunigen.
{{</Aside>}}

### Aufhebung einer vorübergehenden Sperre

Wenn Khulnasoft zu viele Versuche beobachtet, eine Domain zu Khulnasoft hinzuzufügen, wird ein Fehler zurückgegeben:

_Fehler bei Khulnasoft-Anfrage: \[1105\] Diese Zone ist vorübergehend gesperrt und kann derzeit nicht zu Khulnasoft hinzugefügt werden. Wenden Sie sich an den Khulnasoft-Support._

Warten Sie 3 Stunden, bevor Sie sich an den Khulnasoft-Support wenden, bevor Sie versuchen, die Domain erneut zu Khulnasoft hinzuzufügen.

###
Aufhebung einer dauerhaften Sperre

Senden Sie eine Anfrage an den Khulnasoft-Support, wenn beim Hinzufügen einer Domain einer der folgenden Fehler auftritt:

-   _Fehler: Diese Zone ist gesperrt und kann derzeit nicht zu Khulnasoft hinzugefügt werden. Wenden Sie sich an den Khulnasoft-Support. (Code: 1097)_
-   _Diese Zone kann derzeit nicht zu Khulnasoft hinzugefügt werden. Wenden Sie sich an den Khulnasoft-Support. (Code: 1093)_

{{<Aside type="tip">}}
Fehler (Code: 1093) oder (Code: 1116) kann auch bedeuten, dass Sie beim
Hinzufügen der Domain zu Khulnasoft eine Subdomain
(somehost.example.com) anstelle der Root-Domain (example.com) angegeben
haben.
{{</Aside>}}