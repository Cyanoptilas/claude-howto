<picture>
  <source media="(prefers-color-scheme: dark)" srcset="resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="resources/logos/claude-howto-logo.svg">
</picture>

# Claude Code サンプル — クイックリファレンスカード

## 🚀 インストールクイックコマンド

### スラッシュコマンド
```bash
# 全部インストール
cp 01-slash-commands/*.md .claude/commands/

# 特定のものをインストール
cp 01-slash-commands/optimize.md .claude/commands/
```

### メモリ
```bash
# プロジェクトメモリ
cp 02-memory/project-CLAUDE.md ./CLAUDE.md

# 個人メモリ
cp 02-memory/personal-CLAUDE.md ~/.claude/CLAUDE.md
```

### スキル
```bash
# 個人スキル
cp -r 03-skills/code-review ~/.claude/skills/

# プロジェクトスキル
cp -r 03-skills/code-review .claude/skills/
```

### サブエージェント
```bash
# 全部インストール
cp 04-subagents/*.md .claude/agents/

# 特定のものをインストール
cp 04-subagents/code-reviewer.md .claude/agents/
```

### MCP
```bash
# 認証情報を設定
export GITHUB_TOKEN="your_token"
export DATABASE_URL="postgresql://..."

# 設定をインストール（プロジェクトスコープ）
cp 05-mcp/github-mcp.json .mcp.json
```

### フック
```bash
# フックをインストール
mkdir -p ~/.claude/hooks
cp 06-hooks/*.sh ~/.claude/hooks/
chmod +x ~/.claude/hooks/*.sh

# settings.json で設定 (~/.claude/settings.json)
```

### プラグイン
```bash
/plugin install pr-review
/plugin install devops-automation
/plugin install documentation
```

### チェックポイント
```bash
# チェックポイントはすべてのユーザープロンプトで自動的に作成される
# 巻き戻すには Esc を2回押すか、次のコマンドを使用する:
/rewind
```

### 高度な機能
```bash
# プランニングモード
/plan タスクの説明

# パーミッションモード
# default     - リスクのある操作に承認を求める
# acceptEdits - ファイル編集を自動承認、他は確認
# plan        - 読み取り専用、変更なし
# dontAsk     - リスクのある操作以外はすべて承認
# auto        - 安全な操作を自動承認
# bypassPermissions - すべての操作を承認

# セッション管理
/resume           # 前の会話を再開
/rename "name"    # 現在のセッションに名前をつける
/fork             # 現在のセッションをフォーク
claude -c         # 最新の会話を続ける
claude -r "session"  # 名前/IDでセッションを再開
```

---

## 📋 機能チートシート

| 機能 | インストールパス | 使い方 |
|---------|-------------|-------|
| **スラッシュコマンド（55以上）** | `.claude/commands/*.md` | `/コマンド名` |
| **メモリ** | `./CLAUDE.md` | 自動読み込み |
| **スキル** | `.claude/skills/*/SKILL.md` | 自動呼び出し |
| **サブエージェント** | `.claude/agents/*.md` | 自動委任 |
| **MCP** | `.mcp.json`（プロジェクト）または `~/.claude.json`（ユーザー） | `/mcp__server__action` |
| **フック（25イベント）** | `~/.claude/hooks/*.sh` | イベント駆動（4種類） |
| **プラグイン** | `/plugin install` | すべてをバンドル |
| **チェックポイント** | 組み込み | `Esc+Esc` または `/rewind` |
| **プランニングモード** | 組み込み | `/plan <タスク>` |
| **パーミッションモード（6種類）** | 組み込み | `--allowedTools`、`--permission-mode` |

---

## 🎯 よくあるユースケース

### コードレビュー
```bash
# 方法1: スラッシュコマンド
cp 01-slash-commands/optimize.md .claude/commands/
# 使い方: /optimize

# 方法2: サブエージェント
cp 04-subagents/code-reviewer.md .claude/agents/
# 使い方: 自動委任

# 方法3: スキル
cp -r 03-skills/code-review ~/.claude/skills/
# 使い方: 自動呼び出し

# 方法4: プラグイン（ベスト）
/plugin install pr-review
# 使い方: /review-pr
```

### ドキュメント
```bash
# スラッシュコマンド
cp 01-slash-commands/generate-api-docs.md .claude/commands/

# サブエージェント
cp 04-subagents/documentation-writer.md .claude/agents/

# スキル
cp -r 03-skills/doc-generator ~/.claude/skills/

# プラグイン（完全なソリューション）
/plugin install documentation
```

### DevOps
```bash
# 完全なプラグイン
/plugin install devops-automation

# コマンド: /deploy, /rollback, /status, /incident
```

### チーム標準
```bash
# プロジェクトメモリ
cp 02-memory/project-CLAUDE.md ./CLAUDE.md

# チーム向けに編集
vim CLAUDE.md
```

### 自動化とフック
```bash
# フックをインストール（25イベント、4タイプ）
mkdir -p ~/.claude/hooks
cp 06-hooks/*.sh ~/.claude/hooks/
chmod +x ~/.claude/hooks/*.sh
```

### 安全なリファクタリング
```bash
# チェックポイントは各プロンプト前に自動作成される
# リファクタリングを試す
# 成功したら: 続ける
# 失敗したら: Esc+Esc または /rewind で戻る
```

### CI/CD 統合
```bash
# ヘッドレスモードで実行（非インタラクティブ）
claude -p "すべてのテストを実行してレポートを生成する"

# CI 向けパーミッションモード
claude -p "テストを実行" --permission-mode dontAsk
```

---

## 📁 ファイル場所リファレンス

```
プロジェクト/
├── .claude/
│   ├── commands/          # スラッシュコマンド
│   ├── agents/            # サブエージェント
│   ├── skills/            # プロジェクトスキル
│   └── settings.json      # プロジェクト設定（フックなど）
├── .mcp.json              # MCP 設定（プロジェクトスコープ）
├── CLAUDE.md              # プロジェクトメモリ
└── src/api/CLAUDE.md      # ディレクトリ固有のメモリ

ユーザーホーム/
├── .claude/
│   ├── commands/          # 個人コマンド
│   ├── agents/            # 個人エージェント
│   ├── skills/            # 個人スキル
│   ├── hooks/             # フックスクリプト
│   ├── settings.json      # ユーザー設定
│   └── CLAUDE.md          # 個人メモリ
└── .claude.json           # 個人 MCP 設定（ユーザースコープ）
```

---

## 🎓 学習パス

### 1日目
```bash
cat README.md          # 概要を読む
cp 01-slash-commands/optimize.md .claude/commands/  # コマンドをインストール
/optimize              # 試してみる
```

### 2〜3日目
```bash
cp 02-memory/project-CLAUDE.md ./CLAUDE.md
vim CLAUDE.md          # チーム向けに編集
cp 04-subagents/code-reviewer.md .claude/agents/
```

### 4〜5日目
```bash
export GITHUB_TOKEN="your_token"
cp 05-mcp/github-mcp.json .mcp.json
/mcp__github__list_prs  # MCP コマンドを試す
```

### 第2週
```bash
cp -r 03-skills/code-review ~/.claude/skills/
# 自動呼び出しを待つ
# "このコードの問題をレビューして" と言うだけ
```

### 第3週以降
```bash
/plugin install pr-review
/review-pr
/check-security
/check-tests
```

---

## 📊 機能マトリクス

| ニーズ | 使うもの | 例 |
|------|----------|---------|
| クイックショートカット | スラッシュコマンド（55以上） | `01-slash-commands/optimize.md` |
| チーム標準 | メモリ | `02-memory/project-CLAUDE.md` |
| 自動ワークフロー | スキル | `03-skills/code-review/` |
| 専門タスク | サブエージェント | `04-subagents/code-reviewer.md` |
| 外部データ | MCP | `05-mcp/github-mcp.json` |
| イベント自動化 | フック（26イベント） | `06-hooks/pre-commit.sh` |
| 完全なソリューション | プラグイン | `07-plugins/pr-review/` |
| 安全な実験 | チェックポイント | `08-checkpoints/checkpoint-examples.md` |
| CI/CD パイプライン | CLI | `10-cli/README.md` |

---

## ✅ チェックリスト

はじめかたのチェックリスト:

- [ ] `README.md` を読む
- [ ] スラッシュコマンドを1つインストールする
- [ ] コマンドを試す
- [ ] プロジェクト `CLAUDE.md` を作成する
- [ ] サブエージェントを1つインストールする
- [ ] MCP 統合を1つセットアップする
- [ ] スキルを1つインストールする
- [ ] 完全なプラグインを試す
- [ ] ニーズに合わせてカスタマイズする
- [ ] チームと共有する

---

**クイックスタート**: `cat README.md`

**完全インデックス**: `cat INDEX.md`

---
**最終更新**: 2026年4月16日
**Claude Code バージョン**: 2.1.112
**互換モデル**: Claude Sonnet 4.6・Claude Opus 4.7・Claude Haiku 4.5
