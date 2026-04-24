<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../../resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="../../resources/logos/claude-howto-logo.svg">
</picture>

# フック

フックは、Claude Code セッション中に特定のイベントに応答して実行される自動スクリプトです。自動化・バリデーション・パーミッション管理・カスタムワークフローを実現します。

## 概要

フックは、Claude Code で特定のイベントが発生したときに自動的に実行されるアクション（シェルコマンド・HTTP Webhook・LLM プロンプト・サブエージェント評価）です。JSON 入力を受け取り、終了コードと JSON 出力で結果を伝えます。

**主な特徴：**
- イベント駆動の自動化
- JSON ベースの入出力
- コマンド・プロンプト・HTTP・エージェントのフックタイプをサポート
- ツール固有のフックのパターンマッチング

## 設定

フックは設定ファイルに特定の構造で設定します：

- `~/.claude/settings.json` — ユーザー設定（全プロジェクト共通）
- `.claude/settings.json` — プロジェクト設定（共有可能・コミット済み）
- `.claude/settings.local.json` — ローカルプロジェクト設定（コミットしない）

### 基本設定構造

```json
{
  "hooks": {
    "EventName": [
      {
        "matcher": "ToolPattern",
        "hooks": [
          {
            "type": "command",
            "command": "your-command-here",
            "timeout": 60
          }
        ]
      }
    ]
  }
}
```

**主なフィールド：**

| フィールド | 説明 | 例 |
|-------|-------------|---------|
| `matcher` | ツール名にマッチするパターン（大文字小文字区別） | `"Write"`、`"Edit\|Write"`、`"*"` |
| `type` | フックタイプ：`"command"`・`"prompt"`・`"http"`・`"agent"` | `"command"` |
| `command` | 実行するシェルコマンド | `"$CLAUDE_PROJECT_DIR/.claude/hooks/format.sh"` |
| `timeout` | 任意のタイムアウト（秒）（デフォルト60） | `30` |
| `once` | `true` の場合、セッション中に1回だけ実行 | `true` |

## フックタイプ

### コマンドフック

デフォルトのフックタイプ。シェルコマンドを実行し、JSON stdin/stdout と終了コードで通信します。

```json
{
  "type": "command",
  "command": "python3 \"$CLAUDE_PROJECT_DIR/.claude/hooks/validate.py\"",
  "timeout": 60
}
```

### HTTP フック（v2.1.63以降）

JSON 入力を受け取るリモート Webhook エンドポイント。

```json
{
  "hooks": {
    "PostToolUse": [{
      "type": "http",
      "url": "https://my-webhook.example.com/hook",
      "matcher": "Write"
    }]
  }
}
```

### プロンプトフック

Claude が評価する LLM プロンプト。主に `Stop` と `SubagentStop` イベントでタスク完了チェックに使用します。

```json
{
  "type": "prompt",
  "prompt": "Claude がすべてのリクエストされたタスクを完了したか評価してください。",
  "timeout": 30
}
```

### エージェントフック

条件を評価したり複雑なチェックを実行するために専用エージェントを生成するサブエージェントベースの検証フック。

```json
{
  "type": "agent",
  "prompt": "コードの変更がアーキテクチャガイドラインに従っているか検証してください。",
  "timeout": 120
}
```

## フックイベント

Claude Code は **26のフックイベント**をサポートします：

| イベント | トリガーされるとき | ブロック可否 | 一般的な用途 |
|-------|---------------|-----------|------------|
| **SessionStart** | セッション開始/再開/クリア/コンパクト | 不可 | 環境セットアップ |
| **InstructionsLoaded** | CLAUDE.md またはルールファイル読み込み後 | 不可 | 指示の変更/フィルタリング |
| **UserPromptSubmit** | ユーザーがプロンプトを送信 | 可 | プロンプトの検証 |
| **PreToolUse** | ツール実行前 | 可（許可/拒否/確認） | 入力の検証・変更 |
| **PermissionRequest** | パーミッションダイアログ表示 | 可 | 自動承認/拒否 |
| **PostToolUse** | ツール成功後 | 不可 | コンテキスト追加・フィードバック |
| **PostToolUseFailure** | ツール実行失敗 | 不可 | エラーハンドリング・ログ |
| **SubagentStart** | サブエージェント生成 | 不可 | サブエージェントセットアップ |
| **SubagentStop** | サブエージェント終了 | 可 | サブエージェント検証 |
| **Stop** | Claude の応答終了 | 可 | タスク完了チェック |
| **TaskCompleted** | タスク完了マーク | 可 | タスク後の処理 |
| **FileChanged** | 監視ファイルの変更 | 不可 | ファイル監視・再ビルド |
| **SessionEnd** | セッション終了 | 不可 | クリーンアップ・最終ログ |

## 実践的な例

### コード自動フォーマット

ファイルを書き込む前に自動フォーマットします：

```json
{
  "hooks": {
    "PreToolUse": [{
      "matcher": "Write",
      "hooks": [{
        "type": "command",
        "command": "prettier --write $CLAUDE_TOOL_INPUT_FILE_PATH 2>/dev/null || true"
      }]
    }]
  }
}
```

### セキュリティスキャン

ファイル変更後にセキュリティチェックを実行します：

```json
{
  "hooks": {
    "PostToolUse": [{
      "matcher": "Write|Edit",
      "hooks": [{
        "type": "command",
        "command": "bandit -r $CLAUDE_TOOL_INPUT_FILE_PATH 2>/dev/null || true"
      }]
    }]
  }
}
```

### タスク完了の検証

```json
{
  "hooks": {
    "Stop": [{
      "hooks": [{
        "type": "prompt",
        "prompt": "ユーザーのリクエストがすべて完了したか確認してください。未完了の部分があれば指摘してください。"
      }]
    }]
  }
}
```

## フック環境変数

フックは以下の環境変数にアクセスできます：

| 変数 | 説明 |
|------|-------------|
| `CLAUDE_PROJECT_DIR` | 現在のプロジェクトディレクトリ |
| `CLAUDE_TOOL_NAME` | 実行中のツール名 |
| `CLAUDE_TOOL_INPUT_FILE_PATH` | 操作されたファイルのパス |
| `CLAUDE_SESSION_ID` | 現在のセッション ID |

## ベストプラクティス

- フックは冪等にする（複数回実行しても安全）
- タイムアウトを適切に設定する（長いフックはセッションをブロックする）
- テストや CI 環境でのフックの動作を考慮する
- センシティブなデータをフックのログに記録しない

## 関連ガイド

- [スキル](../03-skills/) — フックを含むスキル定義
- [プラグイン](../07-plugins/) — プラグインスコープのフック
- [CLI リファレンス](../10-cli/) — フラグによるフック設定

---
**最終更新**: 2026年4月16日
**Claude Code バージョン**: 2.1.112
**対応モデル**: Claude Sonnet 4.6, Claude Opus 4.7, Claude Haiku 4.5

*[Claude How To](../) ガイドシリーズの一部*
