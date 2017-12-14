> 首先，不要纠结于 Pass By Value 和 Pass By Reference 的字面上的意义，否则很容易陷入所谓的“一切传引用其实本质上是传值”这种并不能解决问题无意义论战中。更何况，要想知道Java到底是传值还是传引用，起码你要先知道传值和传引用的准确含义吧？可是如果你已经知道了这两个名字的准确含义，那么你自己就能判断Java到底是传值还是传引用。这就好像用大学的名词来解释高中的题目，对于初学者根本没有任何意义--（知乎网友Intopass）





### 一.基本数据类型

```java
public class JavaTest {
 
    public static void changeInt(int x){
        x=55;
    }

    public static void main(String[] args) {
    	int x = 8;
        changeInt(x);
        System.out.println(x);
        
    }
}
```

- x是基本类型，值就直接保存在变量中
- 对于基本类型 x ，赋值运算符会直接改变变量的值，原来的值被覆盖掉。
- 结果为8


![image](http://p0wnvdgrj.bkt.clouddn.com/int_passvalue.png)

### 二.字符串String类型

```java
   public static void changeStr(String str){
       str="welcome";
    }

    public static void main(String[] args) {
    	String str ="1234";
    	changeStr(str);
        System.out.println(str);
    }
```
- str是引用类型，变量中保存的只是实际对象的地址。一般称这种变量为"引用"，引用指向实际对象，实际对象中保存着内容。
- 结果为1234

![image](http://p0wnvdgrj.bkt.clouddn.com/string.png)

### 三.StringBuilder

```java
   public static void changeStringBuilder(StringBuilder sb){
	   sb.append("X");
    }


    public static void main(String[] args) {
    	StringBuilder sb = new StringBuilder("iphone");
    	changeStringBuilder(sb);
        System.out.println(sb);
    }
```
- 结果为iphoneX

![image](http://p0wnvdgrj.bkt.clouddn.com/sb.png)

### 四.数组
#### 列子1
```
public class JavaTest {	
	private static void changeValue(int[] arr) {
		for (int i = 0; i < arr.length; i++)
		arr[i] *= 2;
		}
		public static void main(String[] args) {
		    int[] arr = { 1, 2, 3, 4, 5 };	
		    changeValue(arr);
		    System.out.println(Arrays.toString(arr));
		}
}
```
- 结果为[2, 4, 6, 8, 10]

![image](http://p0wnvdgrj.bkt.clouddn.com/arr1.png)

#### 列子2
```
public  class HelloWord {
	private static void changeValue(int[] arr) {
		arr = new int[3];
	}
	public static void main(String[] args) {
		int[] arr = { 1, 2, 3, 4, 5 };	
		changeValue(arr);
		System.out.println(Arrays.toString(arr));
	}
}
```
- 结果为[1, 2, 3, 4, 5]

![image](http://p0wnvdgrj.bkt.clouddn.com/arr2.png)

#### 例子3
```
public  class HelloWord {
	private static void changeValue(int[] arr) {
		arr[1] = 5;
	}
	public static void main(String[] args) {
		int[] arr = { 1, 2, 3, 4, 5 };	
		changeValue(arr);
		System.out.println(Arrays.toString(arr));
	}
}
```
- 结果[1, 5, 3, 4, 5]


![image](http://p0wnvdgrj.bkt.clouddn.com/arr3.png)

#### 例子4
```
public  class HelloWord {
	    public static void main(String[] args) {
	        int[][] arr = {{1, 2, 3}, {4, 5}};
	        System.out.println(Arrays.toString(arr));
	        System.out.println(Arrays.toString(arr[0]));
	        System.out.println(Arrays.toString(arr[1]));
	        change(arr);
	        System.out.println(Arrays.toString(arr));
	        System.out.println(Arrays.toString(arr[0]));
	        System.out.println(Arrays.toString(arr[1]));
	    }

	    public static void change(int[][] arr) {
	        arr[1] = new int[]{7, 8, 9};
	    }
	
}

```
- 结果
```
[[I@15db9742, [I@6d06d69c]
[1, 2, 3]
[4, 5]
[[I@15db9742, [I@7852e922]
[1, 2, 3]
[7, 8, 9]
```
![image](http://p0wnvdgrj.bkt.clouddn.com/arr4.png)


change(arr); 之后

![image](http://p0wnvdgrj.bkt.clouddn.com/arr5.png)
#### 例子5

```
	 public static void main(String[] args) {
	        int[][] arr = {{1, 2, 3}, {4, 5}};
	        System.out.println(Arrays.toString(arr));
	        System.out.println(Arrays.toString(arr[0]));
	        System.out.println(Arrays.toString(arr[1]));
	        change(arr[1]);
	        System.out.println(Arrays.toString(arr));
	        System.out.println(Arrays.toString(arr[0]));
	        System.out.println(Arrays.toString(arr[1]));
	    }

	    public static void change(int[] arr) {
	        arr = new int[]{7, 8, 9};
	    }
```
- 结果

```
[[I@15db9742, [I@6d06d69c]
[1, 2, 3]
[4, 5]
[[I@15db9742, [I@6d06d69c]
[1, 2, 3]
[4, 5]
```

- 大家自己画画这个图吧，玩的开心

> ps.大家有没有推荐好的画图软件