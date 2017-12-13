### Q1,结果输出什么

```java
  public static void main(String[] args) {

      int a = 3, b = 4;

      if (a++ == 3 && ++b == 5 && ++a + b++ == 10 && a++ == 7 && ++b == 11) {
          System.out.println("a:" + a + "   b:" + b);
      } else {
          System.out.println("a:" + a + "   b:" + b);
      }

  }
```

### 分析
#### 这个题就是在考查i++与++i的理解

- i++  表达式 a = i++  它等价于 a = i ; i = i + 1;
- ++i  表达式 a = ++i  它等价于 i = i + 1; a = i;

---
### 运行步骤

- a++ == 3  		true
- ++b == 5  		true
- ++a + b++ == 10 	true
- a++ == 7     		false

### 结果

a:6   b:6

