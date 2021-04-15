# ドル引用符

ドル引用符というものがあり、'name'とおなじ文字列定数を表すが、

中の文字がエスケープされるのでバックスラッシュやシングルクォート、その他の特殊文字を

通常の文字列として解釈します。

```sql
$[tag]$documents$[tag]$
```

## 備考

<details><summary>tag</summary>

`tag`の位置にキーワードを付与することで、そのキーワードはエスケープされません。

</details>

***

## 例

<details><summary>関数に使用される例</summary>

```sql
CREATE FUNCTION func() AS
$func$
expression
$func$
```

</details>

***

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


