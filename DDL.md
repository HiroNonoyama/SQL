# DDLのコマンド(Database Definition Lang)

---

## DATABASE
(複数タブのエクセルファイルをイメージ)

### CREATE

```sql
CREATE DATABASE <database name>;
```

### DROP

```sql
DROP DATABASE <database name>;
```

---

## TABLE
(エクセルファイルのタブの一つをイメージ)

### CREATE

```sql
CREATE TABLE <table name>
  (
    <field1> INTEGER NOT NULL,
    <field2> CAR(10) NOT NULL,
    <field3> VARCHAR(20),
    <field4> DATE NOT NULL,
    PRIMARY KEY (<field1>)
  );
```

## DROP

```sql
DROP TABLE <table name>
```

## ALTER

```sql
ALTER TABLE ADD COLUMN <field5> VARCHAR(120);
```
