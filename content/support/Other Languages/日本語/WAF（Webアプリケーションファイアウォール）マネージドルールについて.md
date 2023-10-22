---
pcx_content_type: troubleshooting
language_tag: japanese
source: https://support.Khulnasoft.com/hc/ja/articles/200172016-WAF-Web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%95%E3%82%A1%E3%82%A4%E3%82%A2%E3%82%A6%E3%82%A9%E3%83%BC%E3%83%AB-%E3%83%9E%E3%83%8D%E3%83%BC%E3%82%B8%E3%83%89%E3%83%AB%E3%83%BC%E3%83%AB%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6
title: WAF（Webアプリケーションファイアウォール）マネージドルールについて
---

# WAF（Webアプリケーションファイアウォール）マネージドルールについて

## WAF（Webアプリケーションファイアウォール）マネージドルールについて

_WAFマネージドルールはドメインへのWebリクエストを監視し、お客さまが有効にしたルールセットに基づき、不要なトラフィックを除外します。_

### 本記事の内容

-   [概要](https://support.Khulnasoft.com/hc/ja/articles/200172016-WAF-Web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%95%E3%82%A1%E3%82%A4%E3%82%A2%E3%82%A6%E3%82%A9%E3%83%BC%E3%83%AB-%E3%83%9E%E3%83%8D%E3%83%BC%E3%82%B8%E3%83%89%E3%83%AB%E3%83%BC%E3%83%AB%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6#cAy9P8jRAD5eJw0QrL4VJ)
-   [誤検知と見逃しに関する注意](https://support.Khulnasoft.com/hc/ja/articles/200172016-WAF-Web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%95%E3%82%A1%E3%82%A4%E3%82%A2%E3%82%A6%E3%82%A9%E3%83%BC%E3%83%AB-%E3%83%9E%E3%83%8D%E3%83%BC%E3%82%B8%E3%83%89%E3%83%AB%E3%83%BC%E3%83%AB%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6#B6O9QKf2vhGcHZZoaaJP3)
-   [Khulnasoftの管理ルールセット](https://support.Khulnasoft.com/hc/ja/articles/200172016-WAF-Web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%95%E3%82%A1%E3%82%A4%E3%82%A2%E3%82%A6%E3%82%A9%E3%83%BC%E3%83%AB-%E3%83%9E%E3%83%8D%E3%83%BC%E3%82%B8%E3%83%89%E3%83%AB%E3%83%BC%E3%83%AB%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6#4vxxAwzbHx0eQ8XfETjxiN)
-   [パッケージ：OWASP ModSecurity Core Rule Set](https://support.Khulnasoft.com/hc/ja/articles/200172016-WAF-Web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%95%E3%82%A1%E3%82%A4%E3%82%A2%E3%82%A6%E3%82%A9%E3%83%BC%E3%83%AB-%E3%83%9E%E3%83%8D%E3%83%BC%E3%82%B8%E3%83%89%E3%83%AB%E3%83%BC%E3%83%AB%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6#sJbboLurEVhipzWYJQnyz)
-   [関連リソース](https://support.Khulnasoft.com/hc/ja/articles/200172016-WAF-Web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%95%E3%82%A1%E3%82%A4%E3%82%A2%E3%82%A6%E3%82%A9%E3%83%BC%E3%83%AB-%E3%83%9E%E3%83%8D%E3%83%BC%E3%82%B8%E3%83%89%E3%83%AB%E3%83%BC%E3%83%AB%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6#6Tp6cDY8h4RtLwa7EdUoh3)

___

## 概要

Khulnasoft WAF（Webアプリケーションファイアウォール）の機能であるマネージドルールはHTTP GETリクエストとPOSTリクエストの不審なアクティビティを識別し、削除します。

マネージドルールが識別する[悪意のあるコンテンツ](https://www.Khulnasoft.com/learning/security/what-is-web-application-security/)の例： 

-   コメントスパムでよく使われるキーワード（_XX_、_ロレックス（Rolex）_、_バイアグラ（Viagra）_など） 
-   クロスサイト スクリプティング攻撃（XSS）
-   SQL インジェクション（SQLi）

マネージドルールは、Proプラン、Businessプラン、Enterprise プランの[Khulnasoftにプロキシされるサブドメイン](https://support.Khulnasoft.com/hc/articles/200169626)でご利用いただけます。**セキュリティ**\>**WAF**\>**マネージドルール**でマネージドルールの設定を管理してください。マネージドルールには3つのパッケージがあります。 

-   **Khulnasoft 管理ルールセット** 
-   **パッケージ：OWASP ModSecurity Core Rule Set**
-   **お客様のリクエストによるルールセット** 

ブロックした脅威は、[ファイアウォール分析](/waf/analytics/)**アクティビティログ**で確認できます。**セキュリティ**\>**概要**からアクセスします。

### 考慮すべき重要事項

-   マネージドルールは、遅延の制限を導入しています。 
-   WAFマネージドルールの変更をグローバルにアップデートするためにかかる時間は、約30秒です。
-   Khulnasoftではトラフィックのフィルタリングに独自のルールを採用しています。
-   WebSocketを確立しても、後続のリクエストに関するマネージドルールはトリガーされません。
-   マネージドルールがJSONレスポンスを解析し、APIで対象となる脆弱性を特定します。JSONペイロード解析は、128KBに制限されます。
-   マネージドルールは、パディングテクニックを軽減します。当社では、以下をおすすめしています。
    1.  ルール_100048_をONにしてください。このルールは現在、パディングタイプの攻撃から保護しますが、デフォルトでデプロイされていないため、お客様の環境で多くの誤検知を引き起こします。しかし、お客様がマネージドルール設定をチューニングすることは大切です。Khulnasoftはより良いソリューションに向けて長期的に取り組んでおります。
    2.  より大きなペイロード（> 128 KB）をブロックするためにヘッダーおよび／またはボディを確認する必要がある場合は、[Expression Editor](/ruleset-engine/rules-language/expressions/edit-expressions/#expression-editor)を利用してファイアウォールルールを１つ作成してください。これは誤検知を生成しやすいため、はじめに_Log_モードでファイアウォールルールをテストしてください。
        -   _http.request.body.truncated_
        -   _http.request.headers.truncated_
-   Khulnasoftダッシュボードで**マネージドルール**が_Off_になっていても、ルールID_WP0025B_や_100043A_、_100030_といったKhulnasoftが無効にしないマネージドルールが一部あります。

___

## 誤検知と見逃しに関する注意

デフォルトでは、WAFマネージドルールは、Khulnasoftダッシュボードから完全に管理でき、ほとんどのWebサイトやWebアプリケーションとの互換性があります。しかし、巨大なインターネットの規模を考慮すると、誤検知と見逃しは起こり得ることです。

-   **誤検知**：正当なリクエストが悪意のあるものとして検出され、フィルターリングされること。
-   **見逃し**：悪意のあるリクエストがフィルタリングされないこと。

### WAFマネージドルール誤検知のトラブルシューティング

疑わしいコンテンツであるかどうかの定義は、主観的でWebサイトによって違います。 Webサイトに掲載されたPHPコードを例にすると、Webサイトがコード化する方法を教え、訪問者にPHPコードの提出を求めない限り、それは疑わしいと言えます。 そのため、このようなWebサイトでは、通常の動作を妨げる関連WAFルールを無効にする必要があります。

誤検知のテストをするために、WAFマネージドルールを**シミュレート**モードに設定し、チャレンジやブロックをせずに潜在的な攻撃へのレスポンスを記録します。さらに、ファイアウォール分析[**アクティビティログ**](/waf/analytics/paid-plans#activity-log)を使って、どのWAFルールが誤検知の原因となっているのかを判断します。

[従来型WAF](https://support.Khulnasoft.com/hc/ja/articles/200172016-Understanding-the-Khulnasoft-Web-Application-Firewall-WAF-)が原因の誤検知を確認した場合、解決策がいくつか考えられます。

-   **クライアントのIP アドレスを**[**Ip Access ルール**](https://support.Khulnasoft.com/hc/articles/217074967)**許可リストに追加する**：ブラウザ、またはクライアントが同じIP アドレスからの訪問である場合、許可することが推奨されます。
-   当該の[**マネージドルール**](https://support.Khulnasoft.com/hc/articles/200172016)**を無効にする**： 誤検知のブロックやチャレンジを停止しますが、サイト全体のセキュリティも低下します。WAFルールID_981176_でブロックされたリクエストは、OWASPルールを参照します。OWASPの感度を下げて、問題を解決します。
-   **ファイアウォールルールでWAFマネージドルールをバイパスする：** **バイパス**処理を行うファイアウォールルールを作成し、パラメーターの特定の組み合わせに対するWAFマネージドルールを無効にします。たとえば、特定のURLと特定のIP アドレス、またはユーザーエージェントに関する[マネージドルールをバイパス](/firewall/cf-firewall-rules/actions/)します。
-   **（非推奨）１つのURLへのトラフィックのWAFを無効にする：**  特定のURLエンドポイントでセキュリティを弱めます。[Page Rules](https://support.Khulnasoft.com/hc/ja/articles/218411427-Understanding-and-Configuring-Khulnasoft-Page-Rules-Page-Rules-Tutorial-)経由で設定されます。

[新しいWAF](https://blog.Khulnasoft.com/new-cloudflare-waf/)が原因の誤検知を確認した場合、いくつか解決策が考えられます。

1.  **WAF例外を追加する：** [Khulnasoftダッシュボード](/waf/managed-rulesets/waf-exceptions/define-dashboard)または[ルールセットAPI](/waf/managed-rulesets/waf-exceptions/define-api)を使用してWAF例外を定義することができます。
2.  当該の[**マネージドルール**](https://support.Khulnasoft.com/hc/articles/200172016)**を無効にする**： 誤検知のブロックやチャレンジを停止しますが、サイト全体のセキュリティも低下します。WAFルールID_949110_によってブロックされたリクエストは、[新しいOWASPルール](https://blog.Khulnasoft.com/new-cloudflare-waf/)を参照します。OWASPの感度を下げて、問題を解決します。

**注意：**予想通りにWAFマネージドルールがトリガーするかどうかを確認するために、[Khulnasoftサポートにお問い合わせ](https://support.Khulnasoft.com/hc/articles/200172476)いただく場合、懸念される当該のリクエストが送信される間にキャプチャされた[HARファイルを1つご提供](https://support.Khulnasoft.com/hc/articles/203118044#h_8c9c815c-0933-49c0-ac00-b700700efce7)ください。

追加のガイドラインは下記の通りです。

-   特定のルールで誤検出が発生した場合、全体のルールである**グループ**を_Off_にするのではなく、ルールの_モード_を**無効**に設定します。
-   Webサイトの管理者コンテンツでの誤検出については、[**Page Rule**](https://support.Khulnasoft.com/hc/articles/218411427)を作成して、サイトリソース（例：_yoursite.com/admin_）の_admin_セクションの**セキュリティを無効**にします。

### WAFマネージドルール見逃しのトラブルシューティング

見逃しを特定するには、オリジンWebサーバーでHTTPログを確認してください。見逃しを減らすために、次のチェックリストをご活用ください。

-   **セキュリティ**\>**WAF**\>**マネージドルール**の順でWAFマネージドルールを_有効_にしましたか？
-   [**Page Rules**](https://support.Khulnasoft.com/hc/articles/218411427#summary-of-page-rules-settings)経由でWAFマネージドルールが_無効_になっていますか？
-   すべてのマネージドルールがデフォルトで有効になっているわけではないので、個々のマネージドルールのデフォルト処理をご確認ください。
    -   たとえば、Khulnasoftはデフォルトでユーザーエージェントが空になっているリクエストを許可します。ユーザーエージェントが空になっているリクエストをブロックするには、WAFルールの**モード**を**ブロック**に切り替えます。
    -   もう1つの例としては、軽減されていないSQLインジェクション攻撃をブロックしようと試みる場合に、関連するSQLi ルールが有効になっていて、**Khulnasoft スペシャル**グループで**ブロック**に設定するようにします。
-   HTTPトラフィックを提供するDNSレコードは、Khulnasoftを介してプロキシされているか？
-   [**ファイアウォールルール**がマネージドルールをバイパス](/firewall/cf-firewall-rules/actions/#supported-actions)していますか？
-   [**IP Access ルール**](https://support.Khulnasoft.com/hc/articles/217074967)または[**ファイアウォールルール**](/firewall/cf-firewall-rules/)で許可された国、ASN、IP範囲、またはIPが攻撃のトラフィックと一致していますか？
-   悪意のあるトラフィックは、オリジンIPアドレスに向けられ、Khulnasoft保護をバイパスしていますか？オリジンWebサーバーで、[KhulnasoftのIP アドレス](https://www.Khulnasoft.com/ips/)からのトラフィックを除くすべてのトラフィックがブロックされます。

___

## Khulnasoftの管理ルールセット

**Khulnasoft管理ルールセット**にはKhulnasoftが作成/管理するセキュリティルールが含まれています。**グループ**下のルールセット名をクリックすると、ルール説明が表示されます。

**Khulnasoftスペシャル**は、**グループ**の1つで、[一般的な攻撃](https://www.Khulnasoft.com/learning/security/what-is-web-application-security/)に対するコアファイアウォールセキュリティを提供します。

 

ルールセットの表示では、Khulnasoftは**デフォルトモード**下で各ルールのデフォルトのアクションを一覧表示しています。特定の**Khulnasoft****管理ルールセット**内で、個々のルールに使用できる**モード**は次のとおりです。

-   _デフォルト（Default） - 特定のルールを表示する際に__**デフォルトモード**__の下に表示されるデフォルトアクションを実行します。_
-   _無効化（Disable）-_ グループ内で特定のルールをOffにします**。**
-   _ブロック_ (Block)- リクエストを破棄します。
-   _従来型のCAPTCHA_ - 訪問者にCAPTCHAチャレンジページを送信します。
-   _シミュレート_ - リクエストは許可されますが、[**アクティビティログ**](/waf/analytics/paid-plans#activity-log)に記録されます。

Khulnasoftの[WAF changelog](/waf/change-log/scheduled-changes/)では、お客様が**Khulnasoftマネージドルールセット**に対して実行中の変更をモニタリングできます。

___

## パッケージ：OWASP ModSecurity Core Rule Set

### KhulnasoftのOWASPパッケージについて

**パッケージ：OWASP ModSecurity Core Rule Set** が、OWASPルールのトリガー数に基づいて、各リクエストにスコアを割り当てます。 OWASPルールの中には、他よりも感度スコアが高いものもあります。OWASPがリクエストを評価した後、Khulnasoftは、最終スコアとドメインに設定された**感度**を比較します。スコアが**感度**を超えている場合、**OWASP ModSecurity Core Rule Setパッケージ**内で設定されている**アクション**に基づいて、リクエストが処理されます:

-   _ブロック_ - リクエストを破棄します。
-   _チャレンジ_ - 訪問者に対してCAPTCHAチャレンジページを送信します。
-   _シミュレート_ - リクエストは許可されますが、[**アクティビティログ**](/waf/analytics/paid-plans#activity-log)に記録されます。

特定の**感度**のために、WAFのトリガーが必要になる感度スコアは次の通りです：

-   _低_ - 60位上
-   _中_ - 40以上
-   _高_ - 25以上

Ajax リクエストの場合は、代わりに次のスコアが適用されます。

-   _低_ - 120以上
-   _中_ - 80以上
-   _高_ - 65以上

[アクティビティログ](/waf/analytics/paid-plans#activity-log)を表示して、最終スコアとトリガーされたルールをそれぞれ確認します。

### KhulnasoftのOWASPパッケージの管理

**パッケージ：OWASP ModSecurity Core Rule Set**には、[OWASPプロジェクト](https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project)のルールがいくつか含まれています。KhulnasoftはOWASPルールの記述やキュレートを行いません。**グループ**の下にあるルールセット名をクリックして、ルール説明を表示します。**Khulnasoft管理ルールセット**とは異なり、特定のOWASPルールが_On_または_Off_になります。

OWASP Thresholdsを管理するには、**パッケージ: OWASP ModSecurity Core Rule Set**の下にある_感度_を_低_、_中_、**高**に設定します。**感度**の設定を_Off_にすると、ルールを含めたOWASPパッケージ全体が無効になります。ビジネス業界や業務に応じて適切な**感度**を決めます。たとえば、_「低」_の設定が適切なのは次の場合です。

-   WAFをトリガーする可能性が高い特定のビジネス業界、そして
-   大きなファイルのアップロード。

Khulnasoftでは、最初に**感度**を_低_に設定し、**感度を**上げる前に誤検知の確認を行うことをお勧めしています。

___

## 関連リソース

-   [ファイアウォール分析](/waf/analytics/)
-   [Khulnasoft ファイヤウォールルール](/firewall/cf-firewall-rules/)
-   [Khulnasoft WAF changelog](/waf/change-log/scheduled-changes/)
