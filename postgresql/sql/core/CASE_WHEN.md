# CASE WHEN

条件分岐して値を返す。値を返す場所ならどこでも挿入できる。

```sql
CASE [expression]
    WHEN expression THEN value
    [WHEN...]
    ELSE value
END
```

## 例

<details><summary>switch文風</summary>

CASEの後に値を入れた場合switch文のように使用でき、WHENの値はbooleanである必要はなく、

CASEで指定した値とWHENで指定した値が等しいかどうかをみる

CASEの後の値を省略した場合はWHENの後にbooleanを返す条件をいれる。

```sql
SELECT a,
    CASE a
        WHEN 1 THEN 'one'
        WHEN 2 THEN 'two'
        ELSE 'other'
    END
FROM test;
```

</details>

***

