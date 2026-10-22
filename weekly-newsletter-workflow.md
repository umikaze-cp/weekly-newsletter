# 📋 AI×DX Weekly ニュースレター — 毎週月曜日の作業プロセス

週刊ニュースレターを発行するときの、作業の順番を示す手順書。仕様は書かない。
手順書と正本が食い違っていたら、正本が優先する。

| 知りたいこと | 正本 |
|---|---|
| ニュースレターの仕様（構成・文体・出典・品質チェック） | `SKILL.md` |
| ファイルの役割・Git 運用・作業終了時にやること | `CLAUDE.md` |
| 発行前監査の範囲と判定基準 | `docs/pre-publish-audit-prompt.md` |
| 現状・残課題・ナレッジ差し替えのタイミング | `docs/aidx-weekly-progress.md` |

---

## 作業全体フロー図

```
Step 0  準備
  ↓
Step 1  制作を指示する（2段階）
  段階1  Claude Code が候補を報告して STOP  ← 人が確認・判断
  段階2  Claude Code が本文・台帳・sitemap・README・work-log・進捗表・レポートまで作成
  ↓
Step 2  生成物の確認・修正
  ↓
Step 3  ブラウザプレビュー（手動）
  ↓
Step 4  発行前監査（Claude Code）
  ↓
Step 5  Git commit & push（Sourcetree）
  ↓
Step 6  GitHub Pages で公開確認（手動）
  ↓
Step 7  発行後のインデックス登録・ナレッジ更新（手動）
```

---

## Step 0：準備

**使用：Claude Code**

VSCodeのターミナルを開き、プロジェクトフォルダにいることを確認する。

```bash
cd ~/weekly-newsletter
```

Claude Codeを起動する。

```bash
claude
```

MCP接続を確認する。

```
/mcp
```

`exa · ✓ connected` を確認。failedの場合はClaude Codeを再起動する。

---

## Step 1：制作を指示する（2段階）

**使用：Claude Code**（Exa MCP が必要）

ルートの `prompt.md` を、その号用に書き換えて Claude Code に渡す。`prompt.md` は git 管理外（`.gitignore`）のローカルファイル。前号のものをコピーして、下の「毎週書き換える箇所」だけを直す。

### 指示の例（Vol.30：2026年10月26日号）

```
【Vol.30 制作：2026年10月26日号】

CLAUDE.md と SKILL.md に従って、AI×DX Weekly Vol.30 を制作してください。

■ この号の指定（SKILL.md「ユーザーへの確認ポイント」への回答）
- 号数：Vol.30（フォルダ：outputs/vol30/）
- 日付：2026年10月26日号
- 特集テーマ：なし
- 除外トピック：なし

■ ニュースの対象期間
- SKILL.md Step 2 セクション1「ニュースの対象期間」に従う。
  Vol.30 の対象期間は 2026年10月20日〜10月26日（前号 Vol.29 の発行日の翌日〜今号の発行日）
- 一次情報で発表日が確認できない候補は、期間内と判定せず、段階1の報告で私に確認する
- 期間外の例外を使うかどうかは私が決める。Claude Code の判断で採用しない

■ 進め方（2段階）
段階1：SKILL.md の Step 1（トピック収集）まで行い、STOP する。
  NEWS TOP3 の候補と次点2件について、それぞれ次を報告する
  - 見出し案
  - 一次情報の URL（英語ページは「（英語）」と付記）と、一次情報に書かれた発表日
  - 対象期間内か、期間外の例外の候補か（例外の候補の場合は3条件それぞれの根拠）
  - 出典の型（SKILL.md「出典の多様性ルール」の分類）
  - 選定理由（1〜2文）
  統計・調査型／制度・政策型が期間内に見つからない場合は、その旨と実行したクエリを書く。
  報告は ~/Downloads/vol30-stage1.md に保存する。
  私が「進めて」と返したら段階2へ進む。差し替えの指示があればそれに従う。

段階2：SKILL.md の Step 2〜7 を行う。
  - NEWS TOP3 の本文を先に確定させ、その本文を受けて TOOL・用語解説・編集者コメント・キャッチコピー・📌行を書く
  - 見出し・イントロ・文体は SKILL.md Step 2 の該当規定に従う
  - TOOL・用語解説は台帳で重複を確認し、確定した段階で両台帳に追記する
  - 保存先は outputs/vol30/index.html とルートの index.html。
    SKILL.md Step 6 の「/mnt/user-data/outputs/」と「present_files」は claude.ai 用の記述のため適用しない
  - sitemap.xml は SKILL.md Step 5「sitemap.xml の更新ルール」に従って更新する

■ 作業終了時
- CLAUDE.md の「作業終了時の必須アクション」に従う。work-log.md への記録は、直近の Phase 番号の次の番号とする
- 品質チェックリストの自己採点・NEWS ごとの一次情報 URL と発表日・変更ファイル一覧（git diff --stat）・推奨コミットメッセージを
  ~/Downloads/vol30-report.md にまとめる
- git の書き込み操作（add / commit / push など）は行わない
```

### 毎週書き換える箇所

| 箇所 | Vol.30 の例 | 決め方 |
|---|---|---|
| 号数・フォルダ | Vol.30 ／ outputs/vol30/ | 直前の号数 +1（SKILL.md「ユーザーへの確認ポイント」） |
| 日付 | 2026年10月26日号 | 発行する月曜日 |
| 対象期間 | 2026年10月20日〜10月26日 | 前号の発行日の翌日〜今号の発行日。休刊明けは延びる（SKILL.md Step 2 セクション1「ニュースの対象期間」） |
| 特集テーマ・除外トピック | なし | 指定があれば書く |
| 報告ファイル名 | vol30-stage1.md ／ vol30-report.md | 号数に書き換える |
| work-log の Phase | 直近の Phase の次 | work-log.md の末尾で確認する |

### 段階1：候補の確認（人の作業）

Claude Code が STOP したら、`~/Downloads/vol30-stage1.md` を読んで次を決め、返信する。

- NEWS の候補を差し替えるか
- 期間外の例外を使うか（使うかどうかは人が決める。条件は SKILL.md Step 2 セクション1「ニュースの対象期間」の「期間外の例外」）
- 発表日が確認できなかった候補の扱い

「進めて」と返すと段階2に進む。

### 段階2：制作（Claude Code）

SKILL.md の Step 2〜7 と、CLAUDE.md の「作業終了時の必須アクション」まで進む。
work-log.md・README.md・進捗表（docs/aidx-weekly-progress.md）の更新も段階2に含まれる。
何を作ったか・何を変更したかは `~/Downloads/vol30-report.md` に出る。

---

## Step 2：生成物の確認・修正

**使用：VSCode と Claude Code**

VSCodeのエクスプローラーで `outputs/volX/index.html` を開く。

### 確認ポイント

チェック項目の正本は SKILL.md の「品質チェックリスト」。Claude Code が段階2の終わりに自己採点した
`~/Downloads/volX-report.md` を読み、次を確認する。

- 自己採点の結果と【対象期間】の発表日一覧を読む。✅ の項目は、気になるものを抜き取って本文と照らす
- `prompt.md` で指定した内容（特集テーマ・除外トピック・対象期間）が反映されているか
- 運営者名が CLAUDE.md の「公開してよい識別情報（筆名）」の筆名になっているか
- 出典リンクの確認（リンク切れ・NG ドメイン・裏づけ）は Step 4 の監査で行う

### 修正が必要な場合

エディタで該当箇所を選択し、Claude Code に修正を依頼する。

```
選択した箇所のニュース要約をもう少し具体的にして
```

```
このツール紹介に料金情報が抜けているので追加して
```

### ルートの index.html と README.md も確認

Weeklyライブラリページ（`index.html`）を開き、新号のエントリが正しく追加されているか確認する。

- Vol.番号が正しいか
- タイトル（ニュース見出し3本）が反映されているか
- 日付が正しいか
- リンク先 `outputs/volX/` が正しいか
- README.md の「発行履歴」と「公開URL」に新号が追加され、見出しが index.html のタイトルと同じ文言か

### sitemap.xml も確認

新号の URL 追加とトップページの lastmod 更新が済んでいるか確認する（書式・lastmod の決め方は SKILL.md Step 5「sitemap.xml の更新ルール」参照）。
これはファイル自体の更新で、Step 7 の Search Console の作業（再送信やリクエスト）とは別。

---

## Step 3：ブラウザプレビュー

**使用：手動操作**

VSCodeの `outputs/volX/index.html` を右クリック → 「Live Serverで開く」 
または、ターミナルで以下を実行：

```bash
open outputs/volX/index.html
```

### 確認ポイント

- PC表示（通常幅）でレイアウトが崩れていないか
- ブラウザのデベロッパーツール（F12）でスマホ表示を確認
- 末尾の「📚 Weeklyライブラリへ」リンク（library-link）から `index.html` に戻れるか
- リンクが正しく開くか

---

## Step 4：発行前監査

**使用：Claude Code**

ブラウザプレビューが終わったら、`docs/pre-publish-audit-prompt.md` の内容をそのまま Claude Code に貼り付けて実行する。
監査の範囲（構造・出典・リンク疎通・注記と母数など）と GO / NO-GO の判定基準は、同ファイルが正本。

### 監査レポートの見方

| 判定 | 対応 |
|-----|------|
| ✅ GO | 次の Step へ進む |
| ⛔ NO-GO | Claude Code が提示する修正案を確認して承認する。修正後に、もう一度監査を実行する |

発行の可否に影響しない「参考情報」の項目は、内容を読み、必要なら修正を依頼する。

---

## Step 5：Git commit & push

**使用：Sourcetree**（運営者の通常ワークフロー：VSCode → Sourcetree → GitHub）

### 5-1. Sourcetreeを開く

weekly-newsletter リポジトリを開くと、変更されたファイルが「作業ツリーのファイル」に表示される。

### 5-2. 変更内容の差分を確認

Claude Code が段階2の終わりに出した変更ファイル一覧（`~/Downloads/volX-report.md`）と、
Sourcetree の「作業ツリーのファイル」が一致しているか確認する。
差分（diff）を見て、意図しない変更がないかチェックする。

### 5-3. ステージに上げる

コミットの分け方は、CLAUDE.md の「Git 運用ルール」に従う。
Claude Code が提示した「推奨コミットメッセージ」の単位で、ステージに上げる。

### 5-4. コミット

Claude Code が提示したコミットメッセージ案を使う。次を確認する。

- 形式が「種類(対象): 内容」になっているか（CLAUDE.md「Git 運用ルール」）
- `Claude-Session:` の行が入っていたら削除する
- Claude Code から「作者情報が筆名と一致しない」という報告があった場合は、コミット前に設定を直す

### 5-5. プッシュ

「プッシュ」ボタンで `origin/master` にプッシュ。

---

## Step 6：GitHub Pages で公開確認

**使用：手動操作**

push後、1〜2分待ってからGitHub PagesのURL（独自ドメイン）にアクセスして確認する。

```
https://www.aidx-weekly.com/
```

- Weeklyライブラリに新号が表示されているか
- 新号をクリックして正しく表示されるか
- 記事末尾の「📚 Weeklyライブラリへ」リンクでWeeklyライブラリに戻れるか

---

## Step 7：発行後のインデックス登録・ナレッジ更新

**使用：手動操作**

Step 6の公開確認が済んだら、検索エンジンへの反映申請とプロジェクトナレッジの更新を行う。

### 7-1. Search Console でインデックス登録をリクエスト

Google Search Console を開き、URL検査に発行した号のURLを入力する。

```
https://www.aidx-weekly.com/outputs/volX/
```

検査結果の画面から「インデックス登録をリクエスト」を実行する。

**sitemap.xml の再送信は不要**（ファイル自体の更新は Step 2 で済ませておく）。送信済みのサイトマップは同じURLをGoogleが定期的に再取得するため、中身（新号のURL追加）は自動で反映される。再送信が必要なのは、サイトマップファイル自体のURL（置き場所）を変更したときだけ。

数日後、「サイトマップ」メニューで検出URL数が増えているかを確認できる。

### 7-2. プロジェクトナレッジの差し替え

差し替え対象・タイミング・手順は、`docs/aidx-weekly-progress.md` の「プロジェクトナレッジの差し替えタイミング」に従う。

---

## 作業プロセスのまとめ表

| Step | 作業内容 | 使用ツール |
|------|---------|-----------|
| 0 | 準備・MCP確認 | Claude Code |
| 1 | 制作を指示する（2段階） | Claude Code |
| 2 | 生成物の確認・修正 | VSCode・Claude Code |
| 3 | ブラウザプレビュー | 手動 |
| 4 | 発行前監査 | Claude Code |
| 5 | Git commit & push | Sourcetree |
| 6 | GitHub Pages 公開確認 | 手動 |
| 7 | 発行後のインデックス登録・ナレッジ更新 | 手動 |

---

## トラブルシューティング

### Exa MCPが「failed」になる場合

```bash
# Claude Codeを終了してから
npm cache clean --force
# 再度 claude を起動
claude
```

### 号数が重複した場合

Claude Code に以下を確認する：

```
index.htmlのWeeklyライブラリで最新のVol.番号を教えて
```

### 生成されたHTMLの品質が低い場合

Claude Code に追加で指示する：

```
Vol.Xのニュース1番目をもっと中小企業目線で書き直して
```
