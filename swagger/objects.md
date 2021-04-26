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

### 属性

<details><summary>openapi</summary>

#### openapi

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
contact:
  Contact
license
  Licence
```

### 属性

<details><summary>title</summary>

#### title

`API`名を指定する

</details>

<details><summary>description</summary>

#### description

APIの説明を記述します。

複数行にすることができ、`Markdown`の`CommonMark`を

サポートしています。

</details>

<details><summary>version</summary>

#### version

APIのバージョンを指定する。

`<major>.<minor>.<patch>`のようなセマンティックバージョニング

以外にも`1.0-beta`や`2017-07-25`のようにも指定できます。

</details>

<details><summary>termsOfService</summary>

#### termsOfService

利用規約への相対パスを記述

</details>

</details>

<details><summary>Contact</summary>

## Contact

連絡先の情報

```yaml
name: <contact_organization>
url: <contact_url>
email: <contact_email>
```

</details>

<details><summary>License</summary>

## License

```yaml
name: <license_name>
url: <license_url>
```

### 属性

<details><summary>url</summary>

APIのライセンス情報をもつページのurl

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

### 属性　

<details><summary>url</summary>

#### url

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

<details><summary>&lt;description&gt;</summary>

#### description

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

### 属性

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

### 属性

<details><summary>enum</summary>

#### enum

列挙型の要素を指定します。

</details>

<details><summary>defualt</summary>

#### default

サーバー変数のデフォルト値。

</details>

<details><summary>description</summary>

#### description

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

### 属性

<details><summary>&lt;path&gt;</summary>

#### &lt;path&gt;

エンドポイントへの相対パスを入れます。

パス属性を含むテンプレートを使用する場合は、

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
  - Parameter | Reference
```

### 属性

<details><summary>summary</summary>

#### summary

エンドポイントの概要。

</details>

<details><summary>description</summary>

#### description

エンドポイントの説明を記述する。

マークダウンを使用できます。

</details>

<details><summary>parameters</summary>

#### parameters

パスレベルのの共通パラメータを指定する。

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
security:
  - SecurityRuquirement
servers:
  - Server
parameters:
  - Parameter | Reference
requestBody:
  RequestBody | Reference
responses:  # required
  Responses
deprecated: <operation_deprecated>
callbacks:
  CallbackMap
```

### 属性

<details><summary>operationId</summary>

#### operationId

操作を識別するために使用される一意の文字列です。

コードを自動生成するときのメソッド名に使用されます。

</details>

<details><summary>tags</summary>

#### tags

操作にタグをつけることで、ほかの操作とグループ化することができます

</details>

<details><summary>summary</summary>

#### summary

操作の概要。

</details>

<details><summary>description</summary>

#### description

操作の詳細。マークダウンをサポート。

</details>

<details><summary>security</summary>

#### security

必要なセキュリティスキームを指定する。

</details>

<details><summary>deprecated</summary>

#### deprecated

操作が非推奨かどうかの真偽値を返す。

</details>

### 例

<details><summary>コールバックの登録</summary>

```yaml
openapi: 3.0.0
info:
  version: 0.0.0
  title: test
paths:
  /subscribe:
    post:
      summary: Subscribe to a webhook
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                callbackUrl:   # Callback URL
                  type: string
                  format: uri
                  example: https://myserver.com/send/callback/here
              required:
                - callbackUrl
      responses:
        '201':
          description: Webhook created
      callbacks:   # Callback definition
        myEvent:   # Event name
          '{$request.body#/callbackUrl}':   # The callback URL,
                                            # Refers to the passed URL
            post:
              requestBody:   # Contents of the callback message
                required: true
                content:
                  application/json:
                    schema:
                      type: object
                      properties:
                        message:
                          type: string
                          example: Some event happened
                      required:
                        - message
              responses:   # Expected responses to the callback message
                '200':
                  description: Your server returns this code if it accepts the callback
```

</details>

</details>

<details><summary>SecurityRequirement</summary>

必要なセキュリティを指定する。

## SecurityRequirement

```yaml
<security_scheme_name>:
  - <scope_name>
```

### 属性

<details><summary>&lt;security_scheme_name&gt;</summary>

`Components`の`securitySchemes`で定義したスキーム名で、

必要なセキュリティ要求をわたす。

`OAuth2`と`OpenIDConnect`の場合は必要なスコープのリストを指定し、

それ以外は、空のリストを渡す。

</details>

### 例

<details><summary>OR</summary>

複数のスキームをリストで渡すとそのどれかを満たしていれば

許可されます。

```yaml
security:
  - basicAuth: []
  - apiKey: []
```

</details>

<details><summary>AND</summary>

ひとつの要素に複数のスキームを指定するとどちらも

満たす必要があrます。

```yaml
security:
  - apiKey1: []
    apiKey2: []
```

</details>

</details>

<details><summary>ParameterMap</summary>

## ParameterMap

```yaml
<parameter_model_name>:
  Parameter
```

### 属性

<details><summary>&lt;parameter_model_name&gt;</summary>

#### &lt;parameter_model_name&gt;

任意のパラメータのモデルの名前。

</details>

</details>

<details><summary>Parameter</summary>

## Parameter

属性の属性を設定する。

```yaml
name: <parameter_name>  # required
in: <parameter_in>  # required
description: <parameter_description>
required: <parameter_required>
schema:
    Schema | Reference
content:
    MediaTypeMap
style: <style_value>
explode: <parameter_explode>
allowReserved: <parameter_allow_reserved>
allowEmptyValue: <parameter_allow_empty_value>
example: Any
examples:
  ExampleMap
deprecated: <parameter_deprecated>
```

### 属性

<details><summary>name</summary>

#### name

属性名

</details>

<details><summary>in</summary>

#### in

属性の種類。

- query
- header
- path
- cookie

##### 例

<details><summary>パスパラメータ</summary>

###### パス属性

URLパスの可変の部分です。これらは通常、IDで識別される

ユーザーなど、コレクション内の特定のリソースをさすために

使用されます。`in: path`を使用して定義されひつようがあり、

パスで指定されたもの同じである必要があります。また

パスパラメータは必須属性なので、`required: true`が

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

クエリ属性はリクエスト`URL`の末尾の`?`のあとに表示され

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

###### ヘッダ属性

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

###### クッキーパラメータ

`in: cookie`を指定します。

```yaml
GET /api/users
Host: example.com
Cookie: debug=0; csrftoken=BUSe35dohU3O1MZvDCUOJ
```

</details>

</details>

<details><summary>description</summary>

#### description

属性の説明。マークダウンをサポート。

</details>

<details><summary>required</summary>

#### required

必須パラメータかどうかの真偽値。

デフォルトではすべてのパラメータがオプションとなるので、

必須パラメータはこの属性を指定する。

</details>

<details><summary>content</summary>

#### content

`schema`の代わりに指定できる。

</details>

<details><summary>style</summary>

#### style

`RFC6570`に基づき、

パス属性、クエリ属性、ヘッダ属性、

クッキー属性で配列やオブジェクトをうけとれるように

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

<details><summary>explode</summary>

#### explode

`object`や`array`をうけとるときに要素ごとにパラメータをつくる。

`style: form`のときはデフォルトで`true`だが、

それ以外はデフォルトは`false`

</details>

<details><summary>allowReserved</summary>

#### allowReserved

パスに含まれるクエリ属性などをパーセントエンコード

しないようにするかどうかの真偽値を指定する。デフォルトはfalse

</details>

<details><summary>allowEmptyValue</summary>

#### allowEmptyValue

クエリパラメータのパラメータ名のみで値を指定しない表現を許可するかどうか。

```
Get /foo?metadata
```

</details>

<details><summary>deprecated</summary>

#### deprecated

属性が非推奨かどうかをいれる。

</details>

</details>

<details><summary>CallbackMap</summary>

## CallbackMap

イベントをうけためコールバックのスキーマを

定義する。

```yaml
<callback_name>:
  Callback | Reference
```

</details>

<details><summary>Callback</summary>

## Callback

```yaml
'<callback_url>':
  Path
```

### 属性

<details><summary>&lt;callback_url&gt;</summary>

#### &lt;callback_url&gt;

ランタイム形式で、コールバックに登録された

`url`を指定する。

|表現|説明|
|:---|:---|
|&dollar;url|クエリ文字列を含む完全なリクエストURL|
|&dollar;method|HTTPメソッドをリクエストする。|
|&dollar;request.query.&lt;param_name&gt;|指定されたクエリパラメータの値|
|&dollar;request.path.&lt;param_name&gt;|指定されたパスパラメータの値|
|&dollar;request.header.&lt;param_name&gt;|指定されたヘッダパラメータの値|
|&dollar;request.body|リクエスト本文全体|
|&dollar;request.body#/foo/bar|jsonポインタによって指定された本文の一部|
|&dollar;statusCode|レスポンスのHTTPステータスコード|
|&dollar;response.header.&lt;header_name&gt;|指定されたレスポンスヘッダの値|
|&dollar;response.body|指定されたレスポンス本文全体|
|&dollar;response.body#/foo/bar|Jsonポインタによって指定されたレスポンス本部の一部|
|foo{<runtime_param>}bar|ランタイム形式の変数を埋め込む|

</details>

</details>

<details><summary>RequestBodyMap</summary>

## RequestBodyMap

```yaml
<request_body_name>:
  RequestBody
```

### 属性

<details><summary>&lt;request_body_name&gt;</summary>

リクエストボディの名前。

</details>

</details>

<details><summary>RequestBody</summary>

## RequestBody

```yaml
description: <request_body_description>
content:  # required
  MediaTypeMap
required: <request_body_required>
```

### 属性

<details><summary>description</summary>

#### description

リクエストボディの説明文。マークダウンをサポート

</details>

<details><summary>required</summary>

#### required

リクエストボディが必須かどうかの真偽値を指定。

</details>

### 例

<details><summary>ファイルのアップロード</summary>

#### ファイルのアップロード

```yaml
requestBody:
  content:
    multipart/form-data:
      schema:
        type: object
        properties:
          orderId:
            type: integer
          userId:
            type: integer
          fileName:
            type: string
            format: binary
        encoding:
          fileName:
            contentType: image/png, image/jpeg
```

</details>

</details>

<details><summary>MediaTypeMap</summary>

## MediaTypeMap

メディアタイプごとのリクエストやレスポンスを定義します。

```yaml
<media_type>:
  MediaType
  [...]
```

### 属性

<details><summary>&lt;media_type&gt;</summary>

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

## EncodingMap

```yaml
<property_name>:
  Encoding
```

### 属性

<details><summary>&lt;property_name&gt;</summary>

#### &lt;property_name&gt;

エンコードを指定するプロパティー名を入れる。

</details>

</details>

<details><summary>Encoding</summary>

## Encoding

```yaml
contentType: <encoding_content_type>
allowReserved: <encoding_allow_reserved>
```

### 属性

<details><summary>contentType</summary>

#### contentType

受け取った値を指定のコンテントタイプにエンコーディングする。

</details>

<details><summary>allowReserved</summary>

#### allowReserved

受け取る属性の`:/?#[]@!$&'()*+,;=`などの予約語

パーセントエンコーディングしないようにするかどうか、

デフォルトでは`false`

</details>

</details>

<details><summary>ResponseMap</summary>

## ResponseMap

```yaml
<resopnse_name>:
  Response
```

### 属性

<details><summary>&lt;response_name&gt;</summary>

レスポンスの名前とレスポンスの属性を指定する。

</details>

</details>

<details><summary>Responses</summary>

## Responses

HTTPステータスコードに期待されるレスポンスを

マッピングします。

```yaml
default:
  Response | Reference
<http_status_code>:
  Response | Reference
  [...]
```

### 属性

<details><summary>default</summary>

#### default

指定した以外のHTTPステータスコードが返された時の

デフォルトのレスポンス。

</details>

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
  links:
    linkMap
  headers:
    HeaderMap
```

### 属性

<details><summary>description</summary>

#### description

レスポンスの説明

</details>

<details><summary>links</summary>

#### links

レスポンスに返されるパラメータを別のリクエストのパラメータ

として利用できるように定義する。

</details>

### 例

<details><summary>リンク</summary>

```yaml
openapi: 3.0.0
info:
  version: 0.0.0
  title: Links example
paths:
  /users:
    post:
      summary: Creates a user and returns the user ID
      operationId: createUser
      requestBody:
        required: true
        description: A JSON object that contains the user name and age.
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/User'
      responses:
        '201':
          description: Created
          content:
            application/json:
              schema:
                type: object
                properties:
                  id:
                    type: integer
                    format: int64
                    description: ID of the created user.
          # -----------------------------------------------------
          # Links
          # -----------------------------------------------------
          links:
            GetUserByUserId:   # <---- arbitrary name for the link
              operationId: getUser
              # or
              # operationRef: '#/paths/~1users~1{userId}/get'
              parameters:
                userId: '$response.body#/id'
              description: >
                The `id` value returned in the response can be used as
                the `userId` parameter in `GET /users/{userId}`.
          # -----------------------------------------------------
  /users/{userId}:
    get:
      summary: Gets a user by ID
      operationId: getUser
      parameters:
        - in: path
          name: userId
          required: true
          schema:
            type: integer
            format: int64
      responses:
        '200':
          description: A User object
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'
components:
  schemas:
    User:
      type: object
      properties:
        id:
          type: integer
          format: int64
          readOnly: true
        name:
          type: string
```

</details>

</details>

<details><summary>LinkMap</summary>

```yaml
<link_name>:
  Link | Reference
```

### 属性

<details><summary>&lt;link_name&gt;</summary>

#### &lt;link_name&gt;

任意のリンクの名前

</details>

</details>

<details><summary>Link</summary>

## Link

レスポンスのパラメータとリクエストのパラメータを

紐づける。

```yaml
operationId: <operation_id>
operationRef: '<operation_ref>'
parameters:
  LinkParameterMap
description: <link_description>
```

### 属性

<details><summary>operationId</summary>

#### operationId

`Operation`の`oprationId`を指定する。

</details>

<details><summary>operationRef</summary>

#### operationRef

operationIdの代わりに使用できますが、推奨されません。

次のようなフォーマットで指定する。

`#paths/<path>/<method>`

これは`json`の参照に基づきます。

外部ファイルも参照できます。

`Reference`の`$ref`と同じです。

また、`<path>`のなかの`/`は`~1`でエンコーディングする

必要がある。

</details>

</details>

<details><summary>LinkParameterMap</summary>

## LinkParameterMap

リンクするパラメータを指定する。

```yaml
<parameter_name>: '<body_parameter_name>'
```

### 属性

<details><summary>&lt;parameter_name&gt;</summary>

#### &lt;parameter_name&gt;

リンクするリクエストのパラメータ名をいれ、

同じパラメータ名が複数ある場合は、

`query.id`や`path.id`など、プレフィックスをつけます。

そして、&lt;body_parameter_name&gt;に対応するレスポンスのパラメータを渡す。

レスポンスのパラメータは次のように渡す。

`$response.body#/<param_name>`

これはランタイム形式です。

`<param_name>`は定数の値でもかまいません。

</details>

### 備考

<details><summary>ランタイム形式</summary>

#### ランタイム形式

&lt;body_parameter_name&gt;の次の形式で指定します。

|表現|説明|
|:---|:---|
|&dollar;url|クエリ文字列を含む完全なリクエストURL|
|&dollar;method|HTTPメソッドをリクエストする。|
|&dollar;request.query.&lt;param_name&gt;|指定されたクエリパラメータの値|
|&dollar;request.path.&lt;param_name&gt;|指定されたパスパラメータの値|
|&dollar;request.header.&lt;param_name&gt;|指定されたヘッダパラメータの値|
|&dollar;request.body|リクエスト本文全体|
|&dollar;request.body#/foo/bar|jsonポインタによって指定された本文の一部|
|&dollar;statusCode|レスポンスのHTTPステータスコード|
|&dollar;response.header.&lt;header_name&gt;|指定されたレスポンスヘッダの値|
|&dollar;response.body|指定されたレスポンス本文全体|
|&dollar;response.body#/foo/bar|Jsonポインタによって指定されたレスポンス本部の一部|
|foo{<runtime_param>}bar|ランタイム形式の変数を埋め込む|

</details>

</details>

<details><summary>HeaderMap</summary>

## HeaderMap

```yaml
<custom_header_name>:
  Header | Reference
```

### 属性

<details><summary>&lt;custom_header_name&lt;</summary>

#### custom_header_name

カスタムヘッダーの名前をいれ、ヘッダの属性を指定する。

</details>

</details>

<details><summary>Header</summary>

## Header

```yaml
description: <header_description>
schema:
  Schema
```

### 属性

<details><summary>description</summary>

#### description

ヘッダの説明。マークダウンをサポート

</details>

<details><summary>schema</summary>

#### schema

ヘッダのスキーマを指定する。

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

### 属性

<details><summary>&lt;schema_name&gt;</summary>

#### &lt;schema_name&gt;

スキーマの名前

</details>

</details>

<details><summary>Schema</summary>

## Schema

スキーマを定義する。

`Wright Draft 00 (Draft 5)`に基づいています。

型を指定しない場合は、全ての型を受け入れます。

```yaml
type: <schema_type>
format: <type_format>
default: <schema_default>
items:
  Schema
uniqueItems: <unique_items>
minItems: <min_itmes>
maxItems: <max_items>
minimum: <schema_minimum>
exclusiveMinimum: <exclusive_minimum>
maximum: <schema_maximum>
exclusiveMaximum: <exclusive_maximum>
maxLength: <max_length>
minLength: <min_length>
pattern: <regex>
properties:
  SchemaMap
enum:
  - <enum_value>
example: Any
required:
  - <required_param>
nullable: <schema_nullable>
oneOf:
  - Schema
anyOf:
  - Schema
allOf:
  - Schema
multipleOf: <multiple>
readOnly: <read_only>
writeOnly: <write_only>
minProperties: <min_properties>
maxProperties: <max_Properties>
additionalProperties:
  Schema
descriminator:
  Discriminator
```

### 属性

<details><summary>type</summary>

#### type

スキーマの型

</details>

<details><summary>format</summary>

#### format

型のフォーマットを指定する。

ファイルは`type: string`で`format: binary`もしくは

`format: byte`で受け取ることができます。

</details>

<details><summary>default</summary>

#### default

デフォルト値をいれる。

</details>

<details><summary>items</summary>

#### items

`type: array`のとき、配列の要素となるスキーマ

</details>

<details><summary>uniqueItems</summary>

#### uniqueItems

配列の要素がユニークかどうかの真偽値を指定する。

</details>

<details><summary>minItems</summary>

#### minItems

配列の要素数の最小値。

</details>

<details><summary>maxItems</summary>

#### maxItems

配列の要素数の最大値。

</details>

<details><summary>minimum</summary>

#### minimum

スキーマの最小値を定義する。

</details>

<details><summary>exclusiveMinimum</summary>

#### exclusiveMinimum

`true`にすることで`minimum`の値を範囲に含めない。

(以上 ではなく より大きい になる。)

</details>

<details><summary>maximum</summary>

#### maximum

スキーマの最大値を定義する。

</details>

<details><summary>exclusiveMaximum</summary>

#### exclusiveMaximum

`true`にすることで`maximum`の値を範囲に含めない。

(以下 ではなく、 未満 になる。)

</details>

<details><summary>maxLength</summary>

#### maxLength

文字列の最大文字数。

</details>

<details><summary>minLength</summary>

#### minLength

文字列の最小文字列。

</details>

<details><summary>pattern</summary>

#### pattern

正規表現でバリデーションできる。

</details>

<details><summary>properties</summary>

#### properties

`type: object`のとき、属性を指定する。

</details>

<details><summary>enum</summary>

#### enum

受け入れられる値の列挙型を指定する。

`nullable: true`のときは、明示的に

列挙の値を指定する必要がある。

```yaml
enum:
  - null
  ...
```

</details>

<details><summary>example</summary>

#### example

スキーマの例を示す。

##### 例

<details><summary>オブジェクトレベル</summary>

###### オブジェクトレベル

```yaml
components:
  schemas:
    User:    # Schema name
      type: object
      properties:
        id:
          type: integer
          format: int64
          example: 1          # Property example
        name:
          type: string
          example: New order  # Property example
```

</details>

<details><summary>プロパティレベル</summary>

###### プロパティレベル

```yaml
components:
  schemas:
    User:       # Schema name
      type: object
      properties:
        id:
          type: integer
        name:
          type: string
      example:   # Object-level example
        id: 1
        name: Jessica Smith
```

</details>

<details><summary>複数のアイテムを含む配列の例</summary>

###### 複数のアイテムを含む配列の例

```yaml
components:
  schemas:
    ArrayOfInt:
      type: array
      items:
        type: integer
        format: int64
      example: [1, 2, 3]
```

</details>

<details><summary>複数のオブジェクトを含む配列の例</summary>

###### 複数のオブジェクトを含む配列の例

```yaml
components:
  schemas:
    ArrayOfUsers:
      type: array
      items:
        type: object
        properties:
          id:
            type: integer
          name:
            type: string
      example:
        - id: 10
          name: Jessica Smith
        - id: 20
          name: Ron Stewart
```

</details>

</details>

<details><summary>required</summary>

#### required

必須の属性名を指定する。

真偽値ではなく、プロパティ名のリストを渡す。

</details>

<details><summary>nullable</summary>

#### nullable

`null`を指定できるかどうかの真偽値をいれる。

デフォルトは`false`

</details>

<details><summary>oneOf</summary>

#### oneOf

混合型を指定できる。

##### 例

<details><summary>代替のスキーマ</summary>

###### 代替のスキーマ

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

<details><summary>anyOf</summary>

指定したスキーマの混合型を作ります。

`oneOf`はスキーマのどれかひとつに当てはまりますが、

`anyOf`はスキーマの2以上に当てはまる場合があります。

</details>

<details><summary>allOf</summary>

#### allOf

スキーマを組み合わせたり、継承する。

##### 例

<details><summary>拡張</summary>

##### 拡張

```yaml
paths:
  /pets:
    patch:
      requestBody:
        content:
          application/json:
            schema:
              oneOf:
                - $ref: '#/components/schemas/Cat'
                - $ref: '#/components/schemas/Dog'
              discriminator:
                propertyName: pet_type
      responses:
        '200':
          description: Updated
components:
  schemas:
    Pet:
      type: object
      required:
        - pet_type
      properties:
        pet_type:
          type: string
      discriminator:
        propertyName: pet_type
    Dog:     # "Dog" is a value for the pet_type property (the discriminator value)
      allOf: # Combines the main `Pet` schema with `Dog`-specific properties 
        - $ref: '#/components/schemas/Pet'
        - type: object
          # all other properties specific to a `Dog`
          properties:
            bark:
              type: boolean
            breed:
              type: string
              enum: [Dingo, Husky, Retriever, Shepherd]
    Cat:     # "Cat" is a value for the pet_type property (the discriminator value)
      allOf: # Combines the main `Pet` schema with `Cat`-specific properties 
        - $ref: '#/components/schemas/Pet'
        - type: object
          # all other properties specific to a `Cat`
          properties:
            hunts:
              type: boolean
            age:
              type: integer
```

</details>

</details>

<details><summary>multipleOf</summary>

#### multipleOf

指定した倍数のバリデーションをかける。

</details>

<details><summary>readOnly</summary>

#### readOnly

読み取り専用にするかどうかの真偽値を指定する。

これはリクエストには含まれず、

レスポンスのみに含まれることを示します。

</details>

<details><summary>writeOnly</summary>

#### writeOnly

書き込み専用にするかどうかの真偽値を指定する。

これはレスポンスには含まれず、リクエストのみに

ふくまれることを示します。

</details>

<details><summary>minProperties</summary>

#### minProperties

プロパティの数の最小値。

`propeties`を指定しないで自由なオブジェクトを受け入れる時に

有効です。

</details>

<details><summary>maxProperties</summary>

#### maxProperties

プロパティの数の最大値

`properties`を指定しないで自由なオブジェクトを受け入れる時に

有効です。

</details>

<details><summary>additionalProperties</summary>

#### additionalProperties

`type: object`しか指定せず、そのオブジェクトを

辞書として受け取るとき、その辞書の属性を定義する。

</details>

<details><summary>discriminator</summary>

#### discriminator

`oneOf, anyOf`などで複数のオブジェクトを許可する時に、

それらのオブジェクトを区別するパラメータを指定する。

</details>

</details>

<details><summary>ExampleMap</summary>

## ExampleMap

```yaml
<example_name>:
  Example | Reference
```

### 属性

<details><summary>&lt;example_name&gt;</summary>

例の名前。

</details>

</details>

<details><summary>Example</summary>

## Example

スキーマの例を指定する。

```yaml
value: Any
summary: <example_summary>
description: <example_description>,
externalValue: <external_url>
```

### 属性

<details><summary>summary</summary>

#### summary

例の概要。

</details>

<details><summary>description</summary>

#### description

例の説明。

</details>

<details><summary>externalValue</summary>

#### externalValue

なんらかの理由で例を挿入できない場合は、

その例をしめす外部urlを指定できる。

</details>

</details>

<details><summary>Reference</summary>

## Reference

内部および外部で、モデルを参照する。

```yaml
$ref: '<reference>'  # required
```

### 属性

<details><summary>&dollar;ref</summary>

#### &dollar;ref

参照先。フォーマットは`json`参照に基づく。

`[<external_file_path>][#<internal_json_path>]`

また、特定の文字はエスケープする必要があります。

|記号|エスケープ文字|
|:---|:---|
|`~`|`~0`|
|`/`|`~1`|

##### 例

<details><summary>内部ファイルのコンポーネントのドキュメント</summary>

###### 内部ファイルのコンポーネントのドキュメント

```yaml
$ref: '#/components/schemas/Pet'
```

</details>

<details><summary>外部ファイルのドキュメント</summary>

###### 外部ファイルのドキュメント

```yaml
$ref: Pet.yaml
```

</details>

<details><summary>外部ファイルと相対ドキュメント</summary>

###### 外部ファイルと相対ドキュメント

```yaml
$ref: definitions.yaml#/Pet
```

</details>

</details>

</details>

<details><summary>Discriminator</summary>

`Schema`の`anyOf, oneOf`で許可された複数のオブジェクトを

区別するためのパラメータを定義する。

## Discriminator

```yaml
propertyName: <property_name>
mapping:
  DiscriminatorMapping
```

### 属性

<details><summary>propertyName</summary>

#### propertyName

区別に使用するパラメータ

</details>

### 例

<details><summary>マッピング</summary>

#### マッピング

```yaml
components:
  responses:
    sampleObjectResponse:
      content:
        application/json:
          schema:
            oneOf:
              - $ref: '#/components/schemas/Object1'
              - $ref: '#/components/schemas/Object2'
              - $ref: 'sysObject.json#/sysObject'
            discriminator:
              propertyName: objectType
              mapping:
                obj1: '#/components/schemas/Object1'
		obj2: '#/components/schemas/Object2'
                system: 'sysObject.json#/sysObject'
  …
  schemas:
    Object1:
      type: object
      required:
        - objectType
      properties:
        objectType:
          type: string
      …
    Object2:
      type: object
      required:
        - objectType
      properties:
        objectType:
          type: string
```
</details>

</details>

<details><summary>DiscriminatorMapping</summary>

`Discrminator`が区別するプロパティの値とオブジェクトを

マッピングする。

## DiscriminatorMapping

```yaml
<property_value>: <reference_path>
[...]
```

### 属性

<details><summary>&lt;property_value&gt;</summary>

#### &lt;property_value&gt;

区別するプロパティがとりうる値とスキーマを紐づける。

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
responses:
  ResponseMap
links:
  LinkMap
callbacks:
  CallbackMap
headers:
  HeaderMap
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

### 属性

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
name: <apikey_name>
in: <apikey_in>
scheme: <http_authorization_scheme>
bearerFormat: <bearere_format>
openIdConnectUrl: <open_id_connect_url>
flows:
  OAuthFlows
```

### 属性

<details><summary>type</summary>

#### type

セキュリティ構成の種類を指定します。

- apiKey
- http
- oauth2
- openIdConnect

</details>

<details><summary>description</summary>

#### description

セキュリティ構成の説明。マークダウンをサポートしています。

</details>

<details><summary>name</summary>

`type: apiKey`のときの`apikey`パラメータの

名前。

</details>

<details><summary>in</summary>

#### in

`type: apiKey`のときの必須パラメータで、

`apiKey`を含める場所を指定する。

- query
- header
- cookie

</details>

<details><summary>scheme</summary>

#### scheme

`type: http`のときは必須パラメータであり、

`Authorization`ヘッダのスキームを指定する。

- bearer
- basic

</details>

<details><summary>bearerFormat</summary>

#### bearerFormat

`Bearer`認証のトークンのフォーマット方法。

- JWT

</details>

<details><summary>openIdConnectUrl</summary>

#### openIdConnectUrl

`type: OpenIdConnect`のとき、`OAuth2`を構成する

情報もつ`url`を指定する。

通常は次のようなものを含んだ`json`を返す。

- OAuthエンドポイント
- スコープとクレームのリスト
- トークンの署名に使用される公開鍵
- etc...

</details>

### 備考

<details><summary>Basic Authentication</summary>

#### Basic Authentication

`Basic`認証は`Authorization`ヘッダに`base64`で

エンコードされた`<user>:<password>`を`Basic`という

キーワードの後につけて渡す認証です。

フォーマットは次のようになります。

`Autorization: Basic <base64_encoded_string>`

`<base64_encoded_string>`は`base64`でエンコードした

`<user>:<password>`です。

</details>

<details><summary>API Key Authentication</summary>

#### API Key Authentication

クライアントとサーバーだけが知るキーを

クエリもしくは、ヘッダ、もしくはクッキーに含ませる

認証。複数の認証方式と組み合わせることが推奨される。

</details>

<details><summary>Bearer Authentication</summary>

#### Bearer Authentication

`Bearer`トークンとう呼ばれるトークンを`Authorization`ヘッダに

含ませる`http`認証です。フォーマットは次のようになります。

`Authorization: Bearer <token>`

このトークンはログインのリクエストごとにサーバーで

生成されます。`Bearer`はもともと`OAuth2`の一部として`RFC6750`で

作成されました。時にはそれ単体で使用することがあります。

</details>

<details><summary>OAuth2.0</summary>

#### OAuth2.0

`OAuth2.0`はユーザーデータへの制限をかけるプロトコルです。

`GitHub, Google, FacebookAPI`はこれを利用しています。

`OAuth2.0`は`flows`と呼ばれる認証シナリオに依存しています。

詳細については`oauth.net`もしくは`RFC6749`にあります。

</details>

<details><summary>OpenID Connect(OIDC)</summary>

#### OpenID Connect(OIDC)

`OpenID Connect`は`OAuth2`プロトコル上で構築され、

`Google`や`Azure`の`ActiveDirectory`などの一部の

OAuth2.0プロバイダーによってサポートとされているIDレイヤーです。

これは、クライアントアプリケーションがユーザーを認証し、

ユーザー名や電子メールなどのユーザー情報を取得できるようにする

サインインフローを定義します。ユーザー識別情報は

`JWT`によってエンコードされます。`OpenID Connect`は

`OpenID Connect Discovery`と呼ばれる検出メカニズムを定義します。

`openIdConnectUrl`は`OAuth`の構成情報を返すエンドポイントです。

その構成情報の例を示します。

```json
{
  "issuer": "https://example.com/",
  "authorization_endpoint": "https://example.com/authorize",
  "token_endpoint": "https://example.com/token",
  "userinfo_endpoint": "https://example.com/userinfo",
  "jwks_uri": "https://example.com/.well-known/jwks.json",
  "scopes_supported": [
    "pets_read",
    "pets_write",
    "admin"
  ],
  "response_types_supported": [
    "code",
    "id_token",
    "token id_token"
  ],
  "token_endpoint_auth_methods_supported": [
    "client_secret_basic"
  ]
}
```

</details>

### 例

<details><summary>Basic Authentication</summary>

#### BasicAuthentication

```yaml
openapi: 3.0.0
paths:
  /something:
    get:
      security:
        - basicAuth: []
...
components:
  securitySchemes:
    basicAuth:     # <-- arbitrary name for the security scheme
      type: http
      scheme: basic
security:
  - basicAuth: []  # 
```

</details>

<details><summary>API Key and App ID</summary>

#### API Key and App ID

一部のAPIはアプリIDとAPIキーをペアにして使用します。

```yaml
components:
  securitySchemes:
    apiKey:
      type: apiKey
      in: header
      name: X-API-KEY
    appId:
      type: apiKey
      in: header
      name: X-APP-ID
security:
  - apiKey: []
    appId:  []   # <-- no leading dash (-)
```

</details>

<details><summary>Bearer Authentication</summary>

#### Bearer Authentication

```yaml
paths:
  /something:
    get:
      security:
        - bearerAuth: []

openapi: 3.0.0
...
# 1) Define the security scheme type (HTTP bearer)
components:
  securitySchemes:
    bearerAuth:            # arbitrary name for the security scheme
      type: http
      scheme: bearer
      bearerFormat: JWT    # optional, arbitrary value for documentation purposes
# 2) Apply the security globally to all operations
security:
  - bearerAuth: []       
```

</details>

<details><summary>OAuth2.0</summary>

#### OAuth2.0

```yaml
# Step 1 - define the security scheme
components:
  securitySchemes:
    oAuthSample:    # <---- arbitrary name
      type: oauth2
      description: This API uses OAuth 2 with the implicit grant flow. [More info](https://api.example.com/docs/auth)
      flows:
        implicit:   # <---- OAuth flow(authorizationCode, implicit, password or clientCredentials)
          authorizationUrl: https://api.example.com/oauth2/authorize
          scopes:
            read_pets: read your pets
            write_pets: modify pets in your account
# Step 2 - apply security globally...
security: 
  - oAuthSample: 
    - write_pets
    - read_pets
# ... or to individual operations
paths:
  /pets:
    patch:
      summary: Add a new pet
      security: 
        - oAuthSample: 
          - write_pets
          - read_pets
      ...
```

</details>

<details><summary>OpenID Connect</summary>

#### OpenID Connect

```yaml
openapi: 3.0.0
...

paths:
  /pets/{petId}:
    get:
      summary: Get a pet by ID
      security:
        - openId:
          - pets_read
      ...
    delete:
      summary: Delete a pet by ID
      security:
        - openId:
          - pets_write
      ...

# 1) Define the security scheme type and attributes
components:
  securitySchemes:
    openId:   # <--- Arbitrary name for the security scheme. Used to refer to it from elsewhere.
      type: openIdConnect
      openIdConnectUrl: https://example.com/.well-known/openid-configuration
# 2) Apply security globally to all operations
security:
  - openId:   # <--- Use the same name as specified in securitySchemes
      - pets_read
      - pets_write
      - admin
```

</details>

<details><summary>Unauthorized</summary>

#### Unauthorized

認証に失敗した時のエラーを定義する。

```yaml
paths:
  /something:
    get:
      ...
      responses:
        ...
        '401':
           $ref: '#/components/responses/UnauthorizedError'
    post:
      ...
      responses:
        ...
        '401':
          $ref: '#/components/responses/UnauthorizedError'
...
components:
  responses:
    UnauthorizedError:
      description: Authentication information is missing or invalid
      headers:
        WWW_Authenticate:
          schema:
            type: string
```

</details>

</details>

<details><summary>OAuthFlows</summary>

## OAuthFlows

セキュリティ構成に`oauth2`を選択したときに

定義しなければならない工程の定義。

```yaml
authorizationCode:
  OAuthFlow
implicit:
  OAuthFlow
clientCredentials:
  OAuthFlow
password:
  OAuthFlow
```

### 属性

<details><summary>authorizationCode</summary>

#### authorizationCode

もっとも一般的に使用されるフローで、主にサーバーや

モバイルWebアプリケーションに使用されます。これは

ユーザーが`Facebook`または`Google`アカウントを使用して

Webアプリケーションにサインアップする方法に似ています。

</details>

<details><summary>implicit</summary>

#### implicit

このフローでは、クライアントがアクセストークンを直接取得する

必要があります。主に、サーバーコンポーネントを含まないWeb、

デスクトップ、およびモバイルアプリケーションに適しています。

</details>

<details><summary>password</summary>

#### password

ユーザー名とパスワードを使用してログインする必要があります。

`API`プロバイダー自身のアプリケーションに適しています。

</details>

<details><summary>clientCredentials</summary>

#### clientCredentials

サーバー間の認証を目的としたフローです。

</details>

### 例

<details><summary>authorizationCode</summary>

#### authorizationCode

```yaml
components:
  securitySchemes:
    oAuth2AuthCode:
      type: oauth2
      description: For more information, see https://api.slack.com/docs/oauth
      flows: 
        authorizationCode:
          authorizationUrl: https://slack.com/oauth/authorize
          tokenUrl: https://slack.com/api/oauth.access
          scopes:
            users:read: Read user information
            users:write: Modify user information
            im:read: Read messages
            im:write: Write messages
            im:history: Access the message archive
            search:read: Search messages, files, and so on
            # etc.
```

</details>

<details><summary>implicit</summary>

#### implicit

`authorizationUrl`からアクセストークンを取得します。

```yaml
components:
  securitySchemes:
    oAuth2Implicit:
      type: oauth2
      description: For more information, see https://developers.getbase.com/docs/rest/articles/oauth2/requests
      flows: 
        implicit:
          authorizationUrl: https://api.getbase.com/oauth2/authorize
          scopes:
            read: Grant read-only access to all your data except for the account and user info
            write: Grant write-only access to all your data except for the account and user info
            profile: Grant read-only access to the account and user info only
```

</details>

<details><summary>password</summary>

#### password

```yaml
components:
  securitySchemes:
    oAuth2Password:
      type: oauth2
      description: See https://developers.getbase.com/docs/rest/articles/oauth2/requests
      flows: 
        password: 
          tokenUrl: https://api.getbase.com/oauth2/token
          scopes: 
            read: Grant read-only access to all your data except for the account and user info
            write: Grant write-only access to all your data except for the account and user info
            profile: Grant read-only access to the account and user info only
```

</details>

<details><summary>clientCredentials</summary>

#### clientCredentials

```yaml
components:
  securitySchemes:
    oAuth2ClientCredentials:
      type: oauth2
      description: See http://developers.gettyimages.com/api/docs/v3/oauth2.html
      flows: 
        clientCredentials: 
          tokenUrl: https://api.gettyimages.com/oauth2/token/
          scopes: {} # Getty Images does not use scopes
```

</details>

<details><summary>複数のフロー</summary>

#### 複数のフロー

```yaml
components:
  securitySchemes:
    oAuth2:
      type: oauth2
      description: For more information, see https://developers.getbase.com/docs/rest/articles/oauth2/requests
      flows: 
        implicit:
          authorizationUrl: https://api.getbase.com/oauth2/authorize
          scopes:
            read: Grant read-only access to all your data except for the account and user info
            write: Grant write-only access to all your data except for the account and user info
            profile: Grant read-only access to the account and user info only
        password: 
          tokenUrl: https://api.getbase.com/oauth2/token
          scopes: 
            read: Grant read-only access to all your data except for the account and user info
            write: Grant write-only access to all your data except for the account and user info
            profile: Grant read-only access to the account and user info only
```

</details>

</details>

<details><summary>OAuthFlow</summary>

## OAuthFlow

```yaml
authorizationUrl: <authorization_url>  #required
tokenUrl: <token_url>
refreshUrl: <refresh_url>
scopes:
  ScopeMap
```

### 属性

<details><summary>authorizationUrl</summary>

#### authorizationUrl

ログインページなどのユーザー情報を入力させるページの相対url

</details>

<details><summary>tokenUrl</summary>

#### tokenUrl

トークンを取得するURLの相対url

</details>

<details><summary>refreshUrl</summary>

#### refreshUrl

更新用トークンを取得する。相対url

</details>

<details><summary>scopes</summary>

#### scopes

リソースにアクセスするための権限のリストです。

通常はトークンに付与されます。

</details>

### 備考

<details><summary>フローと属性の対応表</summary>

#### フロート属性の対応表

|属性|authorizationCode|implicit|password|clientCredentials|
|:---|:---|:---|:---|:---|
|authorizationUrl|+|+|-|-|
|tokenUrl|+|-|+|+|
|refreshUrl|+|+|+|+|
|scopes|+|+|+|+|

</details>

</details>

<details><summary>ScopeMap</summary>

## ScopeMap

```yaml
<scope_name>: <scope_description>
```

### 属性

<details><summary>&lt;scope_name&gt;</summary>

#### &lt;scope_name&gt;

スコープ名とその説明を記述する。

</details>

</details>

<details><summary>SecurityRequirement</summary>

## SecurityRequirement

```yaml
<scheme_name>:
  - <scope>
```

### 属性

<details><summary>&lt;scheme_name&gt;</summary>

#### &lt;scheme_name&gt;

定義したセキュリティ構成の名前。

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

### 属性

<details><summary>url</summary>

#### url

拡張ドキュメントの相対パス。

</details>

<details><summary>description</summary>

#### description

ドキュメントの説明を指定する。

</details>

</details>
