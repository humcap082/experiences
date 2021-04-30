# HttpServletRequest

リクエストオブジェクトのインタフェース

```java
public interface HttpServletRequest extends ServletRequest {
```

## メソッド

<details><summary>getParameter</summary>

クエリパラメータやフォームデータを受けとるメソッド

```java
public String getParameter(String name);

```

</details>

<details><summary>setCharacterEncoding</summary>

リクエストパラメータをエンコーディングする。

```java
public void setCharacterEncoding(String env)
    throws java.io.UnsupportedEncodingException;

```

</details>
