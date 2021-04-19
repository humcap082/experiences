# ROLLBACK

現在のトランザクションをアボートする。

```sql
ROLLBACK [AND CHAIN]
```

## 句

<details><summary>AND CHAIN</summary>

ロールバックした直後に同じトランザクション特性で

新たにトランザクションを開始する。

```sql
AND CHAIN
```

</details>
