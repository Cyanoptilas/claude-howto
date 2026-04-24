<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../../resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="../../resources/logos/claude-howto-logo.svg">
</picture>

# MCP（Model Context Protocol）

このフォルダには、Claude Code での MCP サーバー設定と使用方法に関する包括的なドキュメントと例が含まれています。

## 概要

MCP（Model Context Protocol）は、Claude が外部ツール・API・リアルタイムデータソースにアクセスするための標準化された方法です。メモリとは異なり、MCP は変化するデータへのライブアクセスを提供します。

主な特徴：
- 外部サービスへのリアルタイムアクセス
- ライブデータ同期
- 拡張可能なアーキテクチャ
- セキュアな認証
- ツールベースのインタラクション

## MCP アーキテクチャ

```mermaid
graph TB
    A["Claude"]
    B["MCP サーバー"]
    C["外部サービス"]

    A -->|リクエスト: list_issues| B
    B -->|クエリ| C
    C -->|データ| B
    B -->|レスポンス| A

    A -->|リクエスト: create_issue| B
    B -->|アクション| C
    C -->|結果| B
    B -->|レスポンス| A

    style A fill:#e1f5fe,stroke:#333,color:#333
    style B fill:#f3e5f5,stroke:#333,color:#333
    style C fill:#e8f5e9,stroke:#333,color:#333
```

## MCP エコシステム

```mermaid
graph TB
    A["Claude"] -->|MCP| B["Filesystem<br/>MCP Server"]
    A -->|MCP| C["GitHub<br/>MCP Server"]
    A -->|MCP| D["Database<br/>MCP Server"]
    A -->|MCP| E["Slack<br/>MCP Server"]
    A -->|MCP| F["Google Docs<br/>MCP Server"]

    B -->|ファイル I/O| G["ローカルファイル"]
    C -->|API| H["GitHub リポジトリ"]
    D -->|クエリ| I["PostgreSQL/MySQL"]
    E -->|メッセージ| J["Slack ワークスペース"]
    F -->|ドキュメント| K["Google ドライブ"]

    style A fill:#e1f5fe,stroke:#333,color:#333
    style B fill:#f3e5f5,stroke:#333,color:#333
    style C fill:#f3e5f5,stroke:#333,color:#333
    style D fill:#f3e5f5,stroke:#333,color:#333
    style E fill:#f3e5f5,stroke:#333,color:#333
    style F fill:#f3e5f5,stroke:#333,color:#333
    style G fill:#e8f5e9,stroke:#333,color:#333
    style H fill:#e8f5e9,stroke:#333,color:#333
    style I fill:#e8f5e9,stroke:#333,color:#333
    style J fill:#e8f5e9,stroke:#333,color:#333
    style K fill:#e8f5e9,stroke:#333,color:#333
```

## MCP インストール方法

### HTTP トランスポート（推奨）

```bash
# 基本的な HTTP 接続
claude mcp add my-server --transport http http://localhost:3000/mcp
```

### stdio トランスポート

```bash
# npx を使って MCP サーバーを追加
claude mcp add github -- npx -y @modelcontextprotocol/server-github

# ローカルサーバーを追加
claude mcp add my-server -- /path/to/server
```

### SSE トランスポート

```bash
claude mcp add my-server --transport sse http://example.com/sse
```

## よく使われる MCP サーバー

### GitHub MCP

```bash
export GITHUB_TOKEN="your_token_here"
claude mcp add github -- npx -y @modelcontextprotocol/server-github
```

### データベース MCP

```bash
export DATABASE_URL="postgresql://user:pass@localhost:5432/db"
claude mcp add database -- npx -y @modelcontextprotocol/server-postgres
```

### ファイルシステム MCP

```bash
claude mcp add filesystem -- npx -y @modelcontextprotocol/server-filesystem /path/to/dir
```

## MCP 管理コマンド

```bash
# すべての MCP サーバーをリスト
claude mcp list

# サーバーを削除
claude mcp remove my-server

# 設定を確認
/mcp
```

## プロジェクト設定（.mcp.json）

プロジェクトルートに `.mcp.json` を作成してチームと MCP 設定を共有できます：

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "${GITHUB_TOKEN}"
      }
    }
  }
}
```

## MCP vs メモリ

| 側面 | MCP | メモリ（CLAUDE.md） |
|------|-----|---------------------|
| **データの鮮度** | リアルタイムライブ | 静的・手動更新 |
| **ユースケース** | API・データベース・外部サービス | プロジェクト設定・ガイドライン |
| **セットアップ** | サーバー設定が必要 | ファイル作成のみ |
| **永続性** | サービス依存 | ファイルシステム |

## 関連ガイド

- [メモリ](../02-memory/) — CLAUDE.md による永続的なコンテキスト
- [フック](../06-hooks/) — MCP イベントへの自動レスポンス
- [サブエージェント](../04-subagents/) — MCP ツールを使うエージェント

---
**最終更新**: 2026年4月16日
**Claude Code バージョン**: 2.1.112
**対応モデル**: Claude Sonnet 4.6, Claude Opus 4.7, Claude Haiku 4.5

*[Claude How To](../) ガイドシリーズの一部*
