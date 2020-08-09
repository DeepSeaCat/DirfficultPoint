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

  