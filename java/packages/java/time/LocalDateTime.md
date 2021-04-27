# LocalDateTime

タイムゾーンがついてない日付時間クラス。

```java
public final class LocalDateTime
        implements Temporal, TemporalAdjuster, ChronoLocalDateTime<LocalDate>, Serializable {
```

## メソッド

<details><summary>now()</summary>

### now()

現在時刻を返します。

```java
public static LocalDateTime now();
```

</details>

<details><summary>format()</summary>

### format()

指定したフォーマッタでフォーマットします。

```java
public String format(DateTimeFormatter formatter);
```

</details>

<details><summary>getDayOfMonth()</summary>

### getDayOfMonth()

日付を返します。

```java
public int getDayOfMonth();
```

</details>


<details><summary>getDayOfWeek</summary>

### getDayOfWeek()

曜日を返します。

```java
public DayOfWeek getDayOfWeek();
```

</details>

<details><summary>getDayOfYear()</summary>

### getDayOfYear()

一年で何日目かを返します。

```java
public int getDayOfYear();
```

</details>

<details><summary>getHour()</summary>

### getHour()

時刻を返します。

```java
public int getHour();
```

</details>

<details><summary>getMinute()</summary>

### getMinute()

分を返します。

```java
public int getMinute();
```

</details>

<details><summary>getMonthValue()</summary>

### getMonthValue()

月を返します。

```java
public int getMonthValue();
```

</details>

<details><summary>getNano()</summary>

### getNano()

名の秒を返します。

```java
public int getNano() {
```

</details>

<details><summary>getSecond()</summary>

### getSecond()

秒を返します。

```java
public int getSecond();
```

</details>

<details><summary>getYear()</summary>

### getYear()

年を返します。

```java
public int getYear();
```

</details>

<details><summary>plusYears()</summary>

### plusYears()

年を足します。

```java
public LocalDateTime plusYears(long years);
```

</details>

<details><summary>plusMonths()</summary>

### plusMonths()

月を足します。

```java
public LocalDateTime plusMonths(long months);
```

</details>

<details><summary>plusDays()</summary>

### plusDays()

日にちを足します。

```java
public LocalDateTime plusDays(long days);
```

</details>

<details><summary>minusYears()</summary>

### minusYears()

年を引きます。

```java
public LocalDateTime minusYears(long years);
```

</details>

<details><summary>minusMonths()</summary>

### minusMonths()

月を引きます。

```java
public LocalDateTime minusMonths(long months);
```

</details>

<details><summary>minusDays()</summary>

### minusDays()

日にちを引きます。

```java
public LocalDateTime minusDays(long days);
```

</details>
