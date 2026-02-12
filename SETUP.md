# PAM - 環境セットアップ手順

## Jira MCP サーバーの接続設定

Claude Code から Jira（KAN プロジェクト）に接続するための設定手順。

### 前提条件

- Claude Code がインストール済み
- Python 3.12 以上（3.14 未満）
- `uv` がインストール済み（なければ `pip install uv`）

### 手順

#### 1. `.mcp.json` の確認

プロジェクトルートに `.mcp.json` が配置済み（`.gitignore` 対象）。
トークンの再発行が必要な場合は以下から:
https://id.atlassian.com/manage-profile/security/api-tokens

#### 2. 接続テスト

Claude Code を起動し、Jira 関連のツールが使えることを確認:

```
claude
> /mcp
```

`mcp-atlassian` が表示され、ツール一覧に Jira 関連のツールが含まれていれば成功。

#### 3. 動作確認

```
KAN プロジェクトのチケット一覧を見せて
```

### トラブルシューティング

| 症状 | 対処 |
|------|------|
| `uvx` が見つからない | `pip install uv` を実行 |
| Python 3.14 エラー | `args` を `["--python=3.12", "mcp-atlassian"]` に変更 |
| 認証エラー | API トークンが正しいか確認。期限切れの場合は再発行 |
| MCP が表示されない | `.mcp.json` がプロジェクトルートにあるか確認 |
