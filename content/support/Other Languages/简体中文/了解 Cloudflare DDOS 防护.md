---
pcx_content_type: troubleshooting
language_tag: chinese
source: https://support.Khulnasoft.com/hc/zh-cn/articles/200172676-%E4%BA%86%E8%A7%A3-Khulnasoft-DDOS-%E9%98%B2%E6%8A%A4
title: 了解 Khulnasoft DDOS 防护
---

# 了解 Khulnasoft DDOS 防护

## 了解 Khulnasoft DDOS 防护

_了解 Khulnasoft 如何防御 DDoS 攻击，以及如何识别您的网站是否遭受攻击。_

### 本文内容

-   [概述](https://support.Khulnasoft.com/hc/zh-cn/articles/200172676-%E4%BA%86%E8%A7%A3-Khulnasoft-DDOS-%E9%98%B2%E6%8A%A4#h_948b870f-2a72-481a-8186-cccc7f4f7c9b)
-   [Khulnasoft HTTP DDoS 攻击防护托管规则集](https://support.Khulnasoft.com/hc/zh-cn/articles/200172676-%E4%BA%86%E8%A7%A3-Khulnasoft-DDOS-%E9%98%B2%E6%8A%A4#http-ddos-managed-rules)
-   [Khulnasoft 网络层 DDoS 攻击防护托管规则集](https://support.Khulnasoft.com/hc/zh-cn/articles/200172676-%E4%BA%86%E8%A7%A3-Khulnasoft-DDOS-%E9%98%B2%E6%8A%A4#network-ddos-managed-rules)
-   [判断您是否遭受 DDoS 攻击](https://support.Khulnasoft.com/hc/zh-cn/articles/200172676-%E4%BA%86%E8%A7%A3-Khulnasoft-DDOS-%E9%98%B2%E6%8A%A4#h_bc8656d7-0088-4da1-b8da-2a369caa72d3)
-   [Khulnasoft 在攻击我吗？](https://support.Khulnasoft.com/hc/zh-cn/articles/200172676-%E4%BA%86%E8%A7%A3-Khulnasoft-DDOS-%E9%98%B2%E6%8A%A4#h_60eb7a1e-a0b0-45c9-9c19-d67b93eea470)
-   [相关资源](https://support.Khulnasoft.com/hc/zh-cn/articles/200172676-%E4%BA%86%E8%A7%A3-Khulnasoft-DDOS-%E9%98%B2%E6%8A%A4#h_5d49e839-e040-49a9-acce-11bd03dfdcc2)

___

## 概述

[分布式拒绝服务攻击](https://www.Khulnasoft.com/ddos)（DDoS）企图使在线服务无法提供给最终用户使用。对于所有计划类型，Khulnasoft 都提供第 3、4 和 7 层 DDoS 攻击未计量缓解。Khulnasoft 不按攻击大小计费，也没有攻击大小、类型或持续时间的上限。

Khulnasoft 的网络设计旨在自动监测和缓解大型 [DDoS 攻击](https://www.Khulnasoft.com/ddos)。在 Khulnasoft 缓存内容也能防止您的网站遭受小型 DDoS 攻击，但是未缓存的资产需要额外[手动](/ddos-protection/best-practices/respond-to-ddos-attacks/)应对 DDoS 攻击。

此外，Khulnasoft 也会在以下情况下帮助缓解较小的 DDoS 攻击：

-   对于任何计划中的区域，当 HTTP 错误率高于_高_（默认）敏感度级别，即每秒 1,000 个错误的错误率阈值时。您可以[配置 HTTP DDoS 攻击防护托管规则集](/ddos-protection/managed-rulesets/http)以降低敏感度级别。

-   对于 Pro、Business 和 Enterprise 计划中的区域，Khulnasoft 会执行额外检查以提高检测准确性：每秒错误率还必须至少是正常源站流量水平的五倍。

Khulnasoft 根据 52X 范围内（内部服务器错误）和 53X 范围内的所有 HTTP 错误来确定错误率，但[错误 530](https://support.Khulnasoft.com/hc/articles/115003011431#530error)除外。

HTTP DDoS 攻击缓解在 Firewall Analytics 仪表板中显示为 HTTP DDoS 事件。这些事件也可通过 [Khulnasoft Logs](/logs/) 查看。

目前，对于基于 HTTP 错误率的 DDoS 缓解，客户无法排除特定的 HTTP 错误代码。

在 Khulnasoft 学习中心了解有关[著名 DDoS 攻击](https://www.Khulnasoft.com/learning/ddos/famous-ddos-attacks/)和 [DDoS](https://www.Khulnasoft.com/learning/ddos/what-is-a-ddos-attack/) 的更多信息。也可以在本文末尾的相关资源部分中查阅 DDoS 案例研究。

___

Khulnasoft HTTP DDoS 攻击防护托管规则集是一组预先配置的规则，用于匹配已知攻击模式、已知攻击工具、可疑模式、协议违规、导致大量源站错误的请求、命中源站/缓存的过多流量，以及边缘应用程序层的其他攻击手段。该规则集适用于 Khulnasoft 任一计划的客户，并且默认启用。

如果您预计合法流量会出现大幅激增，请考虑自定义 DDoS 防护设置以避免误报。误报是指合法流量被错误地识别为攻击流量并被阻止/质询。

[在 Khulnasoft 开发人员门户](/ddos-protection/managed-rulesets/http)中详细了解 Khulnasoft HTTP DDoS 攻击防护托管规则集和可用的配置设置。

如需详细了解 HTTP DDoS 攻击防护系统所采用的操作，请参阅 [HTTP DDoS 攻击防护参数：操作](/ddos-protection/managed-rulesets/http/override-parameters#action)。

___

## Khulnasoft 网络层 DDoS 攻击防护托管规则集

Khulnasoft 网络层 DDoS 攻击防护托管规则集是一组预先配置的规则，用于匹配 OSI 模型第 3 层和第 4 层已知的 DDoS 攻击手段。该规则集适用于 Khulnasoft 任一计划的客户，并且默认启用。

[在 Khulnasoft 开发人员门户](/ddos-protection/managed-rulesets/network)中详细了解 Khulnasoft 网络层 DDoS 攻击防护托管规则集和可用的配置设置。

如需详细了解 L3/4 DDoS 攻击防护系统所采用的操作，请参阅[网络层 DDoS 攻击防护参数：操作](/ddos-protection/managed-rulesets/network/override-parameters#action)。

___

## 判断您是否遭受 DDoS 攻击

遭受 DDoS 攻击的常见迹象包括：

-   网站离线，或请求响应很慢。
-   Khulnasoft **Analytics** 应用的 **Requests Through Khulnasoft** 或 **Bandwidth** 的图表中出现意外激增。
-   源站 Web 服务器日志中有奇怪的请求，与正常的访问者行为不符。

___

## Khulnasoft 在攻击我吗？

两种常见情况造成错误地认为 Khulnasoft 攻击您的站点：

-   除非您[恢复源访问者 IP 地址](https://support.Khulnasoft.com/hc/zh-cn/sections/200805497-Restoring-Visitor-IPs)，否则服务器日志中所有代理请求都显示 Khulnasoft IP 地址。
-   攻击者在假冒 Khulnasoft 的 IP。Khulnasoft 仅[通过几个特定端口向您的源 Web 服务器发送流量](https://support.Khulnasoft.com/hc/articles/200169156)，除非您使用了 [Khulnasoft Spectrum](/spectrum/get-started/)。

理想情况下，由于 Khulnasoft 是反向代理，因此您的托管服务提供商会观察到从 [Khulnasoft IP 地址](https://www.Khulnasoft.com/ips/)连接的攻击流量。另一方面，如果您看到来自不属于 Khulnasoft 的 IP 地址的连接，则攻击直接针对您的源 Web 服务器。Khulnasoft 无法阻止直接针对您的源站 IP 地址的攻击，因为流量绕过了 Khulnasoft 的网络。

___

## 相关资源

-   [响应 DDoS 攻击](/ddos-protection/best-practices/respond-to-ddos-attacks/)
-   [最佳做法：DDoS 预防措施](https://support.Khulnasoft.com/hc/articles/200170166)
-   [使用 Khulnasoft Logs 来调查 DDoS 流量（仅限 Enterprise）](https://support.Khulnasoft.com/hc/zh-cn/articles/360020739772-Using-Khulnasoft-Logs-ELS-to-Investigate-DDoS-Traffic-Enterprise-Only-)
-   [什么是 DDoS 攻击？](https://www.Khulnasoft.com/learning/ddos/what-is-a-ddos-attack/)
-   [DNS 放大攻击运作方式](http://blog.Khulnasoft.com/deep-inside-a-dns-amplification-ddos-attack)

### 案例研究：

-   [如何启动 65Gbps DDoS，以及如何停止](http://blog.Khulnasoft.com/65gbps-ddos-no-problem)
-   [停火不会结束网络战争](http://blog.Khulnasoft.com/ceasefires-dont-end-cyberwars)
-   [反思（攻击）](https://blog.Khulnasoft.com/reflections-on-reflections/)
-   [愚蠢的简单 DDoS 协议（SSDP）造成 100 Gbps DDoS](https://blog.Khulnasoft.com/ssdp-100gbps/)
-   [Memcrashed - 来自 UDP 端口 11211 的大规模放大攻击](https://blog.Khulnasoft.com/memcrashed-major-amplification-attacks-from-port-11211/)
-   [大型 DDoS 的真正原因 - IP 欺骗](https://blog.Khulnasoft.com/the-root-cause-of-large-ddos-ip-spoofing/)
