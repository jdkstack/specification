```java
public class Power2 {

  /**
   * 计算2的下一次幂.
   *
   * <p>输入一个整数，根据整数计算出2的下一次幂.
   *
   * @param x 输入一个整数.
   * @return 2的下一次幂.
   * @author admin
   */
  public static int power2(final int x) {
    // 如果x为4，则x1为3。
    int x1 = x - 1;
    // 数字3的二进制是0000 0000 0000 0000 0000 0000 0000 0011。
    // 获取二进制数有多少个0，0有30个。
    int i = Integer.numberOfLeadingZeros(x1);
    // 获取二进制数有多少个非0，非0有2个。
    int s = 32 - i;
    // 返回2的s次方。
    return 1 << s;
  }
}
```
