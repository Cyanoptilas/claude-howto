---
name: api-documentation-generator
description: ソースコードから包括的で正確な API ドキュメントを生成します。API ドキュメントの作成・更新、OpenAPI 仕様の生成、または API ドキュメント・エンドポイント・ドキュメントに言及するときに使用します。
---

# API ドキュメントジェネレータースキル

## 生成するもの

- OpenAPI/Swagger 仕様
- API エンドポイントドキュメント
- SDK 使用例
- 統合ガイド
- エラーコードリファレンス
- 認証ガイド

## ドキュメント構造

### 各エンドポイントについて

```markdown
## GET /api/v1/users/:id

### 説明
このエンドポイントが何をするかの簡単な説明

### パラメータ

| 名前 | 型 | 必須 | 説明 |
|------|------|----------|-------------|
| id | string | Yes | ユーザー ID |

### レスポンス

**200 成功**
```json
{
  "id": "usr_123",
  "name": "John Doe",
  "email": "john@example.com",
  "created_at": "2025-01-15T10:30:00Z"
}
```

**404 見つからない**
```json
{
  "error": "USER_NOT_FOUND",
  "message": "User does not exist"
}
```

### 例

**cURL**
```bash
curl -X GET "https://api.example.com/api/v1/users/usr_123" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

**JavaScript**
```javascript
const user = await fetch('/api/v1/users/usr_123', {
  headers: { 'Authorization': 'Bearer token' }
}).then(r => r.json());
```

**Python**
```python
response = requests.get(
    'https://api.example.com/api/v1/users/usr_123',
    headers={'Authorization': 'Bearer token'}
)
user = response.json()
```
```
