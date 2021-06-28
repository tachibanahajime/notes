---
title: DataWarehouseFundamentalsforBeginners
date: 2021-06-24
tags:
  - Study
  - Udemy
  - Data Integration
  - Data Lake
  - Data Warehouse
---
# Data Warehouse Fundamentals for Beginners
## Link
[Data Warehouse Fundamentals for Beginners](https://nssol.udemy.com/course/data-warehouse-fundamentals-for-beginners/learn/lecture/17728676)  
<br>

## 講師
Alan Simon  
<br>

## 内容
## Section 3 : Data Warehousing Architecture
- Data Warehouseのパターン  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210624_1.png)  

- Cube  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210624_2.png)  

- ODS(Operational Data Store)  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210624_3.png)  

- Data Warehouse Staging Layer  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210624_4.png)  
<br>

## Section 4 : Bring Data Into Your Data Warehouse  
- ETL Transformation Models  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210624_5.png)  
  - Data Value Unification：値の統一（コード変換など）
  - Data Type and Size Unification：データ型・データ桁数の統一
  - De-duplication：重複データの排除
  - Dropping Columns (vertical slicing)：不要カラムの削除（分析に使わないカラムの排除）
  - Value-based Row Filtering (horizontal slicing)：不要データの削除（分析に使わないデータの排除）
  - Correcting Known Errors：データクレンジング（不適切なデータの修正）  
<br>

## Section 5 : Data Warehousing Design: Building Blocks  
- Star Schema vs. Snowflake Schema
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_1.png)  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_2.png)  
  - Star SchemaもSnowflake Schemaも元データの次元は同じ。  
  （例：製品ファミリー 1..N 製品カテゴリー 1..N 製品名）
    - Star Schema：製品ファミリー・製品カテゴリー・製品名をすべて同じテーブルに持つ（正規化を崩す）  
    - Snowflake Schema：製品ファミリー・製品カテゴリー・製品名はそれぞれ別のテーブルで持つ（正規化を残す）  
  
- Data Warehouseing and Natural Keys  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_3.png)  

- Foundational Conepts
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_4.png)  
<br>

## Section 6 : Design Facts, Fact Tables, Dimensions, and Dimension Tables  
- Snowflake Schema PK-FK Rules
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_5.png)  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_6.png)  

  - Fact TableとDimension TableのRelationはSurrogate Keyを使って定義する。  
  - Fact Tableが持つNatural Keyを使えばレコードを一意に特定することはできるが、Dimension TableheへのForeign Keyとしては利用しない。  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_7.png)

- Fact Table Types
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_8.png)  

  - Transaction：特定のトランザクションを管理する（授業料支払トランザクションなど）
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_9.png)  
  - Periodic Snapshot：トランザクションの定期的な履歴を管理する（毎週のミールカード利用履歴など）
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_10.png)  
  - Accumulation Snapshot：あるトランザクションの時間軸での変化を管理する（奨学金審査の進捗状況など）
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_11.png)  
  - Factless：
