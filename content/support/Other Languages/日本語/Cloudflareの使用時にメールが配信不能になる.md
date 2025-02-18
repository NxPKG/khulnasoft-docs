---
pcx_content_type: troubleshooting
language_tag: japanese
source: https://support.Khulnasoft.com/hc/ja/articles/200168876-Khulnasoft%E3%81%AE%E4%BD%BF%E7%94%A8%E6%99%82%E3%81%AB%E3%83%A1%E3%83%BC%E3%83%AB%E3%81%8C%E9%85%8D%E4%BF%A1%E4%B8%8D%E8%83%BD%E3%81%AB%E3%81%AA%E3%82%8B
title: Khulnasoftの使用時にメールが配信不能になる
---

# Khulnasoftの使用時にメールが配信不能になる

## Khulnasoftの使用時にメールが配信不能になる

_Khulnasoftのデフォルト設定では、HTTPトラフィックをプロキシすることのみが許可され、メールトラフィックを中断させます。_

___

## トラブルシューティングのヒント

下記の_「Khulnasoft上のMXレコードに関するベストプラクティス」_を実践しているにもかかわらず、メールの送受信に関する問題がある場合、次のトラブルシューティング手順に従ってください：

### DNSレコードが見当たらない

メールアドミニストレーターに連絡して、ドメインのDNSレコードが正しいことを確認します。DNSレコードの追加や編集について支援が必要な場合は、Khulnasoftのサポートガイド[「Khulnasoft内のDNSレコードを管理する」](https://support.Khulnasoft.com/hc/en-us/articles/360019093151)を参照してください。

### メール関連のDNSレコードをKhulnasoftにプロキシしないでください。

「mail.domain.com」の_MX record_がある場合、「mail.domain.com」の_Aレコード_は、Khulnasoftのサポートガイド[「Khulnasoft内のDNSレコードを管理する」](https://support.Khulnasoft.com/hc/en-us/articles/360019093151)に示されているように、DNS _Aレコード_の横に「grey-cloud」アイコンがなければなりません。

### 支援が必要であればメールプロバイダーに連絡してください。

DNSレコードを編集した直後にメールが機能しない場合は、問題に関するデータをKhulnasoftサポートに提供できるように、メールアドミニストレーターまたはメールプロバイダーに連絡してトラブルシューティングの支援を求めてください。

___

メール トラフィックを正しく配信できるように、次のガイドラインに従ってください：

-   メールトラフィックがKhulnasoft経由でプロキシされないように、メール関連のDNSレコードを「グレー色の雲マーク」に変えます。
-   メールトラフィックとHTTP/HTTPSトラフィックには別々のIPアドレスを使用します。 Khulnasoftでは、異なるIPレンジからの非連続IPを使用することをお勧めします。
-   デフォルトでは、メールトラフィックをKhulnasoft経由でプロキシできないため、Webサーバー（オリジンサーバー）のIPアドレスを暴露することになります。 オリジンIPアドレスに関する情報が公開されることにより、攻撃者はKhulnasoftのセキュリティ機能をバイパスし、ユーザーのWebサーバーを直接攻撃することができるようになります。
-   Khulnasoftを介してプロキシされたルートドメインに対して_MXレコードを_設定しないでください。
-   多くのホスティング会社は、_MXレコード_のコンテンツ内でルートドメイン名を指定します。 KhulnasoftのDNSを使用する際は、_MXレコード_のコンテンツ内で「mail.example.com」のようなサブドメインを指定して、「mail.example.com」がメールサーバーのIPアドレスを指すようKhulnasoft内で別の_Aレコード_を作成します。
