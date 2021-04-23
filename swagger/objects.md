# オブジェクト

<details><summary>OpenAPI</summary>

OpenAPIスキーマの親のオブジェクト。

```yaml
openapi: <openapi_version>
info:
  Info  # required
servers:
  - Server
paths:  # required
  Paths
components:
  Components
security:
  - SecurityRequirement
tags:
  - Tag
externalDocs:
  ExternalDocumentation
```

## パラメータ

<details><summary>&lt;openapi_version&gt;</summary>

`OpenAPI`仕様のバージョンを指定します。

セマンティックバージョン形式。

現在利用可能なバージョンは3.0.0, 3.0.1, 3.0.2, 3.0.3です。

</details>

</details>

<details><summary>Info</summary>

`API`関するメタ情報を提供します。

```yaml
title: <api_title>  # required
description: <api_description>
version: <api_version>  # required
termesOfService: <terms_of_service_path>
```

## パラメータ

<details><summary>&lt;api_title&gt;</summary>

`API`名を指定する

</details>

<details><summary>&lt;api_description&gt;</summary>

APIの説明を記述します。

複数行にすることができ、`Markdown`の`CommonMark`を

サポートしています。

</details>

<details><summary>&lt;api_version&gt;</summary>

APIのバージョンを指定する。

`<major>.<minor>.<patch>`のようなセマンティックバージョニング

以外にも`1.0-beta`や`2017-07-25`のようにも指定できます。

</details>

<details><summary>terms_of_service_path</summary>

利用規約への相対パスを記述

</details>

</details>

<details><summary>Server</summary>

ターゲットサーバーの接続情報を提供します。

本番サーバーやサンドボックスサーバーなど複数のサーバー

を定義、上書きします。

```yaml
url: <server_url>  # required
description: <server_description>
variables:
  ServerVariables
```

## パラメータ　

<details><summary>&lt;server_url&gt;</summary>

ベースのURLを指定します。

`RFC3986`に準拠しており、通常は次のようになります。

`[<scheme>://<host>[:<port>]][/<path>]`

`serverse`が省略され他場合、デフォルトは`/`です。

`path`のみを指定した場合、 ホストはローカルサーバーに

対して解決されます。

### 備考

<details><summary>scheme</summary>

- https
- http
- ws
- wss

</details>

<details><summary>host</summary>

ホストはIPアドレスにも対応しています。

</details>

</details>

<details><summary>&lt;server_description&gt;</summary>

サーバーの説明を記述します。

`CommonMark`というマークダウンをサポートしていて複数行記述できます。

</details>

## 例

<details><summary>サーバーのオーバーライド</summary>

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

<details><summary>ServerVariables</summary>

サーバー変数を定義する。

```yaml
<varaible>:
  ServerVariable
[...]
```

## パラメータ

<details><summary>&lt;variable&gt;</summary>

サーバー変数名。

</details>

</details>

<details><summary>ServerVariable</summary>

サーバー変数の属性を指定する。

サーバー変数は`url`のテンプレートを置換します。

```yaml
enum:
  - <enum_value>
default: <default_value>  # default_value
description: <variable_description>
```

## パラメータ

<details><summary>&lt;enum_value&gt;</summary>

列挙型の要素を指定します。

</details>

<details><summary>&lt;default_value&gt;</summary>

サーバー変数のデフォルト値。

</details>

<details><summary>&lt;variable_description&gt;</summary>

サーバー変数の説明を記述します。

複数行のマークダウンを使用できます。

</details>

## 例

<details><summary>HTTPSおよびHTTP</summary>

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

```yaml
servers:
  - url: '{server}/v1'
    variables:
      server:
        default: https://api.example.com  # SaaS server
```

</details>

<details><summary>リージョンごと</summary>

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

<details><summary>Paths</summary>

エンドポイントを定義する。

```yaml
<path>:
  PathItem
[...]
```

<details><summary>&lt;path&gt;</summary>

エンドポイントへの相対パスを入れます。

パスパラメータを含む場合は、`{}`でパスパラメータを囲みます。

</details>

</details>

<details><summary>PathItem</summary>

エンドポイントを定義できます。

```yaml
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
```

## パラメータ

<details><summary>&lt;path_description&gt;</summary>

パスの説明を記述する。

マークダウンを使用できます。

</details>

</details>

<details><summary>Operation</summary>

操作関数の設定

```yaml
summary: <operation_summary>
description: <operation_discripton>
servers:
  - Server
parameters:
  - Parameter | Reference
requestBody:
  RequestBody | Reference
responses:  # required
  Responses
```

## パラメータ

<details><summary>&lt;operation_summary&gt;</summary>

操作の概要。

</details>

<details><summary>&lt;operation_description&gt;</summary>

操作の詳細。マークダウンをサポート。

</details>

</details>

<details><summary>Parameter</summary>

パラメータの属性を設定する。

```yaml
name: <parameter_name>  # required
in: <parameter_in>  # required
description: <parameter_description>
required: <parameter_required>
schema:
    Schema | Reference
```

## パラメータ

<details><summary>&lt;parameter_name&gt;</summary>

パラメータ名

</details>

<details><summary>&lt;parameter_in&gt;</summary>

パラメータの種類。

- query
- header
- path
- cookie

</details>

<details><summary>&lt;parameter_description&gt;</summary>

パラメータの説明。マークダウンをサポート。

</details>

<details><summary>&lt;parameter_required&gt;</summary>

必須パラメータかどうかの真偽値。

</details>

</details>

<details><summary>RequestBody</summary>

```yaml
description: <request_body_description>
content:  # required
  MediaTypes
required: <request_body_required>
```

## パラメータ

<details><summary>&lt;request_body_description&gt;</summary>

リクエストボディの説明文。マークダウンをサポート

</details>

<details><summary>&lt;request_body_required&gt;</summary>

リクエストボディが必須かどうかのパラメータ

</details>

</details>

<details><summary>MediaTypes</summary>

メディアタイプごとのリクエストやレスポンスを定義します。


```yaml
<media_type>:
  MediaType
  [...]
```

## パラメータ

<details><summary>media_type</summary>

メディアタイプを指定する。

- application/json
- application/xml
- text/plain

</details>

</details>

<details><summary>MediaType</summary>

メディアの内容を定義します。

```yaml
schema:
  Schema | Reference
```

</details>

<details><summary>Responses</summary>

HTTPステータスコードに期待されるレスポンスを

マッピングします。

```yaml
default:
  Response | Reference
<http_status_code>:
  Response | Reference
  [...]
```

</details>

<details><summary>Response</summary>

レスポンスを定義する。

```yaml
Resopnse:
  description: <response_description>  # required
  content: MediaType
```

</details>

<details><summary>Schemas</summary>

スキーマを複数定義する。

```yaml
<schema_name>:
  Schema
  [...]
```

## パラメータ

<details><summary>&lt;schema_name&gt;</summary>

スキーマの名前

</details>

</details>

<details><summary>Schema</summary>

スキーマを定義する。

```yaml
type: <schema_type>
format: <type_format>
minimum: <schema_minimum>
maximum: <schema_maximum>
properties: Schema
example: <schema_example> | Example | Reference
required:
  - <required_param>
```

## パラメータ

<details><summary>&lt;schema_type&gt;</summary>

スキーマの型

</details>

<details><summary>&lt;format&gt;</summary>

型のフォーマットを指定する。

</details>

<details><summary>&lt;schema_minimum&gt;</summary>

スキーマの最小値を定義する。

</details>

<details><summary>&lt;schema_maximum&gt;</summary>

スキーマの最大値を定義する。

</details>

<details><summary>&lt;schema_example&gt;</summary>

スキーマの値の例を示す。

</details>

<details><summary>&lt;required_param&gt;</summary>

必須のパラメータ名

</details>

</details>

<details><summary>Example</summary>

スキーマの例を指定する。

```yaml
value: Any
```

</details>

<details><summary>Reference</summary>

内部および外部で、モデルを参照する。

```yaml
$ref: '<reference>'  # required
```

## パラメータ

<details><summary>&lt;reference&gt;</summary>

参照先。フォーマットは`json`参照に基づく。

`[<external_file_path>][#<internal_json_path>]`

### 例

<details><summary>内部ファイルのコンポーネントのドキュメント</summary>

```yaml
$ref: '#/components/schemas/Pet'
```

</details>

<details><summary>外部ファイルのドキュメント</summary>

```yaml
$ref: Pet.yaml
```

</details>

<details><summary>外部ファイルと相対ドキュメント</summary>

```yaml
$ref: definitions.yaml#/Pet
```

</details>

</details>

</details>

<details><summary>Components</summary>

```yaml
schemas:
  Schemas
securitySchemes:
  SecuritySchemes
```

</details>

<details><summary>SecuritySchemes</summary>

使用できるセキュリティ構成を定義する。

```yaml
<scheme_name>:
  SecurityScheme | Reference
```

## パラメータ

<details><summary>&lt;scheme_name&gt;</summary>

定義するセキュリティスキームの名前

</details>

</details>

<details><summary>SecurityScheme</summary>

セキュリティ構成を定義します。

```yaml
type: <scheme_type>  # required
description: <scheme_description>
flows:
  OAuthFlowsObject
```

<details><summary>&lt;scheme_type&gt;</summary>

セキュリティ構成の種類を指定します。

- apiKey
- http
- oauth2
- openIdConnect

</details>

<details><summary>&lt;scheme_description&gt;</summary>

セキュリティ構成の説明。マークダウンをサポートしています。

</details>

</details>

<details><summary>OAuthFlows</summary>

セキュリティ構成に`oauth2`を選択したときに

定義しなければならない工程の定義。

```yaml
authorizationCode:
  OAuthFlow
```

</details>

<details><summary>OAuthFlow</summary>

```yaml
authorizationUrl: <authorization_url>  #required
tokenUrl: <token_url>  # required
scopes:
  Scopes
```

## パラメータ

<details><summary>&lt;authorization_url&gt;</summary>

認証URLの相対パス。

</details>

<details><summary>&lt;token_url&gt;</summary>

トークンURLの相対パス

</details>

</details>

<details><summary>Scopes</summary>

```yaml
<scope_name>: <scope_description>
```

## パラメータ

<details><summary>&lt;scope_name&gt;</summary>

スコープ名

</details>

<details><summary>&lt;scope_description&gt;</summary>

スコープの説明

</details>

</details>

<details><summary>SecurityRequirement</summary>

```yaml
<scheme_name>:
  - <scope>
```

## パラメータ

<details><summary>scheme_name</summary>

定義したセキュリティ構成の名前

</details>

<details><summary>scope</summary>

`oauth2`と`openConnectId`の場合は、利用可能な

スコープを渡す。それ以外のセキュリティ構成は

`[]`と空のリストを渡す必要がある。

</details>

</details>

<details><summary>ExternalDocumentation</summary>

拡張ドキュメントのための外部リソースを指定する。

```yaml
url: <doc_url>  # required
description: <doc_description>
```

### 説明

<details><summary>doc_url</summary>

拡張ドキュメントの相対パス。

</details>

<details><summary>doc_description</summary>

ドキュメントの説明を指定する。

</details>

</details>
