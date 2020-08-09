### JavaSe

##### 1.自动类型转换

* char-->int-->long-->float-->double

* byte-->short-->int-->long-->float-->double

* (byte,short)与char之间不能自动转换

* byte short char 计算时自动转换为int

* 复合赋值运算符进行自动类型转换

eg：short s=5; 

​	s = s-2; // int--> short 错误 

​	byte num=3；

​	num+=1；//本质上 num=(byte)(num+1);

##### 2.算术运算

```java
class Happy{
    public static void main(String args[]){
        int i=1;
        i*=i++;
        int j=i++;
        if(i==(++j)&&(i++)==j){
            i+=j;
        }
        System.out.println("i="+i);//5
    }
}
```

##### 3.进制

* x进制转换十进制
  * 规则：从最低位开始，将每个位上的数提取出来，乘x的（位数-1）次方，然后求和。

##### 4.位运算

* 二进制的最高位符号位：0表示正数，1表示负数

* 正数
  * 原码、反码、补码都一样

* 负数
  * 反码：符号位不变，其他位取反
  * 补码：反码+1

* java中的数都是有符号的
* 计算机都是以补码的方式来运算的，看结果时需看对应的原码
* '>>' :底位溢出，符号位不变，并用符号为补溢出的高位
* '<<':符号为不变，低位补0
* '>>>':低位溢出，高位补0

eg：1>>2  1/2/2  //0

​	-1>>2 //推导出其补码 进行计算。

​	~-2=?  

##### 5.switch

* 表达式数据类型，应和case后的常量类型一致，或者是可以自动转成可以相互比较的类型
* 表达式返回值必须是：byte、short、int、char、enum、string

* case子句中的值必须是常量，而不能是变量

##### 6.多重循环控制

* 一般有两层
  * 外循环：一般控制行数
  * 内循环：一般控制列数
  * 循环次数=外层循环次数*内层循环次数

eg：打印空心金字塔

```java
public static void main(String[] args){
    int totalLevle=10;
    //先控制外循环 行数
    for(int i=0;i<=totalLevle;i++){
        //内循环为列数
        for(int j=0;j<=totalLevle;j++){
            //找到行数与列数的关系 形成金字塔
            //条件：j/2-(i-1)||j/2+(i-1)
            if(j==totalLevle/2-i*2||j==totalLevle/2+i*2){
                //输出*
            }else{
                //输出空格
            }
        }
    }
}
```

##### 7.交换式排序法

* 冒泡排序法

  ```java
  public static void main(String[] args){
      // 外层循环控制轮数
      int[] arr= {};
      for(int i=0;i<=arr.length-1;i++){
          // 内层循环控制比较次数
          for(int j=0;j<=arr.length-1;i++){
              if(arr[j]>arr[j+1]){
                  int temp =arr[j];
                  arr[j]=arr[j+1];
                  arr[j+1]=arr[j];
              }
          }
      }
  }
  ```

##### 8.查找

* 顺序查找

  ```java
  public static void main(String[] args){
      //一个一个的找
      for(int i=0;i<=arr.length-1;i++){
          if("".equals(arr[i])){
              int index=i;
              break;
          }
      }
  }
  ```

  

* 二分查找

  ```java
  public static void main(String[] args){
      int left;
      int right;
      int index;
      while(true){
          int mid =(right+left)/2;
          if(arr[mid]==index){
             return mid;
          }else if(arr[mid]<index){
              left=mid+1;
          }else if(arr[mid]>index){
              right=mid-1;
          }
      }
  }
  ```


##### 9.数组

* 一维数组
  * 声明方式：int[] x  或者int x[]

* 二维数组
  * 声明方式：int[][] `[]`[] y 或者 int[] y[]  或者 int  y`[]`[]

eg:声明：int[] x,y[]; 

​	x->一维数组，y->二维数组

​	x[0]=y //false

​	y[0]=x //true

##### 10.JVM	

| 区域名称   | 作用                                                         |
| ---------- | ------------------------------------------------------------ |
| 程序计数器 | 程序计数器是CPU中的寄存器，它包含每一个线程下一条要执行的指令的地址 |
| 本地方法栈 | 当程序中调用了native的本地方法时，本地方法执行期间的内存区域 |
| 方法区     | 存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。 |
| 堆内存     | 存储对象（包括数组对象），new来创建的，都存储在堆内存。      |
| 虚拟机栈   | 用于存储正在执行的每个Java方法的局部变量表等。局部变量表存放了编译期可知长度的各种基本数据类型、对象引用，方法执行完，自动释放。 |

eg：Java创建对象的流程简单分析

```java
Person p1 =new Person();
p1.name="jack";
p1.age=10;
```

* 先加载Person类信息(Person.class)，只会加载异常，放在方法去的类加载区
* 在堆中分配空间(地址)，同时进行默认初始化。
* 将堆中的对象地址，赋值p1
* 进行指定初始化 name="jack" age=10
* 可以使用p1对象

方法的调用机制

* 当java程序调用一个方法是，会开辟一个方法空间
* 该空间是独立的空间
* 新开空间，接收形参，也可以创建自己的变量
* 可以执行自己的代码
* 当方法执行完毕后，返回调用的位置，继续执行，原来开辟的空间就释放了

##### 11.方法重载与重写

* 重载
  * 方法名：必须相同
  * 形参列表：必须不同
  * 返回类型：无要求

##### 12.属性与局部变量

* 声明的位置不同

  * 成员变量：类中方法外

  * 局部变量：方法中

* 初始值不同

  * 成员变量：有默认值

  * 局部变量：必须赋值

* 内存存储位置不同

  * 成员变量：
    * 类变量：方法区
    * 实例变量：堆

  * 局部变量：
    * 栈

* 生命周期

  * 成员变量：
    * 类变量：和类的生命周期相同，该类所有对象共享
    * 实例变量：每一个对象的实例变量的生命周期是独立的，随着对象的创建而创建，随着对象的回收而消失

  * 局部变量：随着方法被调用执行在栈中分配，方法调用结束内存就释放，并且还有作用域问题。

* 修饰符
  * 成员变量：有很多修饰符，例如：public,private,static等
  * 局部变量：不能有修饰符