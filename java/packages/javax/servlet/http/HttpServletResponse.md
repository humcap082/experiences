# HttpServletResponse

Httpレスポンスオブジェクトのインタフェース

```java
public interface HttpServletResponse extends ServletResponse {

```

## メソッド

<details><summary>getWriter</summary>

レスポンスボディに書き込むことができる`PrintWriter`を渡す。

```java
PrintWriter getWriter() throws IOException;

```

</details>
