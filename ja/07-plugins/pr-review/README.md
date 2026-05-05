<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../../resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="../../resources/logos/claude-howto-logo.svg">
</picture>

# PR レビュープラグイン

セキュリティ・テスト・ドキュメント確認を含む完全な PR レビューワークフロー。

## 機能

✅ セキュリティ分析
✅ テストカバレッジ確認
✅ ドキュメント検証
✅ コード品質評価
✅ パフォーマンス影響分析

## インストール

```bash
/plugin install pr-review
```

## 含まれるもの

### スラッシュコマンド
- `/review-pr` — 包括的な PR レビュー
- `/check-security` — セキュリティ重視のレビュー
- `/check-tests` — テストカバレッジ分析

### サブエージェント
- `security-reviewer` — セキュリティ脆弱性の検出
- `test-checker` — テストカバレッジ分析
- `performance-analyzer` — パフォーマンス影響評価

### MCP サーバー
- PR データ取得のための GitHub 統合

### フック
- `pre-review.js` — レビュー前の検証

## 使い方

### 基本的な PR レビュー
```
/review-pr
```

### セキュリティチェックのみ
```
/check-security
```

### テストカバレッジチェック
```
/check-tests
```

## 要件

- Claude Code 1.0 以上
- GitHub アクセス
- Git リポジトリ

## 設定

GitHub トークンを設定します:
```bash
export GITHUB_TOKEN="your_github_token"
```

## ワークフロー例

```
ユーザー: /review-pr

Claude:
1. レビュー前フックを実行（git リポジトリを検証）
2. GitHub MCP 経由で PR データを取得
3. security-reviewer サブエージェントにセキュリティレビューを委任
4. test-checker サブエージェントにテスト確認を委任
5. performance-analyzer サブエージェントにパフォーマンス確認を委任
6. すべての結果を統合
7. 包括的なレビューレポートを提供

結果:
✅ セキュリティ: 重大な問題なし
⚠️  テスト: カバレッジが 65%、80% 以上を推奨
✅ パフォーマンス: 大きな影響なし
📝 推奨事項: エッジケースのテストを追加
```
