## index

- INNER JOIN
- OUTER JOIN
- CROSS JOIN

### INNER JOIN
二つのテーブルを結合して一つのテーブルにまとめる。
各テーブルにそれぞれのレコードの集合が存在する。片方のテーブルの主キーが、もう一方のテーブルに外部キーとして保存されている。レコードの主キーと外部キーに注目した時に、どちらのテーブルにも値が存在しているキーの値に紐づくレコードが結合される。

```sql
SELECT tempo_id, tempo_mei, S.shohin_id, shohin_mei, hanbai_tanka
FROM Tenposhohin AS T INNER JOIN Shohin AS S
  ON T.shohin_id = S.shohin_id
;
/*
tempo_id | tempo_mei | shohin_id |   shohin_mei   | hanbai_tanka
----------+-----------+-----------+----------------+--------------
000A     | 東京      | 0001      | Tシャツ         |         1000
000A     | 東京      | 0002      | 穴あけパンチ   |          500
000A     | 東京      | 0003      | カッターシャツ |         4000
000B     | 名古屋    | 0002      | 穴あけパンチ   |          500
000B     | 名古屋    | 0003      | カッターシャツ |         4000
000B     | 名古屋    | 0004      | 包丁           |         3000
000B     | 名古屋    | 0006      | フォーク       |          500
000B     | 名古屋    | 0007      | おろしがね     |          880
000C     | 大阪      | 0003      | カッターシャツ |         4000
000C     | 大阪      | 0004      | 包丁           |         3000
000C     | 大阪      | 0006      | フォーク       |          500
000C     | 大阪      | 0007      | おろしがね     |          880
000D     | 福岡      | 0001      | Tシャツ        |         1000
(13 rows)
*/
```

### OUTER JOIN
レコードの主キーと外部キーに注目した時に、主キーの値の集合をA,外部キーの値の集合をBとすると、A∧Bのキーをもつレコードのみをまとめるのが内部結合。
外部結合はAに含まれるキーをもつレコードを全て、もしくはBに含まれるキーのレコード全てのように、片方のテーブルの情報を全て表示する。このとき、どちらを優先するのかはRIGHTやLEFTで表現する。

```sql
SELECT tempo_id, tempo_mei, S.shohin_id, shohin_mei, hanbai_tanka
FROM Tenposhohin AS T RIGHT OUTER JOIN Shohin AS S
  ON T.shohin_id = S.shohin_id
;
/*
tempo_id | tempo_mei | shohin_id |   shohin_mei   | hanbai_tanka
----------+-----------+-----------+----------------+--------------
000A     | 東京      | 0001      | Tシャツ        |         1000
000A     | 東京      | 0002      | 穴あけパンチ   |          500
000A     | 東京      | 0003      | カッターシャツ |         4000
000B     | 名古屋    | 0002      | 穴あけパンチ   |          500
000B     | 名古屋    | 0003      | カッターシャツ |         4000
000B     | 名古屋    | 0004      | 包丁           |         3000
000B     | 名古屋    | 0006      | フォーク       |          500
000B     | 名古屋    | 0007      | おろしがね     |          880
000C     | 大阪      | 0003      | カッターシャツ |         4000
000C     | 大阪      | 0004      | 包丁           |         3000
000C     | 大阪      | 0006      | フォーク       |          500
000C     | 大阪      | 0007      | おろしがね     |          880
000D     | 福岡      | 0001      | Tシャツ        |         1000
         |           | 0008      | ボールペン     |          100
         |           | 0005      | 圧力鍋         |         6800
(15 rows)
*/
```

### CROSS JOIN
集合Aと集合Bの直積(A×B)を表現
```sql
SELECT tempo_id, tempo_mei, S.shohin_id, shohin_mei, hanbai_tanka
FROM Tenposhohin AS T CROSS JOIN Shohin AS S
  ON T.shohin_id = S.shohin_id
;
```
