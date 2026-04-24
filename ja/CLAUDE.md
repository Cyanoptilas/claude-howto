# CLAUDE.md

このファイルは、このリポジトリのコードを扱う際に Claude Code (claude.ai/code) へのガイダンスを提供します。

## プロジェクト概要

Claude How To は、Claude Code の機能を解説するチュートリアルリポジトリです。これは **documentation-as-code（コードとしてのドキュメント）** であり、実行可能なアプリケーションではなく、番号付きの学習モジュールに整理された Markdown ファイルが主な成果物です。

**アーキテクチャ**: 各モジュール（01〜10）は、コピー＆ペースト用テンプレート・Mermaid 図・サンプルを用いて、Claude Code の特定の機能を解説します。ビルドシステムはドキュメントの品質を検証し、EPUB 電子書籍を生成します。

## よく使うコマンド

### コミット前の品質チェック

すべてのドキュメントは、コミット前に4つの品質チェックを通過する必要があります（pre-commit フックにより自動実行されます）:

```bash
# pre-commit フックのインストール（コミットごとに実行）
pre-commit install

# 全チェックを手動実行
pre-commit run --all-files
```

4つのチェック項目:
1. **markdown-lint** — `markdownlint` による Markdown の構造とフォーマット検証
2. **cross-references** — 内部リンク・アンカー・コードフェンス構文の検証（Python スクリプト）
3. **mermaid-syntax** — すべての Mermaid 図が正しく解析されるか検証（Python スクリプト）
4. **link-check** — 外部 URL の到達可能性確認（Python スクリプト）
5. **build-epub** — EPUB がエラーなく生成されるか確認（`.md` ファイルの変更時）

### 開発環境のセットアップ

```bash
# uv（Python パッケージマネージャー）のインストール
pip install uv

# 仮想環境の作成と Python 依存パッケージのインストール
uv venv
source .venv/bin/activate
uv pip install -r scripts/requirements-dev.txt

# Node.js ツール（Markdown リンターと Mermaid バリデーター）のインストール
npm install -g markdownlint-cli
npm install -g @mermaid-js/mermaid-cli

# pre-commit フックのインストール
uv pip install pre-commit
pre-commit install
```

### テスト

`scripts/` 内の Python スクリプトにはユニットテストが含まれています:

```bash
# 全テストを実行
pytest scripts/tests/ -v

# カバレッジ付きで実行
pytest scripts/tests/ -v --cov=scripts --cov-report=html

# 特定のテストを実行
pytest scripts/tests/test_build_epub.py -v
```

### コード品質

```bash
# Python コードのリントとフォーマット
ruff check scripts/
ruff format scripts/

# セキュリティスキャン
bandit -c scripts/pyproject.toml -r scripts/ --exclude scripts/tests/

# 型チェック
mypy scripts/ --ignore-missing-imports
```

### EPUB ビルド

```bash
# 電子書籍の生成（Kroki.io API で Mermaid 図をレンダリング）
uv run scripts/build_epub.py

# オプション付きで実行
uv run scripts/build_epub.py --verbose --output custom-name.epub --max-concurrent 5
```

## ディレクトリ構成

```
├── 01-slash-commands/      # ユーザーが呼び出すショートカット
├── 02-memory/              # 永続コンテキストのサンプル
├── 03-skills/              # 再利用可能な機能
├── 04-subagents/           # 特化型 AI アシスタント
├── 05-mcp/                 # Model Context Protocol のサンプル
├── 06-hooks/               # イベント駆動型自動化
├── 07-plugins/             # バンドル機能
├── 08-checkpoints/         # セッションスナップショット
├── 09-advanced-features/   # 計画・思考・バックグラウンド処理
├── 10-cli/                 # CLI リファレンス
├── scripts/
│   ├── build_epub.py           # EPUB ジェネレーター（Kroki API で Mermaid をレンダリング）
│   ├── check_cross_references.py   # 内部リンクの検証
│   ├── check_links.py          # 外部 URL のチェック
│   ├── check_mermaid.py        # Mermaid 構文の検証
│   └── tests/                  # スクリプトのユニットテスト
├── .pre-commit-config.yaml    # 品質チェックの定義
└── README.md               # メインガイド（モジュールインデックスも兼ねる）
```

## コンテンツガイドライン

### モジュール構成
各番号付きフォルダーは以下のパターンに従います:
- **README.md** — サンプルを含む機能の概要
- **サンプルファイル** — コピー＆ペースト用テンプレート（コマンド用の `.md`、設定用の `.json`、フック用の `.sh`）
- ファイルは機能の複雑さと依存関係に基づいて整理されています

### Mermaid 図
- すべての図は正常に解析される必要があります（pre-commit フックにより確認）
- EPUB ビルドは Kroki.io API を通じて図をレンダリングします（インターネット接続が必要）
- フローチャート・シーケンス図・アーキテクチャビジュアルに Mermaid を使用してください

### クロスリファレンス
- 内部リンクには相対パスを使用してください（例: `(01-slash-commands/README.md)`）
- コードフェンスには言語を指定してください（例: ` ```bash `、` ```python `）
- アンカーリンクは `#heading-name` 形式を使用します

### リンク検証
- 外部 URL は到達可能である必要があります（pre-commit フックにより確認）
- 一時的なコンテンツへのリンクは避けてください
- 可能な限りパーマリンクを使用してください

## アーキテクチャの重要ポイント

1. **番号付きフォルダーは学習順序を示します** — 01〜10 のプレフィックスは、Claude Code の機能を学ぶ推奨順序を表します。この番号付けは意図的なものであり、アルファベット順に並べ替えないでください。

2. **スクリプトはユーティリティであり、製品ではありません** — `scripts/` 内の Python スクリプトはドキュメントの品質と EPUB 生成をサポートします。実際のコンテンツは番号付きモジュールフォルダーにあります。

3. **pre-commit がゲートキーパーです** — PR が受け入れられるには、4つの品質チェックをすべて通過する必要があります。CI パイプラインはこれらと同じチェックを第二の関門として実行します。

4. **Mermaid のレンダリングにはネットワークが必要です** — EPUB ビルドは Kroki.io API を呼び出して図をレンダリングします。ここでのビルド失敗は、通常ネットワークの問題か Mermaid 構文の誤りが原因です。

5. **これはチュートリアルであり、ライブラリではありません** — コンテンツを追加する際は、明確な説明・コピー＆ペースト用サンプル・視覚的な図に重点を置いてください。価値はコンセプトを教えることにあり、再利用可能なコードを提供することではありません。

## コミット規約

Conventional Commits 形式に従ってください:
- `feat(slash-commands): Add API documentation generator`
- `docs(memory): Improve personal preferences example`
- `fix(README): Correct table of contents link`
- `refactor(hooks): Simplify hook configuration examples`

スコープは、該当する場合はフォルダー名に合わせてください。
