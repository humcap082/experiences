# Depends()

関数の仮引数にわたすことで、指定した別の関数を実行し、その戻り値を引数に渡すことができる関数。

また、クラスを指定することで引数をまとめることもできる。


```python
def Depends(  # noqa: N802
    dependency: Callable = None, *, use_cache: bool = True
) -> Any:
```

## 引数

<details><summary>dependency</summary>

### dependency

引数を受け取り、引数を返す関数やクラスなどを指定する

```python
dependency: Callable = None
```

</details>

<details><summary>use_cache</summary>

### use_cache

引数を受け取り、引数を返す関数やクラスなどを指定する

```python
use_cache: bool = True
```

</details>

### 例

<details><summary>関数を渡す</summary>

```python
from typing import Optional
from fastapi import Depends, FastAPI
app = FastAPI()

async def common_parameters(q: Optional[str] = None, skip: int = 0, limit: int = 100):
    return {'q': q, 'skip': skip, 'limit': limit}

@app.get('/items/')
async def read_items(commons: dict = Depends(common_parameters)):
    return commons

@app.get('/users/')
async def read_users(commons: dict = Depends(common_parameters)):
    return commons
```

</details>

<details><summary>クラスを渡す</summary>

クラスでパラメータをまとめることもできます。

`dependency`に渡されるクラスが宣言されている型(クラス)と同じであれば、引数を省略することができます。

```python
from typing import Optional
from fastapi import Depends, FastAPI
app = FastAPI()

fake_items_db = [{'item_name': 'Foo'}, {'item_name': 'Bar'}, {'item_name': 'Baz'}]

class CommonQueryParams:
    def __init__(self, q: Optional[str] = None, skip: int = 0, limit: int = 100):
        self.q = q
        self.skip = skip
        self.limit = limit

@app.get('/items/')
async def read_items(commons: CommonQueryParams = Depends()):
    response = {}
    if commons.q:
        response.update({'q': commons.q})
    items = fake_items_db[commons.skip:commons.skip + commons.limit]
    response.update({'items': items})
    return response
```

</details>

<details><summary>インスタンスを渡す。</summary>

`__call__`を定義することでインスタンス関数として渡すことができる。

```python
from fastapi import Depends, FastAPI

app = FastAPI()


class FixedContentQueryChecker:
    def __init__(self, fixed_content: str):
        self.fixed_content = fixed_content

    def __call__(self, q: str = ""):
        if q:
            return self.fixed_content in q
        return False


checker = FixedContentQueryChecker("bar")


@app.get("/query-checker/")
async def read_query_check(fixed_content_included: bool = Depends(checker)):
    return {"fixed_content_in_query": fixed_content_included}
```

</details>

<details><summary>ネストする。</summary>

最終的にルーティングされた関数に収束しなければならない。

```python
def get_storage_client() -> storage.Client:
    credentials = service_account.Credentials.from_service_account_info(
        json.loads(settings.cloud_storage_credentials_json),
    )
    storage_client = storage.Client(
        project=credentials.project_id,
        credentials=credentials,
    )
    return storage_client


def get_storage_bucket(
    storage_client: storage.Client = Depends(get_storage_client)
) -> storage.Bucket:
    storage_bucket = storage_client.get_bucket(settings.cloud_storage_bucket)
    return storage_bucket


@app.delete('/images/path:path')
async def(
    storage_bucket: storage.Bucket = Depends(get_storage_bucket),
    path: str = Path(...)
):
    blob = storage_bucket.get_blob(path)
    blob.delete()

```

</details>
