# Task Board — Claude Code Guide

## プロジェクト概要

タスク管理ボードアプリケーション。

## 技術スタック

- **フレームワーク**: React 18
- **ビルドツール**: Vite 5
- **言語**: JavaScript (JSX)
- **スタイリング**: plain CSS（CSS Modules不使用）
- **状態管理**: React useState / useEffect（外部ライブラリなし）
- **永続化**: localStorage

## ディレクトリ構成

```
task-board/
├── src/
│   ├── main.jsx      # エントリーポイント
│   ├── App.jsx       # ルートコンポーネント
│   ├── App.css       # App コンポーネントのスタイル
│   └── index.css     # グローバルスタイル
├── .github/
│   └── workflows/
│       └── deploy.yml  # GitHub Pages 自動デプロイ
├── index.html
├── vite.config.js
└── package.json
```

## コンポーネント命名規約

- コンポーネント名は **PascalCase**（例: `TaskItem`, `AddTaskForm`）
- ファイル名はコンポーネント名と一致させる（例: `TaskItem.jsx`）
- コンポーネントファイルは `src/` 直下に置く（現状規模のため）

## デプロイ先

https://walfinthnk.github.io/task-board/

- `main` ブランチへのプッシュで GitHub Actions が自動ビルド＆デプロイ
- ワークフロー: [.github/workflows/deploy.yml](.github/workflows/deploy.yml)

## 開発コマンド

```bash
# 依存関係インストール
npm install

# 開発サーバー起動
npm run dev

# ビルド
npm run build

# テスト
npm test
```

## コーディング規約

- コメントは原則書かない。WHYが自明でない場合のみ1行で記述する
- エラーハンドリングはシステム境界（ユーザー入力・外部API）のみ行う
- 抽象化は必要最小限。将来の要件のための設計はしない

## Git 運用ルール

**コードを変更するたびに、必ずコミットしてGitHubにプッシュすること。**

### 手順

```bash
# 変更をステージング（ファイルを個別に指定する）
git add <変更ファイル>

# コミット（変更内容を簡潔に記述）
git commit -m "feat: タスク追加機能を実装"

# GitHubにプッシュ
git push origin main
```

### コミットメッセージ規約

| プレフィックス | 用途 |
|---|---|
| `feat:` | 新機能追加 |
| `fix:` | バグ修正 |
| `refactor:` | リファクタリング |
| `style:` | スタイル・フォーマット変更 |
| `docs:` | ドキュメント更新 |
| `test:` | テスト追加・修正 |
| `chore:` | ビルド設定・依存関係の変更 |

### 注意事項

- `.env` などの機密ファイルは絶対にコミットしない
- `git add .` や `git add -A` は使わず、ファイルを個別に指定する
- force push (`git push --force`) は原則禁止
- フック（`--no-verify`）のスキップは禁止
