# ルートディレクトリ

<details><summary>bin</summary>

通常のコマンドなどのバイナリファイルがおかれる

</details>

<details><summary>dev</summary>

特殊デバイスファイル

## ディレクトリ

<details><summary>tty</summary>

`dev/tty1`のように端末をファイルのように扱っており、

ここのファイルに標準入力するとコンソールに標準出力される。

特に直接触る必要はない。

</details>

</details>

<details><summary>home</summary>

一般ユーザのホームディレクトリがおかれる

</details>

<details><summary>lib</summary>

ライブラリがおかれる

</details>

<details><summary>root</summary>

rootのホームディレクトリがおかれる

</details>

<details><summary>tmp</summary>

一時的に作成されるファイルがおかれる

</details>

<details><summary>var</summary>

ログファイルなど頻繁に変更されるファイルがおかれる

</details>

<details><summary>boot</summary>

起動時に必要なファイル

</details>

<details><summary>etc</summary>

各種プログラムの設定ファイルなどがおかれる

## ディレクトリ

<details><summary>passwd</summary>

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

<details><summary>group</summary>

グループ情報が格納される。

フォーマット

group_name:x:group_id:user[,...]

例

wheel:x:10:student

</details>

<details><summary>fstab</summary>

OS起動時にマウントするファイルシステムの一覧

フォーマット

`{hard_id | device_name}path file_system mount_options backup_flag system_check_flag`

</details>

</details>

<details><summary>media</summary>

一時的なマウントポイントなどが置かれる

</details>

<details><summary>proc</summary>

動作中のOSの情報などがおかれる

</details>

<details><summary>sbin</summary>

管理者用のコマンドがおかれる

</details>
