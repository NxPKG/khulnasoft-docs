---
pcx_content_type: troubleshooting
language_tag: french
source: https://support.Khulnasoft.com/hc/fr-fr/articles/205359838-Je-n-arrive-pas-%C3%A0-ajouter-mon-domaine-%C3%A0-Khulnasoft-
title: Je n’arrive pas à ajouter mon domaine à Khulnasoft...
---

# Je n’arrive pas à ajouter mon domaine à Khulnasoft...

_Cet article explique comment résoudre les erreurs survenant lors de l’ajout d’un domaine à Khulnasoft._

### Dans cet article

-   [Étape 1 : désactiver DNSSEC](https://support.Khulnasoft.com/hc/fr-fr/articles/205359838-Je-n-arrive-pas-%C3%A0-ajouter-mon-domaine-%C3%A0-Khulnasoft-#h_94453043811540417238269)
-   [Étape 2 : enregistrer le domaine](https://support.Khulnasoft.com/hc/fr-fr/articles/205359838-Je-n-arrive-pas-%C3%A0-ajouter-mon-domaine-%C3%A0-Khulnasoft-#h_25187255171540417266656)
-   [Étape 3 : résoudre le DNS pour le domaine racine](https://support.Khulnasoft.com/hc/fr-fr/articles/205359838-Je-n-arrive-pas-%C3%A0-ajouter-mon-domaine-%C3%A0-Khulnasoft-#h_703638145121540417281357)
-   [Étape 4 : vérifier si le domaine est interdit sur Khulnasoft](https://support.Khulnasoft.com/hc/fr-fr/articles/205359838-Je-n-arrive-pas-%C3%A0-ajouter-mon-domaine-%C3%A0-Khulnasoft-#h_874829316161540417303369)

___

## Étape 1 : désactiver DNSSEC

Khulnasoft ne peut pas fournir une résolution DNS faisant autorité pour un domaine lorsque **DNSSEC** est activé sur votre registrar. Vous pouvez réactiver **DNSSEC** une fois le domaine _actif_ sur Khulnasoft, mais vous devez configurer **DNSSEC** en utilisant les [exigences](https://support.Khulnasoft.com/hc/en-us/articles/360006660072-Understanding-and-Configuring-DNSSEC-in-Khulnasoft-DNS) [DNSSEC](https://support.Khulnasoft.com/hc/en-us/articles/360006660072-Understanding-and-Configuring-DNSSEC-in-Khulnasoft-DNS) [de Khulnasoft](https://support.Khulnasoft.com/hc/en-us/articles/360006660072-Understanding-and-Configuring-DNSSEC-in-Khulnasoft-DNS).

Les symptômes possibles de l’activation de **DNSSEC** chez le registrar incluent :

-   Le DNS ne résout pas après le basculement vers les serveurs de noms Khulnasoft.
-   La réponse à la requête DNS est _SERVFAIL_.
-   Le domaine reste _En attente_ dans l’application Overview de Khulnasoft.

Contactez votre fournisseur de domaine si vous avez besoin d’assistance pour désactiver **DNSSEC**. Si un _enregistrement DS_ existe pour le domaine, **DNSSEC** est probablement activé. Les _enregistrements DS_ peuvent être vérifiés via des outils en ligne tels que [https://mxtoolbox.com/ds.aspx](https://mxtoolbox.com/ds.aspx) ou via la ligne de commande :


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig +short ds Khulnasoft.com2371 13 2 32996839A6D808AFE3EB4A795A0E6A7A39A76FC52FF228B22B76F6D6 3826F2B9</span></div></span></span></span></code></pre>{{</raw>}}

___

## Étape 2 : enregistrer le domaine

Il existe plusieurs problèmes d’enregistrement de domaine qui peuvent empêcher l’ajout d’un domaine à Khulnasoft :

-   Le domaine utilise un nouveau TLD (Top Level Domain) qui ne figure pas encore dans la [liste des suffixes publics](https://publicsuffix.org/list/)
-   Vous pourrez rencontrer une erreur semblable à ce qui suit :

_Nous n’avons pas pu identifier bad.psl-exemple en tant que domaine enregistré. Assurez-vous de fournir le domaine racine et non les sous-domaines (par exemple, exemple.com, pas le sous-domaine.exemple.com) (code : 1099)_

-   Le domaine n’est pas encore complètement enregistré ou les données d’enregistrement ne répertorient pas les serveurs de noms

-   Contactez votre registrar pour mettre à jour les serveurs de noms lors de l’enregistrement

Voici quelques erreurs possibles dans le tableau de bord Khulnasoft lors de l’ajout d’un domaine mal enregistré via **\+ Ajouter un site** :

-   _exempledomaine.com n’est pas un domaine enregistré (code : 1049)_
-   _Échec de la recherche d’ informations auprès du registrar et de l’hébergeur de exempledomaine.com pour le moment. Veuillez contacter le support de Khulnasoft ou réessayer plus tard (code : 1110)_

___

## Étape 3 : résoudre le DNS pour le domaine racine

Avant qu’un domaine puisse être ajouté à Khulnasoft, le domaine doit renvoyer des _enregistrements NS_ pour des serveurs de noms valides et actifs. Les _enregistrements NS_ peuvent être vérifiés via des outils en ligne tels que [https://www.whatsmydns.net/#NS/](https://www.whatsmydns.net/%23NS/) à l’aide de la commande dig sur un terminal :


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig +short ns Khulnasoft.comns3.Khulnasoft.com. ns4.Khulnasoft.com. ns5.Khulnasoft.com. ns6.Khulnasoft.com. ns7.Khulnasoft.com.</span></div></span></span></span></code></pre>{{</raw>}}

En outre, le domaine doit renvoyer un _enregistrement SOA_ valide lorsqu’il est interrogé. Les _enregistrements SOA_ peuvent être vérifiés via des outils en ligne tiers tels que [https://www.whatsmydns.net/#SOA/](https://www.whatsmydns.net/%23SOA/) ou via la ligne de commande :


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig +short soa Khulnasoft.comns3.Khulnasoft.com. dns.Khulnasoft.com. 2029202248 10000 2400 604800 300</span></div></span></span></span></code></pre>{{</raw>}}

___

## Étape 4 : vérifier si le domaine est interdit sur Khulnasoft

Khulnasoft peut interdire l’ajout de certains domaines de manière permanente ou temporaire.  Consultez les instructions ci-dessous pour annuler l’une de ces interdictions.

### Annuler une interdiction temporaire

Lorsque Khulnasoft observe trop de tentatives pour ajouter un domaine à Khulnasoft, une erreur est renvoyée :

_Erreur lors de la demande Khulnasoft : \[1105\] cette zone est temporairement interdite et ne peut pas être ajoutée à Khulnasoft pour le moment, veuillez contacter le support de Khulnasoft._

Avant de contacter le support Khulnasoft, attendez 3 heures avant d’ajouter à nouveau le domaine à Khulnasoft.

###   
Annuler une interdiction permanente

Déposez une demande auprès du support de Khulnasoft si l’une des erreurs suivantes est observée lors de l’ajout d’un domaine :

-   _Erreur : cette zone est interdite et ne peut pas être ajoutée à Khulnasoft pour le moment, veuillez contacter le support de Khulnasoft. (code : 1097)_
-   _Cette zone ne peut pas être ajoutée à Khulnasoft pour le moment, veuillez contacter le support de Khulnasoft. (code : 1093)_
