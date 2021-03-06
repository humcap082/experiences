# HttpServletRequest

リクエストオブジェクトのインタフェース

```java
public interface HttpServletRequest extends ServletRequest {
```

## メソッド

<details><summary>getParameter()</summary>

### getParameter()

クエリパラメータやフォームデータを受けとるメソッド

```java
public String getParameter(String name);

```

</details>

<details><summary>setAttribute()</summary>

### setAttribute()

任意の属性名にオブジェクトを設定する。

オブジェクトは`Serializable`を実装している必要がある。

```java
public void setAttribute(String name, Object o);

```

</details>

<details><summary>getAttribute()</summary>

### getAttribute()

任意の属性のオブジェクトを取得する。

キャストする必要がある。

```java
public Object getAttribute(String name);

```

</details>

<details><summary>setCharacterEncoding()</summary>

### setCharacterEncoding()

リクエストパラメータをエンコーディングする。

```java
public void setCharacterEncoding(String env)
    throws java.io.UnsupportedEncodingException;

```

</details>

<details><summary>getSession()</summary>

### getSession()

現在のセッションを返す。

```java
public HttpSession getSession(boolean create);
public HttpSession getSession();

```

#### 引数

<details><summary>create</summary>

##### create

セッションが存在しなかった場合に、セッションを新しく

作成するかどうか。

</details>

</details>

<details><summary>getRequestDispatcher()</summary>

### getRequestDispatcher()

指定したパスにフォワードするディスパッチャを取得する。

```java
public RequestDispatcher getRequestDispatcher(String path);

```

</details>
