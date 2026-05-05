<picture>
  <source media="(prefers-color-scheme: dark)" srcset="resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="resources/logos/claude-howto-logo.svg">
</picture>

# 参考リソース一覧

## 公式ドキュメント

| リソース | 説明 | リンク |
|----------|-------------|------|
| Claude Code Docs | Claude Code 公式ドキュメント | [code.claude.com/docs/en/overview](https://code.claude.com/docs/en/overview) |
| Anthropic Docs | Anthropic 全体ドキュメント | [docs.anthropic.com](https://docs.anthropic.com) |
| MCP Protocol | Model Context Protocol 仕様 | [modelcontextprotocol.io](https://modelcontextprotocol.io) |
| MCP Servers | 公式 MCP サーバー実装 | [github.com/modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) |
| Anthropic Cookbook | コード例とチュートリアル | [github.com/anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook) |
| Claude Code Skills | コミュニティスキルリポジトリ | [github.com/anthropics/skills](https://github.com/anthropics/skills) |
| Agent Teams | マルチエージェントの調整・協調 | [code.claude.com/docs/en/agent-teams](https://code.claude.com/docs/en/agent-teams) |
| Scheduled Tasks | `/loop` と cron を使った定期タスク | [code.claude.com/docs/en/scheduled-tasks](https://code.claude.com/docs/en/scheduled-tasks) |
| Chrome Integration | ブラウザ自動化 | [code.claude.com/docs/en/chrome](https://code.claude.com/docs/en/chrome) |
| Keybindings | キーボードショートカットのカスタマイズ | [code.claude.com/docs/en/keybindings](https://code.claude.com/docs/en/keybindings) |
| Desktop App | ネイティブデスクトップアプリ | [code.claude.com/docs/en/desktop](https://code.claude.com/docs/en/desktop) |
| Remote Control | リモートセッション制御 | [code.claude.com/docs/en/remote-control](https://code.claude.com/docs/en/remote-control) |
| Auto Mode | 自動パーミッション管理 | [code.claude.com/docs/en/permissions](https://code.claude.com/docs/en/permissions) |
| Channels | マルチチャンネルコミュニケーション | [code.claude.com/docs/en/channels](https://code.claude.com/docs/en/channels) |
| Voice Dictation | 音声入力 | [code.claude.com/docs/en/voice-dictation](https://code.claude.com/docs/en/voice-dictation) |

## Anthropic エンジニアリングブログ

| 記事 | 説明 | リンク |
|---------|-------------|------|
| Code Execution with MCP | MCP のコンテキスト膨張をコード実行で解決する方法 — トークンを 98.7% 削減 | [anthropic.com/engineering/code-execution-with-mcp](https://www.anthropic.com/engineering/code-execution-with-mcp) |

---

## Claude Code を 30 分でマスターする

_動画_: https://www.youtube.com/watch?v=6eBSHbLKuN0

_**主なヒント**_

- **高度な機能とショートカットを探索する**
  - リリースノートで Claude の新しいコード編集・コンテキスト機能を定期的に確認する
  - キーボードショートカットを習得して、チャット・ファイル・エディタビューを素早く切り替える

- **効率的なセットアップ**
  - 明確な名前・説明でプロジェクト固有のセッションを作成し、簡単に取得できるようにする
  - よく使うファイルやフォルダをピン留めして、Claude がいつでもアクセスできるようにする
  - GitHub や人気 IDE との統合をセットアップしてコーディングプロセスを効率化する

- **コードベースへの効果的な Q&A**
  - アーキテクチャ・デザインパターン・特定モジュールについて詳細な質問をする
  - 質問にファイルと行番号の参照を含める（例: "`app/models/user.py` のロジックは何をしていますか？"）
  - 大規模なコードベースでは、Claude が集中できるようにサマリーやマニフェストを提供する

- **コード編集とリファクタリング**
  - コードブロック内のインラインコメントやリクエストを使って集中した編集を行う
  - 変更前後の比較を依頼する
  - 品質保証のために主要な編集後はテストやドキュメントの生成を依頼する

- **コンテキスト管理**
  - 現在のタスクに関連するコード・コンテキストのみを貼り付ける
  - 構造化されたプロンプトを使う（"ファイル A があり、関数 B があり、質問は X です"）
  - コンテキスト制限を超えないように大きなファイルを折りたたむ

- **チームツールの統合**
  - Claude セッションをチームのリポジトリとドキュメントに接続する
  - 繰り返しのエンジニアリングタスクに組み込みテンプレートやカスタムテンプレートを使用する
  - セッションのトランスクリプトとプロンプトをチームメンバーと共有する

- **パフォーマンスの向上**
  - 明確で目標指向の指示を与える（例: "このクラスを5つの箇条書きでまとめて"）
  - コンテキストウィンドウから不要なコメントや定型文を取り除く
  - 出力がずれたら、コンテキストをリセットするか質問を言い換える

---

## 新機能・新機能（2026年3月）

### 主要な機能リソース

| 機能 | 説明 | 詳細 |
|---------|-------------|------------|
| **Auto Memory** | Claude がセッション間でユーザーの好みを自動的に学習・記憶する | [メモリガイド](02-memory/) |
| **Remote Control** | 外部ツールやスクリプトから Claude Code セッションをプログラム的に制御する | [高度な機能](09-advanced-features/) |
| **Web Sessions** | リモート開発のためブラウザベースのインターフェースで Claude Code にアクセスする | [CLI リファレンス](10-cli/) |
| **Desktop App** | 強化された UI を持つ Claude Code のネイティブデスクトップアプリ | [Claude Code Docs](https://code.claude.com/docs/en/desktop) |
| **Extended Thinking** | `Alt+T`/`Option+T` または `MAX_THINKING_TOKENS` 環境変数で深い推論を有効化 | [高度な機能](09-advanced-features/) |
| **Permission Modes** | 細かな制御: default・acceptEdits・plan・auto・dontAsk・bypassPermissions | [高度な機能](09-advanced-features/) |
| **7 層メモリ** | Managed Policy・Project・Project Rules・User・User Rules・Local・Auto Memory | [メモリガイド](02-memory/) |
| **Hook Events** | 25 イベント: PreToolUse・PostToolUse・Stop・SubagentStart など | [フックガイド](06-hooks/) |
| **Agent Teams** | 複雑なタスクで複数のエージェントを調整して協力させる | [サブエージェントガイド](04-subagents/) |
| **Scheduled Tasks** | `/loop` と cron ツールで定期タスクを設定する | [高度な機能](09-advanced-features/) |
| **Chrome Integration** | ヘッドレス Chromium によるブラウザ自動化 | [高度な機能](09-advanced-features/) |
| **Keyboard Customization** | コードシーケンスを含むキーバインドのカスタマイズ | [高度な機能](09-advanced-features/) |
| **Monitor Tool** | バックグラウンドコマンドの stdout をストリーム監視してイベントに反応する（v2.1.98+） | [高度な機能](09-advanced-features/) |

---
**最終更新**: 2026年4月16日
**Claude Code バージョン**: 2.1.112
**互換モデル**: Claude Sonnet 4.6・Claude Opus 4.7・Claude Haiku 4.5
