# ResultSet

クエリの実行結果を返すオブジェクト

```java
public interface ResultSet extends Wrapper, AutoCloseable {

```

## メソッド

<details><summary>next()</summary>

### next()

次の行にカーソルを移動する。

カーソルは最初`BOF - Begin Of File`に存在するため、

最初の行を取得するには、一度、このメソッドを実行する

必要がある。

次の行が存在しない場合は`false`を返す。

```java
boolean next() throws SQLException;

```

</details>

<details><summary>getInt()</summary>

### getInt()

現在のカーソルの行の整数型の列を指定して取得する。

```java
int getInt(int columnIndex) throws SQLException;

int getInt(String columnLabel) throws SQLException;

```

</details>

<details><summary>getString()</summary>

現在のカーソルの行の文字列型の列を指定して取得する。

### getString()

```java
String getString(int columnIndex) throws SQLException;

String getString(String columnLabel) throws SQLException;

```

</details>

<details><summary>close()</summary>

### close()

```java
void close() throws SQLException;

```

</details>
