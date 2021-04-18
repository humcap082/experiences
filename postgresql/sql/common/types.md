# 型

<details><summary>CHAR</summary>

固定長の文字列の型

```sql
CHAR(<bytes>)
```

</details>

<details><summary>INT4RANGE</summary>

`int4`の範囲型

```sql
INT4RANGE
```

### 関数

<details><summary>INT4RANGE()</summary>

値を返す。

```sql
int4range(<lower>, <upper>, '<pattern>')
```

#### 備考

<details><summary>pattern</summary>

`()`もしくは`[]`から一つずつとって一組にする。

|括弧|説明|
|:---|:---|
|(|大なり|
|)|未満|
|[|以上|
|]|以下|

</details>

#### 例

<details><summary>以上、未満</summary>

```sql
SELECT INT4RANGE(3, 7, '[)')::int4range;
```

</details>

<details><summary>大なり、未満</summary>

```sql
SELECT INT4RANGE(4, 9, '()')::int4range;
```

</details>

</details>

### 備考

<details><summary>ショートカット</summary>

`INT4RANGE()`の代わりに`()`や`[]`を使用できる

```sql
{\[ | (},{) | \]}

```

#### 例

<details><summary>以上、未満</summary>

```sql
SELECT '[3,7)'::int4range;
```

</details>

<details><summary>大なり、未満</summary>

```sql
SELECT '(3,7)'::int4range;
```

</details>

<details><summary>以上、以下</summary>

```sql
SELECT '[4,4]'::int4range;
```

</details>

<details><summary>emptyに正規化される状態</summary>

```sql
SELECT '[4,4)'::int4range;
```

</details>

</details>

</details>

<details><summary>JSONB</summary>

`Json`の型で文字列にキャストできる。`JSON`型が別に存在するが、

基本的には`JSONB`を使用する。 

```sql
JSONB
```

</details>

<details><summary>SMALLINT</summary>

2バイトで-32768から32767までの範囲の整数を表す整数型

```sql
SMALLINT
```

</details>

<details><summary>TEXT</summary>

可変長で制限のない文字列型

```sql
TEXT
```

</details>

<details><summary>TIMESTAMPTZ</summary>

タイムゾーン付きの日時型、`TIMESTAMP WITH TIME ZONE`の省略系

```sql
TIMESTAMPTZ
```

</details>

<details><summary>TIMESTAMP</summary>

タイムゾーンが関係ない日時型、`TIMESTAMP WITHOUT TIME ZONE`の省略形

```sql
TIMESTAMP
```

</details>

<details><summary>UUID</summary>

`UUID`のデータ型

```sql
UUID
```

</details>

<details><summary>VARCHAR</summary>

可変長の文字列型

```sql
VARCHAR(<max_bytes>)
```

</details>

<details><summary>DATE</summary>

日付型

```sql
DATE
```

</details>

<details><summary>TIME</summary>

時間のデータ型

```sql
TIME
```

### 例

<details><summary>加算、減算、比較</summary>

```sql
created_at < (now() AT TIME ZONE 'utc') - TIME '00:10';
```

</details>

</details>
