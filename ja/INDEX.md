<picture>
  <source media="(prefers-color-scheme: dark)" srcset="resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="resources/logos/claude-howto-logo.svg">
</picture>

# Claude Code サンプル — 完全インデックス

このドキュメントは、機能タイプ別に整理されたすべてのサンプルファイルの完全インデックスを提供します。

## 統計サマリー

- **総ファイル数**: 100以上
- **カテゴリ**: 10の機能カテゴリ
- **プラグイン**: 3つの完全なプラグイン
- **スキル**: 6つの完全なスキル
- **フック**: 8つのサンプルフック
- **すぐに使える**: すべてのサンプル

---

## 01. スラッシュコマンド（10ファイル）

よく使うワークフローのためのユーザー呼び出しショートカット。

| ファイル | 説明 | ユースケース |
|------|-------------|----------|
| `optimize.md` | コード最適化アナライザー | パフォーマンス問題の発見 |
| `pr.md` | プルリクエスト準備 | PR ワークフローの自動化 |
| `generate-api-docs.md` | API ドキュメントジェネレーター | API ドキュメントの生成 |
| `commit.md` | コミットメッセージヘルパー | 標準化されたコミット |
| `setup-ci-cd.md` | CI/CD パイプラインのセットアップ | DevOps 自動化 |
| `push-all.md` | すべての変更をプッシュ | クイックプッシュワークフロー |
| `unit-test-expand.md` | ユニットテストカバレッジの拡張 | テスト自動化 |
| `doc-refactor.md` | ドキュメントのリファクタリング | ドキュメントの改善 |
| `README.md` | ドキュメント | セットアップと使い方ガイド |

**インストールパス**: `.claude/commands/`

**使い方**: `/optimize`、`/pr`、`/generate-api-docs`、`/commit`、`/setup-ci-cd`、`/push-all`、`/unit-test-expand`、`/doc-refactor`

---

## 02. メモリ（6ファイル）

永続コンテキストとプロジェクト標準。

| ファイル | 説明 | スコープ | 場所 |
|------|-------------|-------|----------|
| `project-CLAUDE.md` | チームプロジェクト標準 | プロジェクト全体 | `./CLAUDE.md` |
| `directory-api-CLAUDE.md` | API 固有のルール | ディレクトリ | `./src/api/CLAUDE.md` |
| `personal-CLAUDE.md` | 個人設定 | ユーザー | `~/.claude/CLAUDE.md` |
| `README.md` | ドキュメント | - | リファレンス |

**インストール**: 適切な場所にコピーする

**使い方**: Claude が自動的に読み込む

---

## 03. スキル（28ファイル）

スクリプトとテンプレートを持つ自動呼び出し機能。

### コードレビュースキル（5ファイル）
```
code-review/
├── SKILL.md
├── scripts/
│   ├── analyze-metrics.py
│   └── compare-complexity.py
└── templates/
    ├── review-checklist.md
    └── finding-template.md
```

### ブランドボイススキル（4ファイル）
```
brand-voice/
├── SKILL.md
├── templates/
│   ├── email-template.txt
│   └── social-post-template.txt
└── tone-examples.md
```

### ドキュメントジェネレータースキル（2ファイル）
```
doc-generator/
├── SKILL.md
└── generate-docs.py
```

### リファクタースキル（5ファイル）
```
refactor/
├── SKILL.md
├── scripts/
│   ├── analyze-complexity.py
│   └── detect-smells.py
├── references/
│   ├── code-smells.md
│   └── refactoring-catalog.md
└── templates/
    └── refactoring-plan.md
```

### Claude MD スキル（1ファイル）
```
claude-md/
└── SKILL.md
```

### ブログ下書きスキル（3ファイル）
```
blog-draft/
├── SKILL.md
└── templates/
    ├── draft-template.md
    └── outline-template.md
```

**インストールパス**: `~/.claude/skills/` または `.claude/skills/`

---

## 04. サブエージェント（9ファイル）

カスタム機能を持つ特化型 AI アシスタント。

| ファイル | 説明 | ツール | ユースケース |
|------|-------------|-------|----------|
| `code-reviewer.md` | コード品質分析 | read, grep, diff, lint_runner | 包括的なレビュー |
| `test-engineer.md` | テストカバレッジ分析 | read, write, bash, grep | テスト自動化 |
| `documentation-writer.md` | ドキュメント作成 | read, write, grep | ドキュメント生成 |
| `secure-reviewer.md` | セキュリティレビュー（読み取り専用） | read, grep | セキュリティ監査 |
| `implementation-agent.md` | 完全な実装 | read, write, bash, grep, edit, glob | 機能開発 |
| `debugger.md` | デバッグスペシャリスト | read, bash, grep | バグ調査 |
| `data-scientist.md` | データ分析スペシャリスト | read, write, bash | データワークフロー |
| `clean-code-reviewer.md` | クリーンコード標準 | read, grep | コード品質 |
| `README.md` | ドキュメント | - | セットアップと使い方ガイド |

**インストールパス**: `.claude/agents/`

---

## 05. MCP プロトコル（5ファイル）

外部ツールと API の統合。

| ファイル | 説明 | 統合先 | ユースケース |
|------|-------------|-----------------|----------|
| `github-mcp.json` | GitHub 統合 | GitHub API | PR/issue 管理 |
| `database-mcp.json` | データベースクエリ | PostgreSQL/MySQL | ライブデータクエリ |
| `filesystem-mcp.json` | ファイル操作 | ローカルファイルシステム | ファイル管理 |
| `multi-mcp.json` | 複数サーバー | GitHub + DB + Slack | 完全統合 |
| `README.md` | ドキュメント | - | セットアップと使い方ガイド |

---

## 06. フック（9ファイル）

自動的に実行されるイベント駆動型の自動化スクリプト。

| ファイル | 説明 | イベント | ユースケース |
|------|-------------|-------|----------|
| `format-code.sh` | コードの自動フォーマット | PreToolUse:Write | コードフォーマット |
| `pre-commit.sh` | コミット前のテスト実行 | PreToolUse:Bash | テスト自動化 |
| `security-scan.sh` | セキュリティスキャン | PostToolUse:Write | セキュリティチェック |
| `log-bash.sh` | bash コマンドのログ | PostToolUse:Bash | コマンドログ |
| `validate-prompt.sh` | プロンプトの検証 | PreToolUse | 入力検証 |
| `notify-team.sh` | 通知の送信 | Notification | チーム通知 |
| `context-tracker.py` | コンテキストウィンドウ使用量の追跡 | PostToolUse | コンテキスト監視 |
| `README.md` | ドキュメント | - | セットアップと使い方ガイド |

---

## 07. プラグイン（3つの完全なプラグイン、40ファイル）

機能のバンドルされたコレクション。

### PR レビュープラグイン（10ファイル）
```
pr-review/
├── .claude-plugin/plugin.json
├── commands/
│   ├── review-pr.md
│   ├── check-security.md
│   └── check-tests.md
├── agents/
│   ├── security-reviewer.md
│   ├── test-checker.md
│   └── performance-analyzer.md
├── mcp/github-config.json
├── hooks/pre-review.js
└── README.md
```

**インストール**: `/plugin install pr-review`

### DevOps 自動化プラグイン（15ファイル）
```
devops-automation/
├── .claude-plugin/plugin.json
├── commands/
│   ├── deploy.md
│   ├── rollback.md
│   ├── status.md
│   └── incident.md
├── agents/
│   ├── deployment-specialist.md
│   ├── incident-commander.md
│   └── alert-analyzer.md
└── README.md
```

**インストール**: `/plugin install devops-automation`

### ドキュメントプラグイン（14ファイル）
```
documentation/
├── .claude-plugin/plugin.json
├── commands/
│   ├── generate-api-docs.md
│   ├── generate-readme.md
│   ├── sync-docs.md
│   └── validate-docs.md
├── agents/
│   ├── api-documenter.md
│   ├── code-commentator.md
│   └── example-generator.md
├── templates/
│   ├── api-endpoint.md
│   ├── function-docs.md
│   └── adr-template.md
└── README.md
```

**インストール**: `/plugin install documentation`

---

## 08. チェックポイントと巻き戻し（2ファイル）

会話状態を保存して代替アプローチを探索する。

| ファイル | 説明 |
|------|-------------|
| `README.md` | チェックポイントの包括的なガイド |
| `checkpoint-examples.md` | 実際の使用例 |

**使い方**:
```bash
# チェックポイントはすべてのユーザープロンプトで自動的に作成される
# 巻き戻すには Esc を2回押すか、次のコマンドを使用する:
/rewind
```

---

## 09. 高度な機能（3ファイル）

複雑なワークフローのための高度な機能。

| ファイル | 説明 |
|------|-------------|
| `README.md` | すべての高度な機能のドキュメント |
| `config-examples.json` | 設定例 |
| `planning-mode-examples.md` | プランニングモードの例 |

---

## 10. CLI の使い方（1ファイル）

コマンドラインインターフェースの使い方パターンとリファレンス。

| ファイル | 説明 |
|------|-------------|
| `README.md` | フラグ、オプション、使い方パターン |

---

## ユースケース別クイックスタート

### コード品質とレビュー
```bash
cp 01-slash-commands/optimize.md .claude/commands/
cp 04-subagents/code-reviewer.md .claude/agents/
cp -r 03-skills/code-review ~/.claude/skills/
# またはプラグインをインストール
/plugin install pr-review
```

### DevOps とデプロイ
```bash
/plugin install devops-automation
```

### ドキュメント
```bash
cp 01-slash-commands/generate-api-docs.md .claude/commands/
cp 04-subagents/documentation-writer.md .claude/agents/
/plugin install documentation
```

---

## 学習パス

### 初心者（第1週）
1. ✅ `README.md` を読む
2. ✅ スラッシュコマンドを1〜2つインストールする
3. ✅ プロジェクトメモリファイルを作成する
4. ✅ 基本コマンドを試す

### 中級者（第2〜3週）
1. ✅ GitHub MCP をセットアップする
2. ✅ サブエージェントをインストールする
3. ✅ タスクの委任を試す
4. ✅ スキルをインストールする

### 上級者（第4週以降）
1. ✅ 完全なプラグインをインストールする
2. ✅ カスタムスラッシュコマンドを作成する
3. ✅ カスタムサブエージェントを作成する
4. ✅ 自動化のためのフックをセットアップする

---

**最終更新**: 2026年4月16日
**Claude Code バージョン**: 2.1.112
**互換モデル**: Claude Sonnet 4.6・Claude Opus 4.7・Claude Haiku 4.5
