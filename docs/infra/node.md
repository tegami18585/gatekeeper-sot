# Node.js / pnpm（開発環境）

## 方針（SOT）
- Node.js は Volta で固定する（Mac / Windows で体験を統一）
- pnpm は Corepack で固定する
- `latest` は使用しない（明示バージョン固定）

## 採用バージョン
- Node.js: 22.14.0
- pnpm: 9.15.4

## セットアップ（Mac）

### Volta
```bash
brew update
brew install volta
volta --version

```

### Node 固定
```bash
volta install node@22.14.0
node -v
which node
```

### pnpm 固定（Corepack）
```bash
corepack enable
corepack prepare pnpm@9.15.4 --activate
pnpm -v
which pnpm
```

## 補足
- `package.json` の `volta.node` を正（SOT）として扱う
