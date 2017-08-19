# その他のDML / DELETE, UPDATE

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
