
## index

- ビュー
- サブクエリ
- 相関サブクエリ

### VIEW
仮想のテーブルのようなもの
内部的にはSELECT文を保存しているだけなので、HDD容量を圧迫することはなく効率的

```sql
CREATE VIEW ShohinView (shohin_bunrui, cnt_shohin)
AS
SELECT shohin_bunrui, COUNT(*)
FROM Shohin
GROUP BY shohin_bunrui
;
```

もちろんこれを使って SELECT 文を発行することが可能

```sql
SELECT * FROM ShohinView;
```

### SubQuery
VIEW は作成するとテーブルと同じようにDATABASE内に保存されるが、
使い捨ての VIEW を作成することと同値なのがこのサブクエリ

```sql
SELECT shohin_bunrui, cnt_shohin
FROM (SELECT shohin_bunrui, COUNT(*) as cnt_shohin
      FROM Shohin
      GROUP BY shohin_bunrui) AS ShohinSum
;
```

### スカラサブクエリ
行列1×1の結果となるサブクエリのことをスカラサブクエリと呼ぶ
スカラが登場するところならどの項にでも利用することができる

```sql
SELECT shohin_mei, hanbai_tanka
FROM Shohin
WHERE hanbai_tanka > (SELECT AVG(hanbai_tanka)
                      FROM Shohin)
;
```
### 相関サブクエリ
スカラサブクエリのときは、全商品の販売単価の平均の値よりも高い販売単価の商品をWHERE節で条件として指定しているが、各商品分類の平均の販売額と比較する場合も出てくる。(カテゴリーが車と文具のときとでは全体の販売額平均は高くなりすぎてしまい意味を持たない)
そこで相関サブクエリを利用すれば、小分けにしたグループ内で比較を行うことができる

```sql
SELECT shohin_bunrui, shohin_mei, hanbai_tanka
FROM Shohin AS S1
WHERE hanbai_tanka > (SELECT AVG(hanbai_tanka)
                      FROM Shohin AS S2
                      WHERE S1.shohin_bunrui = S2.shohin_bunrui)
;
```
