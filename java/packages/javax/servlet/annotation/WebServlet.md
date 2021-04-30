# WebServlet

エンドポイントをルーティングするアノテーションで

`HTTPServlet`を継承するクラスにつける。

```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
public @interface WebServlet {
    String name() default "";
    String[] value() default {};
    String[] urlPatterns() default {};
    int loadOnStartup() default -1;
    WebInitParam[] initParams() default {};
    boolean asyncSupported() default false;
    String smallIcon() default "";
    String largeIcon() default "";
    String description() default "";
    String displayName() default "";
```

## 属性

<details><summary>name</summary>

エンドポイントをルーティングする相対url。

```java
String name() default "";
```

</details>
