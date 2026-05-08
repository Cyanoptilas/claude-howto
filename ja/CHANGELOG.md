# Changelog

## v2.1.112 — 2026-04-16

### ハイライト

- 英語チュートリアルを Claude Code v2.1.112 と新しい Opus 4.7 モデル（`claude-opus-4-7`）に同期。新しい `xhigh` エフォートレベル（Opus 4.7 のデフォルト、`high` と `max` の間）、2つの新しい組み込みスラッシュコマンド（`/ultrareview`、`/less-permission-prompts`）、Opus 4.7 の Max サブスクライバー向けに `--enable-auto-mode` が不要になった自動モード、Windows 上の PowerShell ツール、「Auto（match terminal）」テーマ、プロンプトにちなんだ名前のプランファイルを含む。18の英語ドキュメントフッターを Claude Code v2.1.112 に更新。@Luong NGUYEN

### 機能

- ウクライナ語（uk）のローカライゼーションをすべてのモジュール・ルートドキュメント・例・参照に追加（039dde2）@Evgenij I

### バグ修正

- pre-tool-check.sh フックプロトコルのバグを修正（bce7cf8）@yarlinghe
- CI を通過させるために不正な mermaid の例をテキストブロックに変更（b8a7b1f）@Evgenij I
- ウクライナ語 claude_concepts_guide.md の目次の CP1251 エンコーディングを修正（d970cc6）@Evgenij I
- スタブのウクライナ語 README を完全な翻訳に置き換え、壊れたアンカーを修正（f6d73e2）@Evgenij I
- すべてのフッターの Claude Code バージョンを 2.1.97 に修正（63a1416）@Luong NGUYEN
- 2026-04-09 のドキュメント精度更新を適用（e015f39）@Luong NGUYEN

### ドキュメント

- Claude Code v2.1.112 に同期（Opus 4.7、`xhigh` エフォート、`/ultrareview`、`/less-permission-prompts`、PowerShell ツール、Auto-match-terminal テーマ）@Luong NGUYEN
- Claude Code v2.1.110 に同期（TUI、プッシュ通知、セッションリキャップ）（15f0085）@Luong NGUYEN
- Claude Code v2.1.101 に `/team-onboarding`、`/ultraplan`、Monitor ツールで同期（2deba3a）@Luong NGUYEN
- ベトナム語ドキュメントを英語ソースと同期（561c6cb）@Thiên Toán
- すべてのファイルの最終更新日と Claude Code バージョンを更新（7f2e773）@Luong NGUYEN
- 言語スイッチャーにウクライナ語リンクを追加（9c224ff）@Luong NGUYEN
- コントリビューターセクションを削除（f07313d）@Luong NGUYEN
- GitHub メトリクスを 21,800+ スター、2,585+ フォークに更新（4f55374）@Luong NGUYEN

**Full Changelog**: https://github.com/luongnv89/claude-howto/compare/v2.3.0...v2.1.112

---

## v2.3.0 — 2026-04-07

### 機能

- 言語ごとに EPUB アーティファクトをビルドして公開（90e9c30）@Thiên Toán
- 06-hooks に不足していた pre-tool-check.sh フックを追加（b511ed1）@JiayuWang
- zh/ ディレクトリに中国語翻訳を追加（89e89d4）@Luong NGUYEN
- performance-optimizer サブエージェントと dependency-check フックを追加（f53d080）@qk

### バグ修正

- Windows Git Bash 互換性 + stdin JSON プロトコル（2cbb10c）@Luong NGUYEN
- 08-checkpoints の autoCheckpoint 設定ドキュメントを修正（749c79f）@JiayuWang
- プレースホルダーに置き換える代わりに SVG 画像を埋め込む（1b16709）@Thiên Toán
- memory README のネストされたコードフェンスレンダリング（ce24423）@Zhaoshan Duan
- スカッシュマージで削除されたレビュー修正を適用（34259ca）@Luong NGUYEN
- フックスクリプトを Windows Git Bash 互換にして stdin JSON プロトコルを使用（107153d）@binyu li

### ドキュメント

- すべてのチュートリアルを最新の Claude Code ドキュメント（2026年4月）と同期（72d3b01）@Luong NGUYEN
- 言語スイッチャーに中国語リンクを追加（6cbaa4d）@Luong NGUYEN
- 英語とベトナム語間の言語スイッチャーを追加（100c45e）@Luong NGUYEN
- GitHub #1 トレンドバッジを追加（0ca8c37）@Luong NGUYEN

**Full Changelog**: https://github.com/luongnv89/claude-howto/compare/v2.2.0...v2.3.0

---

## v2.2.0 — 2026-03-26

### ドキュメント

- すべてのチュートリアルと参照を Claude Code v2.1.84 と同期（f78c094）@luongnv89
  - スラッシュコマンドを 55+ 組み込み + 5 バンドルスキルに更新、3つを非推奨としてマーク
  - フックイベントを 18 から 25 に拡大、`agent` フックタイプを追加（合計4タイプ）
  - 高度な機能に Auto Mode、Channels、Voice Dictation を追加
  - `effort`、`shell` スキルフロントマターフィールド; `initialPrompt`、`disallowedTools` エージェントフィールドを追加

### バグ修正

- CI コンプライアンスのために cSpell ワードと README セクションを追加（93f9d51）@luongnv89

**Full Changelog**: https://github.com/luongnv89/claude-howto/compare/v2.1.1...v2.2.0

---

## v2.1.0 — 2026-03-13

### 機能

- 自己評価とレッスンクイズスキルで適応型学習パスを追加（1ef46cd）@luongnv89
  - `/self-assessment` — 10の機能エリアにわたるインタラクティブな習熟度クイズとパーソナライズされた学習パス
  - `/lesson-quiz [lesson]` — 8〜10の的を絞った質問によるレッスンごとの知識チェック

**Full Changelog**: https://github.com/luongnv89/claude-howto/compare/v2.0.0...v2.1.0

---

## v2.0.0 — 2026-02-01

### 機能

- Claude Code 2026年2月の機能ですべてのドキュメントを同期（487c96d）
  - **Auto Memory**・**Remote Control**・**Web Sessions**・**Desktop App** のドキュメントを追加
  - **Agent Teams**（実験的なマルチエージェント協調）のドキュメントを追加
  - **MCP OAuth 2.0**・**Tool Search**・**Claude.ai Connectors** のドキュメントを追加
  - **HTTP Hooks** と 7 つの新しいフックイベントのドキュメントを追加
  - 17 の新しいスラッシュコマンドを文書化（`/fork`、`/desktop`、`/teleport`、`/tasks`、`/fast` など）

### バグ修正・修正

- モデル名を更新：Sonnet 4.5 → **Sonnet 4.6**、Opus 4.5 → **Opus 4.6**
- パーミッションモード名を修正：架空の名前を実際の `default`/`acceptEdits`/`plan`/`dontAsk`/`bypassPermissions` に置き換え
- チェックポイントコマンドを修正：架空のコマンドを実際の `Esc+Esc` / `/rewind` インターフェースに置き換え

**Full Changelog**: https://github.com/luongnv89/claude-howto/compare/20779db...v2.0.0
