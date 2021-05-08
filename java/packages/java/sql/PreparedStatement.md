# PreparedStatement

`sql`文のインスタンス。

```java
public interface PreparedStatement extends Statement;
```

## メソッド

<details><summary>executeUpdate()</summary>

### executeUpdate()

`sql`文を実行する。

更新した行数を返す。

```java
int executeUpdate() throws SQLException;

```

</details>

<details><summary>executeQuery()</summary>

### executeQuery()

クエリを実行し、結果のオブジェクトを返す。

```java
ResultSet executeQuery() throws SQLException;

```

</details>

<details><summary>setInt()</summary>

### setInt()

ステートメント文に含まれた`?`のプレースホルダを

置換する。

```java
void setInt(int parameterIndex, int x) throws SQLException;

```

#### 引数

<details><summary>parameterIndex</summary>

##### parameterIndex

何番目の`?`かを指定する、(1から始まる。)

</details>

</details>

<details><summary>close()</summary>

### close()

```java
void close() throws SQLException;

```

</details>
