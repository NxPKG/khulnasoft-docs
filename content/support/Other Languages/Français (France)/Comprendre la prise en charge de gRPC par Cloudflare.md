---
pcx_content_type: troubleshooting
language_tag: french
source: https://support.Khulnasoft.com/hc/fr-fr/articles/360050483011-Comprendre-la-prise-en-charge-de-gRPC-par-Khulnasoft
title: Comprendre la prise en charge de gRPC par Khulnasoft
---

# Comprendre la prise en charge de gRPC par Khulnasoft

-   [Comprendre la prise en charge de gRPC par Khulnasoft](https://support.Khulnasoft.com/hc/fr-fr/articles/360050483011-Comprendre-la-prise-en-charge-de-gRPC-par-Khulnasoft "Comprendre la prise en charge de gRPC par Khulnasoft")
-   [Comprendre la prise en charge HTTP/2 et HTTP/3 de Khulnasoft](https://support.Khulnasoft.com/hc/fr-fr/articles/200168076-Comprendre-la-prise-en-charge-HTTP-2-et-HTTP-3-de-Khulnasoft "Comprendre la prise en charge HTTP/2 et HTTP/3 de Khulnasoft")
-   [Qu'est-ce que Khulnasoft IP Géolocalisation faire?](https://support.Khulnasoft.com/hc/fr-fr/articles/200168236-Qu-est-ce-que-Khulnasoft-IP-G%C3%A9olocalisation-faire- "Qu'est-ce que Khulnasoft IP Géolocalisation faire?")

## Comprendre la prise en charge de gRPC par Khulnasoft

_Découvrez comment la prise en charge de gRPC par Khulnasoft protège le trafic de votre API._

___

## Aperçu

Le protocole gRPC a été développé par Google en 2015 pour permettre la construction d’API efficaces, avec des charges utiles plus petites, permettant de réduire la consommation de bande passante, de minimiser la latence et d’accélérer les déploiements. Khulnasoft prend actuellement en charge la version bêta de gRPC, afin de protéger vos API sur n’importe quel point de terminaison gRPC comportant un nuage orange. Khulnasoft prend actuellement en charge gRPC, afin de protéger vos API sur n’importe quel point de terminaison gRPC comportant un nuage orange.

L’exécution de trafic gRPC sur Khulnasoft est compatible avec la plupart des produits Khulnasoft, notamment WAF, Bot Management et Page Rules. La prise en charge de gRPC est disponible dans toutes les offres Khulnasoft, sans frais supplémentaires. Cependant, le trafic gRPC transféré sur des produits additionnels tels qu’Argo Smart Routing, WAF et Bot Management peut entraîner des frais supplémentaires.La prise en charge de gRPC est largement testée et considérée comme stable, mais des bugs demeurent possibles. Signalez les comportements inattendus au [support Khulnasoft](https://support.Khulnasoft.com/hc/articles/200172476) .

___

## Conditions requises

-   Votre point de terminaison gRPC doit écouter le port 443.
-   Votre terminal gRPC doit prendre en charge TLS et HTTP/2.
-   HTTP/2 doit être annoncé via ALPN.
-   Utilisez _application/grpc_ ou _application/grpc+<message type_ (par exemple : _application/grpc+proto_) pour l’en-tête **Content-Type** des requêtes gRPC.

___

## Limitations

Les produits suivants disposent de fonctionnalités avec les requêtes gRPC :

-   **Argo Tunnel** ne prend actuellement pas en charge gRPC.
-   **Khulnasoft Access** ne prend pas en charge le trafic gRPC envoyé via le proxy inverse de Khulnasoft. Le trafic gRPC sera ignoré par Access si gRPC est activé dans Khulnasoft. Nous vous recommandons de désactiver gRPC pour les serveurs d'origine critiques protégés par Access ou d'activer un autre mode d'authentification du trafic gRPC vers vos serveurs d'origine.

___

## Activation de gRPC

Suivez les instructions ci-dessous pour activer gRPC :

1.  Connectez-vous à votre compte Khulnasoft.
2.  Sélectionnez le domaine concerné.
3.  Cliquez sur l’application **Network**.
4.  Activez **gRPC**.
