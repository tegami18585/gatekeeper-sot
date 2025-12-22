# Gatekeeper SOT Index

このドキュメントは、**Gatekeeper プロジェクトにおける Single Source of Truth（SOT）** の入口です。

Gatekeeper に関する設計方針・判断根拠・運用ルールの正本は、  
**すべて本リポジトリの `docs/` 配下に集約**されています。

本 `index.md` は、それらの正本ドキュメントを  
**どの順で、どの目的で読めばよいかを案内するためのガイド**です。

---

## はじめて読む場合の推奨順

Gatekeeper SOT を初めて読む場合は、以下の順で参照してください。

1. **ADR-0001（SOT原則）**  
   Gatekeeper における正本主義・判断の前提  
   → `adr/ADR-0001-sot-principle.md`

2. **ドキュメント配置ルール**  
   ADR / 運用 / 参照 / infra の役割分担  
   → `operations/document-placement.md`

3. **目的別ドキュメント**  
   設計・運用・参照用途に応じて、該当ディレクトリを参照

---

## Docs の位置づけ（制度として）

このディレクトリ（`docs/`）は、gatekeeper-sot における  
**人間向けドキュメントの正本**である。

制度（ADR / 運用）をここに集約し、  
発見性と参照性を担保する。

---

## Quick Links

- ADR: `adr/`
- 運用ルール: `operations/`
- 開発ガイド: `infra/`

---

## Structure Summary

- `docs/`  
  制度・運用・参照・ガイド（正本）

- `infra/`  
  infra 実装と最小説明

- `global/`  
  横断ルール定義

- `projects/`  
  プロジェクト定義・サンプル雛形
