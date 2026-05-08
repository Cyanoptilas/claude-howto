<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../../resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="../../resources/logos/claude-howto-logo.svg">
</picture>

# ドキュメントプラグイン

プロジェクトのための包括的なドキュメント生成・保守。

## 機能

✅ API ドキュメント生成
✅ README の作成・更新
✅ ドキュメントの同期
✅ コードコメントの改善
✅ サンプルコードの生成

## インストール

```bash
/plugin install documentation
```

## 含まれるもの

### スラッシュコマンド
- `/generate-api-docs` — API ドキュメントの生成
- `/generate-readme` — README の作成または更新
- `/sync-docs` — コード変更に合わせたドキュメントの同期
- `/validate-docs` — ドキュメントの検証

### サブエージェント
- `api-documenter` — API ドキュメントスペシャリスト
- `code-commentator` — コードコメントの改善
- `example-generator` — サンプルコードの作成

### テンプレート
- `api-endpoint.md` — API エンドポイントドキュメントテンプレート
- `function-docs.md` — 関数ドキュメントテンプレート
- `adr-template.md` — アーキテクチャ決定記録テンプレート

### MCP サーバー
- ドキュメント同期のための GitHub 統合

## 使い方

### API ドキュメントの生成
```
/generate-api-docs
```

### README の作成
```
/generate-readme
```

### ドキュメントの同期
```
/sync-docs
```

### ドキュメントの検証
```
/validate-docs
```

## 要件

- Claude Code 1.0 以上
- GitHub アクセス（オプション）

## ワークフロー例

```
ユーザー: /generate-api-docs

Claude:
1. /src/api/ 内のすべての API エンドポイントをスキャン
2. api-documenter サブエージェントに委任
3. 関数シグネチャと JSDoc を抽出
4. モジュール/エンドポイントごとに整理
5. api-endpoint.md テンプレートを使用
6. 包括的な Markdown ドキュメントを生成
7. curl・JavaScript・Python のサンプルを追加

結果:
✅ API ドキュメント生成完了
📄 作成されたファイル:
   - docs/api/users.md
   - docs/api/auth.md
   - docs/api/products.md
📊 カバレッジ: 23/23 エンドポイントを文書化
```

## テンプレートの使い方

### API エンドポイントテンプレート
REST API エンドポイントを完全なサンプル付きで文書化する際に使用します。

### 関数ドキュメントテンプレート
個々の関数やメソッドを文書化する際に使用します。

### ADR テンプレート
アーキテクチャの決定を記録する際に使用します。

## 設定

ドキュメント同期のために GitHub トークンを設定します:
```bash
export GITHUB_TOKEN="your_github_token"
```

## ベストプラクティス

- ドキュメントはコードに近い場所に保管する
- コード変更時にドキュメントも更新する
- 実践的なサンプルを含める
- 定期的に検証する
- 一貫性のためにテンプレートを使用する
