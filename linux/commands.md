# コマンド

<details><summary>ls</summary>

ディレクトリ内のファイル一覧

```shell
ls [options] [path]
```

|オプション|説明|
|:---|:---|
|-R|その下の階層まで表示|
|-l|それぞれのフォルダとファイルを1行で詳細に表示|
|-o|標準出力として出力(パイプを使用時に必要)|

### 備考

<details><summary>ls -l フォーマット</summary>

`mode number_of_link user group size at_updated name`

例: `-rw-r--r-- 1 root root 81211 2021-03-04 07:00 myfile`

ファイルモード

|最初の桁|説明|
|:---|:---|
|-|レギュラーファイル|
|d|ディレクトリファイル|
|l|シンボリックリンク|
|b or c|特殊デバイスファイル|

|パーミッション|説明|
|:---|:---|
|r|読み取り(lsなど)|
|w|書き込み(ファイルの追加、削除など)|
|x|実行(cdなど)|
|-|禁止|
|t|スティッキービット。名前の変更や削除。|
|s|SUIDビットもしくは、SGIDビット。実行は実行者ではなく、所有者もしくは所有グループが実行|

2桁目以降順番に

1. 所有ユーザのパーミッション
2. 所有グループのパーミッション　
3. 第3者のパーミッション

#### リンク数

ハードリンクの数

</details>

***

</details>

***

<details><summary>mkdir</summary>

ディレクトリを作成

```shell
mkdir [options] [path]
```

|オプション|説明|
|:---|:---|
|-p|途中のディレクトリも作成|

</details>

***

<details><summary>touch</summary>

ファイルを作成

```shell
touch [options] file_path[ ...]
```

</details>

***

<details><summary>mv</summary>

ファイルをpathに移動、リネーム

```shell
mv [options] file_path[ ...] path
```

|オプション|説明|
|:---|:---|
|-i|同じファイルが存在する場合確認。|

</details>

***

<details><summary>cd</summary>

カレントディレクトリを移動。

pathを省略するとホームディレクトリ

```shell
cd [path]
```

</details>

***

<details><summary>pwd</summary>

カレントディレクトリの絶対パスを表示

```shell
pwd [options]
```

</details>

***

<details><summary>shutdown</summary>

シャットダウンする。

```shell
shutdown [options] {now | +n}
```

|オプション|説明|
|:---|:---|
|-h|シャットダウン(デフォルト)|
|-r|再起動|
|-c|予約したシャットダウンをキャンセル|
|-k|シャットダウンするダイアログを表示|
|+n|n分後にシャットダウン|
|now|いますぐシャットダウン|

</details>

***

<details><summary>rm</summary>

ファイル、ディレクトリを削除

```shell
rm [options] path[ ...]
```

|オプション|説明|
|:---|:---|
|-r|ディレクトリを削除する。|
|-i|事前に確認|

</details>

***

<details><summary>cat</summary>

ファイルの内容を表示

```shell
cat [options] file_path
```

</details>

***

<details><summary>less</summary>

ファイルを一画面ずつ表示する

操作はvimに近い

```shell
less [options] file_path
```

|オプション|説明|
|:---|:---|
|+n|n行目から表示|
|{+/ string | -p string}|stringが見つかった行から表示(正規表現可能)|
|-s|連続した行を1行にする|
|-S|行を折り返さない|
|-zn|一画面の行数|
|-n|行数を表示しない|
|-N|行数を表示する|

</details>

***

<details><summary>who</summary>

誰がログインしているかを表示する

```shell
who [options]
```

|オプション|説明|
|:---|:---|
|-a|すべての情報を表示する|

</details>

***

<details><summary>cp</summary>

ファイルをコピーする

```shell
cp [options] path1[ ...] path2
```

|オプション|説明|
|:---|:---|
|-r|ディレクトリごとコピー|

</details>

***

<details><summary>su</summary>

ユーザを切り替える

```shell
su [options] [user]
```

|オプション|説明|
|:---|:---|
|-|ログインシェルを使用してユーザーを切り替える|

</details>

***

<details><summary>tail</summary>

ファイルの末尾を表示する

```shell
tail [オプション] path
```

|オプション|説明|
|:---|:---|
|-f|リアルタイム|
|-n|末尾からn行表示|

</details>

***

<details><summary>grep</summary>

ファイルの内容から指定したキーワードが含まれる

行のみ表示する。

もしくはパイプを使用してコマンドから指定したキーワードが含まれる

出力だけ出力する。　

```shell
grep [options] regex path
```

</details>

***

<details><summary>useradd</summary>

ユーザを作成する

```shell
useradd [options] username
```

|オプション|説明|
|:---|:---|
|-u n|ユーザーidをnで指定|
|-d dir|ホームディレクトリをdirで指定する|
|-g group_name|グループを指定する。|

</details>

***

<details><summary>passwd</summary>

パスワードを変更する。

```shell
passwd [options] [username]
```

</details>

***

<details><summary>userdel</summary>

ユーザーを削除する

```shell
userdel [options] user
```

|オプション|説明|
|:---|:---|
|-r|ホームディレクトリごと削除する。|

</details>

***

<details><summary>groupadd</summary>

グループを作成する。

```shell
groupadd [options] group_name
```

</details>

***

<details><summary>groups</summary>

どのグループに所属しているか確認する

ユーザ名を省略した場合、自分の所属するグループが表示される

```shell
groups [user_name]
```

</details>

***

<details><summary>usermod</summary>

ユーザが所属するグループを変更する

```shell
usermod [options] username
```

|オプション|説明|
|:---|:---|
|-g primary|プライマリグループを変更する|
|-G sub|サブグループを変更する|

</details>

***

<details><summary>groupdel</summary>

グループを削除する

```shell
groupdel [options] group_name
```

</details>

***

<details><summary>chmod</summary>

ファイルのパーミッションを変更

```shell
chmod permission file_path
```

### 備考

<details><summary>パーミッション指定方法</summary>

1. 次のフォーマットで指定する。
`{u | g | o}{+ | - | =}{r | w | {x | t | s}}[...]`

3. 3桁の8進数で指定
左の桁から所有者権限、グループ権限、第三者権限
それぞれの桁はrwxのうち必要な権限に1をたてた
2進数を作る。rw-なら110でこれを8真数に直して6
rwxr--r--なら744をpermisionに渡す。
例外としてスティッキービットは1777。
SUIDビットは4000を足す。SGIDビットは2000を足す。

</details>

***

</details>

***

<details><summary>ln</summary>

path1のハードリンクを作成。

-sをつけることでシンボリックリンクを作成できる。

ハードリンクはファイルシステムをまたぐことができない。

シンボリックリンクはファイルシステムをまたぐことができる。

```shell
ln [option] path1 link_name
```

|オプション|説明|
|:---|:---|
|-s|シンボリックリンクを作成|

</details>

***

<details><summary>chown</summary>

所有ユーザや所有グループを変更する。

```shell
chown [options] user_name[:group] file_path
```

</details>

***

<details><summary>chgrp</summary>

所有グループのを変更する

```shell
chgrp groupname path
```

</details>

***

<details><summary>umask</summary>

umask値を確認もしくは設定。

値を渡さなければ、現在の値を確認できる。

umask値とはデフォルトの権限を決めるものです。

ファイルのデフォルトの権限は666 - umask値

ディレクトリのデフォルトの権限は777 - umask値

となります。

```shell
umask [値]
```

|オプション||
|:---|:---|
|-p|現在の値をumaskの形式で表示|
|-s|現在の値をrwx(シンボルモード)の形式で表示|

</details>

***

<details><summary>find</summary>

ファイルを検索する

```shell
find path [options]
```

|オプション|説明|
|:---|:---|
|-perm -xxx|パーミッションで検索|
|-ls|ls -lと同じ形式で表示|

</details>

***

<details><summary>tty</summary>

現在使用しているコンソールを表示する

```shell
tty
```

</details>

***

<details><summary>pstree</summary>

プロセスの階層構造を表示する

```shell
pstree [options] [pid | username]
```

|オプション|説明|
|:---|:---|
|-p|プロセスidを表示|

</details>

***

<details><summary>ps</summary>

実行中のプロセスを一覧表示する

```shell
ps [option]
```

|オプション|説明|
|:---|:---|
|a|端末を持つすべてのプロセスを表示|
|x|端末を持たないすべてのプロセスを表示する|
|r|実行中のプロセスだけを表示する|
|u|読みやすい形で表示|

### 備考

<details><summary>psで表示される項目</summary>

|項目|説明|
|:---|:---|
|USER|実行したユーザ名|
|PID|プロセスID|
|TTY|実行している端末|
|TIME|実行時間|
|COMMAND(CMD)|実行コマンド|
|%CPU|CPU利用率|
|%MEM|メモリの使用率|
|VSZ|使用している仮想メモリのサイズ|
|RSS|常駐セットの大きさ|
|STAT|状態(S: スリープ、R: 実行中、T: 一時停止)|
|START|プロセスの開始時間|

</details>

***

</details>

***

<details><summary>kill</summary>

プロセスを停止する

```shell
kill [ptions] {pid | %job_number}
```

|オプション|説明|
|:---|:---|
|-HUP|端末が制御不能もしくは切断による終了|
|-INT|キーボードからの割り込み|
|-KILL|強制終了|
|-TERM|終了(デフォルト)|
|-CONT|停止しているプロセスを再開|
|STOP|一時停止|

</details>

***

<details><summary>jobs</summary>

起動しているジョブの一覧

```shell
jobs [オプション] [ジョブ番号]
```

|オプション|説明|
|:---|:---|
|-l|PIDを表示|

<details><summary>jobsの結果のフォーマット</summary>

`job_number{+ | - | } status jobname`

</details>

***

</details>

***

<details><summary>bg</summary>

ジョブをバックグラウンドで実行

ジョブ番号を省略するとカレントジョブをバックグラウンドで実行

もしくは次のようにコマンドの後ろに

`&`をつけることでバックグランドで実行

`command &`

```shell
bg [%job_number | - | +]
```

</details>

***

<details><summary>fg</summary>

バックグランドジョブをフォアグランドで実行

```shell
fg [%job_number | - | +]
```

</details>

***

<details><summary>echo</summary>

標準出力をする

```shell
echo something
```

</details>

***

<details><summary>date</summary>

日時を表示する

```shell
date
```

</details>

***

<details><summary>set</summary>

シェルのオプションを設定する。

shell_optionを指定せずに

`set -o`とした場合、現在の設定を見れる

```shell
set [options] [shell_option]
```

|オプション|説明|
|:---|:---|
|-o|有効にする|
|+o|無効にする|

### 備考

<details><summary>シェルのオプション</summary>

|シェルのオプション|説明|
|:---|:---|
|noclobber|上書き保存させない|

</details>

***

</details>

***

<details><summary>tee</summary>

パイプを使用することで、ファイル書き込みと標準出力を同時にできる。

```shell
command | tee path
```

</details>

***

<details><summary>gzip</summary>

指定したファイルをGNU zip形式で圧縮したファイルを作成する。

```shell
gzip [options] path[ ...]
```

|オプション|説明|
|:---|:---|
|-c|圧縮した結果をファイルに書き込まずに標準出力する|
|-v|処理情報を詳細に表示する|
|-d|圧縮ファイルを回答する|
|-l|圧縮前後のサイズ、圧縮率、元のファイル名を表示する|

</details>

***

<details><summary>gunzip</summary>

gzipを解凍する

```shell
gunzip [options] path[ ...]
```

|オプション|説明|
|:---|:---|
|-c|圧縮した結果をファイルに書き込まずに標準出力する|
|-v|処理情報を詳細に表示する|

</details>

***

<details><summary>tar</summary>

アーカイブを作成する

```shell
tar [options] path[ ...]
```

|オプション|説明|
|:---|:---|
|c|アーカイブファイルの作成|
|x|アーカイブファイルの展開|
|t|アーカイブファイルの内容をlsコマンド形式で一覧表示|
|r|既存のアーカイブファイルの最後に新たにファイルを追加|
|v|処理情報を詳細に表示する|
|f name|作成するアーカイブに名前をつける|
|z|gzip形式の圧縮、解凍を同時に行う|
|j|bzip2形式の圧縮、解凍を同時に行う|

</details>

***

<details><summary>mkfifo</summary>

名前付きパイプを作成する。

名前付きパイプとは、コマンドの結果を受け取るためのファイル。

これにより別々のタイミングでコマンドからコマンドへ

出力を渡せます。

```shell
mkfifo [option] name
```

</details>

***

<details><summary>mount</summary>

外部のファイルシステムをフォルダにマウントする。

引数を省略した場合は現在マウントされているファイルシステムの一覧が表示されます。

また、fstabに登録されている場合、device_nameもしくはpathどちらかでよい。

```shell
mount [options] [device_name] [path]
```

|オプション|説明|
|:---|:---|
|-t file_system|ファイルシステムを指定する|
|-o mount_option|マウントオプションを指定する|
|-a|/etc/fstabに登録されているすべてのファイルシステムをマウント|

### 備考

<details><summary>mount -oで扱うマウントのオプション</summary>

|マウントオプション||
|:---|:---|
|ro|読み出し専用でマウントする|

</details>

***

</details>

***

<details><summary>unmount</summary>

マウントしたファイルシステムを解除する。

```shell
unmount {device_name | path}
```

</details>

***

<details><summary>df</summary>

現在マウントされているファイルシステムを一覧表示

```shell
df [options]
```

|オプション|説明|
|:---|:---|
|-h|容量や使用量が単位付きで表示される。|
|-i|ファイル数を表示(ノード数)|

</details>

***
