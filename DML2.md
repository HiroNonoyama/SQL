# その他のDML / INSERT, DELETE, UPDATE

## INSERT
レコードを追加する

```sql
INSERT INTO shohin (<field1>, <field2>, <field3>) VALUES ('0002', '2003-02-03', 1000);
/* => INSERT INTO shohin VALUES ('0002', '2003-02-03', 1000); これも同じ結果*/

INSERT INTO shohin_backup (<field1>, <field2>, <field3>)
SELECT <field1>, <field2>, <field3>
FROM shohin; /* shohinのレコード全部をshohin_backupにコピーする */
```

## DELETE
特定のレコードを削除する

```sql
DELETE FROM shohin
WHERE id = '0001';  /* id = 0001 のレコードを削除 */

DELETE FROM shohin;  /* shohinテーブルの全レコードを削除 */
```

## UPDATE
レコードの情報を更新する

```sql
UPDATE shohin
SET torokubi = '2009-02-03', tanka = 1200 /* idが1のレコードの登録日を2009年2月3日、単価を1200円に変更 */
WHERE id = '0001';

UPDATE shohin
SET torokubi = '2009-02-03', tanka = 1200;  /* 商品テーブルの全レコードの登録日を2009年2月3日、単価を1200円に変更 */
```
