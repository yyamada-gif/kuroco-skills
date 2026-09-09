# Kurocoドキュメント: FAQ / assessment

収録ページ一覧。目的のページは Grep でタイトルまたは slug を検索し、該当行から Read してください。

## 収録ページ

- 管理画面の操作ログは確認できますか？（`can-i-access-the-operational-logs-of-the-admin-panel`）
- セキュリティチェックシートへの記入をお願いできますか？（`can-you-audit-my-security-checklist`）
- 脆弱性検査のエビデンスを提供してもらうことはできますか？（`can-you-send-me-your-vulnerability-assessment-findings`）
- 脆弱性診断でCSRFの脆弱性が検出されました。Kurocoではどのように対応すればいいですか？（`csrf-was-detected-in-a-vulnerability-assessment`）
- KurocoはISMAP（政府情報システムのためのセキュリティ評価制度）に対応していますか？（`is-kuroco-ismap-compliant`）
- セキュリティ対策の資料はありますか？（`materials-on-security-measures`）
- 脆弱性診断で指摘を受けたのでどうすればいいか教えてください（`my-site-was-diagnosed-with-a-security-vulnerability`）
- 脆弱性診断・検査に関して教えてください（`what-vulnerability-diagnostic-and-assessment-services-do-you-provide`）
- KurocoのStrict-Transport-Security(HSTS)ヘッダーにincludeSubDomainsが付与されないのはなぜですか？（`why-kuroco-does-not-include-includesubdomains-in-hsts`）


---

# 管理画面の操作ログは確認できますか？

> 元ページ: `faq/can-i-access-the-operational-logs-of-the-admin-panel` ｜ 公式ページ: https://kuroco.app/ja/docs/faq/can-i-access-the-operational-logs-of-the-admin-panel/
> 概要: オペレーション -> ログ管理 -> 管理画面ログで、ログの確認が可能です。

[オペレーション] -> [ログ管理] -> [管理画面ログ]で、ログの確認が可能です。
![Image from Gyazo](https://t.gyazo.com/teams/diverta/45dcf0aafb45f115ae41d952a290a940.png)
## 画面の見方について
![Image from Gyazo](https://t.gyazo.com/teams/diverta/ddc79c7ba3d4273e38d8b0c847e79b10.png)
- 日付毎に確認できます。
- テーブルを横にスクロールするとログインユーザーの情報なども確認できます。
- 更新時に表示されるメッセージも記録されます。
- セキュリティの観点もあり、ログには、更新内容の詳細は記録しておりません。
- message3(HTTPメソッド)がPOSTとなっているところで、操作としては更新がされていることが多いです。
- 「詳細検索」で絞り込み条件を作成して検索できます。

![Image (fetched from Gyazo)](https://t.gyazo.com/teams/diverta/bd5f00c6347968fab0a3b3229ab1d765.png)
詳細な画面の見方は[管理画面マニュアル 管理画面ログ](/ja/docs/management/admin-log-list/)をご確認ください。

## 関連ドキュメント
- [管理画面ログ](/ja/docs/management/admin-log-list/)
- [ログ管理](/ja/docs/management/log-management/)
- [ログインログ](/ja/docs/management/login-log-list/)


---

# セキュリティチェックシートへの記入をお願いできますか？

> 元ページ: `faq/can-you-audit-my-security-checklist` ｜ 公式ページ: https://kuroco.app/ja/docs/faq/can-you-audit-my-security-checklist/
> 概要: IPAの「[安全なウェブサイトの作り方]のセキュリティ実装チェックリストであれば用意がございますので、そちらの提供は可能です。

IPAの「[安全なウェブサイトの作り方](https://www.ipa.go.jp/security/vuln/websecurity.html)」のセキュリティ実装チェックリストであれば用意がございますので、そちらの提供は可能です。  
また、以下のページもご確認ください。  
- [セキュリティ](/ja/docs/about/security/)
- [インフラに関するドキュメント](https://kuroco.app/files/sheets/ja/kuroco_infrastructure.pdf)
- [ディバータ](https://www.diverta.co.jp/) 弊社はISO27001(ISMS)とPマークを取得しております。

別途、オリジナルのチェックシートに記入依頼をされる場合には、基本的には1回毎に55,000円(税込)～の費用がかかります。記載ボリュームを確認させていただきますので[サポート](/ja/docs/about/support/)へご連絡ください。  
なお、前年度と同じ内容のものを確認するだけ場合には費用がかからない場合もあります。
 
## ご依頼にあたってのお願い
セキュリティチェックに関するシートは、各社様で統一したフォーマット、表現、指標が実質的に存在しておりません。そのため、都度、専門のエンジニアのチェックが必要ですので、ご面倒をおかけいたしますが下記についてご協力くださいますようお願いいたします。

- 弊社で入力するべき箇所を明確にご指示ください。  
利用されるシチュエーションやカテゴリが合致しないシート(例：クラウド利用を想定されていないシートなど)を弊社へそのままお送りいただいた場合、弊社では記入するべき箇所が分からずに進めることが出来ない場合もあります。  
必ずお送りいただくシートの内容をご確認の上、ご連絡ください。

- シートは、記入式よりも選択式の方がコストを抑えることが出来ますので、事前にそのようなシートをご用意いただくことをお勧めいたします。

## 注意事項    
- ボリュームによっては急ぎの対応などをお受けできない場合もありますので、スケジュールに余裕をもってご連絡をお願いいたします。  
- 保安上の理由等で回答できない場合もありますので、その点はご了承ください。

## 関連ドキュメント
- [セキュリティ](/ja/docs/about/security/)
- [セキュリティ対策の資料はありますか？](/ja/docs/faq/materials-on-security-measures/)
- [脆弱性診断・検査に関して教えてください](/ja/docs/faq/what-vulnerability-diagnostic-and-assessment-services-do-you-provide/)
- [脆弱性検査のエビデンスを提供してもらうことはできますか？](/ja/docs/faq/can-you-send-me-your-vulnerability-assessment-findings/)
- [サポート](/ja/docs/about/support/)


---

# 脆弱性検査のエビデンスを提供してもらうことはできますか？

> 元ページ: `faq/can-you-send-me-your-vulnerability-assessment-findings` ｜ 公式ページ: https://kuroco.app/ja/docs/faq/can-you-send-me-your-vulnerability-assessment-findings/
> 概要: 申しわけありませんが、脆弱性検査のエビデンス提供はできません。脆弱性に関する調査のエビデンスが必要な場合は、ご自身で調査を手配をしていただくことになります。

申しわけありませんが、脆弱性検査のエビデンス提供はできません。  
脆弱性に関する調査のエビデンスが必要な場合は、ご自身で調査を手配をしていただくことになります。
[VADDY](https://vaddy.net/ja/)はAPIに関する診断もできるサービスになっております。管理画面よりお申し込みいただくと自動連携機能が利用可能です。
調査会社のご紹介も可能ですので、必要な場合は[お問い合わせ](https://kuroco.zendesk.com/)ください。
 
## お客様に確認頂きたい点
フロントエンドでのJavascriptの問題や、管理画面設定の不備により、お客様自身で脆弱性を作ってしまう可能性があります。まずは下記項目を確認してください。
- APIで必要以上の情報を出力していないか  
- 外部ドメインのJavaScriptライブラリなどを利用している場合に、それが信用してよいドメインか
- 利用しているJavaScriptライブラリなどが信用できるものか
- APIのセキュリティ設定は適切か
- メンバー登録時に付与されている権限が適切か 
 
その他にも確認するべき箇所はある場合がありますので、ご自身で気になる点はチェックをされるか、サイト制作委託先にご確認をされるようにお願いいたします。

## Kurocoに起因する脆弱性があった場合
[サポート事務局](https://kuroco.zendesk.com/)へ診断結果をご連絡ください。速やかに改修いたします。
なお、下記の場合弊社で対応しない可能性がございますので、あらかじめご了承ください。
- 脆弱性が重大でない場合
- 弊社で対応する必要がないと判断した場合

## 関連するページ
- [セキュリティ](/ja/docs/about/security/)
- [脆弱性診断で指摘を受けたのでどうすればいいか教えてください](/ja/docs/faq/my-site-was-diagnosed-with-a-security-vulnerability/)

## 関連ドキュメント
- [脆弱性診断・検査に関して教えてください](/ja/docs/faq/what-vulnerability-diagnostic-and-assessment-services-do-you-provide/)
- [脆弱性診断で指摘を受けたのでどうすればいいか教えてください](/ja/docs/faq/my-site-was-diagnosed-with-a-security-vulnerability/)
- [VAddy](/ja/docs/management/vaddy/)
- [VAddyと連携してAPIエンドポイントに対する自動診断を設定する。](/ja/docs/tutorials/integrating-with-vaddy/)
- [セキュリティ](/ja/docs/about/security/)


---

# 脆弱性診断でCSRFの脆弱性が検出されました。Kurocoではどのように対応すればいいですか？

> 元ページ: `faq/csrf-was-detected-in-a-vulnerability-assessment` ｜ 公式ページ: https://kuroco.app/ja/docs/faq/csrf-was-detected-in-a-vulnerability-assessment/
> 概要: 回答はAPIのセキュリティ設定によって異なります。トークン認証ではCSRFは成立しません。Cookie認証でも、エンドポイントが受け付けないContent-Typeは処理される前に400で拒否されるため、`application/json`のみを受け付けるエンドポイントでは基本的に成立しません。form形式を受け付けるエンドポイントや、CORS設定でワイルドカードを指定している場合は設定の確認が必要です。

CSRF(Cross-Site Request Forgery)は、利用者のブラウザが認証情報を自動的に付与してしまうことを利用した攻撃です。
そのため、回答はAPIに設定しているセキュリティの種類によって異なります。

| セキュリティ | 認証情報の送信方法 | CSRFの成立可否 |
| :--- | :--- | :--- |
| 静的アクセストークン | リクエストヘッダーに明示的に指定 | 成立しません |
| 動的アクセストークン | リクエストヘッダーに明示的に指定 | 成立しません |
| 特権付き静的トークン | リクエストヘッダーに明示的に指定 | 成立しません |
| Cookie | ブラウザが自動的に付与 | 基本的に成立しません（[一部のエンドポイントは設定が必要](#cookie認証の場合)です） |
| なし | 認証情報がありません | 成立しません（別の観点での確認が必要です） |

セキュリティの種類については[APIセキュリティ](/ja/docs/management/api-security/)をご覧ください。

![Image from Gyazo](https://t.gyazo.com/teams/diverta/a4768b87dce7ff52860ef970f29112ac.png)

:::note
診断結果への回答を作成する前に、まず[CSRF対策が成立しない設定](#csrf対策が成立しない設定)をご確認ください。
本記事で説明する対策はいずれもこれらの設定に依存しており、該当する場合は対策が働きません。
:::

## トークン認証（静的・動的・特権付き静的）の場合

これらのセキュリティでは、アクセストークンをリクエストヘッダー`X-RCMS-API-ACCESS-TOKEN`に明示的に指定します。
ブラウザが自動的に付与する情報ではないため、攻撃者のサイトから送信されたリクエストにトークンが含まれることはありません。

したがって、**CSRFは構造的に成立しません。** 追加の設定は不要です。

:::note
静的アクセストークンをフロントエンドに埋め込んでいる場合、トークンは第三者も取得できる値です。他者になりすますCSRFは成立しませんが、トークンを取得した第三者がAPIを実行できる状態である点は、別の観点として確認してください。
:::

## Cookie認証の場合

Cookie認証では、ブラウザがCookieを自動的に付与します。
Kurocoが発行するCookieの属性は以下のとおりです。

| 属性 | 値 |
| :--- | :--- |
| SameSite | API:`None` / 管理画面:`Strict` |
| Partitioned | [CookieでPartitionedを利用する](/ja/docs/management/management-screen/#管理画面の項目説明)が有効な場合に付与されます（デフォルトで有効） |
| HttpOnly | 付与されます |
| Secure | 付与されます |

Partitioned属性の設定は、[環境設定] -> [管理画面]の[CookieでPartitionedを利用する]で確認できます。

APIのCookieは`SameSite=None`のため、**クロスサイトからのリクエストであってもCookieは送信されます。**

ただし、KurocoのAPIエンドポイントは、そのエンドポイントが受け付けるContent-Typeをあらかじめ定義しており、それ以外のContent-Typeのリクエストは400で拒否します。
HTMLフォームから送信できるContent-Typeは`application/x-www-form-urlencoded`・`multipart/form-data`・`text/plain`に限られるため、`application/json`のみを受け付けるエンドポイントでは、**攻撃者のサイトのフォームから送信されたリクエストは処理される前に拒否されます。**

`text/plain`は、エンドポイントが受け付けるContent-Typeの設定が存在しないため、常に拒否されます。
Content-Typeヘッダーを付与しないリクエストも、拒否されます。

:::note
ログアウトのエンドポイントのみ、Content-Typeヘッダーを付与しないリクエストを受け付けます。
ログアウトはセッションを破棄する操作であり、他者になりすまして更新や情報の取得を行うものではないため、CSRFとしての影響は限定的です。
:::

これらの拒否は、[CSRF対策が成立しない設定](#csrf対策が成立しない設定)に該当する場合には働きません。

:::info
CookieのSameSite属性が`Strict`ではない点は、脆弱性診断で指摘を受けることがあります。この指摘に対する見解は[脆弱性診断で指摘を受けたのでどうすればいいか教えてください](/ja/docs/faq/my-site-was-diagnosed-with-a-security-vulnerability/)をご覧ください。
:::

### デフォルトの動作

Cookie認証のAPIへのPOSTリクエストのうち、後述の条件を満たさないリクエストは、**デフォルトでは拒否されず、検知ログに記録されるのみです。**

これは、CSRF保護を有効にする前に、影響を受けるリクエストをログから洗い出せるようにするためです。
検知したリクエストは[アプリケーションログ](/ja/docs/management/application-log-list/)に記録されます。[キーワード]に`CsrfGuard`を入力して絞り込んでください。
検知ログは、[Cookie認証APIのCSRF保護を強制する]を有効にした場合と同じ条件で記録されます。後述の`Origin`ヘッダーの条件も判定に含まれるため、有効化する前に`Origin`ヘッダーを送信しないクライアントが存在しないかをログから確認できます。<VersionLabel version="BETA" />

リクエストを実際に拒否するには、次の設定を有効にします。

### Cookie認証のCSRF保護を有効にする

[環境設定] -> [サイト管理]をクリックし、[共通]の[Cookie認証APIのCSRF保護を強制する]にチェックを入れて保存します。
この設定はサイト単位です。API単位では設定できないため、有効にするとサイト内のすべてのCookie認証APIに適用されます。

設定画面の詳細は[サイト管理](/ja/docs/management/site-settings/)をご覧ください。

有効にすると、Cookie認証のAPIへのPOSTリクエストは以下の**両方**を満たす必要があり、満たさないリクエストは403で拒否されます。<VersionLabel version="BETA" />

| 条件 | 説明 |
| :--- | :--- |
| `Origin`ヘッダーが許可されたオリジンであること <VersionLabel version="BETA" /> | `Origin`ヘッダーが存在し、その値が「リクエストが到達したホストのhttpsオリジン」または「APIの`CORS_ALLOW_ORIGINS`に一致するオリジン」「管理画面URL」のいずれかに一致するリクエストです。 |
| `Content-Type: application/json`または`X-Requested-With: XMLHttpRequest`を持つこと | HTMLフォームからは送信できないContent-Type、または付与できないリクエストヘッダーです。 |

`Origin`はブラウザが設定するリクエストヘッダーで、ページ内のJavaScriptから偽装できません。
そのため、自サイトのページからの送信と、攻撃者のサイトからの送信を区別できます。
ブラウザはPOSTリクエストに必ず`Origin`ヘッダーを付与するため、`Origin`ヘッダーのないリクエストはブラウザから送信されたものではないと判断し、拒否します。<VersionLabel version="BETA" />

`Origin`による判定は`CORS_ALLOW_ORIGINS`の指定内容に依存します。ワイルドカード(`*`)を指定している場合は、すべてのオリジンからの送信が許可されるため、CSRF保護として機能しません。サブドメインのワイルドカード(`https://*.example.com`)は、対象となるサブドメインすべてが管理下にある場合に限り有効です。<VersionLabel version="BETA" />

:::caution
次のリクエストも403で拒否されます。有効化する前に、[アプリケーションログ](/ja/docs/management/application-log-list/)の`CsrfGuard`の検知ログで、該当するリクエストがないことを確認してください。<VersionLabel version="BETA" />

- 自サイトのページからの素の`<form>`送信（`Content-Type: application/json`でも`X-Requested-With: XMLHttpRequest`ヘッダー付きでもないため）
- `Origin`ヘッダーを送信しないクライアントからのリクエスト（ネイティブアプリやサーバー間通信など）

ブラウザ以外からAPIを呼び出す構成では、Cookie認証ではなくトークン認証を使用してください。
:::

Admin API（`/direct/rcms_api/admin_api/`）へのPOSTリクエストにも、[Cookie認証APIのCSRF保護を強制する]の設定に従って同じ条件が適用されます。許可されるオリジンは管理画面URLのみです。<VersionLabel version="BETA" />
ブラウザ以外から管理画面のログインセッションでAdmin APIを呼び出すAIエージェントなどのクライアントは、`Origin`ヘッダーに管理画面URLを、あわせて`Content-Type: application/json`を自身で付与する必要があります。管理MCPサーバーはトークン認証のみのため対象外です。<VersionLabel version="BETA" />

判定の対象は、Cookie認証のAPIへのPOSTリクエストのみです。GETは対象外です。
また、bulkや非同期実行、Smartyの`api_internal`などKurocoが内部で発行するリクエストも対象外です。

Kuroco標準のGETオペレーションに、データを更新するものはありません。
ただし、`Api::request_api`（カスタム処理で作成したAPIの実行 (GETメソッド)）のように処理内容を利用者が定義するエンドポイントでは、その処理次第で更新が発生します。GETはCSRF保護の判定対象外で、Content-Typeによる拒否も働きません。
更新を伴う処理は、`Api::request_api_post`（カスタム処理で作成したAPIの実行 (POSTメソッド)）などPOSTのエンドポイントに設定してください。`Api::proxy`・`Api::aggregate`でプロキシ先に副作用がある場合も同様です。

### 正しいCORS設定が前提になる

CORSは単体ではCSRF対策になりませんが、**本記事で説明する対策はいずれもCORS設定が正しいことを前提としています。**

CORSはレスポンスの読み取りをブラウザ側で防ぐ仕組みであり、**リクエストがサーバーに到達すること自体は防ぎません。**
プリフライトリクエストが発生しないリクエスト（HTMLフォームからの送信など）は、CORSで許可されていないオリジンからでもサーバーに到達します。

一方で、**CORSで許可されたオリジンからは、プリフライトリクエストが発生するリクエストも到達します。**
`Content-Type: application/json`によるCSRFの拒否は、攻撃者のオリジンがCORSで許可されていないために、そのプリフライトリクエストが失敗することで成立しています。

:::danger
`CORS_ALLOW_ORIGINS`にワイルドカード(`*`)を指定すると、Kurocoはリクエスト元のOriginをそのまま`Access-Control-Allow-Origin`に返します。
`CORS_ALLOW_CREDENTIALS`とあわせて有効にしている場合、**すべてのオリジンが`Content-Type: application/json`のリクエストの送信とレスポンスの読み取りを許可されます。** オリジンによる境界がなくなるため、**Content-Typeによる拒否も[Cookie認証APIのCSRF保護を強制する]も機能しません。**
`CORS_ALLOW_ORIGINS`には、許可するオリジンを明示的に指定してください。
:::

リクエストにCookieが付与されるかは[Partitioned属性](#partitioned属性による違い)にも依存します。組み合わせごとの結果は[CSRFの成立条件の一覧](#csrfの成立条件の一覧)をご覧ください。

`CORS_ALLOW_ORIGINS`を明示的に指定している場合、CORS設定は次の3つの役割を持ちます。

| 役割 | 内容 |
| :--- | :--- |
| レスポンスの保護 | 許可していないオリジンのページからは、レスポンスの内容を読み取れません。 |
| プリフライトの拒否 | 許可していないオリジンからの、プリフライトリクエストが発生するリクエストを失敗させます。 |
| CSRF保護の判定 | [Cookie認証APIのCSRF保護を強制する]が有効な場合の判定に利用されます。 |

### Partitioned属性による違い

CookieのPartitioned属性は、Cookieをトップレベルサイトごとに分割します。
[CookieでPartitionedを利用する](/ja/docs/management/management-screen/#管理画面の項目説明)が有効な場合、**攻撃者のサイトのページからJavaScriptで送信したリクエストには、Cookieが付与されません。**

一方、攻撃者のサイトのフォームから画面遷移を伴って送信されたリクエストには、遷移先のトップレベルサイトが一致するためCookieが付与されます。
つまりPartitioned属性が有効な場合、攻撃者が送信できるのはHTMLフォームから送信できるContent-Typeに限られます。

### CSRFの成立条件の一覧

`application/json`のみを受け付けるエンドポイントについて、ここまでの条件をまとめます。

| Partitioned属性 | `CORS_ALLOW_ORIGINS` | CSRFの成立可否 |
| :--- | :--- | :--- |
| 有効 | 明示的に指定 | 成立しません |
| 有効 | ワイルドカード(`*`) | 成立しません（Cookieが付与されません） |
| 無効 | 明示的に指定 | 成立しません（400で拒否） |
| 無効 | ワイルドカード(`*`) | **成立します** |

ワイルドカード(`*`)を指定している場合、攻撃者のサイトから送信した`Content-Type: application/json`のリクエストは[Cookie認証APIのCSRF保護を強制する]の通過条件も満たすため、**設定を有効にしても拒否されません。**
Partitioned属性が有効な場合はCookieが付与されないため成立しませんが、CSRF対策がブラウザのCookie分割のみに依存する状態になります。ワイルドカード(`*`)は指定しないでください。
このほか成立条件に影響する設定は[CSRF対策が成立しない設定](#csrf対策が成立しない設定)にまとめています。

### form形式でリクエストを送信するエンドポイントについて

エンドポイントが受け付けるContent-Typeは、[API]の設定で指定します。
`multipart/form-data`や`application/x-www-form-urlencoded`を明示的に指定したエンドポイントでは、HTMLフォームから送信できるContent-Typeを受け付けるため、Content-Typeによる拒否が働きません。

Cookie認証で公開している場合は[Cookie認証APIのCSRF保護を強制する]を有効にしてください。
あわせて、正規のリクエストも`Content-Type: application/json`の条件を満たさないため、フロントエンドの実装で`X-Requested-With: XMLHttpRequest`ヘッダーを付与してください。

`X-Requested-With`はHTMLフォームから付与できないリクエストヘッダーであるため、別オリジンのページから送信する場合はプリフライトリクエストが発生します。
ヘッダーを付与する前に、送信元のオリジンを`CORS_ALLOW_ORIGINS`に登録してください。登録していないと、正規のリクエストが失敗します。

:::note
同一オリジンのページから送信する場合でも`X-Requested-With: XMLHttpRequest`ヘッダーが必要です。素の`<form>`からの送信は拒否されます。詳細は[Cookie認証のCSRF保護を有効にする](#cookie認証のcsrf保護を有効にする)をご覧ください。<VersionLabel version="BETA" />
:::

## セキュリティ「なし」の場合

認証情報を用いないため、他者になりすますCSRFは成立しません。
ただし、更新系のエンドポイントを認証なしで公開している場合は、CSRF以前に誰でも実行できる状態です。
[APIセキュリティ](/ja/docs/management/api-security/)で適切なセキュリティを設定してください。

## CORS設定の確認方法

サイドバーより設定を確認したい[API]をクリックし、[CORS]をクリックします。
`CORS_ALLOW_ORIGINS`に、許可するオリジンを明示的に指定します。ワイルドカード(`*`)は指定しないでください。

![Image from Gyazo](https://t.gyazo.com/teams/diverta/cfaac5034eaf6833b1f5766a05a2fae7.png)

```text
https://example.com
```

ワイルドカード(`*`)は開発時の動作確認にのみ使用し、`http://localhost:8080`のような開発用のオリジンも、本番環境の設定からは削除してください。

設定項目の詳細は[API](/ja/docs/management/api-list/#cors)をご覧ください。

## CSRF対策が成立しない設定

ここまでに説明した対策は、いずれも以下の設定に依存しています。
Cookie認証のログインセッションは、`api_id`が異なる場合でもサイト内のCookie認証API間で共有されます。一方、CORS設定・セキュリティ・受け付けるContent-TypeはAPIごとの設定です。
そのため、診断対象のAPIだけでなく、**サイト内のすべてのCookie認証APIについて**次の項目を確認してください。CORS設定は[CORS設定の確認方法](#cors設定の確認方法)で確認できます。

| 設定 | 影響 | 対処 |
| :--- | :--- | :--- |
| `CORS_ALLOW_ORIGINS`にワイルドカード(`*`)を指定している | 攻撃者のサイトから`Content-Type: application/json`のリクエストを送信できます。Content-Typeによる拒否も[Cookie認証APIのCSRF保護を強制する]も機能せず、レスポンスの内容も読み取られます。 | 許可するオリジンを明示的に指定します。 |
| `CORS_ALLOW_ORIGINS`に開発用のオリジン(`http://localhost:8080`など)が残っている | そのオリジンからのリクエストが許可されます。 | 本番環境の設定から削除します。 |
| `CORS_ALLOW_ORIGINS`にサブドメインのワイルドカード(`https://*.example.com`)を指定しており、対象となるサブドメインすべてが管理下にあると確認できない | 管理外のサブドメインが攻撃者に利用可能な状態になると、`Origin`の条件を満たします。外部サービスに割り当てているサブドメインや、使用を終了して第三者が取得できる状態のサブドメインが該当します。<VersionLabel version="BETA" /> | 管理下にあるオリジンを完全一致で指定します。 |
| `multipart/form-data`または`application/x-www-form-urlencoded`を受け付けるエンドポイントをCookie認証で公開している（[form形式でリクエストを送信するエンドポイントについて](#form形式でリクエストを送信するエンドポイントについて)を参照） | Content-Typeによる拒否が働きません。 | [Cookie認証APIのCSRF保護を強制する](#cookie認証のcsrf保護を有効にする)を有効にします。 |
| ネイティブアプリやサーバー間通信など、`Origin`ヘッダーを送信しないクライアントからCookie認証のAPIを呼び出している | [Cookie認証APIのCSRF保護を強制する]を有効にすると、これらのリクエストが403で拒否されます。<VersionLabel version="BETA" /> | トークン認証に切り替えます。 |
| GETのエンドポイントのカスタム処理で更新を行っている | GETはCSRF保護の判定対象外で、Content-Typeによる拒否も働きません。 | 更新を伴う処理はPOSTのエンドポイントに設定します。 |
| [CookieでPartitionedを利用する]が無効になっている | 攻撃者のサイトのページからJavaScriptで送信したリクエストにも、Cookieが付与されます。 | 有効にします。 |

## 診断結果への説明例

以下の説明例は、[CSRF対策が成立しない設定](#csrf対策が成立しない設定)に該当しないことを確認したうえでご利用ください。

### トークン認証を利用している場合

> 本システムはAPIベースのヘッドレスCMSであるKurocoを採用しており、対象APIの認証にはアクセストークン方式を採用しています。
> アクセストークンはリクエストヘッダーに明示的に指定する必要があり、ブラウザが自動的に付与する情報ではありません。
> したがって、認証情報が自動送信されることを前提とするCSRFは成立しません。

### Cookie認証を利用している場合

`application/json`のみを受け付けるエンドポイントであれば、以下のように説明できます。

> 本システムはAPIベースのヘッドレスCMSであるKurocoを採用しており、対象APIのエンドポイントは`Content-Type: application/json`のリクエストのみを受け付け、それ以外のContent-Typeは処理される前に400で拒否されます。
> HTMLフォームから送信できるContent-Typeに`application/json`は含まれないため、攻撃者のサイトのフォームから送信されたリクエストは処理されません。

`multipart/form-data`や`application/x-www-form-urlencoded`を受け付けるエンドポイントについては、[Cookie認証APIのCSRF保護を強制する]を有効にしたうえで、以下のように説明できます。<VersionLabel version="BETA" />

> 本システムはAPIベースのヘッドレスCMSであるKurocoを採用しており、Cookie認証のAPIへのPOSTリクエストに対してCSRF保護を有効にしています。
> POSTリクエストは「`Origin`ヘッダーが自サイトまたはCORS設定で許可したオリジンであること」と「`Content-Type: application/json`であること、または`X-Requested-With: XMLHttpRequest`ヘッダーを持つこと」の両方を満たす必要があり、満たさないリクエストは403で拒否されます。
> `Origin`はブラウザが設定するリクエストヘッダーであり、攻撃者のページから偽装することはできません。また、HTMLフォームから送信できるContent-Typeに`application/json`は含まれず、`X-Requested-With`のような任意のリクエストヘッダーを付与することもできません。
> したがって、攻撃者のサイトからのリクエストによるCSRFは成立しません。

## 関連ドキュメント
- [API セキュリティ](/ja/docs/management/api-security/)
- [API](/ja/docs/management/api-list/)
- [サイト管理](/ja/docs/management/site-settings/)
- [脆弱性診断で指摘を受けたのでどうすればいいか教えてください](/ja/docs/faq/my-site-was-diagnosed-with-a-security-vulnerability/)
- [脆弱性検査のエビデンスを提供してもらうことはできますか？](/ja/docs/faq/can-you-send-me-your-vulnerability-assessment-findings/)
- [CORS設定の変更が反映されません。](/ja/docs/faq/i-changed-cors-but-it-is-not-reflected/)
- [APIを使ったファイルのアップロードについて](/ja/docs/reference/uploading-files-using-the-api/)
- [セキュリティ](/ja/docs/about/security/)


---

# KurocoはISMAP（政府情報システムのためのセキュリティ評価制度）に対応していますか？

> 元ページ: `faq/is-kuroco-ismap-compliant` ｜ 公式ページ: https://kuroco.app/ja/docs/faq/is-kuroco-ismap-compliant/
> 概要: パブリックSaaS版はISMAP登録済みのGCP上で動作しており、一部利用しているFastly（CDN）はISMAP未登録ですが、CDNとしての利用のためセキュリティ上の問題は基本的にありません。ISMAP登録済みサービスのみでの構成が求められる場合は、ISMAP登録済みのAWS上にKurocoを構築するプライベートSaaS版をご利用いただけます。

## 結論

ISMAPはクラウドサービス（プラットフォーム）を評価・登録する制度です。
Kurocoは提供形態に応じてISMAP登録済みのクラウド上で稼働しており、要件に応じた構成をお選びいただけます。

| 提供形態 | 稼働プラットフォーム | プラットフォームのISMAP登録状況 | 備考 |
|---|---|---|---|
| パブリックSaaS版 | GCP（Fastlyを併用） | GCPはISMAP登録済み | CDNとしてFastlyを利用（ISMAP未登録） |
| プライベートSaaS版（Managed） | AWS | AWSはISMAP登録済み | KurocoをAWS上に構築。Fastly（ISMAP未登録）利用可/不可を選択可能 ※1 |
| プライベートSaaS版（Self-Hosted/BYOC） | AWS | AWSはISMAP登録済み | KurocoをAWS上に構築。Fastly（ISMAP未登録）利用可/不可を選択可能 ※1 |

※1 Fastlyを利用しない場合、Fastlyに依存している機能（APIのキャッシュ機能、画像最適化機能等）は利用不可。他のCDNで代用可能です。

:::note SaaSとしてのISMAP登録について
- パブリックSaaS版のKurocoは、SaaSとしてISMAPに登録はされておりません。
- プライベートSaaS版のKurocoは、ISMAP登録されているプラットフォーム上にKurocoを構築するため、ISMAP対応しているといえます。
:::

提供形態ごとの費用や制約事項を含む詳細な比較は、[利用料金ページの「提供形態」](https://kuroco.app/ja/pricing/)および[オンプレミス版の提供はありますか？](/ja/docs/faq/a-on-premises-version-availability/)もあわせてご確認ください。

## パブリックSaaS版

パブリックSaaS版はISMAP登録済みクラウドである**Google Cloud Platform（GCP）**上で動作しています。
CDNとして利用している**Fastly**はISMAPに登録されていませんが、FastlyはCDN（コンテンツ配信ネットワーク）としての利用であり、データの保管場所ではないため、セキュリティ上の問題は基本的にありません。

ISMAP登録済みサービスのみでシステムを構成することが厳密に求められる場合は、次のプライベートSaaS版をご検討ください。

:::info Fastlyについての補足
FastlyはCDN（コンテンツ配信ネットワーク）であり、データの保管場所ではありません。KurocoにおけるFastlyの役割はAPIレスポンスのキャッシュや画像最適化等であり、情報資産の保管には該当しません。
したがって、ISMAP対応の文脈においてもセキュリティ上の問題は基本的にありませんが、調達要件によっては別途確認・申請が必要となる場合があります。
:::

## プライベートSaaS版

プライベートSaaS版では、Kurocoをソフトウェアやミドルウェアとして、ISMAP登録済みクラウドである**AWS（Amazon Web Services）**上に構築します。
Fastlyを利用しない構成を選択すればISMAP登録済みのクラウドサービスのみでシステム全体を構成できるため、**ISMAP対応が求められるシステムにも利用可能**です。

:::info プライベートSaaS版の位置づけ
ISMAP登録済みのプラットフォーム（AWS）上にKurocoを構築し、Fastlyを利用しない等、ISMAP登録済みサービスのみでシステムを構成することで、ISMAP対応が求められるシステムの要件に対応できる建付けです。
:::

### Managed（弊社がインフラを提供）
- 弊社のAWSアカウント内のお客様専用サブアカウントでプライベート環境を構築し、Kurocoをインストールします
- Fastlyを利用する構成・利用しない構成のいずれも選択可能
- ISMAP対応が必要な場合は、Fastlyを利用しない構成を選択することでISMAP登録済みサービスのみで構成可能
- AWSではFargate / Aurora / EFS / ElastiCache / S3 等を利用してマルチAZで構築

### Self-Hosted（BYOC）（お客様がインフラを用意）
- お客様のAWSアカウント内の環境（Kuroco専用のサブアカウントのご用意を推奨）にKurocoをインストールします
- Fastlyを利用する構成・利用しない構成のいずれも選択可能
- ISMAP対応が必要な場合は、Fastlyを利用しない構成を選択可能
- ※AWS以外（Azure / GCP）へのインストールは応相談となります

## プライベートSaaS版利用時の制約事項

パブリックSaaS版と比べて、プライベートSaaS版には以下の制約事項があります。

- **Fastlyを利用しない構成の場合**：Fastlyに依存している機能（APIのキャッシュ機能、画像最適化機能等）が利用不可となります。CloudFront等の他のCDNでの代替を進めています。
- **ログ検索画面**：BigQueryに依存しているログ検索画面が利用できません。CloudWatchでの確認となります（CloudWatchでも動作するログ検索画面の開発を進めています）。

:::info 情報資産の保管場所について
プライベートSaaS版ではAWS上にデータが保管されるため、「情報資産は日本国内に保管すること」という要件にも、東京リージョン等の国内リージョンを選択することで対応可能です。
:::

## まとめ

- **ISMAP対応が必須の場合** → プライベートSaaS版（Managed または Self-Hosted）で、Fastlyを利用しない構成をご利用ください。ISMAP登録済みのプラットフォーム上にKurocoを構築し、ISMAP登録済みサービスのみでシステムを構成できます。
- **ISMAP登録済みサービスのみでの構成までは必須でない場合** → パブリックSaaS版もISMAP登録済みのGCP上で動作しており、FastlyはCDNとしての利用のみであるため、セキュリティ上の問題は基本的にありません

詳細やお見積もりについては、以下からお問い合わせください。

:::info info
- [フォームから問い合わせする](https://kuroco.zendesk.com/hc/ja/requests/new?ticket_form_id=900002698263)
:::

## 関連ドキュメント
- [オンプレミス版の提供はありますか？](/ja/docs/faq/a-on-premises-version-availability/)
- [Kurocoサービスのサーバーは冗長化されていますか？](/ja/docs/faq/are_the_kuroco_service_redundant/)
- [セキュリティチェックシートへの記入をお願いできますか？](/ja/docs/faq/can-you-audit-my-security-checklist/)
- [セキュリティ](/ja/docs/about/security/)


---

# セキュリティ対策の資料はありますか？

> 元ページ: `faq/materials-on-security-measures` ｜ 公式ページ: https://kuroco.app/ja/docs/faq/materials-on-security-measures/
> 概要: Kurocoのセキュリティ対策については、営業資料の「インフラに関するドキュメント」内「セキュリティ機能について」をご確認ください

はい、資料準備しております。  
Kurocoのセキュリティ対策については、[営業資料](/ja/docs/about/sales/)の[インフラに関するドキュメント](https://kuroco.app/files/sheets/ja/kuroco_infrastructure.pdf)内「セキュリティ機能について」をご確認ください。

## 関連ドキュメント
- [セキュリティ](/ja/docs/about/security/)
- [API セキュリティ](/ja/docs/management/api-security/)


---

# 脆弱性診断で指摘を受けたのでどうすればいいか教えてください

> 元ページ: `faq/my-site-was-diagnosed-with-a-security-vulnerability` ｜ 公式ページ: https://kuroco.app/ja/docs/faq/my-site-was-diagnosed-with-a-security-vulnerability/
> 概要: 脆弱性があると判定された場合には、[弊社サポート]までご連絡を頂ければ速やかに調査・対応をいたします。

脆弱性があると判定された場合には、[弊社サポート](https://kuroco.zendesk.com/)までご連絡を頂ければ速やかに調査・対応をいたします。  

ただし、指摘事項によっては対応の必要がないとの判断になるものもありますのでご了承ください。  
また、ソフトウェアなどでの自動診断は誤診断が発生しやすいものもありますので、診断結果を再確認していただいてからのご連絡をお願いいたします。  
 
## 対応不要な事項について
以下項目は対応不要となります。 

### 対応する予定のない指摘事項
- HTTPレスポンスステータスが300番台等で、X-Content-Type-Options等のヘッダが付与されていない。
 
### CMSという仕組みの特性上対応が難しい指摘事項 
- 管理画面で、X-XSS-Protectionが付与されていない。理由としては、更新画面で更新などの挙動をエラー判定されることが多いためになります。

### 利便性やセキュリティの考え方との兼ね合いで対応をしていない指摘事項  
- パスワードリマインダーでのメールアドレスの存在のあり・なし表示（回数制限は実装） 
- 会員登録時でメールアドレスの存在のあり・なし表示（回数制限は実装・メールのみを入力して返信メールから会員登録する機能などを利用して回避可能）  
- パスワードの定期的変更の強制（管理画面で設定は可能）
- CookieのSameSite属性がStrictではない。管理画面のCookieはStrictになっているが、APIの場合はNoneになります。

### 対応予定のないもの
- 指摘事項内でINFO(情報)などのように脆弱性ではない指摘事項のもの。ただし、ご提示いただいて対応をする場合もあります。

### Kurocoで対応対象外のもの
- フロントエンド実装やAPI・管理画面での設定漏れなどによる脆弱性。指摘事項の解決策はサポートに連絡いただければ解決に向けてのサポートはいたします。


## 関連するページ
- [セキュリティ](/ja/docs/about/security/)
- [脆弱性検査のエビデンスを提供してもらうことはできますか？](/ja/docs/faq/can-you-send-me-your-vulnerability-assessment-findings/)

## 関連ドキュメント
- [セキュリティ](/ja/docs/about/security/)
- [脆弱性検査のエビデンスを提供してもらうことはできますか？](/ja/docs/faq/can-you-send-me-your-vulnerability-assessment-findings/)
- [脆弱性診断・検査に関して教えてください](/ja/docs/faq/what-vulnerability-diagnostic-and-assessment-services-do-you-provide/)
- [セキュリティ対策の資料はありますか？](/ja/docs/faq/materials-on-security-measures/)
- [セキュリティチェックシートへの記入をお願いできますか？](/ja/docs/faq/can-you-audit-my-security-checklist/)
- [脆弱性診断でCSRFの脆弱性が検出されました。Kurocoではどのように対応すればいいですか？](/ja/docs/faq/csrf-was-detected-in-a-vulnerability-assessment/)


---

# 脆弱性診断・検査に関して教えてください

> 元ページ: `faq/what-vulnerability-diagnostic-and-assessment-services-do-you-provide` ｜ 公式ページ: https://kuroco.app/ja/docs/faq/what-vulnerability-diagnostic-and-assessment-services-do-you-provide/
> 概要: アプリケーション開発時には情報処理推進機構(IPA)の「安全なウェブサイトの作り方」などを参照しながら、セキュリティに気をつけながら開発しております。

アプリケーション開発時には情報処理推進機構(IPA)の「[安全なウェブサイトの作り方](https://www.ipa.go.jp/security/vuln/websecurity.html)」などを参照しながら、セキュリティに気をつけながら開発しております。  

自主的な脆弱性検査に関しては、代表FQDNを設定し、[VAddy](https://vaddy.net/ja/)を利用して毎日の自動検査をしております。    
脆弱性検査のエビデンス等の提出は行っておりませんので、必要な場合には別途、手配・発注をお願いいたします。 
[VAddy](https://vaddy.net/ja/)であれば、Kuroco管理画面より設定が可能です。  

また、お客様による脆弱性診断も頻繁に行われますので、そちらで指摘が発生した場合にはクラウド環境全体に対して改修が適用されていきます。  
セキュリティについての詳細は[Kurocoのセキュリティ対策](/ja/docs/about/security/)をご参照ください。
 
## ご自身で脆弱性診断をされる場合
- Kuroco環境に脆弱性診断をされる場合、弊社への事前連絡は必要ありません。
- 診断期間中にアクセスを遮断しないようにする要請は受けられませんのでご了承ください。<br/>(基盤クラウドであるFastlyやGCP側でDDoSを検知して遮断する可能性があるため対応できません。)
- 脆弱性診断により、Kuroco利用料が大きくなった場合でも、減額できかねますのでご注意ください。主にAPIリクエストが利用されることになりますので、想定のリクエスト数をご確認いただくとよいです。（通常は1万リクエスト（550円）以下になることが多いですが念のためご確認ください。）
- 万が一、Kurocoに起因する脆弱性がありましたら、ご連絡いただければ、速やかに改修をいたします。
- 調査会社の紹介も可能ですのでお気軽にお問い合わせください。  

## 関連FAQ
- [脆弱性検査のエビデンスを提供してもらうことはできますか？](/ja/docs/faq/can-you-send-me-your-vulnerability-assessment-findings/)  
- [脆弱性診断で指摘を受けたのでどうすればいいか教えてください](/ja/docs/faq/my-site-was-diagnosed-with-a-security-vulnerability/)

## 関連ドキュメント
- [VAddy](/ja/docs/management/vaddy/)
- [VAddyと連携してAPIエンドポイントに対する自動診断を設定する。](/ja/docs/tutorials/integrating-with-vaddy/)
- [セキュリティ](/ja/docs/about/security/)
- [脆弱性検査のエビデンスを提供してもらうことはできますか？](/ja/docs/faq/can-you-send-me-your-vulnerability-assessment-findings/)
- [脆弱性診断で指摘を受けたのでどうすればいいか教えてください](/ja/docs/faq/my-site-was-diagnosed-with-a-security-vulnerability/)
- [セキュリティ対策の資料はありますか？](/ja/docs/faq/materials-on-security-measures/)


---

# KurocoのStrict-Transport-Security(HSTS)ヘッダーにincludeSubDomainsが付与されないのはなぜですか？

> 元ページ: `faq/why-kuroco-does-not-include-includesubdomains-in-hsts` ｜ 公式ページ: https://kuroco.app/ja/docs/faq/why-kuroco-does-not-include-includesubdomains-in-hsts/
> 概要: Kurocoでは、HSTSヘッダーにincludeSubDomainsディレクティブを意図的に付与していません。これは、サブドメインで運用されている他サービスへの意図しない影響を防ぐためです。

## HSTSとincludeSubDomainsの概要

HSTS（HTTP Strict Transport Security）は、ブラウザに対して「このドメインへの接続は常にHTTPSを使用すること」を指示するセキュリティヘッダーです。

```
Strict-Transport-Security: max-age=31536000
```

ここに`includeSubDomains`ディレクティブを追加すると、当該ドメインだけでなく、すべてのサブドメインにもHSTSポリシーが適用されます。

```
Strict-Transport-Security: max-age=31536000; includeSubDomains
```

## Kurocoがincludesubdomainsを付与しない理由

Kurocoでは、HSTSヘッダーに`includeSubDomains`を**意図的に付与していません**。

### Kurocoの独自ドメイン利用と影響範囲

Kurocoでは、お客様が所有する独自ドメインをKurocoのフロントエンドやAPIに割り当てて利用できます。この場合、Kurocoが管理するのはそのドメインの一部（フロントエンドやAPIのサブドメイン）のみであり、同じドメイン配下の他のサブドメインはお客様自身が別のサービスやサーバーで運用しているケースが一般的です。

`includeSubDomains`が付与されると、ブラウザは当該ドメインのすべてのサブドメインに対してHTTPS接続を強制します。しかし、独自ドメインの場合、ドメイン配下のすべてのサブドメインがKurocoで管理されているとは限りません。

例えば、お客様の独自ドメイン`example.com`をKurocoで利用している場合:

| サブドメイン | 用途 | 管理 |
|---|---|---|
| `www.example.com` | Kurocoフロントエンド | Kuroco |
| `api.example.com` | Kuroco API | Kuroco |
| `internal.example.com` | 社内ツール | 自社サーバー |
| `legacy.example.com` | 旧システム | 他社サービス |

`includeSubDomains`が有効な場合、`internal.example.com`や`legacy.example.com`など、Kurocoの管理外にあるサブドメインにもHTTPS接続が強制されます。

Kurocoはお客様のドメインの一部を借りて運用している立場であるため、お客様のドメイン全体に影響を及ぼすセキュリティポリシーを一方的に適用することは適切ではありません。

### 想定されるリスク

- **HTTPS未対応のサブドメインへのアクセス不能**: サブドメインがHTTPのみで運用されている場合、ブラウザがHTTPSを強制するためアクセスできなくなります
- **証明書の不一致によるエラー**: サブドメインに適切なTLS証明書が設定されていない場合、ブラウザがセキュリティエラーを表示します
- **復旧の困難さ**: HSTSはブラウザにキャッシュされるため、一度適用されると`max-age`の期間中はユーザー側で解除が困難です

## Kurocoの対応方針

Kurocoでは、以下の方針でHSTSを運用しています。

- **HSTSヘッダー自体は付与**: Kurocoで管理するドメインに対してHSTSは有効です
- **includeSubDomainsは付与しない**: Kurocoの管理範囲外のサブドメインに影響を及ぼさないよう、意図的に除外しています
- **影響範囲を限定**: Kurocoが責任を持てる範囲のみにセキュリティポリシーを適用します

## 脆弱性診断でincludeSubDomainsの不備を指摘された場合

脆弱性診断でHSTSの`includeSubDomains`がないことを指摘された場合、以下のように説明することができます。

「本システムはヘッドレスCMSであるKurocoを採用しています。Kurocoではお客様の独自ドメインを利用してサービスを提供しますが、同一ドメイン配下にはKuroco以外のサービスで運用されるサブドメインが存在する場合があります。includeSubDomainsを付与すると、それらKuroco管理外のサブドメインにもHTTPS接続が強制され、意図しないアクセス障害が発生する可能性があります。このため、Kurocoでは影響範囲を自身が管理するドメインのみに限定し、includeSubDomainsを意図的に付与していません。Kurocoが管理するドメイン自体にはHSTSが適用されており、HTTPS通信は強制されています。」

:::info
上記の説明で不十分な場合や、追加のエビデンスが必要な場合は、[弊社サポート](https://kuroco.zendesk.com/)までご連絡ください。
:::

## 関連ドキュメント
- [セキュリティ](/ja/docs/about/security/)
- [脆弱性診断で指摘を受けたのでどうすればいいか教えてください](/ja/docs/faq/my-site-was-diagnosed-with-a-security-vulnerability/)
