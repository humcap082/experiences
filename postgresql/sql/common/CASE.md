# CASE

条件分岐して値を返す。値を返す場所ならどこでも挿入できる。

```sql
CASE [<expression>]
    WHEN THEN
    [WHEN...]
    [ELSE]
END
```

## パラメータ

<details><summary>expression</summary>

CASEの後に値を入れた場合`switch`文のように使用でき、

`WHEN`の後は条件式ではなく値をわたし、

その`expression`とその値を比較する。

</details>


## 句

<details><summary>WHEN</summary>

`CASE`のあとに値が存在する場合は、

その値と`WHEN`の後の値を比較し、`CASE`の後に値が存在しない場合は、

真偽値を返す条件式を`WHEN`の後に渡す。

```sql
WHEN {<condition> | <value>}
```

### パラメータ

<details><summary>condition</summary>

`CASE`の後に値が存在しない場合は、

真偽値を返す条件式を`condition`にわたす。

</details>

<details><summary>value</summary>

`CASE`のあとに値が存在する場合は、その値と`value`を比較する。

</details>

</details>

<details><summary>THEN</summary> 

`WHEN`が`TRUE`の時、指定した値を返す。

```sql
THEN <result>
```

</details>

<details><summary>ELSE</summary>

`WHEN`で指定した条件がすべて`FALSE`のとき

返す値を指定する。

```sql
ELSE <result>
```

</details>

## 例

<details><summary>switch文風</summary>

```sql
SELECT a,
    CASE a
        WHEN 1 THEN 'one'
        WHEN 2 THEN 'two'
        ELSE 'other'
    END
FROM test;
```
