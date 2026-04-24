# 🤖 AI×DX Weekly

中小企業のDX担当者・経営層向け、AI×DXトレンドの週刊ニュースレター。

## 📰 概要

Web検索で最新のAI×DXニュースを収集し、HTMLニュースレターを自動生成するClaudeスキルのプロジェクトです。

**4セクション構成：**
1. 📰 今週のAI×DXニュース TOP3
2. 🛠️ おすすめツール・リソース紹介
3. 📖 用語解説・学習コーナー
4. 💬 編集者コメント・コラム

## 🌐 公開URL（GitHub Pages）

- **Weeklyライブラリ**: [index.html](index.html)
- [Vol.3 — Microsoft対日投資 / Gemma 4 / 補助金2026](outputs/vol3/)（2026年4月13日号）
- [Vol.2 — Japan DX Week 春 / 関西DX戦略 / 補助金申請準備](outputs/vol2/)（2026年4月6日号）
- [Vol.1 特集 — 生成AIの業務活用](outputs/vol1-special/)（2026年4月3日号）
- [Vol.1 — 創刊号](outputs/vol1/)（2026年4月3日号）

## 📁 プロジェクト構成

```
weekly-newsletter/
├── README.md                          ← このファイル
├── SKILL.md                           ← Claudeスキル本体
├── weekly-newsletter.skill            ← スキル登録カード
├── weekly-newsletter-workflow.md      ← 毎週月曜日の作業プロセス
├── index.html                         ← Weeklyライブラリページ
├── work-log.md                        ← 作業ログ・学習メモ
├── .gitignore
├── images/
│   ├── apple-touch-icon.png
│   └── favicon.ico
├── evals/
│   └── evals.json                     ← テストケース定義
└── outputs/                           ← 生成したニュースレター
    ├── vol1/
    │   └── index.html                 ← Vol.1 創刊号
    ├── vol1-special/
    │   └── index.html                 ← Vol.1 特集号
    ├── vol2/
    │   └── index.html                 ← Vol.2
    └── vol3/
        └── index.html                 ← Vol.3
```

## 📱 レスポンシブ対応

| デバイス | 画面幅 | コンテナ幅 | 本文サイズ |
|---------|--------|-----------|-----------|
| PC | 841px〜 | 800px固定 | 15px |
| タブレット | 681〜840px | 画面の94% | 15px |
| スマホ | 〜680px | 画面の100% | 14px |

## 🛠️ 技術スタック

- **HTML**: テーブルレイアウト（メールクライアント互換）
- **CSS**: メディアクエリによるレスポンシブ対応
- **ホスティング**: GitHub Pages
- **コンテンツ生成**: Claude Sonnet 4.6（Claude Code CLI v2.1.114）
- **Web検索**: Exa MCP Server（セマンティック検索 + 記事本文取得）
- **バージョン管理**: Git（Sourcetree）

## 💻 開発環境

| 項目 | 内容 |
|------|------|
| PC | MacBook Pro 13-inch 2017（Intel Core i5） |
| OS | macOS Ventura 13.7.8 |
| エディタ | Visual Studio Code |
| Node.js | v24.15.0（LTS） |
| npm | v11.12.1 |
| Claude Code | v2.1.114（CLI版） |
| MCP | Exa MCP Server（exa-mcp-server via npx） |
| Git GUI | Sourcetree |

## 🔄 毎週の作業フロー

詳細は [weekly-newsletter-workflow.md](weekly-newsletter-workflow.md) を参照。

```
Step 0  準備・MCP確認（ターミナル版）
  ↓
Step 1  ニュースレター生成指示（ターミナル版 + Exa MCP）
  ↓
Step 2  生成物の確認・修正（拡張機能版）
  ↓
Step 3  ブラウザプレビュー（手動）
  ↓
Step 4  Git commit & push（Sourcetree）
  ↓
Step 5  GitHub Pages 公開確認（手動）
  ↓
Step 6  作業記録の更新（拡張機能版）
```

## 📊 発行履歴

| 号数 | 発行日 | テーマ |
|------|--------|--------|
| Vol.1 | 2026/04/03 | 創刊号（大阪市×日立AIエージェント / AWS自律型エージェント / 補助金） |
| Vol.1特集 | 2026/04/03 | 生成AIの業務活用（パナソニック44.8万時間削減） |
| Vol.2 | 2026/04/06 | Japan DX Week春 / 関西DX戦略Next / 補助金申請準備 |
| Vol.3 | 2026/04/13 | Microsoft 1.6兆円対日投資 / Gemma 4 / 補助金2026 |

## 📝 作成者

大井琉誠 — [株式会社EDIX AI×Webクリエイター養成科 在籍]
