# ルートディレクトリ

|ディレクトリ名|説明|
|:---|:---|
|bin|通常のコマンドなどのバイナリファイルがおかれる|
|dev|特殊デバイスファイル|
|home|一般ユーザのホームディレクトリがおかれる|
|lib|ライブラリがおかれる|
|root|rootのホームディレクトリがおかれる|
|tmp|一時的に作成されるファイルがおかれる|
|var|ログファイルなど頻繁に変更されるファイルがおかれる|
|boot|起動時に必要なファイル|
|etc|各種プログラムの設定ファイルなどがおかれる|
|media|一時的なマウントポイントなどが置かれる|
|proc|動作中のOSの情報などがおかれる|
|sbin|管理者用のコマンドがおかれる|

<details><summary>etc/passwd</summary>

ユーザー情報が保存される。

フォーマット

```
username:user_id:group_id:etc:homedirectry_path:shell_path
```

例

```
student:1000:1000:student:/home/student:/bin/bash
```

</details>

<details><summary>etc/group</summary>

グループ情報が格納される。

フォーマット

group_name:x:group_id:user[,...]

例

wheel:x:10:student

</details>

<details><summary>etc/fstab</summary>

OS起動時にマウントするファイルシステムの一覧

フォーマット

`{hard_id | device_name}path file_system mount_options backup_flag system_check_flag`

</details>

<details><summary>dev/tty</summary>

`dev/tty1`のように端末をファイルのように扱っており、

ここのファイルに標準入力するとコンソールに標準出力される。

特に直接触る必要はない。

</details>
