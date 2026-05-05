<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../../resources/logos/claude-howto-logo-dark.svg">
  <img alt="Claude How To" src="../../resources/logos/claude-howto-logo.svg">
</picture>

# DevOps 自動化プラグイン

デプロイ・監視・インシデント対応のための完全な DevOps 自動化。

## 機能

✅ 自動デプロイ
✅ ロールバック手順
✅ システムヘルス監視
✅ インシデント対応ワークフロー
✅ Kubernetes 統合

## インストール

```bash
/plugin install devops-automation
```

## 含まれるもの

### スラッシュコマンド
- `/deploy` — 本番またはステージングへのデプロイ
- `/rollback` — 前のバージョンへのロールバック
- `/status` — システムヘルス確認
- `/incident` — 本番インシデントの対応

### サブエージェント
- `deployment-specialist` — デプロイ操作
- `incident-commander` — インシデント調整
- `alert-analyzer` — システムヘルス分析

### MCP サーバー
- Kubernetes 統合

### スクリプト
- `deploy.sh` — デプロイ自動化
- `rollback.sh` — ロールバック自動化
- `health-check.sh` — ヘルスチェックユーティリティ

### フック
- `pre-deploy.js` — デプロイ前の検証
- `post-deploy.js` — デプロイ後のタスク

## 使い方

### ステージングへのデプロイ
```
/deploy staging
```

### 本番へのデプロイ
```
/deploy production
```

### ロールバック
```
/rollback production
```

### 状態確認
```
/status
```

### インシデント対応
```
/incident
```

## 要件

- Claude Code 1.0 以上
- Kubernetes CLI (kubectl)
- クラスターアクセスの設定

## 設定

Kubernetes の設定を行います:
```bash
export KUBECONFIG=~/.kube/config
```

## ワークフロー例

```
ユーザー: /deploy production

Claude:
1. デプロイ前フックを実行（kubectl とクラスター接続を検証）
2. deployment-specialist サブエージェントに委任
3. deploy.sh スクリプトを実行
4. Kubernetes MCP でデプロイの進捗を監視
5. デプロイ後フックを実行（Pod の待機、スモークテスト）
6. デプロイサマリーを提供

結果:
✅ デプロイ完了
📦 バージョン: v2.1.0
🚀 Pod: 3/3 準備完了
⏱️  所要時間: 2分34秒
```
