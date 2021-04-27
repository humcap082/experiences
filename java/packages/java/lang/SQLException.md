# SQLException

```java
public class SQLException extends java.lang.Exception
                          implements Iterable<Throwable> {
    public SQLException(String reason, String SQLState, int vendorCode);

    public SQLException(String reason, String SQLState);

    public SQLException(String reason);

    public SQLException();

    public SQLException(Throwable cause);

    public SQLException(String reason, Throwable cause);

    public SQLException(String reason, String sqlState, Throwable cause);

    public SQLException(
        String reason,
        String sqlState,
        int vendorCode,
        Throwable cause
    );
```
