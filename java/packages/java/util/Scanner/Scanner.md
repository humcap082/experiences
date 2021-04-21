# Scanner

```java
public final class Scanner implements Iterator<String>, Closeable {
    public Scanner(Readable source);
    
    public Scanner(InputStream source);
    
    public Scanner(InputStream source, String charsetName);
    
    public Scanner(InputStream source, Charset charset);
}
```

## メソッド

<details><summary>nextInt()</summary>

```java
public int nextInt();

public int nextInt(int radix);
```

</details>

<details><summary>nextDouble()</summary>

```java
public double nextDouble();
```

</details>


<details><summary>nextLine()</summary>

```java
public String nextLine();
```

</details>

