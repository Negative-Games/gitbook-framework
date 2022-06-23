# Time Utility

Our custom time utility allows you to parse text to the long format for detailing time. We also allow you to parse long to a human-readable format such as `1h 10m`.

## Code Example

```java
        // current - date
        String readable = TimeUtil.format(System.currentTimeMillis(), date);
        Long time = TimeUtil.longFromString("1d1h");
```
