---
name: weekly-newsletter
description: AI×DXトレンドの週刊ニュースレターをHTML形式で自動生成するスキル。Web検索で最新ニュースを収集し、中小企業のDX担当者・経営層向けにわかりやすくまとめる。ニュースレター、メルマガ、週報、AI最新情報まとめ、DXニュース、トレンドレポートなどのキーワードが出たら必ずこのスキルを使う。「今週のAIニュースをまとめて」「DXの最新動向をレターにして」「メール配信用のニュースレターを作って」のような依頼にも対応する。
---

# Weekly AI×DX Newsletter Skill

中小企業のDX担当者・経営層向けに、AI×DXトレンドの週刊ニュースレターをHTML形式で生成するスキル。

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
  <title>AI×DX Weekly - Vol.XX（YYYY年MM月DD日号）</title>
  <style>
    /* ======================
       タブレット対応（681px〜840px）
       iPad縦向き768px をカバー
       ====================== */
    @media only screen and (min-width: 681px) and (max-width: 840px) {
      /* コンテナを画面幅の94%に広げる */
      .email-container {
        width: 94% !important;
        max-width: 800px !important;
      }
      /* 本文エリアのパディングをやや広めに */
      .content-cell {
        padding-left: 28px !important;
        padding-right: 28px !important;
      }
      /* カード内のパディング調整 */
      .card-cell {
        padding: 18px 20px !important;
      }
      /* 本文テキストをやや大きめに（タブレットの閲覧距離に最適化） */
      .body-text {
        font-size: 15px !important;
        line-height: 1.8 !important;
      }
      /* ヘッダータイトルを少し大きく */
      .header-title {
        font-size: 28px !important;
      }
      /* セクション見出しを少し大きく */
      .section-heading {
        font-size: 21px !important;
      }
    }

    /* ======================
       スマートフォン対応（680px以下）
       iPhone / Android をカバー
       ====================== */
    @media only screen and (max-width: 680px) {
      /* メインコンテナを画面幅に追従させる */
      .email-container {
        width: 100% !important;
        max-width: 100% !important;
      }
      /* ヘッダーのフォントサイズ調整 */
      .header-title {
        font-size: 22px !important;
      }
      /* 本文エリアのパディングを狭める */
      .content-cell {
        padding-left: 16px !important;
        padding-right: 16px !important;
      }
      /* ニュースカードの内側パディング調整 */
      .card-cell {
        padding: 14px 14px !important;
      }
      /* セクション見出しのサイズ調整 */
      .section-heading {
        font-size: 18px !important;
      }
      /* 本文テキストの読みやすさ確保 */
      .body-text {
        font-size: 14px !important;
        line-height: 1.8 !important;
      }
      /* リンクのタップ領域確保 */
      .source-link {
        display: inline-block !important;
        padding: 4px 0 !important;
      }
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
              <h1 class="header-title" style="margin:0; font-size:26px; letter-spacing:1px;">🤖 AI×DX Weekly</h1>
              <p style="margin:8px 0 0; font-size:14px; opacity:0.9;">Vol.XX ｜ YYYY年MM月DD日号</p>
            </td>
          </tr>

          <!-- 各セクションをここに配置 -->
          <!-- 各 <td> に class="content-cell" を付与 -->
          <!-- 各カード内 <td> に class="card-cell" を付与 -->
          <!-- 各 <h2> に class="section-heading" を付与 -->
          <!-- 各本文 <p> に class="body-text" を付与 -->
          <!-- 各ソースリンク <a> に class="source-link" を付与 -->

          <!-- フッター -->
          <tr>
            <td style="background:#1e3a5f; padding:20px; text-align:center; color:#ffffff; font-size:12px;">
              <p style="margin:0;">AI×DX Weekly ｜ 中小企業のDX推進を応援するニュースレター</p>
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
8. メディアクエリは「タブレット（681〜840px）」→「スマホ（680px以下）」の順で記述する。タブレット用ではコンテナ幅を94%・最大800pxに広げ、フォントサイズをPC版よりやや大きく（本文15px、見出し21px、タイトル28px）して閲覧距離に最適化する。iPad横向き（1024px）以上ではPC表示（800px固定）がそのまま適用される

**各セクションのHTML：**
- セクション見出しは `<h2>` タグ、アクセントカラーの左ボーダー付き
- ニュース項目はカード風（薄いボーダー + 角丸 + 軽い影）
- リンクはアクセントカラー（#2563eb）で下線付き
- 英語キーワードは `<span style="color:#6b7280; font-size:0.9em;">` で表示

### Step 4: 出力

生成したHTMLを `/mnt/user-data/outputs/` に保存する。

ファイル名: `ai-dx-weekly-vol{号数}-{YYYYMMDD}.html`

保存後、`present_files` ツールでユーザーに提示する。

## ユーザーへの確認ポイント

生成前に、以下をユーザーに確認する（指定がなければデフォルトで進める）：

- **号数**（Vol.XX）：指定がなければ「Vol.1」から開始
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
