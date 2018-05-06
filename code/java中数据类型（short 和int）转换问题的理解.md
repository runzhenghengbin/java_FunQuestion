> 相信大家刚开始面试时，肯定遇到过这个问题
### 1.第一种情况
```
public class HelloWord {
	//执行结果是？
    public static void main(String[] args){
       short a =1;
        a = a+1;
       System.out.print(a);
    }
}
```
#### 结果大家都知道是编译就会报错
- 具体原因呢，如下

![这里写图片描述](http://img.blog.csdn.net/20171123131437960?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvYWxsZW5qYXkxMQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

### 2.第二种情况

```
public class HelloWord {
    public static void main(String[] args){
       short a =1;
        a +=1;
       System.out.print(a);
    }
}
```
- 此时是可以运行的，也不报错。原因如下
> java语言规范中关于复合赋值的解释是这样的：E1 op=E2等价于
E1=(T)(E1 op E2),这里的T是E1的数据类型，看到这里 ，大家应该豁然开朗了，原来这个复合赋值是自带了隐式的强制类型转换的。

### 3.第三中情况

```java
public class HelloWord {
    public static void main(String[] args){
       short a =1;
       short b =1;
       short c = a+b;
       System.out.print(c);
    }
}
```
- 此时还是无法编译
> 精度小于int的数值运算的时候都回被自动转换为int后进行计算;

- 正确写法

```
public class HelloWord {
    public static void main(String[] args){
       short a =1;
       short b =1;
       short c = (short)(a+b);
       System.out.print(c);
    }
}

```