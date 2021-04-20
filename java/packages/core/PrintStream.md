# PrintStream

```java
public class PrintStream extends FilterOutputStream
    implements Appendable, Closeable {
    public PrintStream(OutputStream out);

    public PrintStream(OutputStream out, boolean autoFlush);

    public PrintStream(OutputStream out, boolean autoFlush, String encoding)
            throws UnsupportedEncodingException;

    public PrintStream(OutputStream out, boolean autoFlush, Charset charset);

    public PrintStream(String fileName) throws FileNotFoundException;

    public PrintStream(String fileName, String csn)
            throws FileNotFoundException, UnsupportedEncodingException;

    public PrintStream(String fileName, Charset charset) throws IOException;

    public PrintStream(File file) throws FileNotFoundException;

    public PrintStream(File file, String csn)
            throws FileNotFoundException, UnsupportedEncodingException;

    public PrintStream(File file, Charset charset) throws IOException;
}

```

## メソッド

<details><summary>println()</summary>

```java
public void println(String x);
```

</details>

