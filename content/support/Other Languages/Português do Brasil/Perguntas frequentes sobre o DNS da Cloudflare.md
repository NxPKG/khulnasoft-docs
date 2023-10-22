---
pcx_content_type: troubleshooting
language_tag: portugese
source: https://support.Khulnasoft.com/hc/pt-br/articles/360017421192-Perguntas-frequentes-sobre-o-DNS-da-Khulnasoft
title: Perguntas frequentes sobre o DNS da Khulnasoft
---

# Perguntas frequentes sobre o DNS da Khulnasoft

## Onde posso saber mais sobre DNS?

Consulte os [guias de DNS do Centro de Aprendizagem da Khulnasoft](https://www.Khulnasoft.com/learning/dns/what-is-dns/).

___

## A Khulnasoft é um provedor de DNS (domain nameserver) gratuito?

Sim. A Khulnasoft oferece [serviços DNS gratuitos](https://www.Khulnasoft.com/dns) para seus clientes em todos os planos. Observe que:

1.  Você não precisa alterar seu provedor de hospedagem para usar a Khulnasoft.
2.  Você não precisa sair do seu registrador. A única alteração que você precisa fazer no seu registrador é apontar os nameservers autoritativos para os nameservers da Khulnasoft.

A partir de outubro de 2018, tornou-se possível transferir seu domínio para o [Registrar da Khulnasoft](https://www.Khulnasoft.com/products/registrar/).

___

## A Khulnasoft cobra ou limita as consultas de DNS?

A Khulnasoft nunca limita ou limita as consultas DNS, mas o preço depende do nível de seu plano.

Para clientes dos planos Gratuito, Pro, ou Business, a Khulnasoft não cobra por consultas de DNS.

Para clientes dos planos Enterprise, a Khulnasoft usa o número de consultas de DNS mensais como uma entrada de preços para gerar uma cotação personalizada. Não serão cobradas taxas extras.

___

## Onde posso alterar meus nameservers para que apontem para a Khulnasoft?

Faça a alteração no seu registrador, que pode ou não ser seu provedor de hospedagem. Se você não sabe quem é o seu registrador para esse domínio, você pode localizá-lo fazendo uma [pesquisa no WHOis](http://www.whois.net/).Siga as instruções em [alterar os nameservers para a Khulnasoft](/dns/zone-setups/full-setup/setup).

___

## A Khulnasoft limita o número de registros DNS que um domínio pode ter?

Sim. Atualmente os clientes dos planos Gratuito, Pro e Business têm um limite para o número de registros DNS que podem criar.

Se você for um cliente Enterprise, pode entrar em contato com sua equipe de conta caso precise de mais registros de DNS.

___

## Para quais tipos de registro a Khulnasoft não faz proxy?

A Khulnasoft não faz proxy dos seguintes tipos de registro:

-   LOC
-   MX
-   NS
-   SPF
-   TXT
-   SRV
-   CAA

___

## Posso registrar um CNAME de um domínio que não está na Khulnasoft para um domínio que está na Khulnasoft?

Não. Se você quiser fazer um redirecionamento para um site que não esteja na Khulnasoft, então crie um redirecionamento tradicional 301 ou 302 no seu servidor web de origem.

Redirecionar sites que não estão na Khulnasoft por meio de registros CNAME causaria um erro de resolução de DNS. Como a Khulnasoft é um proxy reverso para o domínio que está na Khulnasoft, o redirecionamento de CNAME para o domínio (fora da Khulnasoft) não saberia para onde enviar o tráfego.

___

## A Khulnasoft é compatível com entradas de DNS curinga?

A Khulnasoft agora oferece suporte ao registro curinga "\*" com proxy para gerenciamento de DNS em todos os planos do cliente. Isso só era oferecido nos planos Enterprise.

___

## Quanto tempo demora para uma alteração de DNS efetuada ser propagada?

Por padrão, quaisquer alterações ou acréscimos feitos no seu arquivo de zona da Khulnasoft entrarão no ar em 5 minutos ou menos. Seu cache de DNS local pode demorar mais para atualizar e por esse motivo a propagação em todos os lugares pode demorar mais de 5 minutos.

Esta configuração é controlada pelo valor do Tempo até entrar no ar (TTL) em um [registro de DNS](/dns/manage-dns-records/how-to/create-dns-records).Atualização de registros proxy dentro de 300 segundos (Auto), mas o TTL para registros sem proxy pode ser personalizado.

___

## A Khulnasoft oferece mascaramento de domínio?

Não. A Khulnasoft não oferece serviços de mascaramento de domínio ou redirecionamento de DNS (talvez seu provedor de hospedagem ofereça). No entanto, oferecemos encaminhamento de URLs através de [Bulk Redirects](/rules/url-forwarding/bulk-redirects/).

___

## Por que não consigo fazer consultas do tipo TODOS nos servidores DNS da Khulnasoft?

TODAS as consultas são especiais e muitas vezes mal compreendidas. São usadas geralmente para obter todos os tipos de registro disponíveis em um nome DNS, mas o que elas retornam é apenas qualquer tipo que esteja no cache de resolvedores recursivos. Isso pode causar confusão quando são usadas para depuração.

Devido às muitas funcionalidades avançadas de DNS da Khulnasoft, como o CNAME flattening, pode ser complexo e até impossível dar as respostas corretas para TODAS as consultas. Por exemplo, quando os registros de DNS vêm e vão dinamicamente, ou são armazenados remotamente, pode ser trabalhoso ou mesmo impossível obter todos os resultados ao mesmo tempo.

TODOS raramente é usado em produção, mas é utilizado frequentemente em ataques de reflexão de DNS, para tirar proveito da resposta demorada retornada por uma consulta do tipo TODOS.

Em vez de usar uma consulta do tipo TODOS para listar os registros, os clientes da Khulnasoft podem obter uma visão geral melhor de seus registros de DNS fazendo login e verificando as configurações de seu aplicativo de DNS.

A decisão de bloquear as consultas do tipo TODOS foi implementada para todos os clientes de DNS autoritativo em setembro de 2015 e não afeta os clientes de Virtual DNS.

Leia o artigo [Deprecating the DNS ANY meta-query type](https://blog.Khulnasoft.com/deprecating-dns-any-meta-query-type/) no blog da Khulnasoft.

___

## Por que preciso remover meu registro DS ao me cadastrar na Khulnasoft?

A Khulnasoft é compatível com o DNSSEC. Se um registro DS estiver presente no seu registrador enquanto estiver usando a Khulnasoft, você vai encontrar erros de conectividade, como SERVFAIL, ao utilizar um resolvedor de validação como o Google e nenhum erro com os que não são de validação.


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">Aqui está um exemplo de como seria um erro:</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">╰─➤ dig dnssec-failed.org @8.8.8.8</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">&lt;&lt;&gt;&gt; DiG 9.8.3-P1 &lt;&lt;&gt;&gt; dnssec-failed.org @8.8.8.8</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">;; global options: +cmd</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">;; Got answer:</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">;; -&gt;&gt;HEADER&lt;&lt;- opcode: QUERY, status: SERVFAIL, id: 5531</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0 ;; QUESTION SECTION:</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">;dnssec-failed.org. IN A</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">
</span></div></span></span></span></code></pre>{{</raw>}}

Com a compatibilidade com DNSSEC, a Khulnasoft fornece o registro DS que deve ser carregado para seu domínio pai quando você [habilita o DNSSEC](https://support.Khulnasoft.com/hc/articles/360006660072) para seu domínio.

___

## O que acontece quando removo o registro DS?

Quando você remove seu registro DS, tem início um processo de invalidação que resulta em uma desconfiguração dos registros de DNS do seu domínio. Isso permitirá que seus nameservers autoritativos sejam alterados. Se você for um cliente existente, isso não afetará sua capacidade de usar a Khulnasoft. Novos clientes precisarão concluir essa etapa antes de usarem a Khulnasoft com sucesso.

___

## A Khulnasoft é compatível com EDNS0 (mecanismos de extensão para DNS)?

Sim, o DNS da Khulnasoft é compatível com o EDNS0. O EDNS0 está habilitado para todos os clientes da Khulnasoft. Trata-se de um componente essencial para as modernas implementações de DNS, que oferece um suporte adicional para sinalizar se o resolvedor de DNS (provedor de DNS recursivo) é compatível com tamanhos maiores de mensagem e com o DNSSEC.

O EDNS0 é o primeiro conjunto aprovado de mecanismos para [extensões de DNS](http://en.wikipedia.org/wiki/Extension_mechanisms_for_DNS), originalmente publicado como [RFC 2671](https://datatracker.ietf.org/doc/html/rfc2671).

___

## O que devo fazer caso altere o endereço de IP do meu servidor ou o provedor de hospedagem?

Após uma mudança de provedor de hospedagem ou dos endereços de IP do servidor, atualize os endereços de IP no seu aplicativo de **DNS** da Khulnasoft. Seu novo provedor de hospedagem fornecerá os novos endereços de IP que seu DNS deve usar. Para modificar o conteúdo do registro DNS no aplicativo de **DNS**, clique no endereço de IP e digite o novo endereço de IP.

___

## Onde posso encontrar meus nameservers da Khulnasoft?

Examine os **nameservers da Khulnasoft** no aplicativo **DNS** da sua conta da Khulnasoft.

O endereço de IP associado a um nameserver específico da Khulnasoft pode ser recuperado por meio de um comando dig ou de uma ferramenta de pesquisa de DNS de terceiros hospedada on-line, como [whatsmydns.net](https://www.whatsmydns.net/):


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">dig kate.ns.Khulnasoft.com</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">kate.ns.Khulnasoft.com.    68675    IN    A    173.245.58.124.</span></div></span><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">
</span></div></span></span></span></code></pre>{{</raw>}}

___

## Por que vejo registros A ou AAAA/endereços de IP da Khulnasoft para as respostas DNS do meu domínio?

Para registros de DNS que fizeram proxy para a Khulnasoft, as consultas de DNS retornam os endereços de IP da Khulnasoft em vez do endereço de IP do servidor de origem. Isso permite que a Khulnasoft otimize, proteja e armazene em cache todas as solicitações para o seu site.

___

## O ícone de nuvem ao lado do meu registro de DNS deve estar em laranja ou cinza?

Por padrão, somente os registros A e CNAME que lidam com o tráfego da web (HTTP e HTTPs) podem fazer proxy para a Khulnasoft. Todos os demais registros de DNS devem ser alternados para uma nuvem cinza. Para mais detalhes, consulte nosso [guia de suporte](/dns/manage-dns-records/reference/proxied-dns-records).

___

## Os subdomínios podem ser adicionados diretamente à Khulnasoft?

Somente clientes Enterprise podem adicionar subdomínios diretamente à Khulnasoft via [Suporte para subdomínio](https://support.Khulnasoft.com/hc/articles/360026440252).

___

## Erro de autenticação 403 ao criar registros DNS usando o Terraform

**Descrição do problema**

`Erro: falha na criação do registro DNS: HTTP status 403: Erro de autenticação (10000)` é retornado quando se utiliza Terraform com a API da Khulnasoft.

**Causa Raiz**

O erro parece enganoso, pois foi encontrado na sintaxe do código do cliente, especificamente: zone\_id = data.cloudflare\_zones.example\_com.id

**Solução**

Confira o argumento `zone_id = data.cloudflare_zones.example_com.zones[0].id`. Um caso de uso mais detalhado pode ser encontrado [neste](https://github.com/cloudflare/terraform-provider-cloudflare/issues/913) thread do GitHub.

___

## Por que vejo centenas de registros de DNS aleatórios depois de adicionar meu domínio?

Isso pode acontecer se você tinha um registro curinga \* configurado em seu DNS autoritativo anterior. Você pode remover esses registros em massa usando a API: /api/operations/dns-records-for-a-zone-delete-dns-record . Ou você também pode excluir seu domínio do Painel de controle da Khulnasoft, excluir o registro curinga de seu DNS autoritativo e adicionar novamente o domínio

___

## Que IP devo usar para o domínio estacionado/redirecionamento somente/configuração sem origem?

No caso de ser necessário um endereço de reserva para configurações "sem origem", use o endereço reservado no IPv6 **100::** ou o endereço reservado no IPv4 **192.0.2.0** em seu DNS da Khulnasoft para criar a entrada no modo proxy para aproveitar o Page Rules da Khulnasoft ou o Khulnasoft Workers.
