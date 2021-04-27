# List

可変リストを実装するためのインタフェース。

```java
public interface List<E> extends Collection<E> {

```

## メソッド

<details><summary>add()</summary>

### add()

要素を追加します。

```java
boolean add(E e);

void add(int index, E element);
```

</details>

<details><summary>remove()</summary>

### remove()

取り除きます。

```java
boolean remove(Object o);
```

</details>

<details><summary>get()</summary>

指定したインデックスの要素を返します。

```java
E get(int index);
```

</details>

