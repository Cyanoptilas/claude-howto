# プロジェクト設定

## プロジェクト概要
- **名前**: E コマースプラットフォーム
- **技術スタック**: Node.js, PostgreSQL, React 18, Docker
- **チームサイズ**: 5人の開発者
- **締め切り**: Q4 2025

## アーキテクチャ
@docs/architecture.md
@docs/api-standards.md
@docs/database-schema.md

## 開発標準

### コードスタイル
- フォーマットに Prettier を使用
- airbnb config の ESLint を使用
- 最大行長: 100文字
- インデント: 2スペース

### 命名規則
- **ファイル**: kebab-case（user-controller.js）
- **クラス**: PascalCase（UserService）
- **関数/変数**: camelCase（getUserById）
- **定数**: UPPER_SNAKE_CASE（API_BASE_URL）
- **データベーステーブル**: snake_case（user_accounts）

### Git ワークフロー
- ブランチ名: `feature/description` または `fix/description`
- コミットメッセージ: Conventional Commits に従う
- マージ前に PR 必須
- すべての CI/CD チェックが通ること
- 最低1名の承認が必要

### テスト要件
- 最低80%のコードカバレッジ
- すべてのクリティカルパスにテストが必要
- ユニットテストに Jest を使用
- E2E テストに Cypress を使用
- テストファイル名: `*.test.ts` または `*.spec.ts`

### API 標準
- RESTful エンドポイントのみ
- JSON リクエスト/レスポンス
- HTTP ステータスコードを正しく使用
- API エンドポイントのバージョニング: `/api/v1/`
- すべてのエンドポイントを例付きでドキュメント化

### データベース
- スキーマ変更にはマイグレーションを使用
- 認証情報のハードコードは禁止
- コネクションプーリングを使用
- 開発環境でクエリログを有効化
- 定期的なバックアップが必要

### デプロイ
- Docker ベースのデプロイ
- Kubernetes オーケストレーション
- ブルーグリーンデプロイ戦略
- 障害時の自動ロールバック
- デプロイ前にデータベースマイグレーションを実行

## よく使うコマンド

| コマンド | 用途 |
|---------|---------|
| `npm run dev` | 開発サーバーを起動 |
| `npm test` | テストスイートを実行 |
| `npm run lint` | コードスタイルをチェック |
| `npm run build` | 本番用にビルド |
| `npm run migrate` | データベースマイグレーションを実行 |

## チーム連絡先
- テックリード: Sarah Chen (@sarah.chen)
- プロダクトマネージャー: Mike Johnson (@mike.j)
- DevOps: Alex Kim (@alex.k)

## 既知の問題と回避策
- ピーク時に PostgreSQL コネクションプーリングが20に制限される
- 回避策: クエリキューを実装
- async generators に対する Safari 14 の互換性問題
- 回避策: Babel トランスパイラを使用

## 関連プロジェクト
- アナリティクスダッシュボード: `/projects/analytics`
- モバイルアプリ: `/projects/mobile`
- 管理パネル: `/projects/admin`

---
**最終更新**: 2026年4月9日
