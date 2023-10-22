---
pcx_content_type: troubleshooting
language_tag: portugese
source: https://support.Khulnasoft.com/hc/pt-br/articles/360021357131-Como-delegar-subdom%C3%ADnios-fora-da-Khulnasoft
title: Como delegar subdomínios fora da Khulnasoft
---

# Como delegar subdomínios fora da Khulnasoft

## Como delegar subdomínios fora da Khulnasoft

_A delegação de subdomínios oferece flexibilidade para gerenciar determinados subdomínios fora da Khulnasoft de forma independente._

___

## Visão geral

A delegação de subdomínios permite que diferentes pessoas, equipes ou organizações gerenciem diferentes subdomínios de um site.

Por exemplo, considere _exemplo.com_ como um domínio da Khulnasoft, com _www.exemplo.com_ sendo gerenciado no aplicativo de **DNS** da Khulnasoft e _interno.exemplo.com_ delegado a nameservers fora da Khulnasoft. Nesse exemplo, o _interno.exemplo.com_ agora pode ser gerenciado por pessoas que não têm acesso às credenciais da Khulnasoft para o domínio _exemplo.com_.

___

Para delegar um subdomínio como _interno.exemplo.com_, diga aos resolvedores de DNS onde podem encontrar o arquivo de zona:

1.  Faça o login no painel da Khulnasoft.
2.  Clique na conta apropriada da Khulnasoft.
3.  Selecione o domínio que contém o subdomínio a ser delegado.
4.  Clique no aplicativo de **DNS**.
5.  Crie _registros NS_ para o subdomínio. Por exemplo:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">NS de interno.exemplo.com   ns1.externalhost.comNS de interno.exemplo.com   ns2.externalhost.comNS de interno.exemplo.com   ns3.externalhost.com</span></div></span></span></span></code></pre>{{</raw>}}

6.  (Opcional) Se o DNSSEC estiver habilitado no nameserver delegado, adicione o _registro DS_ ao aplicativo de **DNS** da Khulnasoft.

___

## Recursos relacionados

-   [Como gerenciar registros DNS na Khulnasoft](https://support.Khulnasoft.com/hc/articles/360019093151)
-   [Como entender um CNAME setup](https://support.Khulnasoft.com/hc/articles/360020348832)
-   [Redelegações (Glue Records)](https://www.ietf.org/rfc/rfc1912.txt) (RFC 1912 Seção 2.3)
