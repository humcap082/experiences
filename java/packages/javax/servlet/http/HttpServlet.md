# HttpServlet

サーブレットのエンドポイントの操作を定義する抽象クラス。

```java
public abstract class HttpServlet extends GenericServlet {
    public HttpServlet();
```

## メソッド

<details><summary>doGet()</summary>

### doGet()

`GET`リクエストを処理するメソッド

```java
protected void doGet(HttpServletRequest req, HttpServletResponse resp);

```

</details>

<details><summary>doPost()</summary>

### doPost()

`POST`リクエストを処理するメソッド

```java
protected void doPost(HttpServletRequest req, HttpServletResponse resp);

```

</details>

<details><summary>getServletContext()</summary>

### getServletContext()

サーブレットのコンテキストを取得するメソッド。

```java
public ServletContext getServletContext();
```

</details>

<details><summary>init()</summary>

### init()

パスにアクセスされたときに共通して実行するメソッド

```java
@Override
public void init(ServletConfig config) throws ServletException {

```

</details>
