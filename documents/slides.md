---
marp: true
theme: default
paginate: true

backgroundImage: url('./images/background-image.png')
backgroundSize: cover
backgroundPosition: center
---

# 開発環境の改善提案

### Docker + VSCode + DevContainers

---

## アジェンダ

1. 現状の課題
2. 解決策(Docker + VSCode + DevContainers)
3. Before/After
4. 懸念点と向き合い方
5. まとめ

---

# 1. 現状の課題

---

## 環境差異によるトラブル

- **バージョン差異による動作不良**  
  OS（Linux Distribution） / Runtime（Java,Python,...） / Tool（Git,CLI,...）
- **設定差異による成果物のブレ**  
  文字コード / 改行コード / 整形設定
- **再現性の欠如**  
  ローカルデータ差異 / 環境リセットが困難
- **既存環境との競合**  
  既存環境の影響 / 使用ポート競合
- **本番環境との差異**  
  Linux 環境の用意が手間 / フォルダ構成を再現できない

<!--
これがメモ
これがメモ
これがメモ
-->

---

## 環境構築の無駄

- **手順書が必要**  
  作成コスト / 更新されない / 属人化
- **構築の工数**  
  新規参加 / 引き継ぎ / サポート対応
- **トラブル**  
  手作業によるミス / 既存環境の影響

---

# 2. 解決方針

---

### Docker + VSCode + DevContainers

- Docker コンテナにより、開発環境を高い再現性で構築する
- 環境定義をファイルとして管理し、共有や再利用を容易にする
- VSCode + DevContainers により、従来の開発体験を損なわない

---

![Overview](./diagrams/Overview.drawio.png)

---

# 3. Before/After

---

![Before/After1](./diagrams/BeforeAfter-1.drawio.png)

---

![Before/After2](./diagrams/BeforeAfter-2.drawio.png)

---

# 4. 懸念点と向き合い方

---

- **セットアップとバージョン管理**
  VS Code / Git / WSL / Docker の初期セットアップとバージョン統一が必要  
  → 端末ごとに初回のみ対応すれば以降は再利用可能
- **ライセンスの関係で Docker Desktop（GUI）が使えない**
  VS Code から WSL に接続し、CLI ベースで docker コマンドを利用  
  ※ Podman は現時点では採用しない
- **Docker の学習コスト**
  コンテナ技術はモダン開発で必須となりつつあり、  
  中長期的にエンジニアの一般スキルとして必要

---

- **Windows 環境をコンテナで再現するのは不向き**
  VisualStudio を利用すれば十分対応可能
- **ネイティブアプリ開発には不向き**
  Windows アプリは VisualStudio で対応可能  
  モバイルアプリは本提案の対象外とする
- **公式イメージが存在しない場合がある**
  必要に応じて Dockerfile で再現可能  
  エミュレータが提供されているケースも多い(AWS,GCP)

---

# 5. まとめ

---

Docker + VS Code + Dev Containers により
環境を **コードとして管理** し、**再現性・切り分け・復旧性** を大きく改善できる

それにより開発環境の以下の課題が解決する

- **「環境差異によるトラブル」**
- **「環境構築とその変更に伴う無駄」**
