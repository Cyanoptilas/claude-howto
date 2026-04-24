---
description: すべての変更をステージングし、コミットを作成してリモートにプッシュする（注意して使用）
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git commit:*), Bash(git push:*), Bash(git diff:*), Bash(git log:*), Bash(git pull:*)
---

# すべてをコミットしてプッシュ

⚠️ **注意**: すべての変更をステージングし、コミットし、リモートにプッシュします。すべての変更がまとめて属していると確信している場合のみ使用してください。

## ワークフロー

### 1. 変更を分析

並行して実行：
- `git status` — 変更/追加/削除/未追跡のファイルを表示
- `git diff --stat` — 変更の統計を表示
- `git log -1 --oneline` — メッセージスタイルの参考に最新コミットを表示

### 2. セーフティチェック

**❌ 検出された場合は停止して警告：**
- シークレット: `.env*`、`*.key`、`*.pem`、`credentials.json`、`secrets.yaml`、`id_rsa`、`*.p12`、`*.pfx`、`*.cer`
- API キー: 実際の値を持つ `*_API_KEY`、`*_SECRET`、`*_TOKEN` 変数（`your-api-key`、`xxx`、`placeholder` などのプレースホルダーは除く）
- 大きなファイル: Git LFS なしの `>10MB`
- ビルド成果物: `node_modules/`、`dist/`、`build/`、`__pycache__/`、`*.pyc`、`.venv/`
- 一時ファイル: `.DS_Store`、`thumbs.db`、`*.swp`、`*.tmp`

**✅ 確認：**
- `.gitignore` が適切に設定されている
- マージコンフリクトなし
- 正しいブランチ（main/master の場合は警告）
- API キーはプレースホルダーのみ

### 3. 確認を要求

サマリーを提示：
```
📊 変更サマリー:
- X ファイル変更, Y 追加, Z 削除
- 合計: +AAA 追加, -BBB 削除

🔒 安全性: ✅ シークレットなし | ✅ 大ファイルなし | ⚠️ [警告]
🌿 ブランチ: [name] → origin/[name]

実行内容: git add . → コミット → プッシュ

続行するには 'yes'、キャンセルするには 'no' と入力してください。
```

**明示的な "yes" を待ってから続行すること。**

### 4. 実行（確認後）

```bash
git add .
git status  # ステージングを確認
```

### 5. コミットメッセージを生成

変更を分析して Conventional Commit を作成：

**形式：**
```
[type]: 短い概要（最大72文字）

- 主な変更点 1
- 主な変更点 2
- 主な変更点 3
```

**タイプ:** `feat`、`fix`、`docs`、`style`、`refactor`、`test`、`chore`、`perf`、`build`、`ci`

### 6. コミットしてプッシュ

```bash
git commit -m "$(cat <<'EOF'
[生成されたコミットメッセージ]
EOF
)"
git push  # 失敗した場合: git pull --rebase && git push
git log -1 --oneline --decorate  # 確認
```

## 使用すべきとき

✅ **適切なケース：**
- 複数ファイルのドキュメント更新
- テストとドキュメント付きの機能
- ファイルをまたぐバグ修正
- プロジェクト全体のフォーマット/リファクタリング
- 設定の変更

❌ **避けるべきケース：**
- 何がコミットされるか不明な場合
- シークレット/機密データを含む場合
- レビューなしの保護ブランチ
- マージコンフリクトが存在する場合
- 細かいコミット履歴が必要な場合
- Pre-commit フックが失敗している場合

---
**最終更新**: 2026年4月9日
