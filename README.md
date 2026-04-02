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

- [Vol.1 — 創刊号](outputs/vol1/)
- [Vol.1 特集 — 生成AIの業務活用](outputs/vol1-special/)
- [Vol.5](outputs/vol5/)

## 📁 プロジェクト構成

```
weekly-newsletter/
├── README.md              ← このファイル
├── SKILL.md               ← Claudeスキル本体
├── work-log.md            ← 作業ログ・学習メモ
├── .gitignore
├── evals/
│   └── evals.json         ← テストケース定義
└── outputs/               ← 生成したニュースレター
    ├── vol1/
    │   └── index.html     ← Vol.1 創刊号（最終版）
    ├── vol1-special/
    │   └── index.html     ← Vol.1 特集号
    └── vol5/
        └── index.html     ← Vol.5
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

## 📝 作成者

大井琉誠 — [株式会社EDIX AI×Webクリエイター養成科 在籍]
