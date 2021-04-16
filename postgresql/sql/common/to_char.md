# to_char()

日付や数値をフォーマットする。

```sql
to_char(<expression>, '<format>')
```

## 引数

<details><summary>format</summary>

特定の文字を組み合わせてフォーマットを指定する。

## 備考

<details><summary>時間のフォーマットの部品</summary>

|文字|説明|
|:---|:---|
|HH|時間 (01 - 12)|
|HH24|時間 (00 - 23)|
|MI|分|
|SS|秒|
|MS|ミリ秒|
|SSSS|00時からの秒数|
|AM|午前|
|PM|午後|
|YYYY|西暦|
|BD|紀元前|
|AD|紀元後|
|MON|月|
|MM|月番号(01 - 12)|
|DAY|曜日|
|DY|3文字で表現される曜日|
|DDD|一年間の日数|
|DD|一か月の日数|
|D|一週間の日数|
|W|週番号(1 - 5)|
|WW|年間を通じた週番号|
|CC|2桁の世紀|
|TZ|タイムゾーンの名前|

</details>

<details><summary>数値のフォーマットの部品</summary>

|文字|説明|
|:---|:---|
|9[,...]|桁を制限する。超えるとオーバーフロー表現になる。|
|0[,...]|桁を制限する。0詰め。|
|.|小数点|
|,|カンマ区切り点|

</details>

</details>

## 例

<details><summary>3桁区切り</summary>

```sql
SELECT to_char(sal, '9,999,999,999.99') FROM employee;
```

</details>
