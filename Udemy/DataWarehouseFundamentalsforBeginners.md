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
    - Surrogate KeyをPKとして使っておけば、Type 2(後述)のデータ履歴管理がしやすくなる。  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_7.png)

- Fact Table Types
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_8.png)  

  - Transaction：特定のトランザクションを管理する（授業料支払トランザクションなど）
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_9.png)  
  - Periodic Snapshot：トランザクションの定期的な履歴を管理する（毎週のミールカード利用履歴など）
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_10.png)  
  - Accumulation Snapshot：あるトランザクションの時間軸での変化を管理する（奨学金審査の進捗状況など）
  ![](./images/DataWarehouseFundamentalsforBeginners_20210625_11.png)  
  - Factless(1)：集計データを持たないトランザクションを管理する（ウェビナーの受講記録など）
  ![](./images/DataWarehouseFundamentalsforBeginners_20210629_1.png)  
  - Factless(2)：トランザクションが無いディメンション同士の関係を管理する（学生アドバンザーのアサイン履歴など）
  ![](./images/DataWarehouseFundamentalsforBeginners_20210629_2.png)  
<br>

## Section 7 : Managing Data Warehouse History Through Slowly Changing Dimensions  
- Slowly Changing Dimentions(SCDs)  
  - Data Warehouse内でのデータ履歴管理の考え方  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210629_3.png)  

  - Type 1：古いデータを新しいデータで上書きする履歴管理方式
    - データの履歴を保持する必要が無い場合に利用（エラーデータを修正する場合など）
    - ただデータをUpdateすればよいので、アーキテクチャが最もシンプル。
  - Type 2：新しいレコードを新たな行として追加する履歴管理方式
    - 複数行のデータを履歴として保持する必要がある場合に利用（学生の転居履歴を管理する場合など）
    - Effective Date（有効開始日）, Expiration Date（有効終了日）, Current Flag（有効フラグ）を持たせることで、現在どのデータが有効かを管理することができる。
  - Type 3：新旧のデータを別の列で管理する履歴管理方式
    - 新旧のデータを同一行で管理したい場合に利用（支店統合前後の従業員の所属店舗情報を管理する場合など）
    - Current Value（新データ）とOld Value（旧データ）を同一行に保持することで、新旧どちらの切り口でデータを分析する場合にも対応しやすい。  
<br>

## Section 8 : Designing Your ETL  
- ETL best practices and guidelines  
  ![](./images/DataWarehouseFundamentalsforBeginners_20210712_1.png)  
- 変更データ追跡のテクニック  
  - タイムスタンプ比較：データのタイムスタンプが前回のETL実行時間以降のものを連携する  
  - データベースログ：データベースのログを参照し、前回のETL実行時間以降の変更を連携する  
  - データベーススキャン：データベースとDWHの全データをスキャンし、差分を抽出して連携する  
<br>
