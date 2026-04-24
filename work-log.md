# 📋 AI×DX Weekly ニュースレタースキル — 作業ログ

**作成日**: 2026年4月3日  
**作成者**: 大井琉誠 × Claude Opus 4.6

---

## Phase 1: 企画・要件定義

### ① スキルの方向性を決定
- **分野**: AI×DXトレンド
- **出力形式**: HTML（メール配信向け）
- **読者層**: 中小企業のDX担当者・経営層
- **言語**: 日本語メイン＋英語キーワード併記
- **情報取得**: Web検索で最新情報を自動収集

### ② ニュースレターの構成を設計（4セクション）
1. 📰 今週のAI×DXニュース TOP3
2. 🛠️ おすすめツール・リソース紹介（2件）
3. 📖 用語解説・学習コーナー（1用語）
4. 💬 編集者コメント・コラム

---

## Phase 2: スキル（SKILL.md）のドラフト作成

### ③ SKILL.mdの初版を作成
- ワークフロー（トピック収集 → コンテンツ構成 → HTML生成 → 出力）
- HTMLテンプレート（テーブルレイアウト、640px幅、青系アクセントカラー）
- ユーザー確認ポイント（号数、特集テーマ、除外トピック）
- 品質チェックリスト

### ④ テストケースの設計（2パターン）
| # | プロンプト | 検証ポイント |
|---|-----------|------------|
| 1 | 「今週のAI×DXニュースレターを作って」 | 基本パターン |
| 2 | 「生成AIの業務活用をテーマに」 | テーマ指定 |

---

## Phase 3: テスト実行（Iteration 1）

### ⑤ テストケース1 — 基本パターン
- Web検索で2026年4月の最新AI×DXニュースを収集
- HTMLニュースレターを生成・出力
- **結果**: ✅ 4セクション構成、最新ニュース反映、デザイン良好

### ⑥ テストケース2 — テーマ指定パターン
- 「生成AIの業務活用」に焦点を当てたニュース選定
- ヘッダーに特集テーマバッジを表示
- **結果**: ✅ テーマに沿った内容、特集表示あり

---

## Phase 4: レスポンシブ対応（Iteration 2〜3）

### ⑧ スマートフォン対応（メディアクエリ追加）
- `@media (max-width: 680px)` でモバイル最適化
- パディング縮小、フォントサイズ調整、タップ領域拡大
- Outlook対応の MSO条件コメント追加
- **iPhoneで確認**: ✅ 問題なし

### ⑨ タブレット対応（メディアクエリ追加）
- `@media (min-width: 681px) and (max-width: 840px)` を追加
- iPad縦向き（768px）での表示を最適化
- コンテナ幅94%、フォントサイズやや拡大
- **iPadで確認**: ✅ 問題なし

### ⑩ PC向けコンテナ幅を800pxに拡大
- 640px → 800pxに変更（Web公開重視）
- 本文領域720px → 1行あたり約45〜48文字（最適な読みやすさ）
- PC向けフォントサイズ（本文15px、見出し21px）に拡大
- 左右パディング40pxに調整

**最終的なレスポンシブ設計:**

| デバイス | 画面幅 | コンテナ幅 | 左右padding | 本文 | 見出し |
|---------|--------|-----------|------------|------|-------|
| PC | 841px〜 | 800px固定 | 40px | 15px | 21px |
| タブレット | 681〜840px | 画面の94% | 28px | 15px | 21px |
| スマホ | 〜680px | 画面の100% | 16px | 14px | 18px |

---

## Phase 5: 運用と改善（Vol.1〜Vol.3）

### ⑪ Vol.1〜Vol.3の定期発行
- Vol.1 創刊号（2026/04/03）: 大阪市×日立AIエージェント / AWS自律型エージェント / 補助金
- Vol.1 特集号（2026/04/03）: 生成AIの業務活用（パナソニック44.8万時間削減）
- Vol.2（2026/04/06）: Japan DX Week春 / 関西DX戦略Next / 補助金申請準備
- Vol.3（2026/04/13）: Microsoft 1.6兆円対日投資 / Gemma 4 / 補助金2026

### ⑫ バックナンバーページの作成
- ルートに `index.html` を作成し、全号をカード形式で一覧表示
- 各号ページに「戻るボタン」（固定位置フローティング）を追加
- GitHub Pages用のディレクトリ構成: `outputs/volX/index.html`

### ⑬ GitHub Pagesでの公開
- リポジトリ作成・push・GitHub Pages有効化完了
- 公開URLでPC / タブレット / スマホ表示を確認済み

---

## Phase 6: スキル更新（2026年4月17日）

### ⑭ SKILL.mdの改善
- **Step 4 追加**: 戻るボタンのHTMLテンプレートとリンクパスルール
- **Step 5 追加**: バックナンバーページ（index.html）の自動更新ルール
- **Step 7 追加**: 号数の自動採番・管理ルール
- **品質チェックリスト拡充**: 戻るボタン・バックナンバー更新・class属性の確認項目追加

### ⑮ README.mdの更新
- Vol.1〜Vol.3全号のリンクを追記
- プロジェクト構成にindex.html・vol2・vol3を追加
- 発行履歴テーブルを新設

### ⑯ evals.jsonの拡充
- テストケース3件追加（Vol指定、除外トピック指定、キーワード省略パターン）
- 計5件のテストケースに拡大

### ⑰ .skillファイルの再パッケージ
- 全ファイル更新後に再パッケージ化

---

## Phase 7: 次のステップ（TODO）

### ⑱ 運用の安定化
- [x] 配信曜日を決定 → **毎週月曜日**に確定
- [ ] 読者フィードバックの収集方法を検討
- [ ] 過去号の用語解説で取り上げたキーワード一覧を管理

### ⑲ 機能拡張（将来検討）
- [ ] メール配信サービス（Mailchimp等）との連携
- [ ] ニュースソースの定期的な見直し・拡充
- [ ] 読者層に応じたパーソナライズ（業界別フィルタリング等）

---

## Phase 8: Exa MCP導入・Claude Code CLI環境構築（2026年4月18日）

### ⑳ 課題の整理
- claude.ai（Webチャット）でニュースレターを生成 → ダウンロード → VSCodeにコピー → Sourcetreeでcommit/push、という手動ステップが多く非効率だった
- Claude Code（ターミナル版）からWeb検索→HTML生成→ファイル出力を一気通貫で行う環境を構築することを決定

### ㉑ 開発環境の構築

**Node.jsのインストール:**
- nodejs.org から LTS版（v24.15.0）をインストール
- npm v11.12.1 も同時にインストール済み

**Claude Code CLI のインストール:**
- `sudo npm install -g @anthropic-ai/claude-code` で v2.1.114 をインストール
- Claude Proアカウント（サブスクリプション）で認証完了

**つまずいたポイント:**
- `npm install -g` で EACCES（権限エラー）が発生 → `sudo` で解決
- npmキャッシュの権限問題 → `sudo chown -R $(whoami) ~/.npm` + `npm cache clean --force` で解決

### ㉒ Exa MCP サーバーの導入

**Exaを選定した理由:**
- 2026年時点で最も利用されているAI向け検索MCPサーバー
- セマンティック検索（意味ベース）でニュースの関連性が高い
- 記事本文（Full text）まで取得可能 → 要約の品質が向上
- 無料クレジット$10付与（ニュースレター用途では十分）

**セットアップ手順:**
1. exa.ai でアカウント作成（Claude → MCP → News monitoring を選択）
2. APIキーを取得
3. 環境変数に設定: `echo 'export EXA_API_KEY="..."' >> ~/.zshrc`
4. MCPサーバー追加: `claude mcp add-json exa '{"command":"npx","args":["-y","exa-mcp-server"],"env":{"EXA_API_KEY":"..."}}'`
5. `/mcp` で `exa · ✓ connected` を確認

**つまずいたポイント:**
- 最初 `$EXA_API_KEY` の変数展開がうまくいかず `failed` に → APIキーを直接埋め込みで解決
- npmキャッシュの EEXIST エラー → キャッシュクリアで解決

### ㉓ ターミナル版 vs 拡張機能版の使い分けを整理

| 作業 | ターミナル版 | 拡張機能版 |
|------|------------|----------|
| ニュースレター生成（Exa検索必要） | ✅ | ❌ MCP未設定 |
| コードの修正・質問 | ○ | ✅ エディタ連携 |
| Git操作 | ○ | ○ |
| MCP設定 | ✅ | ❌ |

**重要な発見:** ターミナル版と拡張機能版は設定ファイルが別々。ターミナルで設定したMCPは拡張機能側には反映されない。

### ㉔ 毎週月曜日の作業プロセスを策定
- `weekly-newsletter-workflow.md` を作成
- 6ステップの作業フローを定義（準備 → 生成 → 確認 → プレビュー → Git → 公開確認 → 記録更新）
- 各ステップでターミナル版/拡張機能版/Sourcetree/手動のどれを使うか明示
- 所要時間の目安: 約17〜24分/号

### ㉕ README.md・work-log.mdの更新
- README.md: 技術スタックにExa MCP追記、開発環境セクション新設、作業フロー概要追記、プロジェクト構成にworkflowファイル追記
- work-log.md: Phase 8（本セクション）を追記

---

## 📁 生成ファイル一覧

| ファイル名 | 内容 |
|-----------|------|
| `SKILL.md` | ニュースレタースキル本体（v2） |
| `weekly-newsletter.skill` | スキル登録カード |
| `weekly-newsletter-workflow.md` | 毎週月曜日の作業プロセス |
| `README.md` | プロジェクト説明（Exa MCP対応版） |
| `index.html` | バックナンバー一覧ページ |
| `evals/evals.json` | テストケース定義（5件） |
| `work-log.md` | 作業ログ・学習メモ（Phase 8まで） |
| `outputs/vol1/index.html` | Vol.1 創刊号 |
| `outputs/vol1-special/index.html` | Vol.1 特集号 |
| `outputs/vol2/index.html` | Vol.2 |
| `outputs/vol3/index.html` | Vol.3 |
| `outputs/vol4/index.html` | Vol.4 |

---

## Phase 9: 編集者コメント欄スタイル全号統一（2026年4月23日）

### ㉓ 課題の整理
- Vol.1〜Vol.4で編集者コメント欄のHTML構造・スタイルがバラバラだった
- Vol.2を基準として全号統一する方針に決定

### ㉔ 修正内容

**対象ファイルと変更点:**

| ファイル | 変更内容 |
|---------|---------|
| `outputs/vol1/index.html` | 変更なし（すでにVol.2基準を満たしていた） |
| `outputs/vol1-special/index.html` | tdにclass追加、h2にclass追加・font-size修正、カードセルclass/padding修正、p要素のclass・font-size・line-height修正 |
| `outputs/vol3/index.html` | 「編集後記」→「編集者コメント」、見出しとカードを別trに分離、カードのbackground/border/padding/class修正、🚀→📌変更、来週予告にcolor:#92400e適用 |
| `outputs/vol4/index.html` | 見出しとカードを別trに分離、カードのbackground/border/padding/class修正（border-leftのみ→全辺border） |

**統一仕様（Vol.2基準）:**
- カード：`background:#fefce8; border:1px solid #fde68a; border-radius:8px;`
- カードセル：`class="column-box-cell" style="padding:24px;"`
- 来週予告：📌で始まる、`font-size:14px; color:#92400e;`
- 見出しtrとカードtrは別の`<tr>`に分ける

### ㉕ ドキュメント更新
- `SKILL.md` のセクション4にスタイル仕様を追記
- `work-log.md` に本フェーズを記録

### ㉖ 来週予告末尾の全号統一（2026年4月23日）
- 全号（Vol.1〜Vol.4）の来週予告行末尾を「〜お届け予定です。お楽しみに！」に統一
- Vol.1: 「レポート予定です。お楽しみに！」→「お届け予定です。お楽しみに！」
- Vol.1-special: 「お届け予定です！」→「お届け予定です。お楽しみに！」
- Vol.2: 「お届け予定です！」→「お届け予定です。お楽しみに！」
- Vol.3: 「お届け予定です！」→「お届け予定です。お楽しみに！」
- Vol.4: 「取り上げる予定です！」→「お届け予定です。お楽しみに！」
- SKILL.md の来週予告ルールも同様に更新

---

## Phase 10: favicon・ロゴ画像・ヘッダーレイアウト改善（2026年4月23日）

### ㉗ favicon・apple-touch-iconの適用
- `images/` フォルダに `favicon.ico` と `apple-touch-icon.png` を配置
- `index.html`（バックナンバーページ）の `<head>` に favicon・apple-touch-icon の `<link>` タグを追加
- ニュースレター本体テンプレート（SKILL.md Step 3）にも同様に追加（パス: `../../images/`）
- バックナンバーページテンプレート（SKILL.md Step 5）にも追加（パス: `images/`）

### ㉘ ヘッダーの絵文字→ロゴ画像に変更
- `index.html` ヘッダーの `🤖 AI×DX Weekly` を `<img>` タグ（apple-touch-icon.png）+ テキストに変更
- SKILL.md の両テンプレートにも同様の変更を反映
- 品質チェックリストに favicon・ロゴ画像の確認項目を2件追加

### ㉚ スマホヘッダーのロゴ崩れを修正（2026年4月23日）
- iPhone縦・横でロゴが大きすぎて崩れる問題を修正
- `@media (max-width: 680px)` 内の `.header` 関連を変更：
  - スマホでも横並び（`flex-direction: row`）を維持、padding縮小（24px 16px）、gap:14px
  - ロゴを44px×44pxに縮小（`!important` で上書き）
  - h1を20px、pを12pxに縮小、左揃えに統一
- `index.html` と SKILL.md バックナンバーテンプレートの両方に反映

### ㉙ ヘッダーレイアウトを縦並び→横並びに変更
- `.header` に `display:flex; align-items:stretch; justify-content:center; gap:20px;` を追加
- ロゴ画像（56px）の右側にタイトルとサブタイトルを縦配置する `<div style="display:flex; flex-direction:column;">` でラップ
- タイトル（h1）は上端固定（`margin:0`）、サブタイトル（p）は下端固定（`margin-top:auto`）
- スマホ（max-width:680px）では `flex-direction:column` で縦並び・中央揃えに戻す
- `index.html` と SKILL.md バックナンバーテンプレートの両方に反映

### ㉛ フッターレイアウト全号統一（2026年4月24日）
- Vol.3・Vol.4のフッターをVol.2基準の2行構成に統一（Vol.1・Vol.1-special・Vol.2は変更なし）
- 統一仕様：`padding:24px 40px; font-size:13px;` + 2行（キャッチコピー行／コピーライト行）
- Vol.3から削除した行：タイトル行（`font-weight:700`）、号数・日付行、注意書き行
- Vol.4から削除した行：タイトル行（`font-weight:600`）、号数・発行日行
- SKILL.md のフッターテンプレートも同仕様に更新し、「2行構成固定・Vol番号/日付/注意書きを含めない」ルールをコメントで明記

### ㉜ 全号のヘッダーをロゴ画像＋中央揃えに統一（2026年4月24日）
- Vol.1〜Vol.4 のニュースレター本体（`outputs/volX/index.html`）のヘッダーも同様に更新
  - 絵文字 `🤖` → `<img>` タグ（`../../images/apple-touch-icon.png`、56px）に差し替え
  - ロゴ＋テキストを横並び（flex）・中央揃えに統一
  - スマホ（max-width:680px）では縦並び・中央揃えにフォールバック
- `index.html`（バックナンバーページ）のヘッダーも同仕様に合わせて最終調整
- GitHub Pages 再デプロイ（空コミット push）で全ページの表示を確認

---

## Phase 11: manifest.json追加・タイトルタグ統一（2026年4月24日）

### ㉝ manifest.jsonの作成
- プロジェクトルートに `manifest.json` を新規作成
- 設定内容：name/short_name「AI×DX Weekly」、start_url「/weekly-newsletter/」、display「standalone」、theme_color「#1e3a5f」、background_color「#f5f5f5」
- アイコン：`images/apple-touch-icon.png`（180×180）と `images/favicon.ico`（any）

### ㉞ 全HTMLへの `<link rel="manifest">` 追加
| ファイル | href |
|---------|------|
| `index.html`（ルート） | `manifest.json` |
| `outputs/vol1/index.html` | `../../manifest.json` |
| `outputs/vol1-special/index.html` | `../../manifest.json` |
| `outputs/vol2/index.html` | `../../manifest.json` |
| `outputs/vol3/index.html` | `../../manifest.json` |
| `outputs/vol4/index.html` | `../../manifest.json` |

### ㉟ タイトルタグの変更
- ルート `index.html` の `<title>` を「AI×DX Weekly — バックナンバー」→「AI×DX Weekly」に変更（iPhone Safari ホーム画面追加時の表示名統一）
- 各号の `<title>` は「AI×DX Weekly - Vol.X（日付号）」のまま変更なし

### ㊱ ドキュメント更新
- `SKILL.md` に「manifest.json の管理ルール」セクションを追加（設定値・パスルール・新号追加時の確認事項）
- ニュースレター本体テンプレートと バックナンバーページテンプレートの `<head>` に `<link rel="manifest">` を追加
- `work-log.md` に本フェーズを記録

---

## 💡 学んだこと・メモ

- **メディアクエリ**: 画面サイズに応じてCSSを切り替える仕組み。タブレット用を追加するとテスト工数が増えるトレードオフがある
- **コンテナ幅800pxの理由**: 1行あたり45〜48文字（日本語）が最も読みやすい。1000px以上だと目が行を追いにくくなる
- **テーブルレイアウト**: メールクライアント互換性のために必要。ブラウザ用のメディアクエリと併用する
- **MSO条件コメント**: Outlook対応のためのHTML条件分岐
- **GitHub Pagesのディレクトリ構成**: `outputs/volX/index.html` にすると `outputs/volX/` でアクセスできる（index.htmlを省略可能）
- **戻るボタンのenv()関数**: `env(safe-area-inset-bottom)` でiPhoneのホームバーとの干渉を防ぐ
- **スキル運用のポイント**: バックナンバーページの更新を忘れがちなのでワークフローに明記することが重要
- **MCP（Model Context Protocol）**: Claude Codeに外部ツールとの接続口を追加する仕組み。MCPサーバーを追加すると、Claude Codeからデータベース、API、Web検索などが使えるようになる
- **Exa**: AI向けに設計されたセマンティック検索エンジン。キーワードの一致ではなく意味の近さで検索する。記事本文も取得可能
- **ターミナル版 vs 拡張機能版**: 同じClaude Codeでも設定ファイルが別。MCP設定はターミナル版のみ反映される
- **npmキャッシュの権限問題**: `sudo` でグローバルインストールするとキャッシュの所有者がrootになる。`sudo chown -R $(whoami) ~/.npm` で修復可能
- **セマンティック検索の比喩**: 従来の検索が「伝票番号で倉庫を探す」なら、セマンティック検索は「保管条件・商品特性の意味で最適な棚を見つける」方式
