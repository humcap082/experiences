# ArrayIndexOutOfBoundsException

不正なインデックスを使って配列がアクセスされたことを示す

ためにスローされます。たとえば、インデックスが負、または配列のサイズ以上のとき

スローされます。

```java
public class ArrayIndexOutOfBoundsException extends IndexOutOfBoundsException {
    public ArrayIndexOutOfBoundsException();

    public ArrayIndexOutOfBoundsException(String s);

    public ArrayIndexOutOfBoundsException(int index);
```
