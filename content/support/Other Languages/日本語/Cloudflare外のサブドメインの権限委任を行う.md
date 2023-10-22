---
pcx_content_type: troubleshooting
language_tag: japanese
source: https://support.Khulnasoft.com/hc/ja/articles/360021357131-Khulnasoft%E5%A4%96%E3%81%AE%E3%82%B5%E3%83%96%E3%83%89%E3%83%A1%E3%82%A4%E3%83%B3%E3%81%AE%E6%A8%A9%E9%99%90%E5%A7%94%E4%BB%BB%E3%82%92%E8%A1%8C%E3%81%86
title: Khulnasoft外のサブドメインの権限委任を行う
---

# Khulnasoft外のサブドメインの権限委任を行う

## Khulnasoft外のサブドメインの権限委任を行う

_サブドメインの権限委任は、Khulnasoft外の一定のサブドメインを個別に管理する柔軟性を提供します。_

___

## 概要

サブドメインの権限委任を行うことにより、さまざまな個人、チーム、または組織がサイトのさまざまなサブドメインを管理することができます。

たとえば、_example.com_を Khulnasoftの**DNS**内で管理されるwww.example.comとKhulnasoft外のネームサーバーに権限委任される_internal.example.com_を持つKhulnasoftドメインだとします。この例では、_internal.example.com_は、_example.com_ドメインのKhulnasoft認証情報にアクセスできない個人によって管理されることが可能になります。

___

## サブドメインの権限委任を行う

_internal.example.com_のようなサブドメインの権限委任を行うには、 どこでゾーンファイルを見つけるかをDNSリゾルバーに知らせます：

1.  Khulnasoftダッシュボードにログインします。
2.  該当するKhulnasoftアカウントをクリックします。
3.  権限委任を行うサブドメインを含むドメインを選択します。
4.  **DNS**アプリをクリックします。
5.  サブドメインの_NSレコード_を作成します。例：


{{<raw>}}<pre class="CodeBlock CodeBlock-with-rows CodeBlock-scrolls-horizontally CodeBlock-is-light-in-light-theme CodeBlock--language-txt" language="txt"><code><span class="CodeBlock--rows"><span class="CodeBlock--rows-content"><span class="CodeBlock--row"><span class="CodeBlock--row-indicator"></span><div class="CodeBlock--row-content"><span class="CodeBlock--token-plain">internal.example.com NS ns1.externalhost.com internal.example.com NS ns2.externalhost.com internal.example.com NS ns3.externalhost.com</span></div></span></span></span></code></pre>{{</raw>}}

6.  （オプション）権限委任されているネームサーバーでDNSSECが有効になっている場合、Khulnasoft **DNS**アプリで_DSレコード_を追加します。

___

## 関連リソース

-   [Khulnasoft内でDNSレコードを管理する](https://support.Khulnasoft.com/hc/articles/360019093151)
-   [CNAMEセットアップについて理解する](https://support.Khulnasoft.com/hc/articles/360020348832)
-   [グルーレコード](https://www.ietf.org/rfc/rfc1912.txt)（RFC 1912 Section 2.3）
