# node.jsからPostgreSQLを使う

node.jsからPostgreSQLを使う場合のあれこれ

## 基本アクセスはpg

## pgとSequelize

## SQLあれこれ

### データベースが持つテーブルのリスト

### テーブルが持つカラムのリスト

SELECT * FROM information_schema.columns WHERE table_name='テーブル名' ORDER BY ordinal_position;

