# Syria Displacement and Return Atlas（日本語）

🇬🇧 English version: [README.md](README.md)

Python、Pandas、GeoPandas、Foliumを用いて作成した、シリアにおける集落（Settlement）レベルの避難・帰還アトラスです。

本プロジェクトでは、International Organization for Migration（IOM）の人道支援データとOpenStreetMapの地理空間データを統合し、データ検証から集落照合、インタラクティブ地図の作成まで、一連のHumanitarian GISワークフローを実装しました。

## アトラスを見る

- [インタラクティブアトラスを開く](https://marisa1991528-sketch.github.io/Syria-Displacement-and-Return-Atlas/10_syria_displacement_and_return_atlas.html)

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

## データ処理フロー

人道支援データは、再現可能なPythonワークフローにより、以下の工程で処理しました。

### 1. データ準備

- IOM Baseline Assessmentデータの読み込み
- HOT OpenStreetMap集落データの読み込み
- 列名の標準化
- 人口・避難指標の抽出

---

### 2. データ検証

- ADM3行政コードの検証
- 不完全なレコードの除外
- 集落名の整合性確認
- 共通するADM3行政区域の確認

---

### 3. 集落照合

- 集落名の正規化
- 共通ADM3区域内での集落照合
- String Similarityによる類似度計算
- Match Qualityの分類

---

### 4. 空間データ統合

- 検証済み集落ジオメトリとの結合
- GeoDataFrame（EPSG:4326）の作成
- 地図表示用の空間属性を作成

---

### 5. インタラクティブ地図の作成

- High-confidenceデータの抽出
- Foliumレイヤの作成
- 行政境界の追加
- 河川・湖沼レイヤの追加
- インタラクティブアトラスの出力

## 主な機能

完成したアトラスでは、以下の機能を提供しています。

- 集落（Settlement）レベルのインタラクティブな可視化
- Residents、IDPs、IDP Returnees、Total Populationレイヤ
- Folium LayerControlによるレイヤ切替
- 行政境界の表示
- 地理的背景としての河川・湖沼レイヤ
- Hover Tooltipおよびクリック式ポップアップ
- High-confidenceレコードによる集落照合
- 再現可能なHumanitarian GISワークフロー
- 集落レベルの人道支援データ統合

## 使用技術

### プログラミング言語

- Python

### データ分析

- Pandas

### 地理空間解析

- GeoPandas
- Shapely

### インタラクティブ地図

- Folium

### 類似度解析

- difflib（SequenceMatcher）

---

## 習得・実装した技術

- 複数の人道支援データセットのData Harmonisation
- 列名の標準化とスキーマ統一
- ADM3行政コードを用いた行政境界の検証
- 集落名の正規化
- String Similarity（SequenceMatcher）による類似度照合
- Match Qualityの分類
- 集落（Settlement）レベルのデータ統合
- GeoDataFrameの作成
- 座標参照系（EPSG:4326）の管理
- Foliumを用いたインタラクティブ地図の作成
- レイヤ管理および可視化
- 再現可能なHumanitarian GISワークフロー

---

## 結果

本プロジェクトでは、人道支援人口指標と集落レベルの地理空間データを統合し、シリアにおける集落（Settlement）レベルの避難・帰還アトラスを作成しました。

### 統合結果

| 項目 | 結果 |
|------|------:|
| IOM調査レコード | 約33,000件 |
| HOT OpenStreetMap集落データ | 約9,300件 |
| 共通するADM3行政区域 | 268 |
| High-confidenceとして採用したレコード | 処理対象レコードの29.1% |

### 使用した人口・避難指標

- Residents
- Internally Displaced Persons（IDPs）
- IDP Returnees（2024年12月以降）
- Total Population

### アトラスの出力内容

- インタラクティブなFoliumアトラス
- 集落（Settlement）レベルの人道支援データ可視化
- 4種類の人口・避難指標レイヤの切替
- 行政境界の表示
- 河川・湖沼レイヤの表示
- Hover Tooltipおよびクリック式ポップアップ

本プロジェクトでは、体系的なデータ検証、Data Harmonisation、および品質管理を伴う集落照合を通じて、人道支援データと地理空間データを統合し、再現可能な集落（Settlement）レベルのHumanitarian GISワークフローを実現しました。

---

## 今後の展望

本アトラスは、シリアを対象としたHumanitarian GIS解析フレームワークの第一段階として作成しました。

今後は、以下のような発展が考えられます。

- 追加の人道支援評価データとの統合
- 避難・帰還動向の時系列解析
- 複数ソースの人道支援データ統合
- 気候災害と人口移動の関連解析
- データ更新の自動化
- 人道支援指標の拡充

本プロジェクトで構築したワークフローは、今後のHumanitarian GIS解析における再現可能な基盤となることを目指しています。

---

## おわりに

本プロジェクトでは、独立して公開されている人道支援データと地理空間データを、体系的な検証・統合・インタラクティブ地図化を通じて、再現可能な地理空間情報へと変換しました。

このアトラスは、オープンソースの地理空間技術を活用し、人道支援分野におけるGIS解析および意思決定支援へ応用することを目的とした継続的な取り組みの一環として作成したものです。
