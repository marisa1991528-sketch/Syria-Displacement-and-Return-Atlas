# Syria Displacement and Return Atlas

🇬🇧 English version: [README.md](README.md)

Python、Pandas、GeoPandas、Foliumを用いて作成した、シリアにおける集落（Settlement）レベルの避難・帰還アトラス

本プロジェクトでは、International Organization for Migration（IOM）の人道支援データとOpenStreetMapの地理空間データを統合し、データ検証から集落照合、インタラクティブ地図の作成まで、一連のHumanitarian GISワークフローを実装しました。

---

## プロジェクト概要

人道支援分野では、人口指標と集落の地理情報が別々のデータセットとして公開されることが多く、そのままでは空間解析を行うことが困難です。

本プロジェクトでは、この課題に対し、International Organization for Migration（IOM）の人口・避難指標と、OpenStreetMapの集落ジオメトリを、体系的なデータ統合ワークフロー（Data Harmonisation）によって結合しました。

完成したインタラクティブアトラスでは、Residents、Internally Displaced Persons（IDPs）、IDP Returnees、Total Populationを集落レベルで可視化し、Pythonを用いた再現可能なHumanitarian GISデータ統合の実装例を示しています。

---

## ワークフロー

本プロジェクトでは、以下のHumanitarian GISデータ統合ワークフローを実装しました。

1. IOMベースライン人口データの読み込み

2. HOT OpenStreetMap集落データの読み込み

3. データクリーニング・列名の標準化

4. ADM3 PCodeの検証

5. 集落名の正規化

6. 共通ADM3内での集落照合

7. String Similarityによる類似度計算

8. Match Qualityの分類

9. HOT集落ジオメトリとの統合

10. GeoDataFrameの作成

11. High-confidenceデータの抽出

12. インタラクティブFoliumアトラスの作成

本ワークフローでは、データ検証、集落照合、品質管理、地図作成を独立した工程として実装しており、各処理を個別に確認・再現できる構成となっています。

## データセット

本プロジェクトでは、人道支援データとオープンソースの集落ジオメトリを統合し、シリアにおける集落（Settlement）レベルの避難・帰還アトラスを作成しました。

### International Organization for Migration（IOM）

**データセット**

- Baseline Assessment（2026年4月）

**用途**

以下の人道支援人口指標を使用しました。

- Residents
- Internally Displaced Persons（IDPs）
- IDP Returnees
- Total Population

本データセットには人口・避難に関する指標が含まれていますが、インタラクティブ地図の作成に必要な集落ジオメトリは含まれていません。

---

### HOT OpenStreetMap（HOTOSM）

**データセット**

- Populated Places（OpenStreetMap）

**用途**

以下の集落レベルの地理情報を使用しました。

- 集落名
- ADM3行政コード
- 集落区分
- ポイントジオメトリ

本データセットには地理情報が含まれていますが、人道支援人口指標は含まれていません。

---

### 行政境界

**データソース**

- HDX OCHA
- Syrian Arab Republic – Subnational Administrative Boundaries

**用途**

行政境界の検証および地図表示に使用しました。

集落照合では、共通するADM3行政区域内でのみマッチングを実施しています。

---

### 水系データ

**データソース**

- HDX Humanitarian OpenStreetMap Team

**レイヤ**

- Rivers
- Lakes

これらのレイヤは、最終的なインタラクティブアトラスに地理的な背景情報を提供しています。

