# FastAPI

アプリケーションのクラス。

```python
class FastAPI(Starlette):
    def __init__(
        self,
        *,
        debug: bool = False,
        routes: List[BaseRoute] = None,
        title: str = "FastAPI",
        description: str = "",
        version: str = "0.1.0",
        openapi_url: Optional[str] = "/openapi.json",
        openapi_tags: Optional[List[Dict[str, Any]]] = None,
        servers: Optional[List[Dict[str, Union[str, Any]]]] = None,
        default_response_class: Type[Response] = JSONResponse,
        docs_url: Optional[str] = "/docs",
        redoc_url: Optional[str] = "/redoc",
        swagger_ui_oauth2_redirect_url: Optional[str] = "/docs/oauth2-redirect",
        swagger_ui_init_oauth: Optional[dict] = None,
        middleware: Sequence[Middleware] = None,
        exception_handlers: Dict[Union[int, Type[Exception]], Callable] = None,
        on_startup: Sequence[Callable] = None,
        on_shutdown: Sequence[Callable] = None,
        openapi_prefix: str = "",
        root_path: str = "",
        **extra: Dict[str, Any],
    ) -> None:
```

|コンストラクタ引数|型|デファルト|説明|
|:---|:---|:---|:---|
|title|str|'FastAPI'|アプリケーションのタイトル|
|description|str|''|アプリケーションの説明|
|version|str|'0.1.0'|アプリケーションのバージョン|
|openapi_url|Optional[str]|'/openapi.json'|openapiのスキーマを保持するパス。|
|openapi_tags|Optional[List[Dict[str, Any]]]|None|パス操作関数をグループ化するタグに情報をつける|
|docs_url|Optional[str]|'/docs'|`Swagger UI`のパス|
|redoc_url|Optional[str]|'/redoc'|`ReDoc`のパス|
|on_startup|Sequence[Callable]|None|サーバーを立ち上げたときに実行する関数の配列|
|on_shutdown|Sequence[Callable]|None|サーバーを閉じたときに実行する関数の配列|

|属性|型|説明|
|:---|:---|:---|
|dependency_overrides|Dict[Callable, Callable]|`Depend`された関数の辞書|
|state|State|カスタムな値を保持する。|

## メソッド

<details><summary>get()</summary>

getメソッドを処理するルーティングをデコレートするメソッド。

```python
def get(
    self,
    path: str,
    *,
    response_model: Type[Any] = None,
    status_code: int = 200,
    tags: List[str] = None,
    dependencies: Sequence[Depends] = None,
    summary: str = None,
    description: str = None,
    response_description: str = "Successful Response",
    responses: Dict[Union[int, str], Dict[str, Any]] = None,
    deprecated: bool = None,
    operation_id: str = None,
    response_model_include: Union[SetIntStr, DictIntStrAny] = None,
    response_model_exclude: Union[SetIntStr, DictIntStrAny] = set(),
    response_model_by_alias: bool = True,
    response_model_skip_defaults: bool = None,
    response_model_exclude_unset: bool = False,
    response_model_exclude_defaults: bool = False,
    response_model_exclude_none: bool = False,
    include_in_schema: bool = True,
    response_class: Type[Response] = None,
    name: str = None,
    callbacks: List[routing.APIRoute] = None,
) -> Callable:
```

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|path|str|なし|唯一の位置引数、ルーティングするパスをいれる|
|response_model|Type[Any]|None|レスポンスボディの型を定義する|
|status_code|int|200|返されるステータスコード|
|tags|List[str]|None|タグをつけられる。通常は1個だけつける|
|dependencies|Sequence[Depends]|None|複数の依存関係を指定できる。|
|summary|str|None|要約|
|description|str|None|説明文|
|response_description|str|'Successful Response'|レスポンスモデルの説明文|
|responses|Dict[Union[int, str], Dit[str, Any]]|None|デフォルトのレスポンス|
|deprecated|bool|None|非推奨の関数かどうか|
|response_model_include|Union[SetIntStr, DictIntStrAny]|None|response_modelのなかで出力する属性を指定する|
|response_model_exclude|Union[SetIntStr, DictIntStrAny]|set()|response_modelのなかで無視する属性を指定する|
|response_model_exclude_unset|bool|False|response_modelのなかでセット指定されなかったデフォルトの値の出力を無視するかどうかするかどうか|
|response_model_exclude_defaults|bool|False|response_modelのなかでデフォルトのままの値の出力を無視するかどうか|
|response_model_exclude_none|bool|False|response_modelのなかでNoneの出力を無視するかどうか|

</details>

<details><summary>post()</summary>

POSTメソッドを処理するエンドポイントをルーティングするデコレーターメソッド。

```python
def post(
        self,
        path: str,
        *,
        response_model: Type[Any] = None,
        status_code: int = 200,
        tags: List[str] = None,
        dependencies: Sequence[Depends] = None,
        summary: str = None,
        description: str = None,
        response_description: str = "Successful Response",
        responses: Dict[Union[int, str], Dict[str, Any]] = None,
        deprecated: bool = None,
        operation_id: str = None,
        response_model_include: Union[SetIntStr, DictIntStrAny] = None,
        response_model_exclude: Union[SetIntStr, DictIntStrAny] = set(),
        response_model_by_alias: bool = True,
        response_model_skip_defaults: bool = None,
        response_model_exclude_unset: bool = False,
        response_model_exclude_defaults: bool = False,
        response_model_exclude_none: bool = False,
        include_in_schema: bool = True,
        response_class: Type[Response] = None,
        name: str = None,
        callbacks: List[routing.APIRoute] = None,
    ) -> Callable:
```

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|path|str|なし|唯一の位置引数、ルーティングするパスをいれる|
|response_model|Type[Any]|None|レスポンスボディの型を定義する|
|status_code|int|200|返されるステータスコード|
|tags|List[str]|None|タグをつけられる。通常は1個だけつける|
|dependencies|Sequence[Depends]|None|複数の依存関係を指定できる。|
|summary|str|None|要約|
|description|str|None|説明文|
|response_description|str|'Successful Response'|レスポンスモデルの説明文|
|responses|Dict[Union[int, str], Dit[str, Any]]|None|デフォルトのレスポンス|
|deprecated|bool|None|非推奨の関数かどうか|
|response_model_include|Union[SetIntStr, DictIntStrAny]|None|response_modelのなかで出力する属性を指定する|
|response_model_exclude|Union[SetIntStr, DictIntStrAny]|set()|response_modelのなかで無視する属性を指定する|
|response_model_exclude_unset|bool|False|response_modelのなかでセット指定されなかったデフォルトの値の出力を無視するかどうかするかどうか|
|response_model_exclude_defaults|bool|False|response_modelのなかでデフォルトのままの値の出力を無視するかどうか|
|response_model_exclude_none|bool|False|response_modelのなかでNoneの出力を無視するかどうか|

</details>
<details><summary>put()</summary>

PUTメソッドを処理するエンドポイントをルーティングするデコレーターメソッド。

```python
def put(
        self,
        path: str,
        *,
        response_model: Type[Any] = None,
        status_code: int = 200,
        tags: List[str] = None,
        dependencies: Sequence[Depends] = None,
        summary: str = None,
        description: str = None,
        response_description: str = "Successful Response",
        responses: Dict[Union[int, str], Dict[str, Any]] = None,
        deprecated: bool = None,
        operation_id: str = None,
        response_model_include: Union[SetIntStr, DictIntStrAny] = None,
        response_model_exclude: Union[SetIntStr, DictIntStrAny] = set(),
        response_model_by_alias: bool = True,
        response_model_skip_defaults: bool = None,
        response_model_exclude_unset: bool = False,
        response_model_exclude_defaults: bool = False,
        response_model_exclude_none: bool = False,
        include_in_schema: bool = True,
        response_class: Type[Response] = None,
        name: str = None,
        callbacks: List[routing.APIRoute] = None,
    ) -> Callable:
```

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|path|str|なし|唯一の位置引数、ルーティングするパスをいれる|
|response_model|Type[Any]|None|レスポンスボディの型を定義する|
|status_code|int|200|返されるステータスコード|
|tags|List[str]|None|タグをつけられる。通常は1個だけつける|
|dependencies|Sequence[Depends]|None|複数の依存関係を指定できる。|
|summary|str|None|要約|
|description|str|None|説明文|
|response_description|str|'Successful Response'|レスポンスモデルの説明文|
|responses|Dict[Union[int, str], Dit[str, Any]]|None|デフォルトのレスポンス|
|deprecated|bool|None|非推奨の関数かどうか|
|response_model_include|Union[SetIntStr, DictIntStrAny]|None|response_modelのなかで出力する属性を指定する|
|response_model_exclude|Union[SetIntStr, DictIntStrAny]|set()|response_modelのなかで無視する属性を指定する|
|response_model_exclude_unset|bool|False|response_modelのなかでセット指定されなかったデフォルトの値の出力を無視するかどうかするかどうか|
|response_model_exclude_defaults|bool|False|response_modelのなかでデフォルトのままの値の出力を無視するかどうか|
|response_model_exclude_none|bool|False|response_modelのなかでNoneの出力を無視するかどうか|

</details>
<details><summary>patch()</summary>

PATCHメソッドを処理するエンドポイントをルーティングするデコレーターメソッド。

```python
def patch(
        self,
        path: str,
        *,
        response_model: Type[Any] = None,
        status_code: int = 200,
        tags: List[str] = None,
        dependencies: Sequence[Depends] = None,
        summary: str = None,
        description: str = None,
        response_description: str = "Successful Response",
        responses: Dict[Union[int, str], Dict[str, Any]] = None,
        deprecated: bool = None,
        operation_id: str = None,
        response_model_include: Union[SetIntStr, DictIntStrAny] = None,
        response_model_exclude: Union[SetIntStr, DictIntStrAny] = set(),
        response_model_by_alias: bool = True,
        response_model_skip_defaults: bool = None,
        response_model_exclude_unset: bool = False,
        response_model_exclude_defaults: bool = False,
        response_model_exclude_none: bool = False,
        include_in_schema: bool = True,
        response_class: Type[Response] = None,
        name: str = None,
        callbacks: List[routing.APIRoute] = None,
    ) -> Callable:
```

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|path|str|なし|唯一の位置引数、ルーティングするパスをいれる|
|response_model|Type[Any]|None|レスポンスボディの型を定義する|
|status_code|int|200|返されるステータスコード|
|tags|List[str]|None|タグをつけられる。通常は1個だけつける|
|dependencies|Sequence[Depends]|None|複数の依存関係を指定できる。|
|summary|str|None|要約|
|description|str|None|説明文|
|response_description|str|'Successful Response'|レスポンスモデルの説明文|
|responses|Dict[Union[int, str], Dit[str, Any]]|None|デフォルトのレスポンス|
|deprecated|bool|None|非推奨の関数かどうか|
|response_model_include|Union[SetIntStr, DictIntStrAny]|None|response_modelのなかで出力する属性を指定する|
|response_model_exclude|Union[SetIntStr, DictIntStrAny]|set()|response_modelのなかで無視する属性を指定する|
|response_model_exclude_unset|bool|False|response_modelのなかでセット指定されなかったデフォルトの値の出力を無視するかどうかするかどうか|
|response_model_exclude_defaults|bool|False|response_modelのなかでデフォルトのままの値の出力を無視するかどうか|
|response_model_exclude_none|bool|False|response_modelのなかでNoneの出力を無視するかどうか|

</details>
<details><summary>delete()</summary>

DELETEメソッドを処理するエンドポイントをルーティングするデコレーターメソッド。

```python
def delete(
        self,
        path: str,
        *,
        response_model: Type[Any] = None,
        status_code: int = 200,
        tags: List[str] = None,
        dependencies: Sequence[Depends] = None,
        summary: str = None,
        description: str = None,
        response_description: str = "Successful Response",
        responses: Dict[Union[int, str], Dict[str, Any]] = None,
        deprecated: bool = None,
        operation_id: str = None,
        response_model_include: Union[SetIntStr, DictIntStrAny] = None,
        response_model_exclude: Union[SetIntStr, DictIntStrAny] = set(),
        response_model_by_alias: bool = True,
        response_model_skip_defaults: bool = None,
        response_model_exclude_unset: bool = False,
        response_model_exclude_defaults: bool = False,
        response_model_exclude_none: bool = False,
        include_in_schema: bool = True,
        response_class: Type[Response] = None,
        name: str = None,
        callbacks: List[routing.APIRoute] = None,
    ) -> Callable:
```

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|path|str|なし|唯一の位置引数、ルーティングするパスをいれる|
|response_model|Type[Any]|None|レスポンスボディの型を定義する|
|status_code|int|200|返されるステータスコード|
|tags|List[str]|None|タグをつけられる。通常は1個だけつける|
|dependencies|Sequence[Depends]|None|複数の依存関係を指定できる。|
|summary|str|None|要約|
|description|str|None|説明文|
|response_description|str|'Successful Response'|レスポンスモデルの説明文|
|responses|Dict[Union[int, str], Dit[str, Any]]|None|デフォルトのレスポンス|
|deprecated|bool|None|非推奨の関数かどうか|
|response_model_include|Union[SetIntStr, DictIntStrAny]|None|response_modelのなかで出力する属性を指定する|
|response_model_exclude|Union[SetIntStr, DictIntStrAny]|set()|response_modelのなかで無視する属性を指定する|
|response_model_exclude_unset|bool|False|response_modelのなかでセット指定されなかったデフォルトの値の出力を無視するかどうかするかどうか|
|response_model_exclude_defaults|bool|False|response_modelのなかでデフォルトのままの値の出力を無視するかどうか|
|response_model_exclude_none|bool|False|response_modelのなかでNoneの出力を無視するかどうか|

</details>
<details><summary>exception_handler()</summary>

エラーハンドリングするメソッド。新しい例外の作成、既存の例外を上書きする。

```python
def exception_handler(
        self, exc_class_or_status_code: typing.Union[int, typing.Type[Exception]]
    ) -> typing.Callable:
```

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|exc_class_or_status_code|Union[int, Type[Excption]]|なし|ハンドラにするエラークラス、もしくはステータスコード|

</details>
<details><summary>middleware()</summary>

リクエストとエンドポイント、エンドポイントとレスポンスの間の処理を行う

ミドルウェアを実装する。

```python
def middleware(self, middleware_type: str) -> typing.callable:
```

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|middleware_type|str|なし|ミドルウェアのタイプを指定する|

</details>
<details><summary>add_middleware()</summary>

定義されているミドルウェアを追加する。

```python
def add_middleware(self, middleware_class: type, **options: typing.Any) -> None:
```

|引数|型|デフォルト|接見目|
|:---|:---|:---|:---|
|middleware_class|type|なし|設定するミドルウェア|
|**options|Any|なし|ミドルウェアに渡すパラメータ|

</details>
<details><summary>include_router()</summary>

APIRouterで定義したエンドポイントを結合する。

```python
def include_router(
        self,
        router: routing.APIRouter,
        *,
        prefix: str = "",
        tags: List[str] = None,
        dependencies: Sequence[Depends] = None,
        responses: Dict[Union[int, str], Dict[str, Any]] = None,
        default_response_class: Optional[Type[Response]] = None,
    ) -> None:
```

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|router|APIRouter|なし|追加するルータ|
|prefix|str|''|ルータが定義したすべてのパス操作関数のパスの手前に追加するパス|
|tags|List[str]|None|ルータが定義したすべてのパス操作関数に追加するタグ|
|dependendies|Sequence[Depends]|None|ルータが定義したすべてのパス操作関数のdependeciesに追加する依存関係|
|responses|Dict[Union[int, str], Dict[str, Any]]|None|ルータが定義したすべてのresponsesに追加するレスポンス|

</details>
<details><summary>mount()</summary>

指定のパスにアプリケーションなどをマウントするメソッド

```python
def mount(self, path: str, app: ASGIApp, name: str = None) -> None:
```

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|path|str|なし|アプリケーションをマウントするパス|
|app|ASGIApp|なし|マウントするアプリケーションのインスタンス|
|name|str|None|メインのアプリケーションからの名前|

</details>
<details><summary>on_event()</summary>

特定のイベント時に処理する関数を定義できる。

```python
def on_event(self, event_type: str) -> typing.Callable:
```

#### パラメータ

|引数|型|デフォルト|説明|
|:---|:---|:---|:---|
|evnet_type|str|required|リッスンするイベント|

</details>

## 備考

<details><summary>openapi_url</summary>

`None`を設定することでスキーマが無効になり、ドキュメンテーションインターフェースも無効になります。

</details>

<details><summary>openapi_tags</summary>

タグの情報が入った辞書を要素として持つリストを渡す。

それぞれの辞書の属性は次のようになる。

- `name`: タグの名前
- `description`: タグの説明、マークダウンを使用できます。
- `externalDocs`: 外部のドキュメントについての情報の辞書
    - `description`: 外部のドキュメントの説明、マークダウンを使用できます。
    - `url`: 外部のドキュメントのurl、externalDocsの必須のパラメータ

</details>

<details><summary>docs_url</summary>

`None`で無効。

</details>

<details><summary>redoc_url</summary>

`None`で無効

</details>

<details><summary>dependency_overrides</summary>

`Depend`に渡される関数を上書きできる。

</details>

<details><summary>state</summary>

appインスタンスに値を紐づけることができ、シングルトンなインスタンスを保持できる。

`Request`の`app`から取り出しができる。

</details>

<details><summary>description - get(), post(), put(), patch(), delete()</summary>

代わりにdocstringを利用できる。

マークダウン方式で書くことができる。

</details>

<details><summary>event_type - on_event()</summary>

|event_type|説明|
|:---|:---|
|startup|アプリケーション起動|
|shutdown|アプリケーション終了|

</details>

## 例

<details><summary>dependency_overrides</summary>

```python
def override_get_settings():
    return TestSettings()


app.dependency_overrides[get_settings] = override_get_settings
```

</details>

<details><summary>state</summary>

```python
@app.on_event('startup')
async def startup():
    app.state.pool = await asyncpg.create_pool(settings.database_url)

```

</details>
<details><summary>列挙パラメータ</summary>

```python
from enum import Enum
from fastapi import FastAPI

class ModelName(str, Enum):
    alexnet = 'alexnet'
    resnet = 'resnet'
    lenet = 'lenet'

app = FastAPI()

@app.get('/model/{model_name}')
async def get_model(model_name: ModelName):
    return {'model_name': model_name}
```

</details>

<details><summary>パスを含むパスパラメータ</summary>

```python
from fastapi import FastAPI
app = FastAPI()

@app.get('/files/{file_path:path}')
async def read_file(file_path: str):
    return {'file_path': file_path}
```

</details>

<details><summary>description - get(), post(), put(), patch(), delete()</summary>

代わりにdocstringを利用できる。

マークダウン方式で書くことができる。

```python
from typing import Optional, Set
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()


class Item(BaseModel):
    name: str
    description: Optional[str] = None
    price: float
    tax: Optional[float] = None
    tags: Set[str] = []

@app.post(
    '/items/',
    response_model=Item,
    summary='Create an Item',
)
async def create_item(item: Item):
    """Create an item with all the information.
    - **name**: each item must have a name
    - **description**: a long description
    - **price**: required
    - **tax**: if the item doesn't have tax, you can omit this
    - **tags**: a set of unique tag strings for this item
    """
    return item
```

</details>

<details><summary>response_model_include, response_model_exclude - get(), post(), put(), patch(), delete()</summary>

```python
from typing import Optional
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class Item(BaseModel):
    name: str
    description: Optional[str] = None
    price: float
    tax: float = 10.5

items = {
    'foo': {'name': 'Foo', 'price': 50.2},
    'bar': {'name': 'Bar', 'description': 'The Bar fighters', 'price': 62, 'tax': 20.2},
    'baz': {
        'name': 'Baz',
        'description': 'There goes my baz',
        'price': 50.2,
        'tax': 10.5,
    },
}

@app.get(
    '/items/{item_id}/name',
    response_model=Item,
    response_model_include={'name', 'description'},
)
async def read_item_name(item_id: str):
    return items[item_id]

@app.get('/items/{item_id}/public', response_model=Item, response_model_exclude={'tax'})
async def read_item_public_data(item_id: str):
    return items[item_id]
```

</details>

<details><summary>response_model_exclude_unset - get(), post(), put(), patch(), delete()</summary>

```python
from typing import List, Optional
from fastapi import FastAPI
from pydantic import BaseModel
app = FastAPI()

class Item(BaseModel):
    name: str
    description: Optional[str] = None
    price: float
    tax: float = 10.5
    tags: List[str] = []

items = {
    'foo': {'name': 'Foo', 'price': 50.2},
    'bar': {'name': 'Bar', 'description': 'The bartenders', 'price': 62, 'tax': 20.2},
    'baz': {'name': 'Baz', 'description': None, 'price': 50.2, 'tax': 10.5, 'tags': []}
}

@app.get('/items/{item_id}', response_model=Item, response_model_exclude_unset=True)
async def read_item(item_id: str):
    return items[item_id]
```

この場合、`http://127.0.0.1:8000/items/foo`を叩くと

次のように、指定してないデフォルトの値はかえってきません。

```python
{
  "name": "Foo",
  "price": 50.2
}
```

</details>

<details><summary>新規エラーを作成</summary>

```python
from fastapi import FastAPI, Request
from fastapi.responses import JSONResponse

class UnicornException(Exception):
    def __init__(self, name: str):
        self.name = name

app = FastAPI()

@app.exception_handler(UnicornException)
async def unicorn_exception_handler(request: Request, exc: UnicornException):
    return JSONResponse(
        status_code=418,
        content={'message': f'Oops! {exc.name} did something. There goes a rainbow....'}
    )

@app.get('/unicorns/{name}')
async def read_unicorn(name: str):
    if name == 'yolo':
        raise UnicornException(name=name)
    return {'unicorn_name': name}
```

</details>

<details><summary>既存のエラーを上書き</summary>

```python
from fastapi import FastAPI, HTTPException
from fastapi.exceptions import RequestValidationError
from fastapi.responses import PlainTextResponse
from starlette.exceptions import HTTPException as StarletteHTTPException
app = FastAPI()

@app.exception_handler(StarletteHTTPException)
async def http_exception_handler(request, exc):
    return PlainTextResponse(str(exc.detail), status_code=exc.status_code)

@app.exception_handler(RequestValidationError)
async def validation_exception_handler(request, exc):
    return PlainTextResponse(str(exc), status_code=400)

@app.get('/items/{item_id}')
async def read_item(item_id: int):
    if item_id == 3:
        raise HTTPException(status_code=418, detail='Nope! I don\'t like 3.')
    return {'item_id': item_id}
```

</details>

<details><summary>middleware()</summary>

```python
import time
from fastapi import FastAPI, Request
app = FastAPI()

@app.middleware('http')
async def add_process_time_header(request: Request, call_next):
    start_time = time.time()
    response = await call_next(request)
    process_time = time.time() - start_time
    response.headers['X-Process-Time'] = str(process_time)
    return response
```

ミドルウェア関数は以下を受け取ります。

- `request`
- `call_next`: `request`をパラメータとして受け取る関数
    - この関数は`request`を対応するパス操作関数に渡します
    - そして、パス操作関数が作成したレスポンスを返します。
    - そしてさらにレスポンスを修正して返すことができます。

</details>

<details><summary>include_router()</summary>

- app
    - \_\_init\_\_.py
    - main.py
    - routers
        - \_\_init\_\_.py
        - items.py
        - users.py

`users.py`

```python
from fastapi import APIRouter
router = APIRouter()

@router.get('/users/', tags=['users'])
async def read_users():
    return [{'username': 'Foo'}, {'username': 'Bar'}]

@router.get('/users/me', tags=['users'])
async def read_user_me():
    return {'username': 'fakecurrentuser'}

@router.get('/users/{username}', tags=['users'])
async def read_user(username: str):
    return {'username': username}

```

`items.py`

```python
from fastapi import APIRouter, HTTPException
router = APIRouter()

@router.get('/')
async def read_items():
    return [{'name': 'Item Foo'}, {'name': 'item Bar'}]

@router.get('/{item_id}')
async def read_item(item_id: str):
    return {'name': 'Fake Specific Item', 'item_id': item_id}

@router.put(
    '/{item_id}',
    tags=['custom'],
    responses={403: {'description': 'Operation forbidden'}},
)
async def update_item(item_id: str):
    if item_id != 'foo':
        raise HTTPException(status_code=403, detail='You can only update the item: foo')
    return {'item_id': item_id, 'name': 'the Fighters'}

```

`main.py`

```python
from fastapi import Depends, FastAPI, Header, HTTPException
from .routers import items, users
app = FastAPI()

async def get_token_header(x_token: str = Header(...)):
    if x_token != 'fake-super-secret-token':
        raise HTTPException(status_code=400, detail='X-Token header invalid')

app.include_router(users.router)
app.include_router(
    items.router,
    prefix='/items',
    tags=['items'],
    dependencies=[Depends(get_token_header)],
    responses={404: {'description': 'Not found'}}
)

```

</details>


