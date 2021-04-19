# SET TRANSACTION

現在のトランザクションの特性を設定する。

```sql
SET TRANSACTION [ISOLATION LEVEL] [READ WRITE | READ ONLY] [DEFERRABLE]
```

## 句

<details><summary>ISOLATION LEVEL</summary>

分離レベルを指定する。

```sql
ISOLATION LEVEL {
    READ UNCOMMITTED 
    | READ COMMITTED
    | REPEATABLE READ
    | SERIALIZABLE
}
```

### 句

<details><summary>READ UNCOMMITTED</summary>

標準SQLではコミットされないデータを読み取るダーティーリードが可能ですが、

`Postgresql`は`READ COMMITTED`と同等になり、ダーティーリードが許されません。

```sql
READ UNCOMMITTED
```

</details>

<details><summary>READ COMMITTED</summary>

一つの文から見ることができるのは、その文が開始される前にコミットされた

行のみです。これはデフォルトです。

```sql
READ COMMITTED
```

</details>

<details><summary>REPEATABLE READ</summary>

現在のトランザクションにおけるすべての文は、トランザクションで最初の

問い合わせ文またはデータを変更する文が実行される前にコミットされた行を

見ることができます。ほかのトランザクションの更新や削除してコミットしても、

このトランザクション反映されることはありません。

```sql
REPEATABLE READ
```

</details>

<details><summary>SERIALIZABLE</summary>

現在のトランザクションにおけるすべての文は、トランザクションで最初の

問い合わせ文またはデータを変更する文が実行される前にコミットされた行を

見ることができます。ほかのトランザクションが更新や削除に加えて、

挿入された行も個のトランザクションには反映されません。


```sql
SERIALIZABLE
```

</details>

#### 備考

<details><summary>分離レベル</summary>

|分離レベル|ダーティーリード|ファジーリード|ファントムリード|
|:---|:---|:---|:---|
|READ UNCOMMITTED|可能性あり|可能性あり|可能性あり|
|READ COMMITTED|安全|可能性あり|可能性あり|
|REPEATABLE READ|安全|安全|可能性あり|
|SERIALIZABLE|安全|安全|安全|

##### 備考

<details><summary>ダーティーリード</summary>

別のトランザクションでコミットされてない行も読み込む。

(Postgresqlではサポートされていない。)

</details>

<details><summary>ファジーリード</summary>

別のトランザクションで更新や削除された行がコミットされても読み込まない。

</details>

<details><summary>ファントムリード</summary>

別のトランザクションで挿入された行がコミットされも読み込まない。

</details>

</details>

</details>

<details><summary>READ WRITE</summary>

読み書き可能

```sql
READ WRITE
```

</details>

<details><summary>READ ONLY</summary>

読み取り専用

```sql
READ ONLY
```

</details>

<details><summary>DEFERRABLE</summary>

`SERIALIZABLE`でかつ`READ ONLY`のときに効果があります。

これは時間がかかるレポート処理やバックアップによく適しています。

```sql
DEFERRABLE
```

</details>
