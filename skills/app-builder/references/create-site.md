# サイト新規作成（cold start — サイトがまだ無い場合）

app-builder は「サイトが存在し Admin MCP に接続済み」を前提とする（接続は 0-0、対象サイトの確定は 0-6）。**この前提が満たせない＝Kuroco サイトを1つも持っていない状態**からの立ち上げに使う。公開API（未認証で叩ける）でサイトを作り、Admin MCP 接続まで案内して、app-builder のフェーズ0へ戻す。

**このフローは Admin MCP を使わない。** サイトがまだ無い＝そのサイトの MCP も無いため、すべて公開APIへの `curl` で行う。接続は**経路の選択と Kuroco 側の前提（Step 2 の redirect URI 登録・Step 5 の CIMD 有効化）まで**をここで扱い、**クライアント別の細かい設定手順は書かない**——`/kuroco-admin-mcp` と `kuroco-docs` の `reference-mcp-ai.md` が正本で、クライアント（Claude Code / Claude Web・Desktop / ChatGPT / Codex CLI / Cursor など）ごとに異なり古くなるため。

## 目次

- [このフローをどこまでエージェントが実行できるか](#このフローをどこまでエージェントが実行できるかクライアント能力で分岐)
- [Step 1: 情報収集](#step-1-情報収集)
- [Step 2: サイト作成](#step-2-サイト作成siteregist)
- [Step 3: セットアップ完了待機](#step-3-セットアップ完了待機setup_status)
- [Step 4: 管理者アカウントのパスワード設定](#step-4-管理者アカウントのパスワード設定メールから)
- [Step 5: Admin MCP 接続](#step-5-admin-mcp-接続)
- [Step 6: セッションの引き継ぎ](#step-6-セッションの引き継ぎ)
- [暫定回避策](#暫定回避策)

## このフローをどこまでエージェントが実行できるか（クライアント能力で分岐）

「AIが全部やる」ではない。**実行できる範囲は利用クライアントの能力で変わる**。着手前に見極める。

| クライアント | Step 1–3（regist・polling） | Step 4–6（パスワード設定・接続・再開） |
|---|---|---|
| **シェルがある**（Claude Code / Codex CLI 等） | エージェントが `curl` を実行して自動で進める | **パスワード設定・OAuth 同意・再接続はユーザーの手作業**。エージェントは代われない |
| **シェルが無い**（Claude Web・Desktop / ChatGPT 等） | サイト未作成＝MCPも無い＝実行手段が無い。**エージェントはコマンド・手順をユーザーに渡して案内するだけ**。実行はユーザー | 同上 |

- **Step 4（メールからのパスワード設定）・Step 5（CIMD 有効化〈経路A〉／OAuth 同意）はどのクライアントでも本質的にユーザー操作**。エージェントには代行できない。
- 同意はセッションに反映されないため、**Step 6 で必ず新しいセッションに切り替える**。これはクライアント共通の制約。

## Step 1: 情報収集

技術パラメータ名はユーザーに見せず、自然な日本語で確認する。すでに聞いた情報は再度聞かない。一度に全部聞くより会話の流れで集める。

| 収集する情報 | 質問文の例 | バリデーション |
|---|---|---|
| サイトURLキーワード（`site_key`） | 「サイトのURLに使うキーワードを決めてください。`https://【キーワード】.g.kuroco.app` になります。英小文字・数字・ハイフンのみ。」 | 英小文字・数字・ハイフンのみ |
| 管理者メールアドレス（`email`） | 「管理者のメールアドレスを教えてください。」 | メール形式 |
| 姓（`name1`） | 「お名前（姓）を教えてください。」 | 必須 |
| 名（`name2`） | 「お名前（名）を教えてください。」 | 必須 |
| 会社名（`company_nm`） | 「会社名を教えてください。」 | 必須 |

⚠️ **`site_key` は一度決めると変更できない。** 作成前に必ずユーザーに確認する。

**パスワードは事前に聞かない。** サイト作成後、管理者メールアドレス宛に届くメールから設定する方式のため、`regist` にパスワードを渡す必要はない（渡すと拒否される）。

**接続に使うクライアントもここで見当をつける。** Step 2 の `mcp_client_redirect_uris` と Step 5 の接続経路がこれで決まる。自己判定できれば使い、分からず手順に影響するときだけ一度聞く（Claude Code / Cursor / VS Code / ChatGPT / Codex など）。未確定なら Step 2 は3プラットフォーム分を広めに渡しておける。

## Step 2: サイト作成（`site/regist`）

情報が揃ったら、リージョンに対応するホストへ POST する。**`mcp_client_redirect_uris` に接続で使うクライアントの preset を渡す**（下表）。

```bash
curl -s -X POST "https://rcms.g.kuroco.app/rcms-api/1/site/regist?_lang=ja" \
  -H "Content-Type: application/json" \
  -d '{
    "email": "{メールアドレス}",
    "name1": "{姓}",
    "name2": "{名}",
    "site_key": "{site_key}",
    "company_nm": "{会社名}",
    "copy_from_site_key": "nuxt-auth-template",
    "mcp_client_redirect_uris": ["claude", "chatgpt", "cursor"]
  }'
```

| リージョン | ホスト |
|---|---|
| Asia（東京・デフォルト） | `https://rcms.g.kuroco.app` |
| EU（フィンランド） | `https://rcms.g2.kuroco.app` |
| US（アイオワ） | `https://rcms.g3.kuroco.app` |

**`mcp_client_redirect_uris` の決め方**: 自動生成される対話型 MCP クライアントに、どのプラットフォームの redirect URI を登録するかを指定する。**省略すると1つも登録されず、Step 5 の client_id 経路（経路B）が全プラットフォームで繋がらない**（後から管理画面のクライアント編集で追加は可能）。各要素は preset キーか絶対 redirect URI（512字以内・上限10。展開はサーバー側）。

| 接続クライアント | 渡す値 |
|---|---|
| Claude / Claude Code | `["claude"]` |
| ChatGPT | `["chatgpt"]` |
| Cursor | `["cursor"]` |
| 複数使う・未確定 | `["claude","chatgpt","cursor"]`（広く繋がる。同意を絞りたい運営者は必要な分だけに減らす） |
| **CIMD だけで繋ぐ**（経路A） | 不要（`[]` や省略でよい）。CIMD はクライアントのメタデータURLで自己登録するため、自動クライアントの redirect URI に依存しない |

- **`copy_from_site_key` は `nuxt-auth-template` を既定にする。** app-builder の 0-7（引き継がれた既存設定の棚卸し）がこのコピー元を前提に「コンテンツ定義 `id=1` と API `id=1` を上書き流用」の既定を持っているため、揃えておくと後工程が素直になる。別テンプレートを使う場合は 0-7 の振り分けをやり直す。
- `messages: ["registed"]`（HTTP 202）が返れば成功。
- エラーが返ったらユーザーにわかりやすく内容を伝えて止まる（`site_key` 重複・形式エラーが典型）。

## Step 3: セットアップ完了待機（`setup_status`）

作成直後はまだ使えない。以下を **30秒おき・最大40回（約20分）** ポーリングする。

```bash
curl -s "https://rcms.g.kuroco.app/rcms-api/1/site/setup_status?site_key={site_key}"
```

| `data.status` | 対応 |
|---|---|
| `processing` | 30秒待って再試行。「準備中です…（N回目 / 40）」と進捗を伝える |
| `ready` | セットアップ完了。**管理者はまだ一度もログインしていない**状態。`data.oauth` を控えて Step 4 へ進む |
| `active` | 管理者がすでにログイン済み（運用開始済み）。`data.oauth` は**返らない**。cold start の途中で見たなら Step 4 は済んでいるので Step 5 へ。`client_id` は `ready` のときに控えたものを使う（控えていなければ管理画面の Admin MCP 情報ページ `/management/rcms_api/admin_mcp_info/` から取る） |
| `error` | ユーザーにわかりやすく通知して停止 |

- 40回で `ready` にならなければタイムアウトをユーザーに伝える。準備には **10〜20分** かかることがあるが、**即 `ready` になることもある**（コピー元テンプレート次第）。
- **`data.oauth`（`client_id`・`authorize_url`・`admin_mcp_url`）は `ready` のときだけ返る。** 管理者が一度でも管理画面にログインすると（Step 4〜5 の過程で必ず起きる）`active` に変わり、以後は返らない。この API は未認証で誰でも叩けるため、接続情報の公開を初回ログインまでに絞っている仕様。**`ready` を見た時点で `client_id` を控える**——あとから取り直せない。
- `ready` / `active` では **`data.cimd_enabled`（真偽値）** も返る。`true` なら CIMD がすでに有効で、Step 5 経路A の有効化操作は不要（CIMD 対応クライアントは `client_id` なしで接続できる）。
- **シェルの無いクライアントではこのポーリングをエージェントが回せない。** ユーザーに「上のURLを開いて `ready` になったら教えてください」と案内する。

## Step 4: 管理者アカウントのパスワード設定（メールから）

**接続の前に、管理者アカウントのパスワードを設定する。** これを飛ばすと Step 5 の OAuth ログイン画面でサインインできない。**この操作はユーザー本人が行う**（メールを受け取れるのは本人だけ）。

1. `regist` 直後、`email` に指定したアドレスへセットアップ用メールが届く。
2. メール内のリンクを開き、**メールアドレスと仮パスワード**を入力する。
3. 続けて**新しいパスワード**を設定する（英字と数字をそれぞれ1文字以上）。

この「メールアドレス＋新パスワード」が、Step 5 の同意画面でのサインインに使う資格情報になる。

## Step 5: Admin MCP 接続

パスワード設定（Step 4）が済んだら接続する。Step 4 でログインした時点で `setup_status` は `active` に変わり `data.oauth` は返らなくなるので、**経路B の `client_id` は Step 3（`ready`）で控えたものを使う**。**接続URL（スコープ）はこれ:**

```text
https://{site_key}.g.kuroco.app/direct/rcms_api/admin_mcp/x/all
```

**まず接続クライアントを確定する**（自己判定できれば使い、分からず手順選択に影響するときだけ一度聞く。常に聞かない／常に決め打ちもしない）。**Kuroco は動的クライアント登録（DCR / RFC 7591）を実装していない**ので、DCR で自動接続するクライアント（Claude Code の `login` 既定など）は `does not support dynamic client registration` で失敗する。接続経路は次の2つ。**クライアント別の細かい設定手順は複製せず** `/kuroco-admin-mcp`・`kuroco-docs` の `reference-mcp-ai.md`（クライアント別節）に取りにいく。

### 経路A: CIMD（管理画面で1回有効化）

CIMD 対応クライアント（Claude / Claude Code / ChatGPT / Codex CLI / VS Code / GitHub Copilot Chat）向け。**client_id も Step 2 の preset も不要**——クライアントが自分のメタデータURLで自己登録するため、自動クライアントの redirect URI に依存しない。GUI/web クライアント（claude.ai web など）では、手動登録が要らないぶんこちらが明確にスムーズ。

1. **CIMD を有効化する**（**Step 3 の `data.cimd_enabled` が `true` ならすでに有効なので 2 へ**。サイト全体設定なのでユーザー操作。エージェントは代行しない）。次のリンクを提示する:
   `https://{site_key}.g.kuroco-mng.app/management/external/memberregist_sso_oauth_idp_edit/?login_sso_oauth_idp_id={N}`
   （**{N} は `setup_status` の `authorize_url`（`…/oauth_idp/{N}/authorize`）の数字。通常 1**）。開いたら **Admin MCP** の OAuth 設定で「**Client ID Metadata Documents（CIMD）**」を有効にし、下へスクロールして **更新**。
2. クライアントに URL を追加してログイン（例・Claude Code: `claude mcp add --transport http {コネクタ名} {上記の接続URL}` → `claude mcp login {コネクタ名}`）。**`--client-id` は付けない**。
3. 同意画面（下記）。

### 経路B: client_id（ターミナル内で完結・CIMD トグル不要）

CLI（Claude Code / Codex）で管理画面に触れず繋ぎたい場合、および **CIMD 非対応クライアント（Cursor）** 向け。**前提: Step 2 で接続クライアントの preset を渡してあること**（自動クライアントにそのクライアントの redirect URI が登録されている必要があり、無いと redirect_uri 不一致で失敗する）。`ready` のときに `setup_status` が返した `data.oauth.client_id` を使う（`active` になると返らない。控えていなければ管理画面の Admin MCP 情報ページ `/management/rcms_api/admin_mcp_info/` から取る）。

- 例・Claude Code:

  ```bash
  claude mcp add --transport http --client-id {client_id} {コネクタ名} \
    https://{site_key}.g.kuroco.app/direct/rcms_api/admin_mcp/x/all
  claude mcp login {コネクタ名}
  ```

- Cursor: `mcp.json` の `auth.CLIENT_ID` に `client_id` を入れる（Step 2 で `["cursor"]` を渡してあれば Cursor のコールバックは自動クライアントに登録済みなので、**別途の手動クライアント登録は不要**）。正本は `kuroco-docs` の Cursor 節。

### 同意画面（どちらの経路でも・ユーザー操作）

`login`／コネクタ追加で OAuth 画面が開く。**エージェントは代行できない**:

1. Step 4 で設定した**メールアドレスと新パスワード**でサインインする。
2. 委譲の主体は「**自分として**」、権限は用途に足るスコープを選ぶ（同意画面の対象は `openid` / `profile` / `email` ＋ MCP スコープ。構築なら `mcp:admin`、ツール一覧取得の `mcp:tools.list` も付く）。スコープの意味と最小権限の考え方は `/kuroco-admin-mcp`。
3. 同意すると、クライアント側に接続完了（tools が使える）旨が表示される。

- 管理画面: `https://{site_key}.g.kuroco-mng.app/management/`

## Step 6: セッションの引き継ぎ

OAuth 同意は**現在のセッションに反映されない**ため、接続後は**新しいセッションを開始**してもらう。以下の引き継ぎメモを出力し、コピー＆ペーストを促す。

```
app-builder で [サイト名] を作る作業の続きです。

## 前回までの状況
- Kuroco サイトを新規作成し、Admin MCP コネクタの接続まで完了
- site_key: {site_key}
- ドメイン: https://{site_key}.g.kuroco.app
- 接続したコネクタ名: {ユーザーが付けた名前}

## 次にやること
app-builder を起動し、フェーズ0（要件ヒアリング）から開始してください。
まず 0-6 の whoami で上記サイトへの接続を確認してから進めてください。
作りたいアプリ: [作りたいものを書く。未定なら「まず whoami で接続確認だけしたい」でもOK]
```

**この引き継ぎメモは、`{site_key}`・ドメイン・接続したコネクタ名を実値で埋めてから提示する**（プレースホルダのまま出さない）。新セッションで app-builder を起動すると、0-6 の `whoami` で接続先が確定し、そのまま通常フローに戻る。

---

## 暫定回避策

Kuroco 側の現行挙動に対する回避策。**解消条件を満たしたらこの節ごと削除する。**

- **`setup_status` が返す `data.oauth.admin_mcp_url` は末尾に `x/all/` が付かない**（例: `https://{site_key}.g.kuroco.app/direct/rcms_api/admin_mcp/`）。Step 5 で使う接続URLは、必ず末尾に `x/all` を足したもの（`…/admin_mcp/x/all`）を使う。
  - 解消条件: `setup_status` の `admin_mcp_url` が `x/all` 付き（またはそのまま接続できる形）で返るようになったら不要。
- **新規サイトの自動生成 OAuth クライアントの「対象リソース」が、サイト作成APIのホスト（`rcms.g.kuroco.app`）のままで作られることがある。** この状態だと接続時に `invalid_target`（`resource is not permitted for this client`）や `invalid_client` 系で失敗する。管理画面の OAuth 認可サーバー → 対象クライアントの「対象リソース」を、新サイトの MCP URL（`https://{site_key}.g.kuroco.app/direct/rcms_api/admin_mcp/x/all`）に直してから再接続する。管理画面の Admin MCP 情報ページ（`/management/rcms_api/admin_mcp_info/`）を一度開くと自サイトのURLへ自動修復される挙動も報告されている。
  - **状態**: Step 5 経路B（`client_id`）では**本テストで未発生**（追加修正なしで接続成功）。経路A（CIMD）等で出うるため残す。
  - 解消条件: 新規サイトで、対象リソースの手動修正も admin_mcp_info ページを開く操作もなしに接続が通るようになったら不要。
