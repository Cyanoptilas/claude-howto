---
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git commit:*), Bash(git diff:*)
argument-hint: [message]
description: コンテキスト付きで git コミットを作成する
---

## コンテキスト

- 現在の git ステータス: !`git status`
- 現在の git 差分: !`git diff HEAD`
- 現在のブランチ: !`git branch --show-current`
- 最近のコミット: !`git log --oneline -10`

## タスク

上記の変更に基づいて、単一の git コミットを作成してください。

引数でメッセージが提供された場合はそれを使用してください: $ARGUMENTS

それ以外の場合は、変更を分析して Conventional Commits 形式の適切なコミットメッセージを作成してください：
- `feat:` 新機能の追加
- `fix:` バグ修正
- `docs:` ドキュメントの変更
- `refactor:` コードのリファクタリング
- `test:` テストの追加
- `chore:` メンテナンス作業

---
**最終更新**: 2026年4月9日
