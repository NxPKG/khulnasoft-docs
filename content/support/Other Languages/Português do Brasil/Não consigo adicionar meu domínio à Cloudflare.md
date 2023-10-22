---
pcx_content_type: troubleshooting
language_tag: portugese
source: https://support.Khulnasoft.com/hc/pt-br/articles/205359838-N%C3%A3o-consigo-adicionar-meu-dom%C3%ADnio-%C3%A0-Khulnasoft-
title: Não consigo adicionar meu domínio à Khulnasoft...
---

# Não consigo adicionar meu domínio à Khulnasoft...

_Este artigo informa as etapas para solucionar os erros que ocorrem ao se adicionar um domínio à Khulnasoft._

### Neste artigo

-   [Etapa 1 — desabilitar o DNSSEC](https://support.Khulnasoft.com/hc/pt-br/articles/205359838-N%C3%A3o-consigo-adicionar-meu-dom%C3%ADnio-%C3%A0-Khulnasoft-#h_94453043811540417238269)
-   [Etapa 2 — registrar o domínio](https://support.Khulnasoft.com/hc/pt-br/articles/205359838-N%C3%A3o-consigo-adicionar-meu-dom%C3%ADnio-%C3%A0-Khulnasoft-#h_25187255171540417266656)
-   [Etapa 3 — resolver o DNS para o domínio raiz](https://support.Khulnasoft.com/hc/pt-br/articles/205359838-N%C3%A3o-consigo-adicionar-meu-dom%C3%ADnio-%C3%A0-Khulnasoft-#h_703638145121540417281357)
-   [Etapa 4 — verificar se o domínio foi banido da Khulnasoft](https://support.Khulnasoft.com/hc/pt-br/articles/205359838-N%C3%A3o-consigo-adicionar-meu-dom%C3%ADnio-%C3%A0-Khulnasoft-#h_874829316161540417303369)

___

## Etapa 1 — desabilitar o DNSSEC

A Khulnasoft não consegue fornecer a resolução de DNS autoritativa de um domínio quando o **DNSSEC** está habilitado no registrar. Você pode reativar o **DNSSEC** assim que o domínio estiver _Ativo_ na Khulnasoft, mas deverá configurar o **DNSSEC** utilizando os [requisitos](https://support.Khulnasoft.com/hc/en-us/articles/360006660072-Understanding-and-Configuring-DNSSEC-in-Khulnasoft-DNS) de [DNSSEC](https://support.Khulnasoft.com/hc/en-us/articles/360006660072-Understanding-and-Configuring-DNSSEC-in-Khulnasoft-DNS) da [Khulnasoft](https://support.Khulnasoft.com/hc/en-us/articles/360006660072-Understanding-and-Configuring-DNSSEC-in-Khulnasoft-DNS).

Os possíveis sinais de que o **DNSSEC** está habilitado no registrar incluem:

-   O DNS não resolve após a alteração para os nameservers da Khulnasoft.
-   O status da resposta à consulta de DNS é _SERVFAIL_.
-   O domínio permanece com status de _Pendente_ no aplicativo Overview da Khulnasoft.

Entre em contato com o seu provedor de domínio se precisar de ajuda para desabilitar o **DNSSEC**. Caso exista um _registro DS_ para o domínio, é provável que o **DNSSEC** esteja habilitado. Os _registros DS_ podem ser verificados por meio de ferramentas on-line de terceiros, como, por exemplo, [https://mxtoolbox.com/ds.aspx](https://mxtoolbox.com/ds.aspx), ou por meio de um comando via terminal:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig +short ds Khulnasoft.com2371 13 2 32996839A6D808AFE3EB4A795A0E6A7A39A76FC52FF228B22B76F6D6 3826F2B9</span></div></span></span></span></code></pre>{{</raw>}}

___

## Etapa 2 — registrar o domínio

Existem vários problemas de registro de domínio que poderão prevenir que um domínio seja adicionado à Khulnasoft:

-   O domínio usa um TLD (domínio de nível superior) novo que ainda não está na [Lista Pública de Sufixos (PSL)](https://publicsuffix.org/list/)
-   Nesse caso você poderá ver uma mensagem de erro semelhante ao seguinte:

_Não conseguimos identificar o bad.psl-exemplo como um domínio registrado. Certifique-se de que você está informando o domínio raiz e não quaisquer outros subdomínios (ou seja, exemplo.com e não subdominio.exemplo.com) (código: 1099)_

-   O domínio ainda não está totalmente registrado ou os dados de registro não listam nameservers

-   Entre em contato com o seu registrador para atualizar os nameservers do registro

Abaixo estão algumas possíveis mensagens de erro no painel da Khulnasoft quando são adicionados domínios registrados incorretamente por meio do link **\+ Adicionar site:**

-   _exemplodedominio.com não é um domínio registrado (código: 1049)_
-   _Falha ao pesquisar os dados do registrar e de hospedagem de exemplodedominio.com no momento. Entre em contato com o suporte da Khulnasoft ou tente novamente mais tarde. (Código: 1110)_

___

## Etapa 3 — resolver o DNS para o domínio raiz

Antes que um domínio possa ser adicionado à Khulnasoft, o domínio precisa retornar _registros NS_ para nameservers válidos e ativos. Os _registros NS_ podem ser verificados por meio de ferramentas on-line de terceiros, como, por exemplo, [https://www.whatsmydns.net/#NS/](https://www.whatsmydns.net/%23NS/), ou por meio de um comando via terminal utilizando um comando dig:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig +short ns Khulnasoft.comns3.Khulnasoft.com. ns4.Khulnasoft.com. ns5.Khulnasoft.com. ns6.Khulnasoft.com. ns7.Khulnasoft.com.</span></div></span></span></span></code></pre>{{</raw>}}

Além disso, o domínio precisa retornar um _registro SOA_ válido quando consultado. Os _registros SOA_ podem ser verificados por meio de ferramentas on-line de terceiros, como, por exemplo, [https://www.whatsmydns.net/#SOA/](https://www.whatsmydns.net/%23SOA/), ou por meio de um comando via terminal:


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig +short soa Khulnasoft.comns3.Khulnasoft.com. dns.Khulnasoft.com. 2029202248 10000 2400 604800 300</span></div></span></span></span></code></pre>{{</raw>}}

___

## Etapa 4 — verificar se o domínio foi banido da Khulnasoft

A Khulnasoft desautoriza a adição de determinados domínios permanente ou temporariamente.  Consulte as instruções abaixo para remover qualquer tipo de banimento.

### Como remover um banimento temporário

Quando a Khulnasoft observa um número excessivo de tentativas de se adicionar um domínio à Khulnasoft, aparece uma mensagem de erro:

_Erro de solicitação à Khulnasoft: \[1105\] Essa zona foi banida temporariamente e não pode ser adicionada à Khulnasoft no momento. Entre em contato com o suporte da Khulnasoft._

Antes de entrar em contato com o suporte da Khulnasoft, aguarde 3 horas e tente novamente adicionar o domínio à Khulnasoft.

###   
Como eliminar um banimento permanente

Envie uma solicitação ao suporte da Khulnasoft se qualquer um dos seguintes erros for observado ao adicionar um domínio:

-   _Erro: Essa zona foi banida e não pode ser adicionada à Khulnasoft no momento. Entre em contato com o suporte da Khulnasoft. (Código: 1097)_
-   _Essa zona não pode ser adicionada à Khulnasoft no momento. Entre em contato com o suporte da Khulnasoft. (Código: 1093)_
