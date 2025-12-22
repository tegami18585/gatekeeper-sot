# Document Placement Rules (gatekeeper-sot)

本ドキュメントは gatekeeper-sot の「何をどこに置くか」を決める配置ルールである。
目的は整理整頓ではなく、判断のブレをなくし、将来の追加・PR判断を安定させること。

## 1. Golden Rule

- **制度（ADR/規範/運用）は docs/ に置く**
- **infra/ は実装と最小説明に限定する**
- **迷ったら docs/ に置く**
- 例外が必要なら、**新しい ADR を追加して例外ルール化**する

## 2. Decision Flow

1) これは意思決定の記録（なぜそうしたか）か？
- Yes → `docs/adr/`

2) これは制度・運用ルール（破ると混乱する）か？
- Yes → `docs/operations/`

3) これは参照・ガイド（読むためのもの）か？
- Yes → `docs/` 配下（適切なカテゴリ）

4) これは infra 実装を動かすためにだけ必要か？
- Yes → `infra/` 配下（最小）

## 3. Directory Responsibilities

- `docs/`
  - ADR / 運用ルール / 参照 / 開発ガイド（Node/PostgreSQL 等）を置く
- `infra/`
  - Docker 等の infra 実装と、動かすための最小説明を置く
  - ADR/制度ドキュメントは置かない
- `global/`
  - 全プロジェクト横断のルール定義（YAML 等）を置く
- `projects/`
  - プロジェクト単位の定義・計画・ルール（YAML）およびサンプル雛形を置く
  - SOTの制度（ADR等）は置かない

## 4. YAML Placement Rules

- 横断ルール → `global/*.yml`
  - 例: `global/global_rules.yml`
- プロジェクト固有 → `projects/<project>/*.yml`
  - 例: `projects/sample/project_rules.yml`

## 5. Secrets / env files (Safety)

- `infra/docker/*.env*` のうち **実値**は原則としてコミットしない
- 正本は `*.example` とし、配布・共有は example を基準とする
- 例外が必要な場合は ADR でルール化する
