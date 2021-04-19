# LOCK

テーブルレベルのロックを取得する。

```sql
LOCK [TABLE] <name>[, ...] [IN] [NOWAIT]
```

## パラメータ

<details><summary>name</summary>

ロックする既存のテーブル名

</details>

## 句

<details><summary>TABLE</summary>

省略可能

```sql
[TABLE]
```

</details>

<details><summary>IN</summary>

ロックモードを指定する。指定しない場合、`ACCESS EXCLUSIVE`が指定される。

```sql
IN {
    ACCESS SHARE | ROW SHARE | ROW EXCLUSIVE | SHARE UPDATE EXCLUSIVE
        | SHARE | SHARE ROW EXCLUSIVE | EXCLUSIVE | ACCESS EXCLUSIVE
} MODE
```

### 備考

<details><summary>競合の表</summary>

|ロックモード|ACCESS SHARE|ROW SHARE|ROW EXCLUSIVE|SHARE UPDATE EXCLUSIVE|SHARE|SHARE ROW EXCLUSIVE|EXCLUSIVE|ACCESS EXCLUSIVE|
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
|ACCESS SHARE||||||||x|
|ROW SHARE|||||||x|x|
|ROW EXCLUSIVE|||||x|x|x|x|
|SHARE UPDATE EXCLUSIVE||||x|x|x|x|x|
|SHARE|||x|x||x|x|x|
|SHARE ROW EXCLUSIVE|||x|x|x|x|x|x|
|EXCLUSIVE||x|x|x|x|x|x|x|
|ACCESS EXCLUSIVE||x|x|x|x|x|x|x|

</details>

</details>

<details><summary>NOWAIT</summary>

ロックが即座に取得できない場合、エラーを発生させる。

```sql
NOWIAT
```

</details>
