# DML(Data Maniplation Lang) / SELECT

エクセルファイルの一つのタブから、特定の情報だけを一覧表示するイメージ

##### スタンダートな検索
```sql
SELECT <field1>, <field3>
FROM <table name>
WHERE <field1> = 'xxx'
      AND <field3> IS NOT NULL
;
```

## GROUP BY
集約関数(SUM/AVG/MAX/MIN/COUNT)を利用する時にグループ分けに使う <- エクセルのsumとかaverageとかの関数を考えると理解しやすいかもしれない。複数のレコードに対して一つの値を取得するやつ。
エクセルファイルのうち、特定のカラムを元に切り分けをするイメージ(sexのカラムだったら、値が0のレコードと1のレコードとで表を分割する)

```sql
SELECT <field2>, COUNT(*), SUM(<field5>)
FROM <table name>
WHERE <field6> > 500
GROUP BY <field2>;
```

これはまず、1枚のエクセルファイルのデータの内、<field6>が5000以上のレコードに絞りこむ。
<field2>カラムのデータによって、エクセルデータをさらに分割する。
分割されたものはそれぞれ一つの表として集約関数を使って、分割されたひとまとまりから一つのレコードを生成する。

(ex. sex, COUNT(*), AVG(height))

sex = 0 のデータの総数と、平均身長
sex = 1 のデータの総数と、平均身長
っていう結果を表示

## HAVING
上のGROUP BYの結果うち、更に絞込を行う時に利用

```sql

/* Studentテーブルの定義
   Column     |          Type          | Modifiers
---------------+------------------------+-----------
studen_id     | character(4)           | not null
student_name  | character varying(100) | not null
height        | integer                |
weight        | integer                |
sex           | integer                |
class         | integer                |
*/

SELECT class, COUNT(*), AVG(height)
FROM Student
GROUP BY class /* クラスごとに分類 */
HAVING AVG(height) > 170 /* 平均身長が170以上のクラスのみを表示する */
```

## ORDER BY
一番最後に配置するクエリ。並べ替えを行う

```sql
SELECT *
FROM shohin
ORDER BY id ASC(DESC) /* idを昇順(降順)に並べる */
```
