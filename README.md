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

- **バックナンバー一覧**: [index.html](index.html)
- [Vol.3 — Microsoft対日投資 / Gemma 4 / 補助金2026](outputs/vol3/)（2026年4月13日号）
- [Vol.2 — Japan DX Week 春 / 関西DX戦略 / 補助金申請準備](outputs/vol2/)（2026年4月6日号）
- [Vol.1 特集 — 生成AIの業務活用](outputs/vol1-special/)（2026年4月3日号）
- [Vol.1 — 創刊号](outputs/vol1/)（2026年4月3日号）

## 📁 プロジェクト構成

```
weekly-newsletter/
├── README.md              ← このファイル
├── SKILL.md               ← Claudeスキル本体
├── index.html             ← バックナンバー一覧ページ
├── work-log.md            ← 作業ログ・学習メモ
├── .gitignore
├── evals/
│   └── evals.json         ← テストケース定義
└── outputs/               ← 生成したニュースレター
    ├── vol1/
    │   └── index.html     ← Vol.1 創刊号
    ├── vol1-special/
    │   └── index.html     ← Vol.1 特集号
    ├── vol2/
    │   └── index.html     ← Vol.2
    └── vol3/
        └── index.html     ← Vol.3
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
- **コンテンツ生成**: Claude Opus 4.6 + Web検索

## 📊 発行履歴

| 号数 | 発行日 | テーマ |
|------|--------|--------|
| Vol.1 | 2026/04/03 | 創刊号（大阪市×日立AIエージェント / AWS自律型エージェント / 補助金） |
| Vol.1特集 | 2026/04/03 | 生成AIの業務活用（パナソニック44.8万時間削減） |
| Vol.2 | 2026/04/06 | Japan DX Week春 / 関西DX戦略Next / 補助金申請準備 |
| Vol.3 | 2026/04/13 | Microsoft 1.6兆円対日投資 / Gemma 4 / 補助金2026 |

## 📝 作成者

大井琉誠 — [株式会社EDIX AI×Webクリエイター養成科 在籍]
