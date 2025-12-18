# PostgreSQL（開発用）

本リポジトリでは、ローカル開発用の PostgreSQL を **Docker Compose** で起動します。
ホスト（macOS）への PostgreSQL の直接インストールは **採用しません**。

## バージョン方針
- 再現性のため、PostgreSQL は **パッチ版まで固定**します。
- 固定バージョン：**PostgreSQL 16.4**（`postgres:16.4`）
- `latest` は使用しません。

## 関連ファイル
- `infra/docker/compose.db.yml`：開発用 PostgreSQL 定義（DBのみ）
- `infra/docker/.env.db.example`：環境変数テンプレート（コミット可）
- `infra/docker/.env.db`：ローカル用環境変数（**コミット禁止**）

## セットアップ
1. ローカル用 env ファイルを作成
   ```bash
   cp infra/docker/.env.db.example infra/docker/.env.db
   ```

2. （任意）ホストの 5432 が使用中の場合、ホスト側ポートを変更
   `infra/docker/.env.db` の `HOST_DB_PORT` を例として `15432` に変更します。

3. PostgreSQL 起動
   ```bash
   cd infra/docker
   docker compose --env-file .env.db -f compose.db.yml up -d
   ```

## 動作確認
```bash
docker exec -it gatekeeper-db psql -U gatekeeper -d gatekeeper -c "select current_database(), current_user, version();"
```

## よく使うコマンド
停止（データ保持）
```bash
cd infra/docker
docker compose --env-file .env.db -f compose.db.yml stop
```

起動
```bash
cd infra/docker
docker compose --env-file .env.db -f compose.db.yml start
```

停止（データ保持）
```bash
cd infra/docker
docker compose --env-file .env.db -f compose.db.yml down
```

停止（データ削除：破壊的）
```bash
cd infra/docker
docker compose --env-file .env.db -f compose.db.yml down -v
```

## 注意
- `infra/docker/.env.db` は機密情報を含み得るため、必ず `.gitignore` 対象にします。
- データは Docker の named volume（例：`docker_gatekeeper_pgdata`）に永続化されます。
