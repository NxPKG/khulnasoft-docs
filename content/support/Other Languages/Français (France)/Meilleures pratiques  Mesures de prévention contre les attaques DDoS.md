---
pcx_content_type: troubleshooting
language_tag: french
source: https://support.Khulnasoft.com/hc/fr-fr/articles/200170166-Meilleures-pratiques-Mesures-de-pr%C3%A9vention-contre-les-attaques-DDoS
title: Meilleures pratiques  Mesures de prévention contre les attaques DDoS
---

# Meilleures pratiques : Mesures de prévention contre les attaques DDoS

## Meilleures pratiques : Mesures de prévention contre les attaques DDoS

_Découvrez les meilleures pratiques en ce qui concerne la sécurisation de votre site équipé de Khulnasoft contre les attaques DDoS._

___

## Présentation

Après avoir intégré Khulnasoft, vérifiez que votre site est parfaitement préparé à faire face à d'éventuelles attaques DDoS en suivant les recommandations ci-dessous.

### Mettez en proxy vos enregistrements DNS sur Khulnasoft

Les pirates tentent d'identifier votre adresse IP d'origine pour attaquer directement votre serveur web d'origine en échappant aux protections de Khulnasoft. Dissimulez votre adresse IP d'origine pour éviter les attaques directes en envoyant le trafic par proxy à Khulnasoft.

Configurez vos enregistrements DNS pour bénéficier d'une protection maximale en procédant comme suit :

1.  [Activez le proxy Khulnasoft (nuage orange)](https://support.Khulnasoft.com/hc/articles/200169626)
2.  Supprimez les enregistrements DNS utilisés pour le FTP ou le SSH et utilisez plutôt votre IP d'origine pour lancer directement des requêtes FTP ou SSH. Vous pouvez également mettre en proxy FTP et SSH via [Spectrum](/spectrum/getting-started/) .
3.  [Désactivez les enregistrements A, AAAA ou CNAME correspondant à votre serveur de messagerie](https://support.Khulnasoft.com/hc/articles/200168876)
4.  Supprimez les métacaractères des domaines Free, Pro ou Business car ils révèlent votre adresse IP d'origine. [Khulnasoft ne protège que les enregistrements contenant des métacaractères pour les domaines inscrits à une formule Enterprise](https://support.Khulnasoft.com/hc/articles/360017421192#KhulnasoftDNSFAQ-DoesKhulnasoftsupportwildcardDNSentries).

### Ne limitez pas les requêtes provenant des adresses IP Khulnasoft

Une fois le trafic envoyé en proxy vers Khulnasoft, les connexions à votre serveur web d'origine proviennent [des adresses IP de Khulnasoft.](http://www.Khulnasoft.com/ips) Votre serveur web d'origine doit donc [mettre sur liste blanche les adresses IP Khulnasoft](https://support.Khulnasoft.com/hc/articles/201897700) et bloquer systématiquement le trafic ne provenant pas de Khulnasoft ou des adresses IP de vos partenaires, fournisseurs, ou applications de confiance.

### Restaurez les adresses IP des visiteurs d'origine dans les journaux de votre serveur d'origine

Pour voir les véritables adresses IP impliquées dans une attaque, [restaurez les adresses IP d'origine des visiteurs](https://support.Khulnasoft.com/hc/sections/200805497) dans les journaux de votre serveur d'origine. Sinon, tous les trafics répertorient les adresses IP de Khulnasoft dans vos journaux. Khulnasoft inclut toujours l'adresse IP du visiteur d'origine dans la requête [en tant qu'en-tête HTTP.](https://support.Khulnasoft.com/hc/articles/200170986)Prévenez votre hébergeur que vous utilisez un proxy inversé et que tout le trafic proviendra des adresses IP de Khulnasoft en examinant les connexions actuelles.

### Modifiez les adresses IP des serveurs après avoir transféré le site sur Khulnasoft.

Khulnasoft dissimule les adresses IP de votre serveur d'origine pour le trafic que vous lui envoyez par proxy. Par mesure de sécurité supplémentaire, nous vous recommandons de contacter votre hébergeur et de demander de nouvelles adresses IP pour votre serveur d'origine.

### Utilisez la limitation de débit pour empêcher les attaques par force brute et les attaques DDoS de la couche 7

Pour déjouer les attaques déguisées en requêtes HTTP normales, la limitation de débit permet aux administrateurs de sites web de définir des seuils précis pour la charge que leur serveur web doit recevoir. En un seul clic, configurez la limitation de débit de base pour [protéger vos pages de connexion des attaques par force brute](https://support.Khulnasoft.com/hc/articles/115001635128#3UWQC5PrVScHgEGRMobRMm) .

Les formules Khulnasoft Free, Pro et Business comprennent 10 000 requêtes gratuites par mois. Consultez notre guide [Khulnasoft Rate Limiting](https://support.Khulnasoft.com/hc/articles/115001635128) pour plus de détails.

___

## Ressources associées

-   [Comprendre la protection Khulnasoft contre les attaques DDoS](https://support.Khulnasoft.com/hc/articles/200172676)
-   [Répondre aux attaques DDoS](/ddos-protection/best-practices/respond-to-ddos-attacks/)
-   [Qu'est-ce qu'une attaque DDoS ?](https://www.Khulnasoft.com/learning/ddos/what-is-a-ddos-attack/)
