# String

文字列のクラス。

```java
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence,
               Constable, ConstantDesc {
    @HotSpotIntrinsicCandidate
    public String(String original);

    public String(char value[]);

    public String(char value[], int offset, int count);

    public String(int[] codePoints, int offset, int count);

    public String(byte bytes[], int offset, int length, String charsetName);

    public String(byte bytes[], int offset, int length, Charset charset);

    public String(byte bytes[], String charsetName);

    public String(byte bytes[], Charset charset);

    public String(byte bytes[], int offset, int length);

    public String(byte[] bytes);

    public String(StringBuffer buffer);

    public String(StringBuilder builder);
```

## メソッド

<details><summary>length()</summary>

### length()

文字列の長さを返します。

```java
public int length();
```

</details>

<details><summary>charAt()</summary>

### charAt()

指定されたインデックスの`char`型の値を返します。

```java
public char charAt(int index);
```

</details>

<details><summary>substring()</summary>

### substring()

部分文字列を抽出します。

```java
public String substring(int beginIndex);
public String substring(int beginIndex, int endIndex);
```

</details>

<details><summary>indexOf()</summary>

### indexOf()

指定した文字が最初に出現するインデックスを返します。

```java
public int indexOf(int ch);

public int indexOf(int ch, int fromIndex);
```

</details>

<details><summary>lastIndexOf()</summary>

### lastIndexOf()

指定した文字が最後に出現するインデックスを返します。

```java
public int lastIndexOf(int ch);
```

</details>

<details><summary>startsWith()</summary>

### startsWith()

指定した接頭辞から文字列が始まるかどうかを返します。

```java
public boolean startsWith(String prefix);
public boolean startsWith(String prefix, int toffset);
```

</details>

<details><summary>endsWith()</summary>

### endsWith()

指定した末尾が文字列の末尾にマッチするかどうか返します。

```java
public boolean endsWith(String suffix);
```

</details>

<details><summary>equals()</summary>

### equals()

文字列が指定のオブジェクトと一致するか返します。

```java
public boolean equals(Object anObject);
```

</details>

<details><summary>concat()</summary>

### concat()

文字列を結合します。

```java
public String concat(String str);
```

</details>

<details><summary>trim()</summary>

### trim()

文字列の両端の空白を取り除いて返します。

```java
public String trim();
```

</details>

<details><summary>toLowerCase()</summary>

### toLowerCase()

文字列をすべて小文字に変換して返します。

```java
public String toLowerCase(Locale locale);
public String toLowerCase();
```

</details>

<details><summary>toUpperCase()</summary>

### toUpperCase()

文字列をすべて大文字にして返します。

```java
public String toUpperCase(Locale locale);
    public String toUpperCase();
```

</details>

<details><summary>contains()</summary>

### contains()

指定の文字列を含んでいるかを返します。

```java
public boolean contains(CharSequence s) {
```

</details>
