# DriverManager

データベースのドライバとの接続を管理する。

ドライバは別途、ダウンロードする必要がある。

インストールしたドライバはパスを通した後、`Class.forName()`で

メモリに読み込む。

```java
public class DriverManager {

```

## メソッド

<details><summary>getConnection()</summary>

### getConnection()

データベースとのコネクションを取得する。

```java
@CallerSensitive
public static Connection getConnection(String url)
    throws SQLException;

public static Connection getConnection(
    String url,
    String user,
    String password
) throws SQLException;

@CallerSensitive
public static Connection getConnection(
    String url,
    java.util.Properties info
) throws SQLException;

```

</details>
