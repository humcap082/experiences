# gitコマンド

```bash
git
```

## サブコマンド

<details><summary>add</summary>

ワークツリーからインデックスにファイルを追加する。

```bash
add <path>
```

### オプション

<details><summary>-A</summary>

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

インデックスからローカルレポジトリに追加する。

```bash
commit [<path>]
```

### オプション

<details><summary>-m</summary>

コミットメッセージをつける。

```bash
-m <message>
```

</details>

<details><summary>--amend</summary>

直前のコミットを修正

`:q`で終了。

```bash
--amend
```

</details>

</details>

<details><summary>push</summary>

現在のローカルブランチからリモートブランチに追加する。

```bash
push <url_alias> [<branch_name>]
```

### オプション

<details><summary>-U</summary>

現在のブランチを上流ブランチとする。

```bash
-U
```

</details>

<details><summary>-f</summary>

`git reset`でプッシュ以前のコミットに戻したときに、

強制的にリモートにプッシュする。

```bash
-f
```

</details>

</details>

<details><summary>clone</summary>

リモートレポジトリを端末上にダウンロードする。

```bash
clone remote_url
```

</details>

<details><summary>pull</summary>

リモートレポジトリから`fetch`し、現在のブランチに`merge`する。

```bash
pull [<repository>] [<branch>]
```

</details>

<details><summary>fetch</summary>

リモートブランチを保持するローカルのリモート追跡ブランチを更新

```bash
fetch [<url_alias>]
```

</details>

<details><summary>merge</summary>

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

ブランチを切り替える。

```bash
git checkout <branch_name>
```

### オプション

<details><summary>-b</summary>

ブランチを作成して切り替える。

```bash
-b
```

</details>

</details>

<details><summary>remote</summary>

```bash
remote
```

### サブコマンド

<details><summary>add</summary>

リモートブランチのエイリアスをつくる。

```bash
add [<remote_url>] [<alias>]
```

</details>

</details>

<details><summary>rm</summary>

インデックスやワークツリーからファイルを削除する。

```bash
rm <path>
```

### オプション

<details><summary>-r</summary>

 フォルダを指定するときにつける。

```sql
-r
```

</details>

<details><summary>--cached</summary>

インデックスからのみ削除し、ワーキングツリーから削除しない。

```sql
--cached
```

</details>

</details>
