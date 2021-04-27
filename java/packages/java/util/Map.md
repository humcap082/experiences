# Map

連想配列を実装するためのインタフェース

```java
public interface Map<K, V> {
```

## メソッド

<details><summary>put()</summary>

### put()

要素を追加します。

```java
V put(K key, V value);
```

</details>

<details><summary>keySet()</summary>

### keySet()

キーの集合を返します。

```java
Set<K> keySet();
```

</details>
