---
description: コードのクリーンアップ、変更のステージング、Pull Request の準備をする
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git diff:*), Bash(npm test:*), Bash(npm run lint:*)
---

# Pull Request 準備チェックリスト

PR を作成する前に以下の手順を実行してください：

1. リンティングを実行: `prettier --write .`
2. テストを実行: `npm test`
3. git 差分をレビュー: `git diff HEAD`
4. 変更をステージング: `git add .`
5. Conventional Commits に従ったコミットメッセージを作成:
   - `fix:` バグ修正
   - `feat:` 新機能
   - `docs:` ドキュメント
   - `refactor:` コードの再構成
   - `test:` テストの追加
   - `chore:` メンテナンス

6. 以下を含む PR サマリーを生成:
   - 何が変更されたか
   - なぜ変更されたか
   - 実施したテスト
   - 潜在的な影響

---
**最終更新**: 2026年4月9日
