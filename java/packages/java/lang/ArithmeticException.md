# ArithmeticException

算術計算で例外的条件が発生した場合にスローされます。

たとえば、ゼロ除算が発生したときにスローされます。

```java
public class ArithmeticException extends RuntimeException {
    public ArithmeticException();
    public ArithmeticException(String s);
``` 
