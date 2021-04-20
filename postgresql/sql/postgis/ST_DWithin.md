# ST_DWithin()

ある地点がある地点と指定した距離以内かどうかを真偽値で返す。

`geometry`型と`geography`型に対応している。

user_pheroidはデフォルトでtrueで回転楕円体を使用した計算になり、

高速に計算するにはfalseを渡す

```sql
ST_Dwithin(geography gg1, geography gg2, double distance, boolean use_pheroid)
```

## 引数

<details><summary>gg1</summary>
</details>

<details><summary>gg2</summary>
</details>

<details><summary>distance</summary>
</details>

<details><summary>user_pheroid</summary>
</details>
