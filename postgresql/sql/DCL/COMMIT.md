# COMMIT

トランザクションをコミットする。

```sql
COMMIT [AND CHAIN]
```

## 句

<details><summary>AND CHAIN</summary>

これをつけると、コミットした後、同じトランザクション特性で

新しくトランザクションを開始します。

```sql
AND CHAIN
```

</details>
