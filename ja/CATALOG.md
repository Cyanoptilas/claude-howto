<picture>
  <source media="(prefers-color-scheme: dark)" srcset="resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="resources/logos/claude-howto-logo.svg">
</picture>

# Claude Code 機能カタログ

> Claude Code のすべての機能へのクイックリファレンス: コマンド・エージェント・スキル・プラグイン・フック。

**ナビゲーション**: [コマンド](#スラッシュコマンド) | [パーミッションモード](#パーミッションモード) | [サブエージェント](#サブエージェント) | [スキル](#スキル) | [プラグイン](#プラグイン) | [MCP サーバー](#mcp-サーバー) | [フック](#フック) | [メモリ](#メモリファイル) | [新機能](#新機能2026年4月)

---

## サマリー

| 機能 | 組み込み | サンプル | 合計 | リファレンス |
|---------|----------|----------|-------|-----------|
| **スラッシュコマンド** | 60以上 | 8 | 68以上 | [01-slash-commands/](01-slash-commands/) |
| **サブエージェント** | 6 | 11 | 17 | [04-subagents/](04-subagents/) |
| **スキル** | 5（バンドル） | 4 | 9 | [03-skills/](03-skills/) |
| **プラグイン** | - | 3 | 3 | [07-plugins/](07-plugins/) |
| **MCP サーバー** | 1 | 8 | 9 | [05-mcp/](05-mcp/) |
| **フック** | 25イベント | 8 | 8 | [06-hooks/](06-hooks/) |
| **メモリ** | 7タイプ | 3 | 3 | [02-memory/](02-memory/) |
| **合計** | **99** | **45** | **119** | |

---

## スラッシュコマンド

コマンドは特定のアクションを実行するユーザー呼び出しのショートカットです。

### 組み込みコマンド

| コマンド | 説明 | 使い場面 |
|---------|-------------|-------------|
| `/help` | ヘルプ情報を表示 | はじめかた、コマンドを学ぶ |
| `/btw` | コンテキストに追加せず質問 | クイックな余談 |
| `/clear` | 会話履歴をクリア | 新鮮なスタート、コンテキスト削減 |
| `/config` | 設定を表示/編集 | 動作のカスタマイズ |
| `/status` | セッション状態を表示 | 現在の状態を確認 |
| `/agents` | 利用可能なエージェントを一覧 | 委任オプションを確認 |
| `/skills` | 利用可能なスキルを一覧 | 自動呼び出し機能を確認 |
| `/hooks` | 設定済みフックを一覧 | 自動化のデバッグ |
| `/mcp` | MCP サーバーを一覧 | 外部統合を確認 |
| `/memory` | 読み込まれたメモリファイルを表示 | コンテキスト読み込みのデバッグ |
| `/plan` | プランニングモードに入る | 複雑な実装 |
| `/rewind` | チェックポイントに巻き戻す | 変更を取り消す、代替案を探索 |
| `/checkpoint` | チェックポイントを管理 | 状態を保存/復元 |
| `/cost` | トークン使用コストを表示 | 支出を監視 |
| `/export` | 会話をエクスポート | 参照用に保存 |
| `/feedback` | フィードバックやバグレポートを送信 | 問題を報告 |
| `/sandbox` | サンドボックスモードを切り替え | 安全なコマンド実行 |
| `/doctor` | 診断を実行 | 問題のトラブルシューティング |
| `/todo` | タスクリストを表示/管理 | タスクを追跡 |
| `/tasks` | バックグラウンドタスクを表示 | 非同期操作を監視 |
| `/fork` | 現在の会話をフォーク | 代替案を探索 |
| `/resume` | 前のセッションを再開 | 作業を続ける |
| `/rename` | 現在のセッションの名前を変更 | セッションを整理 |
| `/fast` | 高速出力モードを切り替え | レスポンスを高速化 |
| `/focus` | フォーカスビューを切り替え（気を散らさない出力表示） | 長いタスク中のノイズ削減 |
| `/recap` | 戻ったときのセッション概要を表示 | 離れていた後にコンテキストを把握 |
| `/tui` | フルスクリーン TUI モードを切り替え | tmux でのちらつきなしのレンダリング |
| `/undo` | `/rewind` のエイリアス | `/rewind` と同じ |
| `/team-onboarding` | チームメンバー向けランプアップガイドを生成 | 新しいチームメンバーのオンボーディング |
| `/ultraplan` | プランニングモードのクラウドセッションに計画タスクを渡す | 重いプランニングのオフロード |
| `/ultrareview` | 現在の変更に対してクラウドマルチエージェントコードレビューを実行 | マージ前の深いレビュー |

### カスタムコマンド（サンプル）

| コマンド | 説明 | 使い場面 | スコープ | インストール |
|---------|-------------|-------------|-------|--------------|
| `/optimize` | 最適化のためにコードを分析 | パフォーマンス改善 | プロジェクト | `cp 01-slash-commands/optimize.md .claude/commands/` |
| `/pr` | プルリクエストを準備 | PR 提出前 | プロジェクト | `cp 01-slash-commands/pr.md .claude/commands/` |
| `/generate-api-docs` | API ドキュメントを生成 | API のドキュメント化 | プロジェクト | `cp 01-slash-commands/generate-api-docs.md .claude/commands/` |
| `/commit` | コンテキスト付き git コミットを作成 | 変更のコミット | ユーザー | `cp 01-slash-commands/commit.md .claude/commands/` |
| `/push-all` | ステージ・コミット・プッシュ | クイックデプロイ | ユーザー | `cp 01-slash-commands/push-all.md .claude/commands/` |
| `/doc-refactor` | ドキュメントを再構成 | ドキュメントの改善 | プロジェクト | `cp 01-slash-commands/doc-refactor.md .claude/commands/` |
| `/setup-ci-cd` | CI/CD パイプラインをセットアップ | 新しいプロジェクト | プロジェクト | `cp 01-slash-commands/setup-ci-cd.md .claude/commands/` |
| `/unit-test-expand` | テストカバレッジを拡張 | テスト改善 | プロジェクト | `cp 01-slash-commands/unit-test-expand.md .claude/commands/` |

> **スコープ**: `ユーザー` = 個人ワークフロー（`~/.claude/commands/`）、`プロジェクト` = チーム共有（`.claude/commands/`）

**全カスタムコマンドのクイックインストール**:
```bash
cp 01-slash-commands/*.md .claude/commands/
```

---

## パーミッションモード

Claude Code はツール使用の承認方法を制御する6つのパーミッションモードをサポートします。

| モード | 説明 | 使い場面 |
|------|-------------|-------------|
| `default` | 各ツール呼び出しにプロンプト | 標準的なインタラクティブ使用 |
| `acceptEdits` | ファイル編集を自動承認、他はプロンプト | 信頼できる編集ワークフロー |
| `plan` | 読み取り専用ツールのみ、書き込みなし | プランニングと探索 |
| `auto` | プロンプトなしですべてのツールを承認 | 完全自律操作（Research Preview） |
| `bypassPermissions` | すべてのパーミッションチェックをスキップ | CI/CD、ヘッドレス環境 |
| `dontAsk` | パーミッションが必要なツールをスキップ | 非インタラクティブスクリプト |

---

## サブエージェント

独立したコンテキストを持つ特定タスク向けの特化型 AI アシスタント。

### 組み込みサブエージェント

| エージェント | 説明 | ツール | モデル | 使い場面 |
|-------|-------------|-------|-------|-------------|
| **general-purpose** | マルチステップタスク、調査 | 全ツール | モデルを継承 | 複雑な調査、複数ファイルのタスク |
| **Plan** | 実装プランニング | Read, Glob, Grep, Bash | モデルを継承 | アーキテクチャ設計、プランニング |
| **Explore** | コードベース探索 | Read, Glob, Grep | Haiku 4.5 | クイック検索、コードの理解 |
| **Bash** | コマンド実行 | Bash | モデルを継承 | Git 操作、ターミナルタスク |
| **statusline-setup** | ステータスライン設定 | Bash, Read, Write | Sonnet 4.6 | ステータスライン表示の設定 |
| **Claude Code Guide** | ヘルプとドキュメント | Read, Glob, Grep | Haiku 4.5 | ヘルプを得る、機能を学ぶ |

### カスタムサブエージェント（サンプル）

| エージェント | 説明 | 使い場面 | スコープ | インストール |
|-------|-------------|-------------|-------|--------------|
| `code-reviewer` | 包括的なコード品質 | コードレビューセッション | プロジェクト | `cp 04-subagents/code-reviewer.md .claude/agents/` |
| `test-engineer` | テスト戦略とカバレッジ | テストプランニング | プロジェクト | `cp 04-subagents/test-engineer.md .claude/agents/` |
| `documentation-writer` | 技術ドキュメント | API ドキュメント、ガイド | プロジェクト | `cp 04-subagents/documentation-writer.md .claude/agents/` |
| `secure-reviewer` | セキュリティ重視のレビュー | セキュリティ監査 | プロジェクト | `cp 04-subagents/secure-reviewer.md .claude/agents/` |
| `implementation-agent` | 完全な機能実装 | 機能開発 | プロジェクト | `cp 04-subagents/implementation-agent.md .claude/agents/` |
| `debugger` | 根本原因分析 | バグ調査 | ユーザー | `cp 04-subagents/debugger.md .claude/agents/` |
| `data-scientist` | SQL クエリ、データ分析 | データタスク | ユーザー | `cp 04-subagents/data-scientist.md .claude/agents/` |
| `performance-optimizer` | プロファイリングとチューニング | ボトルネック調査 | プロジェクト | `cp 04-subagents/performance-optimizer.md .claude/agents/` |

**全カスタムエージェントのクイックインストール**:
```bash
cp 04-subagents/*.md .claude/agents/
```

---

## スキル

指示・スクリプト・テンプレートを持つ自動呼び出し機能。

### スキルのサンプル

| スキル | 説明 | 自動呼び出しのタイミング | スコープ | インストール |
|-------|-------------|-------------------|-------|--------------|
| `code-review` | 包括的なコードレビュー | "このコードをレビューして"、"品質をチェックして" | プロジェクト | `cp -r 03-skills/code-review .claude/skills/` |
| `brand-voice` | ブランド一貫性チェッカー | マーケティングコピーを書くとき | プロジェクト | `cp -r 03-skills/brand-voice .claude/skills/` |
| `doc-generator` | API ドキュメントジェネレーター | "ドキュメントを生成して"、"API をドキュメント化して" | プロジェクト | `cp -r 03-skills/doc-generator .claude/skills/` |
| `refactor` | 体系的なコードリファクタリング | "これをリファクタして"、"コードをクリーンアップして" | ユーザー | `cp -r 03-skills/refactor ~/.claude/skills/` |

### スキル構造

```
~/.claude/skills/skill-name/
├── SKILL.md          # スキル定義と指示
├── scripts/          # ヘルパースクリプト
└── templates/        # 出力テンプレート
```

**全スキルのクイックインストール**:
```bash
cp -r 03-skills/* ~/.claude/skills/
```

### バンドルスキル

| スキル | 説明 | 自動呼び出しのタイミング |
|-------|-------------|-------------------|
| `/simplify` | コードの品質をレビュー | コードを書いた後 |
| `/batch` | 複数ファイルにプロンプトを実行 | バッチ操作 |
| `/debug` | 失敗したテスト/エラーをデバッグ | デバッグセッション |
| `/loop` | 定期的にプロンプトを実行 | 繰り返しタスク |
| `/claude-api` | Claude API でアプリを構築 | API 開発 |

---

## プラグイン

コマンド・エージェント・MCP サーバー・フックのバンドルされたコレクション。

### サンプルプラグイン

| プラグイン | 説明 | コンポーネント | 使い場面 | インストール |
|--------|-------------|------------|-------------|--------------|
| `pr-review` | PR レビューワークフロー | 3コマンド、3エージェント、GitHub MCP | コードレビュー | `/plugin install pr-review` |
| `devops-automation` | デプロイと監視 | 4コマンド、3エージェント、K8s MCP | DevOps タスク | `/plugin install devops-automation` |
| `documentation` | ドキュメント生成スイート | 4コマンド、3エージェント、テンプレート | ドキュメント | `/plugin install documentation` |

**プラグイン管理コマンド**:
```bash
/plugin list              # インストール済みプラグインを一覧
/plugin install <name>    # プラグインをインストール
/plugin remove <name>     # プラグインを削除
/plugin update <name>     # プラグインを更新
```

---

## MCP サーバー

外部ツールと API アクセスのための Model Context Protocol サーバー。

### 一般的な MCP サーバー

| サーバー | 説明 | 使い場面 | スコープ | インストール |
|--------|-------------|-------------|-------|--------------|
| **GitHub** | PR 管理、issues、コード | GitHub ワークフロー | プロジェクト | `claude mcp add github -- npx -y @modelcontextprotocol/server-github` |
| **Database** | SQL クエリ、データアクセス | データベース操作 | プロジェクト | `claude mcp add db -- npx -y @modelcontextprotocol/server-postgres` |
| **Filesystem** | 高度なファイル操作 | 複雑なファイルタスク | ユーザー | `claude mcp add fs -- npx -y @modelcontextprotocol/server-filesystem` |
| **Slack** | チームコミュニケーション | 通知、更新 | プロジェクト | 設定で構成 |
| **Memory** | 永続メモリ | クロスセッション記憶 | ユーザー | 設定で構成 |
| **Context7** | ライブラリドキュメント | 最新ドキュメント検索 | 組み込み | 組み込み |

**クイックインストール（GitHub MCP）**:
```bash
export GITHUB_TOKEN="your_token" && claude mcp add github -- npx -y @modelcontextprotocol/server-github
```

---

## フック

Claude Code のイベントに応じてシェルコマンドを実行するイベント駆動型の自動化。

### フックイベント

| イベント | 説明 | トリガー | ユースケース |
|-------|-------------|----------------|-----------|
| `SessionStart` | セッション開始/再開 | セッション初期化 | セットアップタスク |
| `UserPromptSubmit` | プロンプト処理前 | ユーザーがメッセージを送信 | 入力検証 |
| `PreToolUse` | ツール実行前 | ツールが実行される前 | 検証、ログ |
| `PostToolUse` | ツール成功後 | ツール完了後 | フォーマット、通知 |
| `Stop` | Claude がレスポンス完了 | レスポンス完了 | クリーンアップ、レポート |
| `SubagentStart` | サブエージェントが生成 | サブエージェントタスク開始 | コンテキスト注入 |
| `SubagentStop` | サブエージェントが完了 | サブエージェントタスク完了 | アクションの連鎖 |
| `SessionEnd` | セッション終了 | セッション終了 | クリーンアップ、状態保存 |

### フック設定

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "command": "~/.claude/hooks/validate-bash.py"
      }
    ],
    "PostToolUse": [
      {
        "matcher": "Write",
        "command": "~/.claude/hooks/format-code.sh"
      }
    ]
  }
}
```

**全フックのクイックインストール**:
```bash
mkdir -p ~/.claude/hooks && cp 06-hooks/*.sh ~/.claude/hooks/ && chmod +x ~/.claude/hooks/*.sh
```

---

## メモリファイル

セッション間で自動的に読み込まれる永続コンテキスト。

### メモリタイプ

| タイプ | 場所 | スコープ | 使い場面 |
|------|----------|-------|-------------|
| **Managed Policy** | 組織管理ポリシー | 組織 | 組織全体の標準を適用 |
| **Project** | `./CLAUDE.md` | プロジェクト（チーム） | チーム標準、プロジェクトコンテキスト |
| **Project Rules** | `.claude/rules/` | プロジェクト（チーム） | モジュール式プロジェクトルール |
| **User** | `~/.claude/CLAUDE.md` | ユーザー（個人） | 個人設定 |
| **User Rules** | `~/.claude/rules/` | ユーザー（個人） | モジュール式個人ルール |
| **Auto Memory** | 自動 | セッション | 自動キャプチャされた洞察と修正 |

**クイックインストール**:
```bash
cp 02-memory/project-CLAUDE.md ./CLAUDE.md
cp 02-memory/personal-CLAUDE.md ~/.claude/CLAUDE.md
```

---

## 新機能（2026年4月）

| 機能 | 説明 | 使い方 |
|---------|-------------|------------|
| **/focus** | 気を散らさない出力表示のフォーカスビューを切り替え（v2.1.110） | `/focus` を実行してノイズを削減 |
| **/proactive** | `/loop` のエイリアス — 同じ繰り返しタスクの動作（v2.1.105） | `/proactive` を `/loop` と同じように使用 |
| **/recap** | 既存セッションに戻ったときのセッション概要を表示（v2.1.108） | 離れていた後に `/recap` を実行 |
| **/tui** | フルスクリーン TUI モードを切り替えてちらつきなしのレンダリング（v2.1.110） | フルスクリーンターミナルや tmux で `/tui` を使用 |
| **/undo** | `/rewind` のエイリアス（v2.1.108） | `/undo` を `/rewind` と同じように使用 |
| **Monitor Tool** | バックグラウンドコマンドの stdout をストリーム監視（v2.1.98+） | [高度な機能](09-advanced-features/) 経由で Monitor ツールを使用 |
| **/team-onboarding** | プロジェクトの Claude Code 使用からチームメンバーのランプアップガイドを自動生成（v2.1.101） | プロジェクトで `/team-onboarding` を実行 |
| **Remote Control** | API 経由で Claude Code セッションをリモート制御 | リモートコントロール API を使用 |

---

## クイックリファレンスマトリクス

### 機能選択ガイド

| ニーズ | 推奨機能 | 理由 |
|------|---------------------|-----|
| クイックショートカット | スラッシュコマンド | 手動、即時 |
| 永続コンテキスト | メモリ | 自動読み込み |
| 複雑な自動化 | スキル | 自動呼び出し |
| 専門タスク | サブエージェント | 独立したコンテキスト |
| 外部データ | MCP サーバー | リアルタイムアクセス |
| イベント自動化 | フック | イベントトリガー |
| 完全なソリューション | プラグイン | オールインワンバンドル |

---

## 完全な1コマンドインストール

このリポジトリのすべてのサンプルをインストールします:

```bash
# ディレクトリを作成
mkdir -p .claude/{commands,agents,skills} ~/.claude/{hooks,skills}

# すべての機能をインストール
cp 01-slash-commands/*.md .claude/commands/ && \
cp 02-memory/project-CLAUDE.md ./CLAUDE.md && \
cp -r 03-skills/* ~/.claude/skills/ && \
cp 04-subagents/*.md .claude/agents/ && \
cp 06-hooks/*.sh ~/.claude/hooks/ && \
chmod +x ~/.claude/hooks/*.sh
```

---

**最終更新**: 2026年4月16日
**Claude Code バージョン**: 2.1.112
**互換モデル**: Claude Sonnet 4.6・Claude Opus 4.7・Claude Haiku 4.5
