# Connection

データベースのコネクション

```java
public interface Connection  extends Wrapper, AutoCloseable {
```

## メソッド

<details><summary>prepareStatement()</summary>

### prepareStatement

sql文のインスタンスを取得。

```java
    PreparedStatement prepareStatement(String sql)
        throws SQLException;
```

</details>

<details><summary>close()</summary>

### close()

```java
void close() throws SQLException;
```

</details>

