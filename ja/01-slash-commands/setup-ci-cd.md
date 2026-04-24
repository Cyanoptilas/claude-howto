---
name: CI/CD パイプラインセットアップ
description: 品質保証のための pre-commit フックと GitHub Actions を実装する
tags: ci-cd, devops, automation
---

# CI/CD パイプラインセットアップ

プロジェクトの種類に合わせた包括的な DevOps 品質ゲートを実装してください：

1. **プロジェクトを分析**: 言語・フレームワーク・ビルドシステム・既存ツールを検出
2. **言語固有のツールで pre-commit フックを設定**:
   - フォーマット: Prettier/Black/gofmt/rustfmt 等
   - リンティング: ESLint/Ruff/golangci-lint/Clippy 等
   - セキュリティ: Bandit/gosec/cargo-audit/npm audit 等
   - 型チェック: TypeScript/mypy/flow（該当する場合）
   - テスト: 関連するテストスイートを実行
3. **GitHub Actions ワークフローを作成** (.github/workflows/):
   - プッシュ/PR 時に pre-commit チェックを反映
   - マルチバージョン/プラットフォームマトリックス（該当する場合）
   - ビルドとテストの検証
   - デプロイ手順（必要な場合）
4. **パイプラインを検証**: ローカルでテスト・テスト PR を作成・すべてのチェックが通ることを確認

無料/オープンソースツールを使用してください。既存の設定を尊重し、実行を高速に保ってください。

---
**最終更新**: 2026年4月9日
