# Command

<details><summary>node</summary>

## node

javascriptを実行。

```
node [<file_path>]
```

### オプション

<details><summary>-v</summary>

#### -v

バージョンを表示

--versionと等価。

```
-v
```

</details>

</details>

<details><summary>npm</summary>

## npm

```
npm [sub_command]
```

### オプション

<details><summary>-v</summary>

#### -v

```
-v
```

</details>

### サブコマンド

<details><summary>init</summary>

#### init

`package.json`を作成する。

```
init
```

##### オプション

<details><summary>-y</summary>

###### -y

質問項目を飛ばす。`-yes`と等価

```
-yes
```

</details>

##### 備考

<details><summary>package.json</summary>

###### package.json

インストールするモジュールを記述し、

依存関係を示すファイル。

</details>

<details><summary>質問項目</summary>

###### 質問項目

何も入れずにEnterでとばすこともできる。

- package name
- version
- description
- test command
- git repository
- keywords
- author
- license

</details>

</details>

<details><summary>install</summary>

#### install

指定したパッケージをインストールする。

指定しなかった場合は

`package.json`に記述されているパッケージをインストールする。

`package.json`は上書きされる。

`i`と等価。

```
install [<package>]
```

##### オプション

<details><summary>-g</summary>

###### -g

パッケージをすべてのプロジェクトで使用できるようにする。

`--global`と等価。

```
--g
```

</details>

<details><summary>-S</summary>

###### -S

指定してインストールしたパッケージを

`package.json`のdependenciesに記述する。

--saveと等価。

省略可能。

```
-S
```

</details>

<details><summary>--D</summary>

###### -D

指定してインストールしたパッケージを

`package.json`の`devDependencies`に記述する。

リリースに含めないパッケージを`devDependencies`に

記述する。`--save-dev`と等価

```
-D
```


</details>

</details>

<details><summary>ci</summary>

#### ci

`package.json`に記述されているパッケージをクリーンインストールする。

`package.json`は上書きされない。

</details>

<details><summary>uninstall</summary>

#### uninstall

指定したパッケージをアンインストールする。

```
uninstall <package_name>
```

##### オプション

<details><summary>-g</summary>

###### -g

グローバルのパッケージをアンインストールする。

```
-g
```

</details>

<details><summary>-S</summary>

###### -S

`package.json`の`dependencies`からも削除する。

`--save`と等価。

```
-S
```

</details>

<details><summary>-D</summary>

###### -D

`package.json`の`devDependencies`からも削除する。

`--save-dev`と等価。

```
-D
```

</details>

</details>

<details><summary>list</summary>

#### list

インストールされたパッケージの一覧。

```
list
```

##### オプション

<details><summary>-g</summary>

##### -g

インストールしたグローバルのパッケージの一覧

```
-g
```

</details>

</details>

</details>

