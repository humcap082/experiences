# JSP基本文法

## ディレクティブ

<details><summary>page</summary>

### page

ページの属性を指定する。

```jsp
<%@ page <attr>="<value>"[ ...]%>
```

#### パラメータ

<details><summary>&lt;attr&gt;</summary>

##### &lt;attr&gt;

|attr|説明|
|:---|:---|
|language|使用するプログラミング言語(java)|
|contentType|コンテントタイプ|
|import|使用するパッケージ|
|pageEncoding|文字コード|

</details>

</details>

<details><summary>include</summary>

### include

ファイルを埋め込む。

```jsp
<%@ include file="<file_path>"%>
```

</details>

<details><summary>taglib</summary>

### taglib

カスタムタグのライブラリ名を指定する。

```jsp
<%@ taglib prefix="<prefix>" uri="<uri>">
```

#### パラメータ

<details><summary>prefix</summary>

##### prefix

指定したプレフィックスを次のように指定することで

カスタムタグを使用できる。

```jsp
<<prefix>:<custom_tag_name>>
```

</details>

</details>

## スクリプティング

<details><summary>scriptlet</summary>

### scriptlet

`Java`のコードを埋め込む

```jsp
<% <expression> %>
```

</details>

<details><summary>expression</summary>

### expression

`Java`のデータを`html`に出力する。

```jsp
<%= <expression> %>
```

</details>

<details><summary>declaration</summary>

### declaration

フィールドやメソッドを定義する。

```jsp
<%! <declaration> %>
```

</details>

## アクション

<details><summary>include</summary>

### include

指定したjspファイルを埋め込む。

```jsp
<jsp:include page="<path>" />
```

</details>

<details><summary>forward</summary>

### forward

指定したパスにフォワードする。

```jsp
<jsp:forward page="<path>"/>
```

</details>


## 備考

<details><summary>コメント</summary>

### コメント

```jsp
<%-- <comment> --%>
```

</details>

<details><summary>暗黙オブジェクト</summary>

### 暗黙オブジェクト

ファイル内で使用できる予約語

|オブジェクト|インタフェース|説明|
|:---|:---|:---|
|request|HttpServletRequest|リクエストオブジェクト|
|response|HttpServletResponse|レスポンスオブジェクト|
|pageContext|PageContext|ページコンテキスト|
|session|HttpSession|セッションオブジェクト|
|application|ServletContext|アプリケーションコンテキスト|
|out|JspWriter|jspの出力ストリーム|
|config|ServletConfig|初期化情報オブジェクト|
|page|Object|ファイルページ自身のオブジェクトを参照。|
|exception|Exception|例外オブジェクト|

</details>

<details><summary>EL</summary>

### EL

ページスコープ、リクエストスコープ、セッションスコープ、アプリケーションスコープ

に含まれる属性名を直接指定して出力する。同じ属性名が存在する場合、

先に見つかった属性を出力する。また見つからなかった場合は、何も

出力されない。

```jsp
${<data>}
```

#### 備考

<details><summary>暗黙オブジェクト</summary>

### 暗黙オブジェクト

|オブジェクト|インタフェース|説明|
|:---|:---|:---|
|pageScope|Map|ページスコープ|
|requestScope|Map|リクエストスコープ|
|sessionScope|Map|セッションスコープ|
|applicationScope|Map|アプリケーションスコープ|
|param|Map|リクエストパラメータ|

</details>

<details><summary>演算子と別名</summary>

### 演算子

`EL`式内で演算子を使用でき、

紛らわしい演算子は別名も使用できる。

|演算子|別名|
|:---|:---|
|/|div|
|%|mod|
|==|eq|
|!=|ne|
|&lt;|lt|
|&lt;=|le|
|&gt;|gt|
|&gt;=|ge|
|&&|and|
|&#124;&#124;|or|
|!|not|
|(空の評価)|empty|

</details>

</details>

<details><summary>JSTL</summary>

### JSTL

次のライブラリが必要なので[ここから](https://serarch.maven.org/)

検索してダウンロードします。

```
javax.servlet.jsp.jstl-api.jar
jstl-impl.jar
```

`taglib`ディレクティブで次のように指定します。

```jsp
<%@ taglib prefix="c" url="http://java.sun.com/jsp/jstl/core" %>
```

#### タグ

<details><summary>if</summary>

##### if

```jsp
<c:if test="<condition>">
    <expression>
</c:if>
```

</details>

<details><summary>choose</summary>

##### choose

多分枝

```jsp
<c:choose>
    <c:when test="<condition>"> <expression> </c:when>
    [...]
    <c:otherwise> <expression> </c:otherwise>
</c:choose>
```

</details>

<details><summary>forEach</summary>

##### forEach

```jsp
<c:forEach items="<items>" var="<variable>" [varStatus="<stat>"]>
    <expression>
</c:forEach>
```

もしくは

```jsp
<c:forEach var="<i>" begin="<b>" end="<e>" step="<s>">
    <expression>
</c:forEach>
```

###### 属性

<details><summary>varStatus</summary>

|属性|説明|
|:---|:---|
|current|現在のオブジェクト|
|index|現在のループインデックス(0から)|
|count|現在のループインデックス(1から)|
|first|ループの開始かどうか|
|end|ループの終わりかどうか|

</details>

</details>

</details>
