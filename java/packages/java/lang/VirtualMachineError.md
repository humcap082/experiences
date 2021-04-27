# VirtualMachineError

`JVM`が壊れているか、動作を継続するのに必要なリソースが足りなくなった

ことを示すためにスローされるエラークラス。

```java
public abstract class VirtualMachineError extends Error {
    public VirtualMachineError();

    public VirtualMachineError(String message);

    public VirtualMachineError(String message, Throwable cause);

    public VirtualMachineError(Throwable cause);
```
