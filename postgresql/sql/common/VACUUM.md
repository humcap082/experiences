# VACUUM

データベースの不要領域の回収とデータベースの解析をおこなう。

```sql
VACUUM [
    (
        [FULL]
        [FREEZE]
        [VERBOSE]
        [ANALYZE]
        [DISABLE_PAGE_SKIPPING]
        [SKIP_LOCKED]
        [INDEX_CLEANUP]
        [TRUNCATE]
    )
    | [FULL] [FREEZE] [VERBOSE] [ANALYZE]
] [<table_name> [(<column_name>[, ...])]][, ...]
```
## パラメータ

<details><summary>table_name</summary>
</details>

<details><summary>column_name</summary>
</details>

## 句

<details><summary>FULL</summary>

```sql
FULL
```

</details>

<details><summary>FREEZE</summary>

```sql
FREEZE
```

</details>

<details><summary>VERBOSE</summary>

```sql
VERBOSE
```

</details>

<details><summary>ANALYZE</summary>

```sql
ANALYZE
```

</details>

<details><summary>DISABLE_PAGE_SKIPPING</summary>

```sql
DISABLE_PAGE_SKIPPING
```

</details>

<details><summary>SKIP_LOCKED</summary>

```sql
SKIP_LOCKED
```

</details>

<details><summary>INDEX_CLEANUP</summary>

```sql
INDEX_CLEANUP
```

</details>

<details><summary>TRUNCATE</summary>

```sql
TRUNCATE
```

</details>
