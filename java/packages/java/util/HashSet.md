# HashSet

`Set`を実装した集合クラス。

```java
public class HashSet<E>
    extends AbstractSet<E>
    implements Set<E>, Cloneable, java.io.Serializable {

    public HashSet();

    public HashSet(Collection<? extends E> c);

    public HashSet(int initialCapacity, float loadFactor);

    public HashSet(int initialCapacity);
```
