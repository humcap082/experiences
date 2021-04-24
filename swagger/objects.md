# オブジェクト

<details><summary>OpenAPI</summary>

## OpenAPI

OpenAPIスキーマの親のオブジェクト。

```yaml
openapi: <openapi_version>
info:
  Info  # required
servers:
  - Server
paths:  # required
  PathMap
components:
  Components
security:
  - SecurityRequirement
tags:
  - Tag
externalDocs:
  ExternalDocumentation
```

### パラメータ

<details><summary>&lt;openapi_version&gt;</summary>

#### &lt;openapi_version&gt;

`OpenAPI`仕様のバージョンを指定します。

セマンティックバージョン形式。

現在利用可能なバージョンは3.0.0, 3.0.1, 3.0.2, 3.0.3です。

</details>

</details>

<details><summary>Info</summary>

## Info

`API`関するメタ情報を提供します。

```yaml
title: <api_title>  # required
description: <api_description>
version: <api_version>  # required
termesOfService: <terms_of_service_path>
```

### パラメータ

<details><summary>&lt;api_title&gt;</summary>

#### &lt;api_title&gt;

`API`名を指定する

</details>

<details><summary>&lt;api_description&gt;</summary>

#### &lt;api_description&gt;

APIの説明を記述します。

複数行にすることができ、`Markdown`の`CommonMark`を

サポートしています。

</details>

<details><summary>&lt;api_version&gt;</summary>

#### &lt;api_version&gt;

APIのバージョンを指定する。

`<major>.<minor>.<patch>`のようなセマンティックバージョニング

以外にも`1.0-beta`や`2017-07-25`のようにも指定できます。

</details>

<details><summary>&lt;terms_of_service_path&gt;</summary>

#### &lt;terms_of_service_path&gt;

利用規約への相対パスを記述

</details>

</details>

<details><summary>Server</summary>

## Server

ターゲットサーバーの接続情報を提供します。

本番サーバーやサンドボックスサーバーなど複数のサーバー

を定義、上書きします。

```yaml
url: <server_url>  # required
description: <server_description>
variables:
  ServerVariableMap
```

### パラメータ　

<details><summary>&lt;server_url&gt;</summary>

#### &lt;server_url&gt;

ベースのURLを指定します。

`RFC3986`に準拠しており、通常は次のようになります。

`[<scheme>://<host>[:<port>]][/<path>]`

`serverse`が省略され他場合、デフォルトは`/`です。

`path`のみを指定した場合、 ホストはローカルサーバーに

対して解決されます。

##### 備考

<details><summary>scheme</summary>

##### scheme

- https
- http
- ws
- wss

</details>

<details><summary>host</summary>

##### host

ホストはIPアドレスにも対応しています。

</details>

</details>

<details><summary>&lt;server_description&gt;</summary>

#### &lt;server_description&gt;

サーバーの説明を記述します。

`CommonMark`というマークダウンをサポートしていて複数行記述できます。

</details>

### 例

<details><summary>サーバーのオーバーライド</summary>

#### サーバーのオーバーライド

一部のエンドポイントがほかのAPIとは異なるサーバーや

ベースパスを使用する場合に、グローバルの`servers`を

上書きできます。

```yaml
servers:
  - url: https://api.example.com/v1
paths:
  /files:
    description: File upload and download operations
    servers:
      - url: https://files.example.com
        description: Override base path for all operations with the /files path
  /ping:
    get:
      servers:
        - url: https://echo.example.com
          description: Override base path for the GET /ping operation
```

</details>

</details>

<details><summary>ServerVariableMap</summary>

## ServerVariableMap

サーバー変数を定義する。

```yaml
<varaible>:
  ServerVariable
[...]
```

### パラメータ

<details><summary>&lt;variable&gt;</summary>

#### &lt;variable&gt;

サーバー変数名。

</details>

</details>

<details><summary>ServerVariable</summary>

## ServerVariable

サーバー変数の属性を指定する。

サーバー変数は`url`のテンプレートを置換します。

```yaml
enum:
  - <enum_value>
default: <default_value>  # default_value
description: <variable_description>
```

### パラメータ

<details><summary>&lt;enum_value&gt;</summary>

#### &lt;enum_value&gt;

列挙型の要素を指定します。

</details>

<details><summary>&lt;default_value&gt;</summary>

#### &lt;default_value&gt;

サーバー変数のデフォルト値。

</details>

<details><summary>&lt;variable_description&gt;</summary>

#### &lt;variable_description&gt;

サーバー変数の説明を記述します。

複数行のマークダウンを使用できます。

</details>

### 例

<details><summary>HTTPSおよびHTTP</summary>

#### HTTPSおよびHTTP

```yaml
servers:
  - url: '{protocol}://api.example.com'
    variables:
      protocol:
        enum:
          - http
          - https
        default: https
```

</details>

<details><summary>ProductionとDevelopmentとStaging</summary>

#### ProductionとDevelopmentとStaging

```yaml
servers:
  - url: https://{environment}.example.com/v2
    variables:
      environment:
        default: api    # Production server
        enum:
          - api         # Production server
          - api.dev     # Development server
          - api.staging # Staging server
```

</details>

<details><summary>SaaSとOn-Premise</summary>

#### SaaSとOn-Premise

```yaml
servers:
  - url: '{server}/v1'
    variables:
      server:
        default: https://api.example.com  # SaaS server
```

</details>

<details><summary>リージョンごと</summary>

#### リージョンごと

```yaml
servers:
  - url: https://{region}.api.cognitive.microsoft.com
    variables:
      region:
        default: westus
        enum:
          - westus
          - eastus2
          - westcentralus
          - westeurope
          - southeastasia
```

</details>

</details>

<details><summary>PathMap</summary>

## PathMap

エンドポイントを定義する。

```yaml
<path>:
  Path
[...]
```

### パラメータ

<details><summary>&lt;path&gt;</summary>

#### &lt;path&gt;

エンドポイントへの相対パスを入れます。

パスパラメータを含むテンプレートを使用する場合は、

`{<parameter_name>}`のように中括弧で囲った部分が

置換されます。

</details>

</details>

<details><summary>Path</summary>

## Path

エンドポイントを定義できます。

```yaml
summary: <path_summary>
description: <path_description>
servers:
  - Server
get:
  Operation
post:
  Operation
put:
  Operation
patch:
  Operation
delete:
  Operation
options:
  Operation
head:
  Operation
trace:
  Operation
parameters:
  - Parameter | References
```

### パラメータ

<details><summary>&lt;path_summary&gt;</summary>

#### &lt;path_summary&gt;

エンドポイントの概要。

</details>

<details><summary>&lt;path_description&gt;</summary>

#### &lt;path_description&gt;

エンドポイントの説明を記述する。

マークダウンを使用できます。

</details>

### 例

<details><summary>共通パラメータ</summary>

#### 共通パラメータ

```yaml
paths:
  /user/{id}:
    parameters:
      - in: path
        name: id
        schema:
          type: integer
        required: true
        description: The user ID
    get:
      summary: Gets a user by ID
      ...
    patch:
      summary: Updates an existing user with the specified ID
      ...
    delete:
      summary: Deletes the user with the specified ID
      ...
```

</details>

</details>

<details><summary>Operation</summary>

## Operation

操作関数の設定

```yaml
operationId: <operation_id>
tags:
  - <operation_tag>
summary: <operation_summary>
description: <operation_discripton>
servers:
  - Server
parameters:
  - Parameter | Reference
requestBody:
  RequestBody | Reference
responses:  # required
  ResponseMap
deprecated: <operation_deprecated>
```

### パラメータ

<details><summary>&lt;operation_id&gt;</summary>

#### &lt;operation_id&gt;

操作を識別するために使用される一意の文字列です。

コードを自動生成するときのメソッド名に使用されます。

</details>

<details><summary>&lt;operation_tag&gt;</summary>

#### &lt;operation_tag&gt;

操作にタグをつけることで、ほかの操作とグループ化することができます

</details>

<details><summary>&lt;operation_summary&gt;</summary>

#### &lt;operation_summary&gt;

操作の概要。

</details>

<details><summary>&lt;operation_description&gt;</summary>

#### &lt;operation_description&gt;

操作の詳細。マークダウンをサポート。

</details>

<details><summary>&lt;operation_deprecated&gt;</summary>

#### &lt;operation_deprecated&gt;

操作が非推奨かどうかの真偽値を返す。

</details>

</details>

<details><summary>ParameterMap</summary>

## ParameterMap

```yaml
<parameter_model>:
  Parameter
```

### パラメータ

<details><summary>&lt;parameter_model&gt;</summary>

任意のパラメータのモデル名。

</details>

</details>

<details><summary>Parameter</summary>

## Parameter

パラメータの属性を設定する。

`schema`と`content`は排他であり、どちらかを

指定する。

```yaml
name: <parameter_name>  # required
in: <parameter_in>  # required
description: <parameter_description>
required: <parameter_required>
schema:
    Schema | Reference
content:
    MediaTypes
style: <style_value>
explode: <parameter_explode>
allowReserved: <parameter_allow_reserved>
allowEmptyValue: <parameter_allow_empty_value>
example: Any
examples:
  ExampleMap
deprecated: <parameter_deprecated>
```

### パラメータ

<details><summary>&lt;parameter_name&gt;</summary>

#### &lt;parameter_name&gt;

パラメータ名

</details>

<details><summary>&lt;parameter_in&gt;</summary>

#### &lt;parameter_in&gt;

パラメータの種類。

- query
- header
- path
- cookie

##### 例

<details><summary>パスパラメータ</summary>

###### パスパラメータ

URLパスの可変の部分です。これらは通常、IDで識別される

ユーザーなど、コレクション内の特定のリソースをさすために

使用されます。`in: path`を使用して定義されひつようがあり、

パスで指定されたもの同じである必要があります。また

パスパラメータは必須パラメータなので、`required: true`が

必要になります。

```yaml
paths:
  /users/{id}:
    get:
      parameters:
        - in: path
          name: id   # Note the name is the same as in the path
          required: true
          schema:
            type: integer
            minimum: 1
          description: The user ID
```

</details>

<details><summary>クエリパラメータ</summary>

###### クエリパラメータ

クエリパラメータはリクエスト`URL`の末尾の`?`のあとに表示され

複数指定する場合は`&`で区切られます。クエリパラメータは

必須およびオプションです。

```yaml
parameters:
        - in: query
          name: offset
          schema:
            type: integer
          description: The number of items to skip before starting to collect the result set
        - in: query
          name: limit
          schema:
            type: integer
          description: The numbers of items to return
```

</details>

<details><summary>ヘッダパラメータ</summary>

###### ヘッダパラメータ

カスタムリクエストヘッダーを定義する。

```yaml
paths:
  /ping:
    get:
      summary: Checks if the server is alive
      parameters:
        - in: header
          name: X-Request-ID
          schema:
            type: string
            format: uuid
          required: true
```

</details>

<details><summary>クッキーパラメータ</summary>

`in: cookie`を指定します。

```yaml
GET /api/users
Host: example.com
Cookie: debug=0; csrftoken=BUSe35dohU3O1MZvDCUOJ
```

</details>

</details>

<details><summary>&lt;parameter_description&gt;</summary>

#### &lt;parameter_description&gt;

パラメータの説明。マークダウンをサポート。

</details>

<details><summary>&lt;parameter_required&gt;</summary>

#### &lt;parameter_required&gt;

必須パラメータかどうかの真偽値。

デフォルトではすべてのパラメータがオプションとなるので、

必須パラメータはこの属性を指定する。

</details>

<details><summary>&lt;style_value&gt;</summary>

#### &lt;style_value&gt;

`RFC6570`に基づき、

パスパラメータ、クエリパラメータ、ヘッダパラメータ、

クッキーパラメータで配列やオブジェクトをうけとれるように

指定する。

|style|type|in|
|:---|:---|:---|
|matrix|primitive, array, object|path|
|label|primitive, array, object|path|
|form|primitive, array, object|query, qookie|
|simple|array|path, header|
|spaceDelimited|array|query|
|pipeDelimited|array|query|
|deepObject|object|query|

</details>

<details><summary>&lt;parameter_explode&gt;</summary>

#### &lt;parameter_explode&gt;

`object`や`array`をうけとるときに要素ごとにパラメータをつくる。

`style: form`のときはデフォルトで`true`だが、

それ以外はデフォルトは`false`

</details>

<details><summary>&lt;parameter_allow_reserved&gt;</summary>

#### &lt;parameter_allow_reserved&gt;

パスに含まれるクエリパラメータなどをパーセントエンコード

しないようにするかどうか。

</details>

<details><summary>&lt;parameter_allow_empty_value&gt;</summary>

クエリパラメータなどの名前のみで値を指定しない表現を許可するかどうか。

```
Get /foo?metadata
```

</details>

<details><summary>&lt;parameter_deprecated&gt;</summary>

パラメータが非推奨かどうかをいれる。

</details>

</details>

<details><summary>RequestBodyMap</summary>

## RequestBodyMap

```yaml
<request_body_name>:
  RequestBody
```

### パラメータ

<details><summary>&lt;request_body_name&gt;</summary>

リクエストボディの名前。

</details>

</details>

<details><summary>RequestBody</summary>

## RequestBody

```yaml
description: <request_body_description>
content:  # required
  MediaTypes
required: <request_body_required>
```

### パラメータ

<details><summary>&lt;request_body_description&gt;</summary>

#### &lt;request_body_description&gt;

リクエストボディの説明文。マークダウンをサポート

</details>

<details><summary>&lt;request_body_required&gt;</summary>

#### &lt;request_body_required&gt;

リクエストボディが必須かどうかのパラメータ

</details>

</details>

<details><summary>MediaTypes</summary>

## MediaTypes

メディアタイプごとのリクエストやレスポンスを定義します。


```yaml
<media_type>:
  MediaType
  [...]
```

### パラメータ

<details><summary>media_type</summary>

#### &lt;media_type&gt;

メディアタイプを指定する。`RFC6838`に準拠している必要があります。

ベンダー固有も使用できます。

- application/json
- application/xml
- application/x-www-form-urlencoded
- multipart/form-data
- text/plain; charset=utl-8
- text/html
- application/pdf
- image/png

##### 備考

<details><summary>application/x-www-form-urlencoded</summary>

一般的に使用されるフォーム送信の形式で、キーと値がペアのテキスト形式。

`html`の`POST`は基本的にこの方式で行われる。

</details>

<details><summary>multipart/form-data</summary>

バイナリデータやマルチメディアのデータをひとつのメッセージに

まとめた形式で、通常はファイルのアップロードなどに使用される形式。

</details>

</details>

### 例

<details><summary>複数のメディアタイプに同じスキーマを使用する。</summary>

#### 複数のメディアタイプに同じスキーマを使用する。

```yaml
paths:
  /employees:
    get:
      responses:
        '200':      # Response
          description: OK
          content:  # Response body
            application/json:  # Media type
             schema: 
               $ref: '#/components/schemas/Employee'    # Reference to object definition
            application/xml:   # Media type
             schema: 
               $ref: '#/components/schemas/Employee'    # Reference to object definition
components:
  schemas:
    Employee:      # Object definition
      type: object
      properties:
        id:
          type: integer
        name:
          type: string
        fullTime: 
          type: boolean
```

</details>

<details><summary>プレースホルダを使用する。</summary>

#### プレースホルダを使用する。

`*/*`や`application/*`、`image/*`などのプレースホルダーを使用できます。

```yaml
paths:
  /info/logo:
    get:
      responses:
        '200':           # Response
          description: OK
          content:       # Response body
            image/*:     # Media type
             schema: 
               type: string
               format: binary
```

</details>

</details>

<details><summary>MediaType</summary>

## MediaType

メディアの内容を定義します。

```yaml
schema:
  Schema | Reference
encoding:
  EncodingMap
examples:
  ExampleMap | Reference
example:
  Example

```

</details>

<details><summary>EncodingMap</summary>

# EncodingMap

```yaml
<propertie_name>:
  Encoding
```

</details>

<details><summary>Encoding</summary>

```yaml
contentType: <encoding_content_type>
allowReserved: <encoding_allow_reserved>
```

### パラメータ

<details><summary>&lt;encoding_allow_reserved&gt;</summary>

#### &lt;encoding_allow_reserved&gt;

受け取るパラメータの`:/?#[]@!$&'()*+,;=`などの予約語

パーセントエンコーディングしないようにするかどうか、

デフォルトでは`false`

</details>

<details><summary>&lt;encoding_content_type&gt;</summary>

#### &lt;encoding_content_type&gt;

受け取った値を指定のコンテントタイプにエンコーディングする。

</details>

</details>

<details><summary>ResponseMap</summary>

## ResponseMap

HTTPステータスコードに期待されるレスポンスを

マッピングします。

```yaml
default:
  Response | Reference
<http_status_code>:
  Response | Reference
  [...]
```

### パラメータ

<details><summary>&lt;http_status_code&gt;</summary>

HTTPステータスコードを記述する。

</details>

</details>

<details><summary>Response</summary>

## Response

レスポンスを定義する。

```yaml
Resopnse:
  description: <response_description>  # required
  content: MediaType
```

### パラメータ

<details><summary>response_description</summary>

レスポンスの説明

</details>

</details>

<details><summary>SchemaMap</summary>

## SchemaMap

スキーマを複数定義する。

```yaml
<schema_name>:
  Schema
  [...]
```

### パラメータ

<details><summary>&lt;schema_name&gt;</summary>

#### &lt;schema_name&gt;

スキーマの名前

</details>

</details>

<details><summary>Schema</summary>

## Schema

スキーマを定義する。

```yaml
type: <schema_type>
format: <type_format>
default: <schema_defualt>
minimum: <schema_minimum>
maximum: <schema_maximum>
properties:
    SchemaMap
example: <schema_example> | Example | Reference
required:
  - <required_param>
nullable: <schema_nullable>
oneOf:
  - Schema
anyOf:
  - Schema
```

### パラメータ

<details><summary>&lt;schema_type&gt;</summary>

#### &lt;schema_type&gt;

スキーマの型

</details>

<details><summary>&lt;format&gt;</summary>

#### &lt;format&gt;

型のフォーマットを指定する。

</details>

<details><summary>&lt;schema_default&gt;</summary>

#### &lt;schema_default&gt;

デフォルト値をいれる。

</details>

<details><summary>&lt;schema_minimum&gt;</summary>

#### &lt;schema_minimum&gt;

スキーマの最小値を定義する。

</details>

<details><summary>&lt;schema_maximum&gt;</summary>

#### &lt;schema_maximum&gt;

スキーマの最大値を定義する。

</details>

<details><summary>&lt;schema_example&gt;</summary>

#### &lt;schema_example&gt;

スキーマの値の例を示す。

</details>

<details><summary>&lt;required_param&gt;</summary>

#### &lt;required_param&gt;

必須のパラメータ名

</details>

<details><summary>&lt;nullable&gt;</summary>

#### &lt;nullable&gt;

`null`を指定できるかどうかの真偽値をいれる。

デフォルトは`false`

</details>

### 例

<details><summary>代替のスキーマ</summary>

#### 代替のスキーマ

```yaml
requestBody:
        description: A JSON object containing pet information
        content:
          application/json:
            schema:
              oneOf:
                - $ref: '#/components/schemas/Cat'
                - $ref: '#/components/schemas/Dog'
                - $ref: '#/components/schemas/Hamster'
```

</details>

</details>

<details><summary>ExampleMap</summary>

## ExampleMap

```yaml
<example_name>:
  Example | Reference
```

### パラメータ

<details><summary>&lt;example_name&gt;</summary>

例の名前。

</details>

</details>

<details><summary>Example</summary>

## Example

スキーマの例を指定する。

```yaml
value: Any
```

</details>

<details><summary>Reference</summary>

## Reference

内部および外部で、モデルを参照する。

```yaml
$ref: '<reference>'  # required
```

### パラメータ

<details><summary>&lt;reference&gt;</summary>

#### &lt;reference&gt;

参照先。フォーマットは`json`参照に基づく。

`[<external_file_path>][#<internal_json_path>]`

### 例

<details><summary>内部ファイルのコンポーネントのドキュメント</summary>

#### 内部ファイルのコンポーネントのドキュメント

```yaml
$ref: '#/components/schemas/Pet'
```

</details>

<details><summary>外部ファイルのドキュメント</summary>

#### 外部ファイルのドキュメント

```yaml
$ref: Pet.yaml
```

</details>

<details><summary>外部ファイルと相対ドキュメント</summary>

#### 外部ファイルと相対ドキュメント

```yaml
$ref: definitions.yaml#/Pet
```

</details>

</details>

</details>

<details><summary>Components</summary>

## Components

```yaml
schemas:
  SchemaMap
parameters:
  ParameterMap
securitySchemes:
  SecuritySchemeMap
examples:
  ExampleMap
requestBodies:
  RequestBodyMap
```

### 例

<details><summary>共通パラメータ</summary>

#### 共通パラメータ

```yaml
components:
  parameters:
    offsetParam:  # <-- Arbitrary name for the definition that will be used to refer to it.
                  # Not necessarily the same as the parameter name.
      in: query
      name: offset
      required: false
      schema:
        type: integer
        minimum: 0
      description: The number of items to skip before starting to collect the result set.
    limitParam:
      in: query
      name: limit
      required: false
      schema:
        type: integer
        minimum: 1
        maximum: 50
        default: 20
      description: The numbers of items to return.
paths:
  /users:
    get:
      summary: Gets a list of users.
      parameters:
        - $ref: '#/components/parameters/offsetParam'
        - $ref: '#/components/parameters/limitParam'
      responses:
        '200':
          description: OK
  /teams:
    get:
      summary: Gets a list of teams.
      parameters:
        - $ref: '#/components/parameters/offsetParam'
        - $ref: '#/components/parameters/limitParam'
      responses:
        '200':
          description: OK
```

</details>

</details>

<details><summary>SecuritySchemeMap</summary>

## SecuritySchemeMap

使用できるセキュリティ構成を定義する。

```yaml
<scheme_name>:
  SecurityScheme | Reference
```

### パラメータ

<details><summary>&lt;scheme_name&gt;</summary>

#### &lt;scheme_name&gt;

定義するセキュリティスキームの名前

</details>

</details>

<details><summary>SecurityScheme</summary>

## SecurityScheme

セキュリティ構成を定義します。

```yaml
type: <scheme_type>  # required
description: <scheme_description>
flows:
  OAuthFlowMapObject
```

### パラメータ

<details><summary>&lt;scheme_type&gt;</summary>

#### &lt;scheme_type&gt;

セキュリティ構成の種類を指定します。

- apiKey
- http
- oauth2
- openIdConnect

</details>

<details><summary>&lt;scheme_description&gt;</summary>

#### &lt;scheme_description&gt;

セキュリティ構成の説明。マークダウンをサポートしています。

</details>

</details>

<details><summary>OAuthFlowMap</summary>

## OAuthFlowMap

セキュリティ構成に`oauth2`を選択したときに

定義しなければならない工程の定義。

```yaml
authorizationCode:
  OAuthFlow
```

</details>

<details><summary>OAuthFlow</summary>

## OAuthFlow

```yaml
authorizationUrl: <authorization_url>  #required
tokenUrl: <token_url>  # required
scopes:
  ScopeMap
```

### パラメータ

<details><summary>&lt;authorization_url&gt;</summary>

#### &lt;authorization_url&gt;

認証URLの相対パス。

</details>

<details><summary>&lt;token_url&gt;</summary>

#### &lt;token_url&gt;

トークンURLの相対パス

</details>

</details>

<details><summary>ScopeMap</summary>

## ScopeMap

```yaml
<scope_name>: <scope_description>
```

### パラメータ

<details><summary>&lt;scope_name&gt;</summary>

#### &lt;scope_name&gt;

スコープ名

</details>

<details><summary>&lt;scope_description&gt;</summary>

#### &lt;scope_description&gt;

スコープの説明

</details>

</details>

<details><summary>SecurityRequirement</summary>

## SecurityRequirement

```yaml
<scheme_name>:
  - <scope>
```

### パラメータ

<details><summary>&lt;scheme_name&gt;</summary>

#### &lt;scheme_name&gt;

定義したセキュリティ構成の名前

</details>

<details><summary>&lt;scope&gt;</summary>

#### &lt;scope&gt;

`oauth2`と`openConnectId`の場合は、利用可能な

スコープを渡す。それ以外のセキュリティ構成は

`[]`と空のリストを渡す必要がある。

</details>

</details>

<details><summary>ExternalDocumentation</summary>

## ExternalDocumentation

拡張ドキュメントのための外部リソースを指定する。

```yaml
url: <doc_url>  # required
description: <doc_description>
```

### パラメータ

<details><summary>&lt;doc_url&gt;</summary>

#### &lt;doc_url&gt;

拡張ドキュメントの相対パス。

</details>

<details><summary>&lt;doc_description&gt;</summary>

ドキュメントの説明を指定する。

</details>

</details>
