# StringBuilder

文字の可変シーケンスです。

```java
public final class StringBuilder
    extends AbstractStringBuilder
    implements java.io.Serializable, Comparable<StringBuilder>, CharSequence

    @HotSpotIntrinsicCandidate
    public StringBuilder();

    @HotSpotIntrinsicCandidate
    public StringBuilder(int capacity);

    @HotSpotIntrinsicCandidate
    public StringBuilder(String str);

    public StringBuilder(CharSequence seq);
```

## メソッド

<details><summary>append()</summary>

### append()

指定した文字列を末尾に追加します。

```java
@Override
public StringBuilder append(Object obj);

@Override
@HotSpotIntrinsicCandidate
public StringBuilder append(String str);

public StringBuilder append(StringBuffer sb)

@Override
public StringBuilder append(CharSequence s)

@Override
public StringBuilder append(CharSequence s, int start, int end);

@Override
public StringBuilder append(char[] str);

@Override
public StringBuilder append(char[] str, int offset, int len);

@Override
public StringBuilder append(boolean b);

@Override
@HotSpotIntrinsicCandidate
public StringBuilder append(char c);

@Override
@HotSpotIntrinsicCandidate
public StringBuilder append(int i);

@Override
public StringBuilder append(long lng);

@Override
public StringBuilder append(float f);

@Override
public StringBuilder append(double d)
```

</details>

<details><summary>insert()</summary>

### insert()

指定した文字列を指定した場所に挿入します。

```java
    @Override
    public StringBuilder insert(int index, char[] str, int offset, int len);

    @Override
    public StringBuilder insert(int offset, Object obj);

    @Override
    public StringBuilder insert(int offset, String str);

    @Override
    public StringBuilder insert(int offset, char[] str);

    @Override
    public StringBuilder insert(int dstOffset, CharSequence s);

    @Override
    public StringBuilder insert(
        int dstOffset,
        CharSequence s,
        int start,
        int end
    );

    */
    @Override
    public StringBuilder insert(int offset, boolean b);

    @Override
    public StringBuilder insert(int offset, char c);

    @Override
    public StringBuilder insert(int offset, int i);

    @Override
    public StringBuilder insert(int offset, long l);

    @Override
    public StringBuilder insert(int offset, float f);

    @Override
    public StringBuilder insert(int offset, double d);
```

</details>

<details><summary>replace()</summary>

## replace()

指定した範囲の部分文字列を指定した文字列に置換します。

```java
@Override
public StringBuilder replace(int start, int end, String str)
```

</details>

<details><summary>length()</summary>

### length()

文字列の文字数を返します。

```java
public int length();
```

</details>

<details><summary>capacity()</summary>

### capacity()

文字列のバッファを返します。

```java
public int capacity();
```

</details>

