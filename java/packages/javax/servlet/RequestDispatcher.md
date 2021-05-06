# RequestDispatcher

リクエストをフォワードするクラスのインタフェース

```java
public interface RequestDispatcher {}
```

## メソッド

<details><summary>forward()</summary>

### forward()

リクエストをフォワードする。

```java
public void forward(ServletRequest request, ServletResponse response)
        throws ServletException, IOException;

```

</details>
