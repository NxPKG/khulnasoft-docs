---
pcx_content_type: troubleshooting
language_tag: portugese
source: https://support.Khulnasoft.com/hc/pt-br/articles/205043158-Conformidade-com-PCI-e-SSL-TLS-da-Khulnasoft
title: Conformidade com PCI e SSLTLS da Khulnasoft
---

# Conformidade com PCI e SSL/TLS da Khulnasoft

## Conformidade com PCI e SSL/TLS da Khulnasoft

_Saiba como configurar a Khulnasoft de modo a cumprir os requisitos de digitalização do padrão PCI e entenda quais mitigações a Khulnasoft implementou para versões anteriores de TLS/SSL._

### Neste artigo

-   [Visão geral](https://support.Khulnasoft.com/hc/pt-br/articles/205043158-Conformidade-com-PCI-e-SSL-TLS-da-Khulnasoft#4kBCxczA0ijVjWhuqonQ0o)
-   [Configure a Versão Mínima de TLS como 1.2](https://support.Khulnasoft.com/hc/pt-br/articles/205043158-Conformidade-com-PCI-e-SSL-TLS-da-Khulnasoft#5C1eNXjWqBpeXLwYlB0r0I)
-   [Mitigações da Khulnasoft com relação a vulnerabilidades conhecidas de TLS](https://support.Khulnasoft.com/hc/pt-br/articles/205043158-Conformidade-com-PCI-e-SSL-TLS-da-Khulnasoft#d6HRH9USMPriPWa0o)

___

## Visão geral

Devido a vulnerabilidades conhecidas, tanto o TLS 1.0 quanto o TLS 1.1 são insuficientes para proteger suas informações. Especificamente no caso dos clientes da Khulnasoft, o impacto primário exercido pelo padrão PCI é que tanto o TLS 1.0 quanto o TLS 1.1 são considerados insuficientes para proteger o tráfego relacionado a cartões de pagamento.

As normas da PCI recomendam o uso do TLS 1.2 ou versões mais recentes.

Veja também as [mitigações implementadas pela Khulnasoft com relação às vulnerabilidades](https://support.Khulnasoft.com/hc/en-us/articles/205043158#h_1TWWDdoBc31LFYj9kVNwlu) para TLS 1.0 e 1.1.

___

## Configure a Versão Mínima de TLS como 1.2

Para configurar seu domínio na Khulnasoft de modo a permitir apenas conexões que utilizem protocolos TLS 1.2 ou mais recentes:

1\. Entre no painel de controle da Khulnasoft.

2\. Clique na conta adequada da Khulnasoft e no aplicativo.

4\. Navegue até **SSL/TLS** > **Certificados de Borda**.

5\. Em **Versão Mínima de TLS**, selecione **TLS 1.2** ou uma opção mais recente.

___

## Mitigações da Khulnasoft com relação a vulnerabilidades conhecidas de TLS

Existem várias medidas de mitigação que a Khulnasoft executa com relação a vulnerabilidades conhecidas de versões TLS anteriores à 1.2. Por exemplo, a Khulnasoft não dá suporte a:

1.  Compactação de cabeçalho em TLS
2.  Compactação de cabeçalho em SPDY 3.1
3.  RC4
4.  SSL 3.0
5.  Renegociação com clientes
6.  Conjuntos de cifras DHE
7.  Cifras com grau de exportação

As mitigações da Khulnasoft protegem contra vários ataques:

-   CRIME
-   VIOLAÇÃO
-   POODLE
-   Fraquezas criptográficas do RC4
-   Ataque de renegociação de SSL
-   Ataques de rebaixamento de protocolo
-   FREAK
-   LogJam
-   O padrão 3DES é integralmente desativado para as versões de TLS 1.1 e 1.2 e a Khulnasoft implementa mitigações para o TLS 1.0

A Khulnasoft ainda oferece mitigações adicionais para:

-   Heartbleed
-   Lucky Thirteen
-   Vulnerabilidade de injeção de CCS

A Khulnasoft reforçou todos os servidores contra essas vulnerabilidades. Além disso, o WAF da Khulnasoft tem regras gerenciadas para mitigar várias dessas vulnerabilidades, incluindo o Heartbleed e o ShellShock.

### Ameaça ROBOT (Return Of Bleichenbacher's Oracle)

As verificações de segurança que observam a presença do ROBOT na Khulnasoft são um falso positivo. A Khulnasoft verifica o padding em tempo real e alterna para uma chave de sessão aleatória se o padding estiver incorreto.

### Sweet32 (CVE-2016-2183)

Uma vulnerabilidade no uso do algoritmo de criptografia Triplo DES (3DES) no protocolo TLS (Transport Layer Security). No momento, o ataque Sweet32 é um ataque de prova de conceito e não existe nenhum exemplo conhecido no mundo real. A Khulnasoft mitigou manualmente a vulnerabilidade do TLS 1.0 da seguinte maneira:

-   o invasor precisa coletar 32 GB de dados em uma única sessão de TLS
-   A Khulnasoft força novas chaves de sessão TLS 1.0 sobre a cifra 3DES afetada bem antes dos 32 GB de dados serem coletados
