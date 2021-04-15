# postgresqlコマンド

<details><summary>pg_ctl</summary>

`postgres`コマンドのラッパコマンドでサーバーの起動、停止、制御ができる。

```bash
pg_ctl sub_command
```

### サブコマンド

<details><summary>start</summary>

サーバーをバックグランドで起動

```bash
pg_ctl start [options]
```

</details>

***

<details><summary>stop</summary>

サーバーを終了

```bash
pg_ctl stop [options]
```

</details>

***

</details>

***

<details><summary>createdb</summary>

データベースを作成する。

```bash
createdb [options] db_name
```

### オプション

<details><summary>-o</summary>

所有者を指定する。

```bash
createdb -o user_name db_name
```

</details>

***


</details>

***

<details><summary>create_user</summary>

ユーザーアカウントを作成する。

```bash
create_user [options] user_name
```

</details>

***


<details><summary>psql</summary>

データーベースに接続するコマンド

```bash
psql [options] [db_name [user_name]]
```

### オプション

<details><summary>-l</summary>

データベース一覧を表示

```bash
psql -l [options]
```

</details>

***

<details><summary>-U</summary>

 ユーザーを指定する

```bash
psql [options] -U user_name [dbname]
```

</details>

***


### 接続後のコマンド

<details><summary> \d </summary>

ディメンションテーブル一覧

```sql
\d
```

</details>

***

<details><summary>\q</summary>

接続終了

```bash
\q
```

</details>

***

<details><summary>\i</summary>

指定したファイルのsqlを実行する。

```bash
\i path
```

</details>

***


</details>

***


