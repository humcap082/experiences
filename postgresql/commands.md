# postgresqlコマンド

<details><summary>pg_ctl</summary>

`postgres`コマンドのラッパコマンドでサーバーの起動、停止、制御ができる。

```bash
pg_ctl
```

### サブコマンド

<details><summary>start</summary>

サーバーをバックグランドで起動

```bash
start
```

</details>

<details><summary>stop</summary>

サーバーを終了

```bash
stop
```

</details>

</details>

<details><summary>createdb</summary>

データベースを作成する。

```bash
createdb <db_name>
```

### オプション

<details><summary>-o</summary>

所有者を指定する。

```bash
-o <user_name>
```

</details>

</details>

<details><summary>dropdb</summary>

データベースを削除する。

```bash
dropdb <db_name>
```

</details>

<details><summary>createuser</summary>

ユーザーアカウントを作成する。

```bash
createuser <user_name>
```

### オプション

<details><summary>-P</summary>

新しいパスワードを設定する。

```bash
-P <user_name>
```

</details>

</details>

<details><summary>psql</summary>

データーベースに接続するコマンド

```bash
psql [<db_name> [<user_name>]]
```

### オプション

<details><summary>-l</summary>

データベース一覧を表示

```bash
-l
```

</details>

<details><summary>-U</summary>

 ユーザーを指定する

```bash
-U <user_name>
```

</details>

### 接続後のコマンド

<details><summary>\d</summary>

ディメンションテーブル一覧もしくは、

テーブルの定義を見る。

```sql
\d [<table_name>]
```

</details>

<details><summary>\d</summary>

ユーザの一覧を表示する。

```sql
\du
```

</details>

<details><summary>\dp</summary>

権限を表示する。

```sql
\dp
```

</details>

<details><summary>\di</summary>

インデックスの一覧を表示する。

```sql
\di
```

</details>

<details><summary>\q</summary>

接続終了

```sql
\q
```

</details>

<details><summary>\i</summary>

指定したファイルのsqlを実行する。

```sql
\i <path>
```

</details>

<details><summary>\l</summary>

データベース一覧

```sql
\l
```

</details>

<details><summary>\c</summary>

データベースを切り替える。

```sql
\c <database_name>
```

</details>

</details>

<details><summary>initdb</summary>

テンプレートデータベース`template0, template1`を作成する。

```sql
initdb
```

</details>
