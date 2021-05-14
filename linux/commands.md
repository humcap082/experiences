# コマンド

<details><summary>ls</summary>

## ls

ディレクトリ内のファイル一覧

```shell
ls [<path>]
```

## オプション

<details><summary>-R</summary>

### -R

その下の階層まで表示

```bash
-R
```

</details>

<details><summary>-l</summary>

### -l

それぞれのフォルダとファイルを1行で詳細に表示

```bash
-l
```

</details>

<details><summary>-o</summary>

### -o

標準出力として出力(パイプを使用時に必要)

```bash
-o
```

</details>

#### 備考

<details><summary>ls -l フォーマット</summary>

##### ls -l フォーマット

`<mode> <number_of_link> <user> <group> <size> <at_updated> <name>`

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

###### リンク数

ハードリンクの数

</details>

</details>

<details><summary>mkdir</summary>

ディレクトリを作成

```shell
mkdir [<path>]
```

## オプション

<details><summary>-p</summary>

途中のディレクトリも作成

```bash
-p
```

</details>

</details>

<details><summary>touch</summary>

ファイルを作成

```shell
touch <file_path>[ ...]
```

</details>

<details><summary>mv</summary>

ファイルをpathに移動、リネーム

```shell
mv [options] <file_path>[ ...] <path>
```

## オプション

<details><summary>-i</summary>

同じファイルが存在する場合確認。

```bash
-i
```

</details>

</details>

<details><summary>cd</summary>

カレントディレクトリを移動。

pathを省略するとホームディレクトリ

```shell
cd [<path>]
```

</details>

<details><summary>pwd</summary>

カレントディレクトリの絶対パスを表示

```shell
pwd
```

</details>

<details><summary>shutdown</summary>

シャットダウンする。

```shell
shutdown {now | +}
```

## オプション

<details><summary>-h</summary>

シャットダウン(デフォルト)

```bash
-h
```

</details>

<details><summary>-r</summary>

再起動

```bash
-r
```

</details>

<details><summary>-c</summary>

予約したシャットダウンをキャンセル。

```bash
-c
```

</details>

<details><summary>-k</summary>

シャットダウンするダイアログを表示

```bash
-k
```

</details>

### パラメータ

<details><summary>now</summary>

今すぐシャットダウン

```bash
now
```

</details>

<details><summary>+</summary>

シャットダウンを予約する。

```bash
+<n>
```

</details>

</details>

<details><summary>rm</summary>

ファイル、ディレクトリを削除

```shell
rm <path>[ ...]
```

## オプション

<details><summary>-r</summary>

ディレクトリを削除する。

```bash
-r
```

</details>

<details><summary>-i</summary>

事前に確認

```bash
-i
```

</details>

</details>

<details><summary>cat</summary>

ファイルの内容を表示

```shell
cat <file_path>
```

</details>

<details><summary>less</summary>

ファイルを一画面ずつ表示する

操作はvimに近い

```shell
less <file_path>
```

## オプション

<details><summary>+</summary>

指定した行を表示

```bash
+<n>
```

</details>

<details><summary>-p</summary>

指定した正規表現にマッチする最初の行から表示

```bash
-p <string>
```

</details>

<details><summary>-s</summary>

連続した行を1行にする

```bash
-s
```

</details>

<details><summary>-S</summary>

行を折り返さない

```bash
-S
```

</details>

<details><summary>-z</summary>

一画面の行数を指定する。

```bash
-z<n>
```

</details>

<details><summary>-n</summary>

行数を表示しない。

```bash
-n
```

</details>

<details><summary>-N</summary>

行数を表示する。

```bash
-N
```

</details>

</details>

<details><summary>who</summary>

誰がログインしているかを表示する

```shell
who
```

## オプション

<details><summary>-a</summary>

すべての情報を表示する。

```bash
-a
```

</details>

</details>

<details><summary>cp</summary>

ファイルをコピーする

```shell
cp <path1>[ ...] <path2>
```

## オプション

<details><summary>-r</summary>

ディレクトリごとコピー

```bash
-r
```

</details>

</details>

<details><summary>su</summary>

ユーザを切り替える

```shell
su [<user>]
```

## オプション

<details><summary>-</summary>

ログインシェルを使用してユーザーを切り替える

```bash
-
```

</details>

</details>

<details><summary>tail</summary>

ファイルの末尾を表示する

```shell
tail <path>
```

## オプション

<details><summary>-f</summary>

リアルタイム

```bash
-f
```

</details>

<details><summary>-</summary>

行数を指定。

```bash
-<n>
```

</details>

</details>

<details><summary>grep</summary>

ファイルの内容から指定したキーワードが含まれる

行のみ表示する。

もしくはパイプを使用してコマンドから指定したキーワードが含まれる

出力だけ出力する。　

```shell
grep <regex> <path>
```

</details>

<details><summary>useradd</summary>

ユーザを作成する

```shell
useradd username
```

## オプション

<details><summary>-u</summary>

ユーザーidを指定。

```bash
-u <n>
```

</details>

<details><summary>-d</summary>

ホームディレクトリを指定する。

```bash
-d <dir>
```

</details>

<details><summary>-g</summary>

グループを指定する。

```bash
-g <group_name>
```

</details>

</details>

<details><summary>passwd</summary>

パスワードを変更する。

```shell
passwd [<username>]
```

</details>

<details><summary>userdel</summary>

ユーザーを削除する

```shell
userdel <user>
```

## オプション

<details><summary>-r</summary>

ホームディレクトリごと削除する。

```bash
-r
```

</details>

</details>

<details><summary>groupadd</summary>

グループを作成する。

```shell
groupadd <group_name>
```

</details>

<details><summary>groups</summary>

どのグループに所属しているか確認する

ユーザ名を省略した場合、自分の所属するグループが表示される

```shell
groups [<user_name>]
```

</details>

<details><summary>usermod</summary>

ユーザが所属するグループを変更する

```shell
usermod <username>
```

## オプション

<details><summary>-g</summary>

プライマリグループを変更する。

```bash
-g <primary>
```

</details>

<details><summary>-G</summary>

サブグループを変更する。

```bash
-G <sub>
```

</details>

</details>

<details><summary>groupdel</summary>

グループを削除する

```shell
groupdel <group_name>
```

</details>

<details><summary>chmod</summary>

ファイルのパーミッションを変更

```shell
chmod <permission> <file_path>
```

### パラメータ

<details><summary>permission</summary>

指定方法は以下です。

1. 次のフォーマットで指定する。
`{u | g | o}{+ | - | =}{r | w | {x | t | s}}[...]`

2. 3桁の8進数で指定
左の桁から所有者権限、グループ権限、第三者権限
それぞれの桁はrwxのうち必要な権限に1をたてた
2進数を作る。rw-なら110でこれを8真数に直して6
rwxr--r--なら744をpermisionに渡す。
例外としてスティッキービットは1777。
SUIDビットは4000を足す。SGIDビットは2000を足す。

</details>

</details>

<details><summary>ln</summary>

path1のハードリンクを作成。

-sをつけることでシンボリックリンクを作成できる。

ハードリンクはファイルシステムをまたぐことができない。

シンボリックリンクはファイルシステムをまたぐことができる。

```shell
ln <path> <link_name>
```

## オプション

<details><summary>-s</summary>

```bash
-s
```

</details>

</details>

<details><summary>chown</summary>

所有ユーザや所有グループを変更する。

```shell
chown <user_name>[:<group>] <file_path>
```

</details>

<details><summary>chgrp</summary>

所有グループのを変更する

```shell
chgrp <groupname> <path>
```

</details>

<details><summary>umask</summary>

umask値を確認もしくは設定。

値を渡さなければ、現在の値を確認できる。

umask値とはデフォルトの権限を決めるものです。

ファイルのデフォルトの権限は666 - umask値

ディレクトリのデフォルトの権限は777 - umask値

となります。

```shell
umask [<number>]
```

## オプション

<details><summary>-p</summary>

現在の値を`umask`の形式で表示

```bash
-p
```

</details>

<details><summary>-s</summary>

現在の値を`rwx`の形式(シンボルモード)で表示

```bash
-s
```

</details>

</details>

<details><summary>find</summary>

ファイルを検索する

```shell
find <path>
```

## オプション

<details><summary>-perm</summary>

パーミッションで検索

```bash
-perm -<xxx>
```

</details>

<details><summary>-ls</summary>

`ls -l`の形式で表示

```bash
-ls
```

</details>

</details>

<details><summary>tty</summary>

現在使用しているコンソールを表示する

```shell
tty
```

</details>

<details><summary>pstree</summary>

プロセスの階層構造を表示する

```shell
pstree [<pid> | <username>]
```

## オプション

<details><summary>-p</summary>

プロセスidを表示

```bash
-p
```

</details>

</details>

<details><summary>ps</summary>

実行中のプロセスを一覧表示する

```shell
ps
```

## オプション

<details><summary>a</summary>

コンソールが持つすべてのプロセスを表示

```bash
a
```

</details>

<details><summary>x</summary>

コンソールが持たないすべてのプロセスを表示する。

```bash
x
```

</details>

<details><summary>r</summary>

実行中のプロセスだけ表示する。

```bash
r
```

</details>

<details><summary>u</summary>

読みやす形で表示

```bash
u
```

</details>

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

</details>

<details><summary>kill</summary>

プロセスを停止する

```shell
kill {<pid> | %<job_number>}
```

## オプション

<details><summary>-HUP</summary>

端末が制御不能もしくは切断として終了

```bash
-HUP
```

</details>

<details><summary>-INT</summary>

キーボードからの割り込みとして終了。

```bash
-INT
```

</details>

<details><summary>-KILL</summary>

強制終了

```bash
-KILL
```

</details>

<details><summary>-TERM</summary>

デフォルトの終了

```bash
-TERM
```

</details>

<details><summary>-CONT</summary>

一時停止しているプロセスを再開

```bash
-CONT
```

</details>

<details><summary>-STOP</summary>

一時停止する。

```bash
-STOP
```

</details>

</details>

<details><summary>jobs</summary>

起動しているジョブの一覧

```shell
jobs [%<job_number>]
```

<details><summary>-l</summary>

`PID`を表示

```bash
-l
```

</details>

<details><summary>jobsの結果のフォーマット</summary>

`<job_number>{+ | - | } <status> <jobname>`

</details>

</details>

<details><summary>bg</summary>

ジョブをバックグラウンドで実行

ジョブ番号を省略するとカレントジョブをバックグラウンドで実行

もしくは次のようにコマンドの後ろに

`&`をつけることでバックグランドで実行

`<command> &`

```shell
bg [%<job_number>L | - | +]
```

</details>

<details><summary>fg</summary>

バックグランドジョブをフォアグランドで実行

```shell
fg [%<job_number> | - | +]
```

</details>

<details><summary>echo</summary>

標準出力をする

```shell
echo <something>
```

</details>

<details><summary>date</summary>

日時を表示する

```shell
date
```

</details>

<details><summary>set</summary>

シェルのオプションを設定する。

shell_optionを指定せずに

`set -o`とした場合、現在の設定を見れる

```shell
set [<shell_option>]
```

## オプション

<details><summary>-o</summary>

有効にする

```bash
-o
```

</details>

<details><summary>+o</summary>

無効にする。

```bash
+o
```

</details>

### 備考

<details><summary>シェルのオプション</summary>

|シェルのオプション|説明|
|:---|:---|
|noclobber|上書き保存させない|

</details>

</details>

<details><summary>tee</summary>

パイプを使用することで、ファイル書き込みと標準出力を同時にできる。

```shell
command | tee <path>
```

</details>

<details><summary>gzip</summary>

指定したファイルをGNU zip形式で圧縮したファイルを作成する。

```shell
gzip <path>[ ...]
```

## オプション

<details><summary>-c</summary>

圧縮した結果をファイルに書き込まずに標準出力する

```bash
-c
```

</details>

<details><summary>-v</summary>

処理情報を詳細に表示する。

```bash
-v
```

</details>

<details><summary>-d</summary>

アシュクファイルを解凍する。

```bash
-d
```

</details>

<details><summary>-l</summary>

圧縮前後のサイズ、圧縮率、元のファイル名を表示する。

```bash
-l
```

</details>

</details>

<details><summary>gunzip</summary>

gzipを解凍する

```shell
gunzip <path>[ ...]
```

## オプション

<details><summary>-c</summary>

圧縮した結果をファイルに書き込まずに標準出力する

```bash
-c
```

</details>

<details><summary>-v</summary>

勝利情報を詳細に表示する。

```bash
-v
```

</details>

</details>

<details><summary>tar</summary>

アーカイブを作成する

```shell
tar <path>[ ...]
```

## オプション

<details><summary>c</summary>

アーカイブファイルの作成

```bash
c
```

</details>

<details><summary>x</summary>

アーカイブファイルの展開

```bash
x
```

</details>

<details><summary>t</summary>

アーカイブファイルんの`ls`コマンド形式で一覧表示

```bash
t
```

</details>

<details><summary>r/summary>

既存のアーカイブファイルの最後に新たにファイルを追加

```bash
r
```

</details>

<details><summary>v</summary>

処理情報を詳細に表示する。

```bash
v
```

</details>

<details><summary>f</summary>

作成するアーカイブに名前をつける。

```bash
f <name>
```

</details>

<details><summary>z</summary>

`gzip`形式の圧縮、解凍を同時におこなう。

```bash
z
```

</details>

<details><summary>j</summary>

`bzip2`形式の圧縮、解凍を同時に行う。

```bash
j
```

</details>

</details>

<details><summary>mkfifo</summary>

名前付きパイプを作成する。

名前付きパイプとは、コマンドの結果を受け取るためのファイル。

これにより別々のタイミングでコマンドからコマンドへ

出力を渡せます。

```shell
mkfifo <name>
```

</details>

<details><summary>mount</summary>

外部のファイルシステムをフォルダにマウントする。

引数を省略した場合は現在マウントされているファイルシステムの一覧が表示されます。

また、fstabに登録されている場合、device_nameもしくはpathどちらかでよい。

```shell
mount [<device_name>] [<path>]
```

## オプション

<details><summary>-t</summary>

ファイルシステムを指定する。

```bash
-t <file_system>
```

</details>

<details><summary>-o</summary>

マウントオプションを指定する。

```bash
-o <mount_option>
```

### パラメータ

<details><summary>mount_option</summary>

|マウントオプション||
|:---|:---|
|ro|読み出し専用でマウントする|

</details>

</details>

<details><summary>-a</summary>

/etc/fstabに登録されているすべてのファイルシステムをマウント

```bash
-a
```

</details>

</details>

<details><summary>unmount</summary>

マウントしたファイルシステムを解除する。

```shell
unmount {<device_name> | <path>}
```

</details>

<details><summary>df</summary>

現在マウントされているファイルシステムを一覧表示

```shell
df
```

## オプション

<details><summary>-h</summary>

容量や使用料が単位付きで表示される。

```bash
-h
```

</details>

<details><summary>-i</summary>

ファイル数を表示(ノード数)

```bash
-i
```

</details>

</details>

<details><summary>ssh-keygen</summary>

## ssh-keygen

sshの秘密鍵、公開鍵を作成する。

鍵はデフォルトで`.ssh/`に配置され、

拡張子に`.pub`ついているファイルが公開鍵になる。

```bash
ssh-keygen
```

### オプション

<details><summary>-t</summary>

暗号化のアルゴリズムを指定する。

```bash
-t <algorithm>
```

</details>

<details><summary>-C</summary>

メッセージをつける。

```bash
-C '<message>'
```

</details>

<details><summary></summary>
</details>

</details>
