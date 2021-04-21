# APIRouter

`FastAPI`と持つメソッドはほとんど同じで、`FastAPI`の`include_router()`によって統合できる。

```python
class APIRouter(routing.Router):
    def __init__(
        self,
        routes: List[routing.BaseRoute] = None,
        redirect_slashes: bool = True,
        default: ASGIApp = None,
        dependency_overrides_provider: Any = None,
        route_class: Type[APIRoute] = APIRoute,
        default_response_class: Type[Response] = None,
        on_startup: Sequence[Callable] = None,
        on_shutdown: Sequence[Callable] = None,
    ) -> None:
```

<details><summary>get()</summary>

`GET`リクエストを処理する関数をルーティングするデコレータ

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

</details>

<details><summary>post()</summary>

`POST`リクエストを処理する関数をルーティングするデコレータ

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

</details>

<details><summary>put()</summary>

`PUT`リクエストを処理する関数をルーティングするデコレータ

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

</details>

<details><summary>patch()</summary>

`PATCH`リクエストを処理する関数をルーティングするデコレータ

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

</details>

<details><summary>delete()</summary>

`DELETE`リクエストを処理する関数をルーティングするデコレータ

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

</details>
