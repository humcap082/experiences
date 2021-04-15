# gitコマンド

```bash
git [options] sub_command
```

## サブコマンド

<details><summary>add</summary>

ワークツリーからインデックスにファイルを追加する。

```bash
git add [options] path
```

### オプション

<details><summary>-A</summary>

gitで管理してないファイルも含めてインデックスに追加する。

(ワークツリーから削除したファイルも削除したことを登録する。)

```bash
git add -A path
```

</details>

***

### 例

<details><summary>プロジェクト下のすべてのファイルを追加</summary>

```bash
git add -A .
```

</details>

***

</details>

***

<details><summary>commit</summary>

インデックスからローカルレポジトリに追加する。

```bash
git commit [options] [path]
```

### オプション

<details><summary>-m</summary>

コミットメッセージをつける。

```bash
git commit -m message [path]
```

</details>

***

<details><summary>--amend</summary>

直前のコミットを修正

`:q`で終了。

```bash
git commit --amend
```

</details>

***

</details>

***

<details><summary>push</summary>

現在のローカルブランチからリモートブランチに追加する。

```bash
git push [options] url_alias [branch_name]
```

### オプション

<details><summary>-U</summary>

現在のブランチを上流ブランチとする。

```bash
git push -U url_alias branch_name
```

</details>

***

</details>

***

<details><summary>clone</summary>

リモートレポジトリを端末上にダウンロードする。

```bash
git clone remote_url
```

</details>

***

<details><summary>pull</summary>

リモートレポジトリから`fetch`し、現在のブランチに`merge`する。

```bash
git pull [options] [repository] [branch]
```

</details>

***

<details><summary>fetch</summary>

リモートブランチを保持するローカルのブランチ　

`origin/main`を更新

```bash
git fetch
```

</details>

***


<details><summary>merge</summary>

現在のブランチに指定したブランチを結合する。

指定したブランチの最後のコミットメッセージが適用される。

```bash
git merge branch_name
```

</details>

***

<details><summary>rebase</summary>

現在のブランチに指定したブランチを結合する。

指定したらブランチの途中のコミットメッセージも適用される。

```bash
git rebase [--options] branch_name
```

### オプション

<details><summary>--continue</summary>

競合が起こって修正したあとのコマンド

```bash
git rebase --continue
```

</details>

***


</details>

***

<details><summary>reset</summary>

ワークツリーやインデックス、ローカルレポジトリの変更を

指定したコミット位置になるまで取り消しできる。

```bash
git reset [options] [commit_id] [path]
```

## オプション

<details><summary>--soft</summary>

ローカルレポジトリのみをリセットする。

```bash
git reset --soft [commit_id] [path]
```

</details>

***

<details><summary>--mixed</summary>

デフォルトのオプションでローカルレポジトリとインデックスまでリセットする。

```bash
git reset --mixed [commit_id] [path]
```

</details>

***

<details><summary>--hard</summary>

ローカルレポジトリとインデックスとワークツリーまでリセットする。

```bash
git reset --hard [commit_id] [path]
```

</details>

***

### 備考

<details><summary>HEAD</summary>

現在のコミットidのエイリアス。`@`も同じ。

#### 備考

<details><summary>HEAD^</summary>

語尾に`^`をつけることで一個前のコミットになる。

</details>

***

<details><summary>HEAD~n</summary>

`n`個前のコミット

</details>

***


</details>

***


</details>

***

<details><summary>branch</summary>

ブランチを作成する。引数を省略すると、現在のブランチを表示

```bash
git branch [options] [branch_name]
```

</details>

***

<details><summary>checkout</summary>

ブランチを切り替える。

```bash
git checkout [options] branch_name
```

### オプション

<details><summary>-b</summary>

ブランチを作成して切り替える。

```bash
git checkout -b branch_NAME
```

</details>

***

</details>

***

<details><summary>remote</summary>

```bash
git remote [options] [sub_command]
```

### サブコマンド

<details><summary>add</summary>

リモートブランチのエイリアスをつくる。

```bash
git remote add [remote_url] [alias]
```

</details>

***

</details>

***

