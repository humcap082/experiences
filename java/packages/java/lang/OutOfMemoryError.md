# OutOfMemoryError

メモリ不足のために`JVM`がオブジェクトを割り当てらず、

ガベージコレクションによっても使用可能なメモリをこれ以上

確保できない場合にスローされる例外クラス。

```java
public class OutOfMemoryError extends VirtualMachineError {
    public OutOfMemoryError();

    public OutOfMemoryError(String s);
```
