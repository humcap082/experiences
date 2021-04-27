# Integer

データ型`int`のラッパークラス

```java
public final class Integer extends Number
        implements Comparable<Integer>, Constable, ConstantDesc {
```

## メソッド

<details><summary>valueOf()</summary>

### valueOf()

`Integer`にキャストする。

```java
public static Integer valueOf(int i);

public static Integer valueOf(String s) throws NumberFormatException;

public static Integer valueOf(String s, int radix) throws NumberFormatException;
```

</details>

<details><summary>intValue()</summary>

### intValue()

`int`型にして返す。

```java
@HotSpotIntrinsicCandidate
public int intValue()
```

</details>

<details><summary>parseInt()</summary>

### parseInt()

`String`型を`Integer`型にパースする。

```java
public static int parseInt(String s) throws NumberFormatException;
```

</details>

<details><summary>toBinaryString()</summary>

### toBinaryString()

2進数の文字列を返す。

```java
public static String toBinaryString(int i);
```

</details>

<details><summary>toOctalString()</summary>

### toOctalString()

8進数の文字列を返す。

```java
public static String toOctalString(int i);
```

</details>

<details><summary>toHexString()</summary>

### toHexString()

16進数の文字列を返す。

```java
public static String toHexString(int i);
```

</details>

## 例

<details><summary>Auto Boxing</summary>

### Auto Boxing

```java
Integer num1 = 1;  // Integer.valueOf(1)
Integer num2 = 2;  // Integer.valueOf(2)
int num3 = num1 + num2;  // num1.intValue() + num2.intValue()
```

</details>
