# PERFORM

`SELECT`と同じ役割ではあるが、結果を破棄するので結果を必要としない場合に使用する。

たとえば、単に関数を実行したい場合も直接よびだすことができないので、

`SELECT`内に記述する必要があるが、結果を必要としない場合は`PERFORM`を使用する。

```sql
PERFORM <query>;
```

## パラメータ

<details><summary>query</summary>

`SELECT`の後ろの文と同様の文を記述できる。

</details>

