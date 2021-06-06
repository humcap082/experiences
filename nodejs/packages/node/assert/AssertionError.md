# AssertionError

アサーションエラークラス。

```typescript
class AssertionError extends Error {
    actual: any;
    expected: any;
    operator: string;
    generatedMessage: boolean;
    code: 'ERR_ASSERTION';

    constructor(options?: {
        /** If provided, the error message is set to this value. */
        message?: string;
        /** The `actual` property on the error instance. */
        actual?: any;
        /** The `expected` property on the error instance. */
        expected?: any;
        /** The `operator` property on the error instance. */
        operator?: string;
        /** If provided, the generated stack trace omits frames before this function. */
        // tslint:disable-next-line:ban-types
        stackStartFn?: Function;
    });
}
```

## 継承

- [Error](../Error.md)
