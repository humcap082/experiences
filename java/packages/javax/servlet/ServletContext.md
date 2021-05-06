# ServletContext

サーブレットのコンテキストのクラス。

```java
public interface ServletContext {}

```

## メソッド

<details><summary>getAttribute()</summary>

### getAttribute()

指定したパラメータを取得する。

```java
public Object getAttribute(String name);

```

</details>

<details><summary>setAttribute()</summary>

### setAttribute()

パラメータを設定する。

```java
public void setAttribute(String name, Object object);

```

</details>
