# gitコマンド

```bash
git
```

## サブコマンド

<details><summary>init</summary>

### init

レポジトリを作成する。(`.git`を作成。)

```bash
init [<directory_name>]

```

#### オプション

<details><summary>--bare</summary>

##### --bare

ワーキングツリーのないレポジトリを作成

```bash
--bare
```

</details>

<details><summary>--shared</summary>

##### --shared

共有リポジトリとして作成する。

```bash
--shared[=<permission>]
```

</details>

#### パラメータ

<details><summary>&lt;directory_name&gt;</summary>

新しいディレクトリを作成し、そこにレポジトリを作成する。

</details>

</details>

<details><summary>add</summary>

### add

ワークツリーからインデックスにファイルを追加する。

```bash
add <path>
```

#### オプション

<details><summary>-A</summary>

##### -A

gitで管理してないファイルも含めてインデックスに追加する。

(ワークツリーから削除したファイルも削除したことを登録する。)

```bash
-A
```

</details>

### 例

<details><summary>プロジェクト下のすべてのファイルを追加</summary>

```bash
git add -A .
```

</details>

</details>

<details><summary>commit</summary>

### commit

インデックスからローカルレポジトリに追加する。

```bash
commit [<path>]
```

#### オプション

<details><summary>-m</summary>

##### -m

コミットメッセージをつける。

```bash
-m <message>
```

</details>

<details><summary>--amend</summary>

##### --amend

直前のコミットを修正

`:q`で終了。

```bash
--amend
```

</details>

</details>

<details><summary>push</summary>

### push

現在のローカルブランチからリモートブランチに追加する。

```bash
push <url_alias> [<branch_name>]
```

#### オプション

<details><summary>-U</summary>

##### -U

現在のブランチを上流ブランチとする。

```bash
-U
```

</details>

<details><summary>-f</summary>

##### -f

`git reset`でプッシュ以前のコミットに戻したときに、

強制的にリモートにプッシュする。

```bash
-f
```

</details>

</details>

<details><summary>clone</summary>

### clone

リモートレポジトリを端末上にダウンロードする。

```bash
clone <remote_url>
```

</details>

<details><summary>pull</summary>

### pull

リモートレポジトリから`fetch`し、現在のブランチに`merge`する。

```bash
pull [<repository>] [<branch>]
```

</details>

<details><summary>fetch</summary>

### fetch

リモートブランチを保持するローカルのリモート追跡ブランチを更新

```bash
fetch [<url_alias>]
```

</details>

<details><summary>merge</summary>

### merge

現在のブランチに指定したブランチを結合する。

指定したブランチの最後のコミットメッセージが適用される。

```bash
merge <branch_name>
```

</details>

<details><summary>rebase</summary>

現在のブランチに指定したブランチを結合する。

指定したらブランチの途中のコミットメッセージも適用される。

```bash
rebase <branch_name>
```

### オプション

<details><summary>--continue</summary>

競合が起こって修正したあとのコマンド

```bash
--continue
```

</details>

</details>

<details><summary>reset</summary>

ワークツリーやインデックス、ローカルレポジトリの変更を

指定したコミット位置になるまで取り消しできる。

```bash
reset [<commit_id>] [<path>]
```

### オプション

<details><summary>--soft</summary>

ローカルレポジトリのみをリセットする。

```bash
--soft
```

</details>

<details><summary>--mixed</summary>

デフォルトのオプションでローカルレポジトリとインデックスまでリセットする。

```bash
--mixed
```

</details>

<details><summary>--hard</summary>

ローカルレポジトリとインデックスとワークツリーまでリセットする。

```bash
--hard
```

</details>

### パラメータ

<details><summary>commit_id</summary>

戻りたい過去のコミットID

#### 備考

<details><summary>HEAD</summary>

現在のコミットidのエイリアス。`@`も同じ。

##### 備考

<details><summary>HEAD^</summary>

語尾に`^`をつけることで一個前のコミットになる。

</details>

<details><summary>HEAD~n</summary>

`n`個前のコミット

</details>

</details>

</details>

</details>

<details><summary>branch</summary>

ブランチを作成する。引数を省略すると、現在のブランチを表示

```bash
branch [<branch_name>]
```

### オプション

<details><summary>-m</summary>

ブランチ名を変更する。

```bash
-m <old_branch_name> <new_branch_name>
```

</details>

<details><summary>-d</summary>

指定したマージ済みブランチを削除

```bash
-d
```

</details>

<details><summary>-D</summary>

マージされているかにかかわらず指定したブランチを削除。

```bash
-D
```

</details>

<details><summary>-a</summary>

追跡レポジトリも含め、表示

```bash
-a
```

</details>

</details>

<details><summary>checkout</summary>

### checkout

ブランチを切り替える。

```bash
git checkout <branch_name>
```

#### オプション

<details><summary>-b</summary>

##### -b

ブランチを作成して切り替える。

```bash
-b
```

</details>

</details>

<details><summary>remote</summary>

### remote

```bash
remote
```

### サブコマンド

<details><summary>add</summary>

#### add

リモートブランチのエイリアスをつくる。

```bash
add [<remote_url>] [<alias>]
```

</details>

</details>

<details><summary>rm</summary>

#### rm

インデックスやワークツリーからファイルを削除する。

```bash
rm <path>
```

### オプション

<details><summary>-r</summary>

 フォルダを指定するときにつける。

```bash
-r
```

</details>

<details><summary>--cached</summary>

インデックスからのみ削除し、ワーキングツリーから削除しない。

```bash
--cached
```

</details>

</details>

<details><summary>config</summary>

### config

設定ファイルの設定の表示や編集をする。

```bash
config [<name> [<value>]]
```

#### パラメータ

<details><summary>&lt;name&gt;</summary>

##### &lt;name&gt;

設定項目

|項目|説明|
|:---|:---|
|color.ui|Gitの色分け、デフォルトは(auto)|
|core.editor|コミットメッセージなどの編集に用いるエディタ|
|user.name|ユーザー名|
|user.email|Eメールアドレス|

</details>

<details><summary>&lt;value&gt;</summary>

##### $lt;value&gt;

設定する項目の値。

</details>

#### オプション

<details><summary>--system</summary>

##### --system

全ユーザーの全レポジトリの設定ファイル。

設定ファイルのパスは`/etc/gitconfig`

```bash
--system
```

</details>

<details><summary>--global</summary>

##### --global

ユーザーの全レポジトリの設定ファイル。

設定ファイルのパスは`~/.gitconfig`

```bash
--global
```

</details>

<details><summary>--local</summary>

##### --local

リポジトリ単体の設定ファイル。これがデフォルトです。

設定ファイルのパスは`<project_name>/.git/config`

```bash
--local
```

</details>

<details><summary>-l</summary>

##### -l

設定値をすべて表示する。

```bash
-l
```

</details>

<details><summary>-e</summary>

##### -e

設定ファイルをエディタで直接編集する。

</details>

</details>

<details><summary>status</summary>

### status

ワーキングツリーの状態を表示する。

```bash
status
```

</details>

<details><summary>log</summary>

### log

コミット履歴を表示

```bash
log
```

##### オプション

<details><summary>-p</summary>

##### -p

変更点を表示する。

```bash
-p [-<n>]
```

###### パラメータ

<details><summary>&lt;n&gt;</summary>

直近からの件数を指定する。

</details>

</details>

</details>

## 備考

<details><summary>ワーキングツリーの状態</summary>

### ワーキングツリーの状態

|状態|説明|
|:---|:---|
|Untracked|インデックスツリーに入ってない(addされていない)|
|Staged|インデックスツリーに入っていてローカルレポジトリにない|
|Unmodified|ローカルレポジトリにあって、ワーキングツリーと差分がない|
|Modified|ローカルレポジトリにあって、ワーキングツリーと差分がある|

</details>

