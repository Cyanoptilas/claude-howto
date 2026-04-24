<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="../resources/logos/claude-howto-logo.svg">
</picture>

# Claude How To へのコントリビューション

このプロジェクトへのコントリビューションに興味を持っていただきありがとうございます！このガイドは効果的にコントリビューションする方法を理解するのに役立ちます。

## このプロジェクトについて

Claude How To は、Claude Code のビジュアルで事例主導のガイドです。以下を提供しています：
- 機能の仕組みを説明する **Mermaid ダイアグラム**
- すぐに使える**本番環境対応テンプレート**
- コンテキストとベストプラクティスを含む**実際の例**
- 初級から上級への**段階的学習パス**

## コントリビューションの種類

### 1. 新しい例やテンプレート
既存の機能の例を追加（スラッシュコマンド・スキル・フックなど）：
- コピーペーストできるコード
- 動作方法の明確な説明
- ユースケースとメリット
- トラブルシューティングのヒント

### 2. ドキュメントの改善
- わかりにくいセクションを明確にする
- タイポや文法を修正する
- 不足している情報を追加する
- コードの例を改善する

### 3. 機能ガイド
新しい Claude Code 機能のガイドを作成：
- ステップバイステップのチュートリアル
- アーキテクチャダイアグラム
- 一般的なパターンとアンチパターン
- 実際のワークフロー

### 4. バグレポート
発生した問題を報告：
- 期待したことを説明する
- 実際に起きたことを説明する
- 再現手順を含める
- Claude Code のバージョンと OS を追加する

### 5. フィードバックと提案
ガイドの改善に協力：
- より良い説明を提案する
- カバレッジのギャップを指摘する
- 新しいセクションや再編成を推薦する

## 始め方

### 1. フォークとクローン

```bash
git clone https://github.com/luongnv89/claude-howto.git
cd claude-howto
```

### 2. 開発環境のセットアップ

```bash
# uv をインストール
pip install uv

# 仮想環境を作成
uv venv
source .venv/bin/activate

# 依存関係をインストール
uv pip install -r scripts/requirements-dev.txt

# マークダウンリンターをインストール
npm install -g markdownlint-cli

# pre-commit フックをインストール
uv pip install pre-commit
pre-commit install
```

### 3. ブランチを作成

```bash
git checkout -b add/feature-name
git checkout -b fix/bug-description
git checkout -b docs/improvement
```

### 4. 変更を加える

コンテンツガイドラインに従ってください：
- すべての Mermaid ダイアグラムが正しい構文であること
- コードフェンスに言語を指定すること（例：` ```bash `、` ```python `）
- 内部リンクに相対パスを使用すること
- 適切に形式化された Conventional Commits に従うこと

### 5. 品質チェック

```bash
pre-commit run --all-files
```

### 6. コミットとプッシュ

```bash
git add .
git commit -m "feat(hooks): Add database backup hook example"
git push origin add/feature-name
```

### 7. Pull Request を作成

変更内容の明確な説明と PR を作成してください：
- 何を変更したか
- なぜ変更したか
- テスト方法

## コンテンツガイドライン

### モジュールの構造

各番号付きフォルダはこのパターンに従います：
- **README.md** — 例付きの機能概要
- **例示ファイル** — コピーペーステンプレート（コマンドは `.md`、設定は `.json`、フックは `.sh`）

### コミット規則

Conventional Commits 形式に従ってください：
- `feat(slash-commands): Add API documentation generator`
- `docs(memory): Improve personal preferences example`
- `fix(README): Correct table of contents link`
- `refactor(hooks): Simplify hook configuration examples`

スコープは該当する場合はフォルダ名と一致させてください。

## コミュニティ基準

- [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) — メンバー間の接し方
- [SECURITY.md](SECURITY.md) — セキュリティポリシーと脆弱性の報告

## セキュリティ問題の報告

セキュリティの脆弱性を発見した場合は、責任を持って報告してください：
1. パブリックな Issue は開かないでください
2. GitHub のプライベート脆弱性レポートを使用してください

---
**最終更新**: 2026年4月16日
