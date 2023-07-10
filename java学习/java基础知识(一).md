# java基础知识（一）
## 一、运算符
1. 算数运算符(加减乘除取余)

```java
       // +
        System.out.println(3+2);
        // -
        System.out.println(3-1);
        // *
        System.out.println(3*2);
        // /
        System.out.println(16/3);
        // %
        System.out.println(16%3);
        //如何由小数参与以上运算，结果有可能不准，原因待解释
```
- 隐式转换
取值范围小的数值向取值范围大的数值转换；（byte<short<int<long<float<double）
byte、short、char 在参与运算时，都会先直接提升为int ，然后进行运算。
- 强制转换
格式：目标数据类型 变量名=（目标数据类型）被强制转换数据
- 字符+数字 ，会先把字符转换成对应的数字在相加（如 'a' 对应的时97，'A'对应的是65）
2. 自增自减运算符
3. 赋值运算符
4. 关系运算符
5. 逻辑运算符
- ^  逻辑异或，相同为false,不同为true
- 短路逻辑运算符（&&,||），效果和&,| 一样，但是具有短路效果
6. 三元运算符
7. 补码和反码
## 二、判断和循环
1. 回文数
```java
        Scanner sc= new Scanner(System.in);
        System.out.println("请输入一个数字");
        int x=sc.nextInt();//赋值一个数字
        int number=x;
        int num=0;
        while(number!=0){
           int ge= number%10;
           number/=10;
           num=num*10+ge;
        }
        System.out.println(num==x?"是回文数":"不是回文数");
```
2. 求商和余数（要求不使用乘除和%）
思想：循环实现
```java
      Scanner sc= new Scanner(System.in);
        System.out.println("请输入被除数");
        int x=sc.nextInt();//赋值一个数字
        System.out.println("请输入除数");
        int y=sc.nextInt();//赋值一个数字
        int remainder=0;//余数初始化
        int business=0;//商初始化
        while(x>=y){
        x-=y;
        business+=1;
        remainder=x;
        }
        System.out.println("商:"+business);
        System.out.println("余数"+remainder);
```
3. 逢7过（从任意数字开始报数，如果报的数字包含7或者是7的倍数，就说过;打印1-100之间满足规则的数字）
```java
    for(int num=1;num<=100;num++){
            if(num%7==0||num%10==7||num/10%10==7)//条件判断的条件要充分考虑各种情况
            System.out.println(num);
        }
```
## 三、数组
1. 数组格式
- 完整格式（数据类型[] 数组名=new 数据类型 [] {元素1，元素2}）
- 简化格式 （数据类型[] 数组名={元素1，元素2}）
- 数据类型有double,int,String
2. 数组初始化长度
- 格式： 数据类型[] 数组名 =new 数据类型[数组长度]
3. 二维数组
- 格式 数据类型[][] 数组名=new 数据类型[][] {{元素1，元素2},{元素1，元素2}};
- 简化格式 数据类型[][] 数组名={{元素1，元素2},{元素1，元素2}}
## 四、方法
1. 方法概念及用途
- 方法是程序中最小的执行单元;将重复的代码、具有独立功能的代码可以抽取到方法中;方法可以提高代码的复用性和可维护性。
- 方法必须先定义后调用
2. 最简单方法格式：
```java
public static void 方法名（）{
  方法体
}
```
3. 带参数的方法定义和调用
```java
public static 返回值类型 方法名（int number1,int number2）{
  ...
  ...
  return 返回值
}
//注意方法返回值类型 和返回值的类型 是一样的
```
4. 方法的重载
- 同一个类中，方法名相同，参数不同的方法（个数不同，顺序不同，类型不同），与返回值无关。
```java
//买飞机票
   public static void main(String[] args) {
        Scanner sc= new Scanner(System.in);
        System.out.println("请输入机票价格");
        int price=sc.nextInt();
        System.out.println("请输入月份数（1-12）");
        int month=sc.nextInt();
        System.out.println("请输入机票类型（1-头等舱，0-经济舱）");
        int type=sc.nextInt();
        double num=airPrice(price,month,type);
        System.out.println("当前季节机票价格为:"+num);
    }
    public static double airPrice(int price,int month,int  type) {
        if(month>=5 && month<=10){
            if(type==1)//代表头等舱
            {
                return price*0.9;
            }else{
                return price*8.5;
            }
        }else{
            if(type==1)//代表头等舱
            {
                return price*0.7;
            }else{
                return price*0.65;
            }
        }
    }
    //注意事项: 定义有参数的方法时候，传入的参数类型要与方法定义的参数类型一致；
    //方法如果有返回值，接受该方法返回值的变量，要与方法返回值的类型一样

//开发验证码（验证码长度为5，前四位是大小写字母，最后一位是数字）
  public static void main(String[] args) {
        char[] arr= new char[52];
        for(int i=0;i<arr.length;i++){
            if(i<26){
                //添加小写字母
                arr[i]=(char)(97+i);
            }else{
                //添加大写字母
                arr[i]=(char)(65+i-26);
            }
        }
        String result="";
        //随机抽取四个字母
        Random r=new Random();
        for(int i=0;i<4;i++){
            int randomIndex=r.nextInt(arr.length);
            result+=arr[randomIndex];
        }
        //随机抽取一个数字
        int num=r.nextInt(10);
        result+=num;
        System.out.println(result);
    }
```
