# Class

クラスとしてキャストするクラス。

```java
public final class Class<T> implements java.io.Serializable,
                              GenericDeclaration,
                              Type,
                              AnnotatedElement,
                              TypeDescriptor.OfField<Class<?>>,
                              Constable {}
```

## メソッド

<details><summary>forName()</summary>

### forName()

指定された文字列名を持つクラスまたはインタフェースに

関連付けられた、クラスオブジェクトを返す。

```java
public static Class<?> forName(String className)
            throws ClassNotFoundException;

public static Class<?> forName(
    String name,
    boolean initialize,
    ClassLoader loader
    ) throws ClassNotFoundException;


```

</details>

