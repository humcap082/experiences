## Exception

アプリケーションでキャッチされる可能性のある例外のクラスであり、

その他の例外クラスの親クラス。

```java
public class Exception extends Throwable {
    public Exception();

    public Exception(String message);

    public Exception(String message, Throwable cause);

    public Exception(Throwable cause);

    protected Exception(
        String message,
        Throwable cause,
        boolean enableSuppression,
        boolean writableStackTrace
    );
```

### メソッド


<details><summary>printStackTrace()</summary>

### printStackTrace()

```java
public void printStackTrace();

public void printStackTrace(PrintStream s);

private void printStackTrace(PrintStreamOrWriter s);

```

</details>

