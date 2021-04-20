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
public void println();

public void println(boolean x);

public void println(char x);

public void println(int x);

public void println(long x);

public void println(float x);

public void println(double x);

public void println(char x[]);

public void println(String x); 

public void println(Object x);
```

</details>

<details><summary>print()</summary>

```java
public void print(boolean b);

public void print(char c);

public void print(int i);

public void print(long l);

public void print(float f);

public void print(double d);

public void print(char s[]);

public void print(String s);

public void print(Object obj);
```

</details>

