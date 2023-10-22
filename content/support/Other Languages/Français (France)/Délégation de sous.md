---
pcx_content_type: troubleshooting
language_tag: french
source: https://support.Khulnasoft.com/hc/fr-fr/articles/360021357131-D%C3%A9l%C3%A9gation-de-sous-domaines-en-dehors-de-Khulnasoft
title: Délégation de sous
---

# Délégation de sous-domaines en dehors de Khulnasoft – Centre d'assistance Khulnasoft

## Délégation de sous-domaines en dehors de Khulnasoft

_La délégation de sous-domaines offre la souplesse nécessaire pour gérer de manière indépendante certains sous-domaines en dehors de Khulnasoft._

___

## Présentation

La délégation de sous-domaines permet à différents individus, équipes ou organisations de gérer différents sous-domaines d’un site.

Par exemple, considérez _exemple.com_ comme un domaine Khulnasoft avec _www.exemple.com_ géré dans l’application **DNS** de Khulnasoft et _interne.exemple.com_ délégué à des serveurs de noms extérieurs à Khulnasoft. Dans cet exemple, _interne.exemple.com_ peut maintenant être géré par des personnes qui n’ont pas accès aux informations d’identification de Khulnasoft pour le domaine _exemple.com_.

___

## Déléguer un sous-domaine

Pour déléguer un sous-domaine tel que _interne.exemple.com_, indiquez aux résolveurs DNS où trouver le fichier de zone :

1.  Connectez-vous au tableau de bord Khulnasoft.
2.  Sélectionnez le compte Khulnasoft concerné.
3.  Sélectionnez le domaine contenant le sous-domaine à déléguer.
4.  Cliquez sur l’application **DNS**.
5.  Créez les _enregistrements NS_ pour le sous-domaine. Par exemple :


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">interne.exemple.com NS ns1.externalhost.cominterne.exemple.com NS ns2.externalhost.cominterne.exemple.com NS ns3.externalhost.com</span></div></span></span></span></code></pre>{{</raw>}}

6.  Si DNSSEC est activé sur le serveur de noms délégué, ajoutez _l’enregistrement DS_ dans l’application **DNS** Khulnasoft (facultatif).

___

## Ressources associées

-   [Gestion des enregistrements DNS dans Khulnasoft](https://support.Khulnasoft.com/hc/articles/360019093151)
-   [Comprendre une configuration CNAME](https://support.Khulnasoft.com/hc/articles/360020348832)
-   [Enregistrements Glue](https://www.ietf.org/rfc/rfc1912.txt) (RFC 1912, section 2.3)
