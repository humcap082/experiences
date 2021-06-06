# deepStrictEqual&lt;T&gt;()

再帰的に同値のアサーションチェックを行う。異なったときにエラーを表示。

```typescript
function deepStrictEqual<T>(
    actual: any,
    expected: T,
    message?: string | Error
): asserts actual is T;
```

## 引数

<details><summary>actual</summary><section>

### actual

チェックする値

#### 型

- any

</section></details>

<details><summary>expected</summary><section>

### expected

予測される値

#### 型

- T

</section></details>

## 例

<details><summary>error diff</summary><section>

### error diff

```javascript
const assert = require('assert');

assert = deepStrictEqual([[[1, 2, 3], 4, 5]], [[[1, 2, 3], '4', 5]]);
```

</section></details>

