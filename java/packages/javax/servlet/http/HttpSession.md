# HTTPSession

セッション管理するインタフェース

```java
public interface HttpSession {

```

## メソッド

<details><summary>getAttribute()</summary>

### getAttribute()

セッションパラメータを取得する。

```java
public Object getAttribute(String name);

```

</details>

<details><summary>setAttribute()</summary>

### setAttribute()

セッションパラメータを設定する。

```java
public void setAttribute(String name, Object value);

```

</details>

<details><summary>setMaxInactiveInterval()</summary>

### setMaxInactiveIInterval

セッションのタイムアウト時間を設定する。

```java
public void setMaxInactiveInterval(int interval);
```

#### 備考

<details><summary>web.xml</summary>

デフォルトで`web.xml`に設定することができます。

```xml
<session-config>
    <session-timeout>30</session-timeout>
</session-config>
```

</details>

</details>

<details><summary>invalidate()</summary>

### invalidate()

セッションを破棄する。

```java
public void invalidate();

```

</details>
