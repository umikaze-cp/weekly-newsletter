---
name: weekly-newsletter
description: AI×DXトレンドの週刊ニュースレターをHTML形式で自動生成するスキル。Web検索で最新ニュースを収集し、中小企業のDX担当者・経営層向けにわかりやすくまとめる。ニュースレター、メルマガ、週報、AI最新情報まとめ、DXニュース、トレンドレポートなどのキーワードが出たら必ずこのスキルを使う。「今週のAIニュースをまとめて」「DXの最新動向をレターにして」「メール配信用のニュースレターを作って」のような依頼にも対応する。
---

# Weekly AI×DX Newsletter Skill

中小企業のDX担当者・経営層向けに、AI×DXトレンドの週刊ニュースレターをHTML形式で生成するスキル。

## 📑 目次

1. ワークフロー概要 (Step 1〜7)
2. 各Stepの詳細仕様
   - Step 1: トピック収集
   - Step 2: コンテンツ構成
   - Step 3: HTML生成
   - Step 5: Weeklyライブラリページの更新
   - Step 6: 出力
   - Step 7: 号数管理
3. 🎯 設計思想・判断の根拠
4. manifest.json の管理ルール
5. ユーザーへの確認ポイント
6. 品質チェックリスト
7. フッター仕様（デザイン統一ルール）

## ワークフロー

### Step 1: トピック収集

Web検索ツールを使い、以下のカテゴリで今週の注目トピックを収集する。

**検索クエリの例：**
- `AI 最新ニュース 今週` / `AI news this week`
- `DX 中小企業 事例 2026` / `生成AI ビジネス活用`
- `AI ツール 新リリース` / `業務効率化 AI`

各カテゴリで2〜3件の信頼できるソースから情報を取得する。公式発表、大手メディア、専門メディアを優先し、個人ブログや未確認情報は避ける。

### Step 2: コンテンツ構成

ニュースレターは以下の4セクションで構成する。

#### セクション1: 📰 今週のAI×DXニュース TOP3
- 今週最も重要なニュースを3本選定
- 各ニュースは以下のフォーマットで記述：
  - **見出し**（日本語 + 英語キーワード併記）
  - **要約**（3〜4文。何が起きたか → なぜ重要か → 中小企業への影響）
  - **ソースリンク**

ニュースの選定基準：中小企業のDX担当者が「自社に関係あるかも」と思えるものを優先する。大企業だけの話、研究段階すぎる話は避け、「明日から使える」「導入を検討できる」レベルの話題を選ぶ。

#### セクション2: 🛠️ 今週のおすすめツール・リソース
- AI/DX関連のツールやリソースを2件紹介
- 各ツールは以下のフォーマットで記述：
  - **ツール名**（英語名 + 日本語での一言説明）
  - **何ができるか**（2〜3文）
  - **こんな人におすすめ**（ターゲット明記）
  - **料金目安**（無料/有料/フリーミアムなど）
  - **リンク**

選定基準：中小企業でも導入しやすいもの（コスト・技術ハードルが低い）を優先する。

#### セクション3: 📖 用語解説・学習コーナー
- AI/DX関連の用語を1つピックアップして解説
- フォーマット：
  - **用語**（日本語 + 英語）
  - **一言でいうと**（1文で簡潔に）
  - **もう少し詳しく**（3〜4文。具体例を交えて）
  - **ビジネスでの使いどころ**（中小企業の実務に即した活用シーン）

用語選定の基準：ニュースセクションで出てきたキーワードや、最近バズワードになっているものを選ぶ。読者が会議で「それ知ってる」と言えるレベルの理解を目指す。

#### セクション4: 💬 編集者コメント・コラム
- 今週のニュースやトレンドを踏まえた短いコラム（150〜200字程度）
- トーンは「詳しい先輩が雑談で教えてくれる」感じ
- 締めに、来週への期待や読者へのアクションを一言添える

**スタイル仕様（全号統一、Vol.2基準）:**
- 見出し：h2要素、`class="section-heading"`、`font-size:21px; color:#1e3a5f; border-left:4px solid #2563eb; padding-left:12px;`
- カード背景色：`background:#fefce8; border:1px solid #fde68a; border-radius:8px;`
- カードセル：`class="column-box-cell" style="padding:24px;"`
- 本文：`class="body-text" style="font-size:15px; line-height:1.8;"`
- 来週予告：`📌`で始まり「〜お届け予定です。お楽しみに！」で終わる。`style="font-size:14px; color:#92400e;"`（classなし）
- 見出しtrとカードtrは別の`<tr>`に分ける

### Step 3: HTML生成

以下のデザインガイドラインに従ってHTMLメールを生成する。

**デザイン原則：**
- メール配信を想定し、テーブルレイアウトを使用（メールクライアント互換性のため）
- 最大幅: 800px、中央揃え（Web公開重視。メール配信専用の場合は640pxに戻す）
- フォント: system-ui, -apple-system, "Hiragino Sans", "Yu Gothic", sans-serif
- 背景色: #f5f5f5（外側）、#ffffff（コンテンツ部分）
- アクセントカラー: #2563eb（青系、リンクや見出しに使用）
- セクション間は水平線またはスペースで区切る
- レスポンシブ対応（メディアクエリでモバイル最適化）

**レスポンシブ対応の方針：**
テーブルレイアウトはメールクライアント互換性のためそのまま維持し、`<head>` 内に `<style>` ブロックを追加してメディアクエリで上書きする。この方式ならメールクライアントでもブラウザでも正しく表示される。

**HTMLテンプレート構造：**

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="manifest" href="../../manifest.json">
  <link rel="icon" href="../../images/favicon.ico" type="image/x-icon">
  <link rel="apple-touch-icon" href="../../images/apple-touch-icon.png">
  <title>AI×DX Weekly - Vol.XX（YYYY年MM月DD日号）</title>
  <style>
    /* ======================
       タブレット対応（681px〜840px）
       iPad縦向き768px をカバー
       ====================== */
    @media only screen and (min-width: 681px) and (max-width: 840px) {
      .email-container { width: 94% !important; max-width: 800px !important; }
      .content-cell { padding-left: 28px !important; padding-right: 28px !important; }
      .card-cell { padding: 18px 20px !important; }
      .body-text { font-size: 15px !important; line-height: 1.8 !important; }
      .header-title { font-size: 28px !important; }
      .section-heading { font-size: 21px !important; }
    }

    /* ======================
       スマートフォン対応（680px以下）
       iPhone / Android をカバー
       ====================== */
    @media only screen and (max-width: 680px) {
      .email-container { width: 100% !important; max-width: 100% !important; }
      .header-title { font-size: 22px !important; }
      .content-cell { padding-left: 16px !important; padding-right: 16px !important; }
      .card-cell { padding: 14px 14px !important; }
      .section-heading { font-size: 18px !important; }
      .body-text { font-size: 14px !important; line-height: 1.8 !important; }
      .source-link { display: inline-block !important; padding: 4px 0 !important; }
      .library-link { font-size: 13px !important; }
    }
    .library-link { transform-origin: right center; }
    .library-link:hover { transform: scale(1.2); }
    .library-link:hover .library-emoji {
      display: inline-block;
      animation: book-wiggle 0.4s ease-in-out;
    }
    @keyframes book-wiggle {
      0% { transform: rotate(0deg); }
      25% { transform: rotate(-8deg); }
      50% { transform: rotate(8deg); }
      75% { transform: rotate(-4deg); }
      100% { transform: rotate(0deg); }
    }
  </style>
</head>
<body style="margin:0; padding:0; background-color:#f5f5f5; font-family:system-ui,-apple-system,'Hiragino Sans','Yu Gothic',sans-serif;">
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0">
    <tr>
      <td align="center" style="padding:20px 10px;">
        <!--[if mso]><table role="presentation" width="800" cellpadding="0" cellspacing="0"><tr><td><![endif]-->
        <table role="presentation" class="email-container" width="800" cellpadding="0" cellspacing="0" style="background:#ffffff; border-radius:8px; overflow:hidden; max-width:800px; width:100%;">

          <!-- ヘッダー -->
          <tr>
            <td style="background:linear-gradient(135deg,#1e3a5f,#2563eb); padding:30px; text-align:center; color:#ffffff;">
              <div style="display:inline-flex; align-items:center; gap:8px;">
                <img src="../../images/apple-touch-icon.png" alt="" width="32" height="32" style="border-radius:6px; width:32px; height:32px;">
                <h1 class="header-title" style="margin:0; font-size:26px; letter-spacing:1px;">AI×DX Weekly</h1>
              </div>
              <p style="margin:8px 0 0; font-size:14px; opacity:0.9;">Vol.XX ｜ YYYY年MM月DD日号</p>
            </td>
          </tr>

          <!-- ============================================ -->
          <!-- ★ 配置順序の厳守ルール ★                      -->
          <!-- ヘッダー直下から始まり、以下の順序で配置する: -->
          <!--   1. 📰 今週のニュース TOP3                    -->
          <!--   2. 🛠️ 今週のおすすめツール                   -->
          <!--   3. 📖 用語解説                              -->
          <!--   4. 💬 編集者コメント                        -->
          <!--   5. 📚 Weeklyライブラリへリンク（フッター直前）-->
          <!--   6. フッター                                  -->
          <!-- 📚リンクは「必ず編集者コメントの後・フッターの前」 -->
          <!-- ヘッダー直下に絶対に置かないこと              -->
          <!-- ============================================ -->

          <!-- ↓ ここに各セクション（ニュース・ツール・用語解説・編集者コメント）を配置 ↓ -->

          <!-- 📚 Weeklyライブラリへのリンク（編集者コメント直後・フッター直前） -->
          <tr>
            <td class="content-cell" style="padding:8px 40px 20px; text-align:right;">
              <a href="../../index.html" class="library-link" style="color:#2563eb; text-decoration:none; font-size:16px; display:inline-block; transition:transform 0.2s;">
                <span class="library-emoji" style="display:inline-block; transition:transform 0.3s;">📚</span> Weeklyライブラリへ
              </a>
            </td>
          </tr>

          <!-- フッター -->
          <!-- ルール: 2行構成で固定。Vol番号・日付・注意書きは含めない -->
          <!-- bgcolor属性はOutlook等グラデーション非対応メーラー向けフォールバック -->
          <tr>
            <td bgcolor="#1e3a5f" style="background:#1e3a5f; background:linear-gradient(135deg,#1e3a5f,#2563eb); padding:24px 40px; text-align:center; color:#ffffff; font-size:13px;">
              <p style="margin:0 0 4px;">AI×DX Weekly ｜ 中小企業のDX推進を応援するニュースレター</p>
              <p style="margin:0; opacity:0.7;">© 2026 AI×DX Weekly. All rights reserved.</p>
            </td>
          </tr>

        </table>
        <!--[if mso]></td></tr></table><![endif]-->
      </td>
    </tr>
  </table>
</body>
</html>
```

**レスポンシブ対応で必ず守ること：**
1. メインテーブル（`.email-container`）には `width="800"` と `style="max-width:800px; width:100%;"` を両方指定する（width属性はメールクライアント用、max-width+width:100%はブラウザ用）
2. コンテンツ領域の `<td>` には `class="content-cell"` を付けて、モバイル時にパディングが16pxに縮む
3. カード内の `<td>` には `class="card-cell"` を付けて、モバイル時にパディングが14pxに縮む
4. `<h2>` セクション見出しには `class="section-heading"` を付与
5. 本文の `<p>` には `class="body-text"` を付与（モバイル時にline-height:1.8で読みやすく）
6. ソースリンクの `<a>` には `class="source-link"` を付与（モバイル時にタップ領域拡大）
7. MSO条件コメント `<!--[if mso]>` でOutlook対応の固定幅テーブルをラップする
8. メディアクエリは「タブレット（681〜840px）」→「スマホ（680px以下）」の順で記述する

**各セクションのHTML：**
- セクション見出しは `<h2>` タグ、アクセントカラーの左ボーダー付き
- ニュース項目はカード風（薄いボーダー + 角丸 + 軽い影）
- リンクはアクセントカラー（#2563eb）で下線付き
- 英語キーワードは `<span style="color:#6b7280; font-size:0.9em;">` で表示

### Step 4: (削除済み)

フローティング戻るボタン（`class="back-btn"`）は2026年4月27日に全Vol号から削除。
末尾の `class="library-link"` リンクとブラウザ標準の戻る機能で十分な導線を確保。

### Step 5: Weeklyライブラリページの更新

新しい号を生成したら、ルートのWeeklyライブラリページも更新する。

**更新ルール：**
1. `<ul class="issue-list">` の先頭（最初の `<li>` の前）に新しい号のエントリを追加する（新しい号が一番上に来る）
2. エントリのフォーマット：

```html
<li>
  <a href="outputs/volX/">
    <span class="vol">Vol.X</span>
    <div class="title">ニュース見出し1 / ニュース見出し2 / ニュース見出し3</div>
    <div class="date">YYYY年MM月DD日号</div>
  </a>
</li>
```

3. 特集号の場合は `<span class="vol">Vol.X 特集号</span>` とし、タイトルに `🎯 特集：` プレフィックスを付ける
4. ニュースレターHTML本体と一緒にWeeklyライブラリページも出力する

**Weeklyライブラリページのテンプレート：** 初回作成時は以下の構造で生成する。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AI×DX Weekly</title>
  <link rel="manifest" href="manifest.json">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: system-ui, -apple-system, 'Hiragino Sans', 'Yu Gothic', sans-serif;
      background: #f5f5f5; color: #333; line-height: 1.7;
    }
    .header {
      background: linear-gradient(135deg, #1e3a5f, #2563eb);
      color: #fff; text-align: center; padding: 48px 20px;
    }
    .header h1 { font-size: 32px; letter-spacing: 1px; }
    .header p { margin-top: 8px; font-size: 16px; opacity: 0.85; }
    .container { max-width: 800px; margin: 0 auto; padding: 32px 20px; }
    h2 {
      font-size: 20px; color: #1e3a5f;
      border-left: 4px solid #2563eb; padding-left: 12px; margin-bottom: 20px;
    }
    .issue-list { list-style: none; }
    .issue-list li {
      background: #fff; border: 1px solid #e5e7eb;
      border-radius: 8px; margin-bottom: 12px; transition: box-shadow 0.2s;
    }
    .issue-list li:hover { box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
    .issue-list a { display: block; padding: 20px 24px; text-decoration: none; color: #333; }
    .issue-list .vol { font-size: 12px; color: #2563eb; font-weight: bold; text-transform: uppercase; }
    .issue-list .title { font-size: 17px; font-weight: bold; color: #1e3a5f; margin-top: 4px; }
    .issue-list .date { font-size: 13px; color: #6b7280; margin-top: 4px; }
    .footer { background: linear-gradient(135deg, #1e3a5f, #2563eb); color: #ffffff; text-align: center; padding: 24px 20px; font-size: 13px; }
    @media (max-width: 680px) {
      .header h1 { font-size: 24px; }
      .container { padding: 20px 16px; }
      .issue-list a { padding: 16px; }
    }
  </style>
</head>
<body>
  <div class="header">
    <h1>🤖 AI×DX Weekly</h1>
    <p>中小企業のDX推進を応援するニュースレター</p>
  </div>
  <div class="container">
    <h2>📚 Weeklyライブラリ</h2>
    <ul class="issue-list">
      <!-- ここに各号のエントリを新しい順に追加 -->
    </ul>
  </div>
  <div class="footer">
    <p style="color: #ffffff; opacity: 0.7;">© 2026 AI×DX Weekly. All rights reserved.</p>
  </div>
</body>
</html>
```

### Step 6: 出力

生成したHTMLを `/mnt/user-data/outputs/` に保存する。

**出力ファイル：**
- ニュースレター本体: `outputs/volX/index.html`（GitHub Pages用のディレクトリ構造）
- Weeklyライブラリページ: `index.html`（新号エントリ追加済み）

保存後、`present_files` ツールでユーザーに提示する。

### Step 7: 号数管理

**号数（Vol.）の管理ルール：**
- ユーザーから号数の指定がなければ、Weeklyライブラリページの最新号数 +1 で自動採番する
- 特集号は同じVol.番号に「特集号」サフィックスを付ける（例: Vol.1 特集号）
- フォルダ名は `vol{数字}`、特集号は `vol{数字}-special` とする

## 🎯 設計思想・判断の根拠

このセクションは「なぜそうなっているか」(Why)を記録する。
仕様(What)はSKILL.md他セクションに、判断根拠(Why)はここに集約することで、
Claude Code が SKILL.md だけで判断・実行できるようにする。

work-log.md は人間用の学習記録として独立しており、
Claude Code は work-log.md を主要参照する必要はない。

---

### 構造順序の不変ルール（Vol.5以降確立 / 2026年5月）

#### ルール本文
ニュースレターの主要要素は、以下の順序で配置する。これは**Vol.5以降固定**であり、
**「より良いUX」「Web標準のベストプラクティス」を理由に変更してはならない**。

| 順序 | 要素 | 配置箇所 |
|-----|------|---------|
| 1 | ヘッダー（タイトル・号数・日付） | 最上部 |
| 2 | 📰 今週のAI×DXニュース TOP3 | ヘッダー直下 |
| 3 | 🛠️ 今週のおすすめツール | ニュース直下 |
| 4 | 📖 用語解説 | ツール直下 |
| 5 | 💬 編集者コメント | 用語解説直下 |
| 6 | 📚 Weeklyライブラリへ リンク | **編集者コメント直後・フッター直前** |
| 7 | フッター | 最下部 |

#### 📚 Weeklyライブラリリンクの配置根拠（Why）
- **読了後の自然な誘導**: 本文を全部読み終えた読者が「他の号も読みたい」と感じる
  タイミングで誘導するため、最下部寄りに配置する
- **ヘッダー直下に置かない理由**: まだ本文を読んでいない読者を別ページに誘導
  してしまうと、本号の読了率が下がる
- **右寄せの根拠**: 主導線（本文）の邪魔をせず、補助的な動線として機能させるため

#### 変更時のルール
この順序を変更する必要がある場合は、**必ずユーザー（編集責任者）の事前承認**を
取ること。Claude Code側の判断で「より良い」と思っても変更しない。

---

### ヘッダー・フッターのグラデーション

**仕様**: `linear-gradient(135deg, #1e3a5f, #2563eb)`

**なぜグラデーション**:
- 紺一色だと単調で重い印象
- ヘッダーとフッターを同デザインにすることで「枠」として機能
- 中身の本文を視覚的に挟み込み、読みやすさを向上

**色の意味**:
- `#1e3a5f`(紺): 信頼感・公的な印象
- `#2563eb`(青): クリエイティブ・革新性
- 組み合わせで「信頼できるDX情報」というブランドを表現

**メール配信対応**:
- `bgcolor="#1e3a5f"` 属性 + `background:#1e3a5f` + `linear-gradient` の3層構造
- Outlook等の非対応メーラーには単色 `#1e3a5f` でフォールバック
- 詳細はフッター仕様セクション参照

---

### ニュースカードのカラーパターン (Vol.4基準)

**仕様**: NEWS 01〜03 を3色で配置(寒色→暖色のグラデーション)

| カード | background | border | 配置の意図 |
|-------|-----------|--------|----------|
| NEWS 01 | `#f0f6ff` | `#bfdbfe` | 薄青 ─ 公的・信頼度高(補助金、行政、公式発表) |
| NEWS 02 | `#f0fdf4` | `#bbf7d0` | 薄緑 ─ 革新・新鮮(新製品、新機能、AI技術) |
| NEWS 03 | `#fefce8` | `#fde68a` | 薄黄 ─ 注目・温かみ(成功事例、ストーリー) |

**なぜ色分け**:
- 同色だと3つのニュースが視覚的に区別できない
- 読者がスクロール中に「今どのニュースか」即座に分かる
- 特にモバイル表示で効果が大きい(画面が小さく区切りが見えにくい)

**なぜ寒色→暖色**:
- 視線を自然に上から下へ誘導
- 最後を温かみのある黄色で締めることで、
  編集者コメント(同じ黄系)への視覚的繋がりを作る

**色彩心理学的な根拠**:
- 青=信頼、緑=新鮮、黄=注目 という直感的な意味づけ
- 内容と色が自然にマッチ(補助金は青、新技術は緑、事例は黄)

**Vol.5以降も継承**:
- 上記3色のカラーパターンを Vol.5 以降のニュース3本にも適用
- ニュースの内容と色をマッチングさせる

**NEWS番号ラベルの仕様**:
- スタイル: `color:#6b7280; font-size:12px; font-weight:600; letter-spacing:0.5px;`
- 「NEWS 01」「NEWS 02」「NEWS 03」と全角大文字英字で記載

---

### ツールカードのデザイン

**仕様**:
```css
background: #ffffff;
border: 1px solid #e5e7eb;
box-shadow: 0 1px 4px rgba(0,0,0,0.06);
```

TOOLラベル(青タグ): `background:#2563eb; color:#fff; font-size:11px; font-weight:700; padding:2px 8px; border-radius:4px; letter-spacing:0.5px;`

**なぜ白カード**:
- ニュース(色付きカード)とは異なる質感で「情報の種類が違う」を表現
- 白は中立的・実用的な印象でツール紹介に最適

**なぜ box-shadow を控えめに(0.06)**:
- 強い影は古臭い印象になる
- `0.06` という極めて控えめな値で、上品な「浮き上がり感」を演出

**なぜラベルが青タグ**:
- ニュースカードと違って、ツールは行動(導入検討)を促す
- 青は信頼+クリック誘導の色として機能

---

### 用語解説の薄紫

**仕様**: `background:#faf5ff`, `border:1px solid #e9d5ff`

**なぜ紫**:
- 紫は伝統的に「学習・知性・思索」を象徴する色
- 用語解説セクション(=学びの場)の役割と完全にマッチ
- 他のセクション(青/緑/黄/白)と被らないので視覚的独立性が高い

---

### 用語解説「一言でいうと」の紫文字

**仕様**: `color:#7c3aed; font-weight:600; font-size:14px;`

**配置**: 用語名(h3)の直後、詳細説明(p)の前

**なぜこのスタイル**:
- 用語解説カードの薄紫背景(`#faf5ff`)と調和する濃紫
- 「ここは要点」という視覚的サイン
- 読者がここだけ読んでも用語の本質を理解できる設計

**HTML例**:
```html
<p style="margin:0 0 14px; font-size:14px; color:#7c3aed; font-weight:600;">
  一言でいうと：「{用語の本質を1文で}」
</p>
```

---

### 編集者コメントの黄色(NEWS 03と同色)

**仕様**: `background:#fefce8`, `border:1px solid #fde68a`

**なぜNEWS 03と同色**:
- 黄色は人間味・温かみを表現する色
- ストーリー(NEWS 03)と編集者の感想で同じ黄色を使うことで
  「最後は人間味のある内容で締まる」という設計思想を表現
- 読者に良い後味を残す

---

### 来週予告の文字色

**仕様**: `color:#92400e; font-size:14px;` (classなし、styleで直接指定)

**フォーマット**: 📌で始まり、「〜お届け予定です。お楽しみに！」で終わる

**なぜこの色**:
- 編集者コメントカードの黄色背景(`#fefce8`)に対して
  読みやすいコントラストを確保
- 黄色背景に明るい文字色だと読めないので、濃いオレンジブラウンを選択
- 「📌」絵文字との視覚的調和も良い

**HTML例**:
```html
<p style="margin:0; font-size:14px; color:#92400e;">📌 来週は{予告内容}お届け予定です。お楽しみに！</p>
```

---

### 全体の「色のジャーニー」

```
紺グラデ(ヘッダー)
   ↓
薄青(NEWS 01) ← 公的・信頼
   ↓
薄緑(NEWS 02) ← 革新
   ↓
薄黄(NEWS 03) ← 実例
   ↓
白(TOOL 01-02) ← 具体的ツール
   ↓
薄紫(用語解説) ← 学習
   ↓
薄黄(編集者) ← 人間味
   ↓
紺グラデ(フッター)
```

**設計の核心**:
- ヘッダーとフッターを紺グラデで挟む(枠としての機能)
- 中身は寒色→暖色のグラデーション(視線誘導)
- すべてパステル(明度・彩度抑制)で統一(ビジネス文書としての上品さ)

---

### テキスト色の体系

ニュースレター全体で使用するテキスト色の標準仕様。

| 用途 | 色コード | 例 |
|------|---------|-----|
| 本文(body-text) | `#374151` | 各カード内の説明文 |
| 見出し(h2, h3) | `#1e3a5f` | ブランドの紺色、信頼感 |
| 補足テキスト | `#6b7280` | NEWS番号ラベル、英訳キーワード |
| リンク・アクセント | `#2563eb` | 出典リンク、library-link |
| ヘッダー/フッター文字 | `#ffffff` | グラデ背景上の白文字 |

**設計思想**:
- 本文の `#374151` は純黒(`#000`)より柔らかく、長文でも目が疲れにくい
- 見出しの `#1e3a5f`(ブランド紺)で全セクションを縫い合わせる統一感
- 補足の `#6b7280` は本文よりトーンを落とし、視覚的階層を作る

**例外色**(特定用途のみ):
- `#7c3aed`(濃紫): 用語解説「一言でいうと」のみ
- `#92400e`(オレンジブラウン): 来週予告のみ
- これらは**それぞれの背景色との読みやすさ**を計算した固有の色

---

### フローティング戻るボタンを採用しない理由 (Phase 16)

**経緯**: Vol.1〜4まで画面右下にフローティング戻るボタンを配置していたが、
Phase 16 で全Vol号から削除した。

**なぜ削除**:
- 戻る導線が3つあった(ブラウザ戻る、末尾library-link、フローティング)
- 機能の重複は認知負荷を高める
- モバイルで本文の最後の行と被って読みにくい
- メール配信時に position:fixed が動作不安定

**現在の戻る導線(2層)**:
1. ブラウザの戻るボタン(標準UI、削除不可)
2. 記事末尾の「📚 Weeklyライブラリへ」リンク(library-link)

**Vol.5以降への指示**:
- フローティング戻るボタンは追加しない
- library-link は記事末尾(編集者コメント直後、フッター直前)に配置する

---

### レスポンシブ対応の設計思想

**3段階対応**: PC(841px〜) / タブレット(681〜840px) / スマホ(〜680px)

**なぜテーブルレイアウト**:
- メールクライアント互換性のため(Outlookなど)
- メディアクエリと併用してブラウザでも適切に表示

**なぜ最大幅800px**:
- 1行あたり45〜48文字(日本語)が最も読みやすい
- 1000px以上だと目が行を追いにくくなる(視線移動の負荷増)

---

### library-link のホバー効果

**仕様**: ホバー時に `transform: scale(1.2)` + 📚絵文字の `book-wiggle` アニメーション

**なぜホバー効果**:
- 楽しさ・遊び心を演出(堅すぎないニュースレターの個性)
- メール配信時はホバーが効かないだけで表示は崩れない設計

**なぜ右端基点**:
- `transform-origin: right center` で右寄せ配置と整合
- 拡大時に左方向に広がるので、画面端にはみ出さない

**font-size**: `16px`(微調整済み、Phase 13の㊶で14px→16px変更)

**末尾**: 「📚 Weeklyライブラリへ」(末尾の「→」は不要、Phase 13で削除)

## manifest.json の管理ルール

プロジェクトルート（`index.html` と同じ階層）に `manifest.json` を1つ配置する。

**設定値（変更しないこと）：**
```json
{
  "name": "AI×DX Weekly",
  "short_name": "AI×DX Weekly",
  "description": "中小企業のDX推進を応援するニュースレター",
  "start_url": "/weekly-newsletter/",
  "display": "standalone",
  "background_color": "#f5f5f5",
  "theme_color": "#1e3a5f",
  "icons": [
    { "src": "images/apple-touch-icon.png", "sizes": "180x180", "type": "image/png" },
    { "src": "images/favicon.ico", "sizes": "any", "type": "image/x-icon" }
  ]
}
```

**`<link rel="manifest">` のパス：**
- ルート `index.html` → `href="manifest.json"`
- 各号 `outputs/volX/index.html` → `href="../../manifest.json"`

**新号追加時の確認事項：**
- `<head>` に `<link rel="manifest" href="../../manifest.json">` が含まれているか（テンプレートには既に記載済み）
- `manifest.json` 自体は変更不要

---

## ユーザーへの確認ポイント

生成前に、以下をユーザーに確認する（指定がなければデフォルトで進める）：

- **号数**（Vol.XX）：指定がなければ直前の号数 +1 で自動採番
- **特集テーマ**：指定があればそのテーマを重点的にカバー
- **除外トピック**：「この話題は入れないで」という指定があれば対応

## 品質チェックリスト

HTMLを出力する前に、以下を確認する：

- [ ] ニュースは3件あるか
- [ ] 各ニュースに出典リンクがあるか
- [ ] ツール紹介は2件あるか
- [ ] 用語解説が1つあるか
- [ ] 編集者コラムがあるか
- [ ] 英語キーワードが各所に併記されているか
- [ ] HTMLがメールクライアントで崩れない構造か（テーブルレイアウト使用）
- [ ] 著作権に配慮し、要約は独自の言葉で書かれているか
- [ ] Weeklyライブラリページに新号エントリが追加されているか
- [ ] レスポンシブ用のclass属性（content-cell, card-cell, section-heading, body-text, source-link）が全要素に付与されているか
- [ ] フッターの `<td>` に `bgcolor="#1e3a5f"` 属性と `background:linear-gradient(135deg,#1e3a5f,#2563eb)` が設定されているか（Outlook等メーラー向けフォールバック含む）
- [ ] **【構造順序】** 以下の順序で `<tr>` ブロックが配置されているか:
      ① ヘッダー → ② 📰 ニュースTOP3 → ③ 🛠️ ツール → ④ 📖 用語解説
      → ⑤ 💬 編集者コメント → ⑥ 📚 Weeklyライブラリへリンク → ⑦ フッター
- [ ] **【📚 リンク位置】** Weeklyライブラリへのリンクが
      「編集者コメントの直後・フッターの直前」に配置されているか
      （ヘッダー直下にあったらNG）
- [ ] **【前号との構造比較】** 前号（Vol.N-1）と同じセクション順序か
      （diffで比較し、構造の差異がないことを確認）

## フッター仕様（デザイン統一ルール）

- フッター背景はヘッダーと同じグラデーション `linear-gradient(135deg,#1e3a5f,#2563eb)` を使用する
- メール配信対応として、Outlook等グラデーション非対応メーラー向けに以下の3つを併記する:
  1. `bgcolor="#1e3a5f"` 属性（HTML属性フォールバック）
  2. `background:#1e3a5f` インラインスタイル（CSS フォールバック単色）
  3. `background:linear-gradient(135deg,#1e3a5f,#2563eb)` インラインスタイル（対応ブラウザ用グラデーション）
- 今後新規作成するVol号も同じフッター仕様を踏襲する
- padding/text-align/color/font-size 等の他プロパティはVol号ごとの値を維持する
