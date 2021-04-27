# StackOverflowError

アプリケーションでの再帰の回数が多すぎたときにスローされる例外クラス。

```java
class StackOverflowError extends VirtualMachineError {
    public StackOverflowError();

    public StackOverflowError(String s);
```
