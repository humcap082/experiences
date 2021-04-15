# extract()

日付や時刻から年やなどの部分フィールドを抽出します。

これは`SQL`標準ですが、`postgresql`独自関数の`date_part()`も同様。

```sql
extract(field FROM source)
```

## 引数

<details><summary>field</summary>

部分フィールドを指定します。

|field|説明|
|:---|:---|
|CENTURY|世紀|
|DAY|日にち|
|DECADE|年フィールドを10で割ったもの|
|DOW|曜日(0 - 6)。0が日曜日。`to_char()`とは番号が異なる。|
|ISO|曜日(1 - 7)。1が月曜日|
|DOY|通算日数|
|EPOCH|エポック時間|
|HOUR|時間|
|MILLENNIUM|千年期|
|MILLISECONDS|ミリセカンド|
|MINUTE|分|
|MONTH|月|
|QUARTER|四半期|
|SECOND|秒|
|TIMEZONE|タイムゾーン|
|TIMEZONE_HOUR|時差|
|TIMEZONE_MINUTE|時差の分|
|WEEK|週|
|YEAR|年|

</details>

***

<details><summary>source</summary>

抽出される対象の時間。

```sql
{TIME | TIMESTAMP | INTERVAL} source
```

</details>

***

