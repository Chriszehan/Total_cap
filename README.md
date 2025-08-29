# JAVAstudy

## 1、运行一个JAVA 程序 先将.java文件交由编译器编译为.class 再交给JVM执行

一个Java源码只能定义一个public类型的class，并且class名称和文件名要完全一致；

使用javac可以将.java源码编译成.class字节码；

使用java可以运行一个已编译的Java程序，参数是类名。

## 2、程序基本结构
面向对象的程序 基本单位就是class 要求类名--------驼峰

Java入口程序规定的方法必须是静态方法，方法名必须为main，括号内的参数必须是String数组。

## 3、变量
基本类型的变量和引用类型的变量

基本类型变量 在Java中，变量必须先定义后使用 

同一变量无需再次定义变量类型  变量可重新赋值

## 4、基本数据类型 
CPU可直接进行运算的类型
整型：byte（8个bit）、short、int 、long
浮点型：float、double
字符型：char
布尔类型：boolean

计算机内存的最小存储单元是字节（byte），一个字节就是一个8位二进制数，即8个bit。

它的二进制表示范围从00000000~11111111，换算成十进制是0~255，换算成十六进制是00~ff。

内存单元从0开始编号，称为内存地址
![image](https://github.com/user-attachments/assets/36c72179-63bc-4bc3-be55-a0a67a1009f1)

### 整型
  int类型可以赋值给long 
  表示为 long n1 = 900;
  但是不能把long型赋值给int


### 浮点型
  float f1 = 3.14f;
  float f2 = 3.14e38f; // 科学计数法表示的3.14x10^38
  float f3 = 1.0; // 错误：不带f结尾的是double类型，不能赋值给float

  double d = 1.79e308;
  double d2 = -1.79e308;
  double d3 = 4.9e-324; // 科学计数法表示的4.9x10^-324


### 布尔类型
  boolean b1 = true;
  boolean b2 = false;
  boolean isGreater = 5 > 3; // 计算结果为true
  int age = 12;
  boolean isAdult = age >= 18; // 计算结果为false

### 字符类型
  char a = 'A'  
  注意char类型使用单引号'，且仅有一个字符，要和双引号"的字符串类型区分开。


### 引用类型
  String s = "hello";
  内部存储一个地址 ，指向某个对象在内存的位置

### 常量
  final修饰符 变量加上此修饰符之后 就变成常量
  初始化定义后 不可再次赋值 会导致编译错误

### var关键字
  有些时候，类型的名字太长，写起来比较麻烦。例如：
  
  StringBuilder sb = new StringBuilder();
  
  这个时候，如果想省略变量类型，可以使用var关键字：
  
  var sb = new StringBuilder();
  
  编译器会根据赋值语句自动推断出变量sb的类型是StringBuilder。
  
  对编译器来说，语句：
  var sb = new StringBuilder();
  
  实际上会自动变成：
  StringBuilder sb = new StringBuilder();
  因此，使用var定义变量，仅仅是少写了变量类型而已。

变量作用域以{}为准

## 整数运算
  n++ 自增运算
  ++n表示先加1再引用n
  n++表示先引用n再加1 

### 移位运算
  计算机中 整数总是以二进制的形式表示 int类型移位运算

  向左移 实际上是不断地 x2 

  int n = 7;       // 00000000 00000000 00000000 00000111 = 7
  
  int a = n << 1;  // 00000000 00000000 00000000 00001110 = 14
  
  int b = n << 2;  // 00000000 00000000 00000000 00011100 = 28
  
  int c = n << 28; // 01110000 00000000 00000000 00000000 = 1879048192
  
  int d = n << 29; // 11100000 00000000 00000000 00000000 = -536870912

  向右移 实际上是不断地 /2
  
  int n = 7;       // 00000000 00000000 00000000 00000111 = 7
  
  int a = n >> 1;  // 00000000 00000000 00000000 00000011 = 3
  
  int b = n >> 2;  // 00000000 00000000 00000000 00000001 = 1
  
  int c = n >> 3;  // 00000000 00000000 00000000 00000000 = 0

  >>有符号位移运算  >>>无符号位移运算 右移后高位总是补0
     因此对一个负数进行>>>右移 会变成正数 最高位有1变成0

### 位运算
  
  与运算的规则是，必须两个数同时为1，结果才为1：
  
  n = 0 & 0; // 0
  n = 0 & 1; // 0
  n = 1 & 0; // 0
  n = 1 & 1; // 1

  或运算的规则是，只要任意一个为1，结果就为1：
  
  n = 0 | 0; // 0
  n = 0 | 1; // 1
  n = 1 | 0; // 1
  n = 1 | 1; // 1

  非运算的规则是，0和1互换：
  
  n = ~0; // 1
  n = ~1; // 0

  异或运算的规则是，如果两个数不同，结果为1，否则为0：

  n = 0 ^ 0; // 0
  n = 0 ^ 1; // 1
  n = 1 ^ 0; // 1
  n = 1 ^ 1; // 0

### 类型自动提升 和 强制转型

如果参与运算的两个数类型不一致 
那么计算自动提升类型为较大的类型
// 类型自动提升与强制转型

public class Main {
    public static void main(String[] args) {
        short s = 1234;
        int i = 123456;
        int x = s + i; // s自动转型为int
        short y = s + i; // 编译错误!
    }
}

也可以将结果强制转型，即将大范围的整数转型为小范围的整数。

强制转型使用(类型)，例如，将int强制转型为short：

int i = 12345;

short s = (short) i; // 12345

要注意，超出范围的强制转型会得到错误的结果，原因是转型时，int的两个高位字节直接被扔掉，仅保留了低位的两个字节：

// 强制转型
public class Main {
    public static void main(String[] args) {
        int i1 = 1234567;
        short s1 = (short) i1; // -10617
        System.out.println(s1);
        int i2 = 12345678;
        short s2 = (short) i2; // 24910
        System.out.println(s2);
    }
}

因此，强制转型的结果很可能是错的。

## 浮点数运算
  只能加减乘除 无法精确表示 存在运算误差 一般通过判断两个浮点数之差的绝对值是否小于一个很小的数 
  
  类型提升：
    如一个是整型 另一个是浮点型 那么整型自动提升到浮点型


## 布尔运算
  三元运算 b ? x : y
  注意到三元运算b ? x : y会首先计算b，如果b为true，则只计算x，否则，只计算y。此外，x和y的类型必须相同，因为返回值不是boolean，而是x和y之一

## 字符和字符串
  字符类型char是基本数据类型 一个char保存一个Unicode字符
  
  int n1 = 'A' 
  int n2 = '中'

  字符串类型String是引用类型  一个字符穿可以存储0-任意个字符
  如果用+连接字符串和其他数据类型，会将其他数据类型先自动转型为字符串，再连接
  
  java 字符串重要特性 字符串不可变
  // 字符串不可变
public class Main {
    public static void main(String[] args) {
        String s = "hello";
        System.out.println(s); // 显示 hello
        s = "world";  这里改变了变量s的指向地址  原来的"hello"无法通过变量s访问
        System.out.println(s); // 显示 world  
    }
}

  java13 可以使用""" xxx """ 表示多行字符串了

public class Main {
    public static void main(String[] args) {
        String s = """
                   SELECT * FROM
                     users
                   WHERE id > 100
                   ORDER BY name DESC
                   """;
        System.out.println(s);
    }
}

引用类型的变量可以指向一个空值null 表示不存在 既该变量不指向任何对象

## 数组类型
    所有元素初始化为默认值 整型都是0，浮点型为0.0 布尔型是false
    一旦创建后 大小不可改变;
    索引从0开始  可以通过复制修改数组中某个元素 n[15] = 79;
    S.length 获取数组大小

    数组是引用类型 
    // 数组
public class Main {
    public static void main(String[] args) {
        // 5位同学的成绩:
        int[] ns;
        ns = new int[] { 68, 79, 91, 85, 62 };
        System.out.println(ns.length); // 5
        ns = new int[] { 1, 2, 3 };                //实则更换了新的地址赋值给到ns
        System.out.println(ns.length); // 3
    }
}

      问？
        String[] names = {"ABC", "XYZ", "zoo"};
        String s = names[1];
        names[1] = "cat";
        System.out.println(s); // s是"XYZ"还是"cat"?

## 输入/输出
  ### 输出
  如果要把数据显示成我们期望的格式，就需要使用格式化输出的功能。
  
  格式化输出使用System.out.printf()，
  
  通过使用占位符%?，printf()可以把后面的参数格式化成指定格式：

  例
    double d = 3.1415926;
    System.out.printf("%.2f\n", d); // 显示两位小数3.14
    System.out.printf("%.4f\n", d); // 显示4位小数3.1416
    
  格式化占位符：
  
  占位符	说明
  %d	格式化输出整数
  %x	格式化输出十六进制整数
  %f	格式化输出浮点数
  %e	格式化输出科学计数法表示的浮点数
  %s	格式化字符串

 ### 输入
   使用scanner 创建scanner对象并传入System.in 
   
   再使用scanner.nextline() 读取用户输入字符串
   或
   scanner.nextInt() 读取用户输入整数

## if条件判断

### if
  通过 (条件) 判断是否满足 满足时执行{}中的语句
  if(){
    //abcs
  }
  
### else
  当条件判断为false时 将执行else语句块
  if(){}
  else if(){}
  else {}

  判断引用类型的变量内容是否相等 ，必须使用equals()方法
  引用类型的变量可以指向不同对象 内容相同 类似与指向不同的地址
  String s1

## Switch多重选择
  根据option 匹配到对应的case 若无匹配会执行default
  可以比较字符串 还可以比较枚举

  int option = 1;
        switch (option) {
        case 1:
            System.out.println("Selected 1");
            break;   //要加break 否则 下列语句会继续执行一直遇到break
        case 2:
            System.out.println("Selected 2");
            break;
        case 3:
            System.out.println("Selected 3");
            break;
        default:
            System.out.println("Selected other");
            yield pdd;
            break;
        }
  通过yield 返回一个值作为switch语句返回值

## while循环

  while(条件)满足时继续循环，条件不满足时退出循环
  每次循环开始前 判断条件是否成立 
  
   int sum = 0; // 累加的和，初始化为0
        int n = 1;
        while (n <= 100) { // 循环条件是n <= 100
            sum = sum + n; // 把n累加到sum中
            n ++; // n自身加1
        }

## do..while循环

  先执行循环再判断条件 因此循环最少都会执行一次
  
## for循环
  略
  先初始化计数器 在每次开始循环前检查条件 
### for each循环
  int[] ns = { 1, 4, 9, 16, 25 };
  for (int n : ns) {
      System.out.println(n);
  }
  for each循环的变量n 不再是计数器 而是直接对应到数组的每个元素 
  且也不只是 数组  for each循环能够遍历所有"可迭代"的数据类型 包括List、Map等

### break和continue
  在循环过程中，使用break语句跳出当前循环 既此for或while语句结束不再执行
  而continue 则是提前结束本次循环，直接继续执行下次循环
  
## 数组操作
### 遍历数组
    1、 for循环
    2、 for each循环
      public class Main {
    public static void main(String[] args) {
        int[] ns = { 1, 4, 9, 16, 25 };
        for (int n : ns) {
            System.out.println(n);
        }
    }
}
      //其中变量n 直接拿到ns数组的元素 而不是索引

### 打印数组内容
    1、循环打印
    2、用轮子 Arrays.toString();

### 数组排序
    1、冒泡排序
      一个大循环遍历数组一个小循环的对比
    
### 多维数组
    1、二维数组---数组里元素是数组
    int[][] ns = {
            { 1, 2, 3, 4 },
            { 5, 6, 8 },
            { 9, 10, 11, 12，77 }
        };
    用两层循环打印 或者 轮子 Arrays.deepToString()。
    2、三维数组---数组里元素是数组-再放数组

### 命令行参数
    Java程序的入口是main方法 ，而main方法可以接受一个命令行参数，它是一个String[]数组

## 面向对象编程
### 面向对象基础

抽象概念 作为类（class)  转具体则为实例(Instance)

class是一种对象模板 定义了如何创建实例,因此class本身是一种数据类型
instance 是对象实例 根据class模板创建的实例 类型相同 但是属性可能不同

### 定义class 

class Person{
  public String name;
  public int age;
}

一个class可以包含多个字段（field），字段用来描述一个类的特征。

上面的person类，我们定义了两个字段。

一个是String类型的字段，命名为name，一个是int类型的字段，命名为age。

因此，通过class，把一组数据汇集到一个对象上，实现了数据封装。

### 创建实例

定义了class，只是定义了对象模版，而要根据对象模版创建出真正的对象实例，必须用new操作符。

new操作符可以创建一个实例，然后，我们需要定义一个引用类型的变量来指向这个实例：

Person ming = new Person();

上述代码创建了一个Person类型的实例，并通过变量ming指向它。

注意区分Person ming是定义Person类型的变量ming，而new Person()是创建Person实例。

访问实例字段的方法是变量名.字段名；

指向instance的变量都是引用变量。

>> 一个Java源文件可以包含多个类的定义，但只能定义一个public类，且public类名必须与文件名一致。
>> 如果要定义多个public类，必须拆到多个Java源文件中。

### 方法
一个class可以包含多个field

直接用public 会破坏封装性 则将public修改为private修饰

外部代码不能直接读取private字段，但可以通过getName()和getAge()间接获取private字段的值。


所以，一个类通过定义方法，就可以给外部代码暴露一些操作的接口，同时，内部自己保证逻辑一致性。

虽然外部代码不能直接修改private字段，但是，外部代码可以调用方法setName()和setAge()来间接修改private字段。

在方法内部，我们就有机会检查参数对不对。

比如，setAge()就会检查传入的参数，参数超出了范围，直接报错。

这样，外部代码就没有任何机会把age设置成不合理的值。

调用方法的语法是实例变量.方法名(参数);。

一个方法调用就是一个语句，所以不要忘了在末尾加;。

例如：ming.setName("Xiao Ming");。

通过setName(String name) 方法 对入参判断 传入值 如传入null或空字符串 则用throw抛出异常

### 定义方法
定义方法的语法是：

*** 
    修饰符 方法返回类型 方法名(方法参数列表) {

    若干方法语句;
    
    return 方法返回值;
    
}
***

方法返回值通过return语句实现，如果没有返回值，返回类型设置为void，可以省略return。

### private方法

有public方法，自然就有private方法。

和private字段一样，private方法不允许外部调用，那我们定义private方法有什么用？

定义private方法的理由是内部方法是可以调用private方法的。例如：

// private method
public class Main {
    public static void main(String[] args) {
        Person ming = new Person();
        ming.setBirth(2008);
        System.out.println(ming.getAge());
    }
}

class Person {
    private String name;
    private int birth;

    public void setBirth(int birth) {
        this.birth = birth;
    }

    public int getAge() {
        return calcAge(2019); // 调用private方法
    }

    // private方法:
    private int calcAge(int currentYear) {
        return currentYear - this.birth;
    }
}

观察上述代码，calcAge()是一个private方法，外部代码无法调用，但是，内部方法getAge()可以调用它。

此外，我们还注意到，这个Person类只定义了birth字段，没有定义age字段，

获取age时，通过方法getAge()返回的是一个实时计算的值，并非存储在某个字段的值。

这说明方法可以封装一个类的对外接口，调用方不需要知道也不关心Person实例在内部到底有没有age字段。

### this变量

在方法内部，可以使用一个隐含的变量this，它始终指向当前实例。因此，通过this.field就可以访问当前实例的字段。

如果没有命名冲突，可以省略this。例如：

class Person {
    private String name;

    public String getName() {
        return name; // 相当于this.name
    }
}
但是，如果有局部变量和字段重名，那么局部变量优先级更高，就必须加上this：

class Person {
    private String name;

    public void setName(String name) {
        this.name = name; // 前面的this不可少，少了就变成局部变量name了
    }
}

### 方法参数
  方法可以包含0个或任意个参数。方法参数用于接收传递给方法的变量值。
  
  调用方法时，必须严格按照参数的定义一一传递。例如：

class Person {
    ...
    public void setNameAndAge(String name, int age) {
        ...
    }
}

调用这个setNameAndAge()方法时，必须有两个参数，且第一个参数必须为String，第二个参数必须为int：

Person ming = new Person();

ming.setNameAndAge("Xiao Ming"); // 编译错误：参数个数不对

ming.setNameAndAge(12, "Xiao Ming"); // 编译错误：参数类型不对

### 可变参数

可变参数用类型... 定义，可变参数相当于数组类型：

class Group {
    private String[] names;

    public void setNames(String... names) {
        this.names = names;
    }
}


上面的setNames() 定义了一个可变参数。调用时，可以这么写：
Group g = new Group();
Group g = new Group();
g.setNames("Xiao Ming", "Xiao Hong", "Xiao Jun"); // 传入3个String
g.setNames("Xiao Ming", "Xiao Hong"); // 传入2个String
g.setNames("Xiao Ming"); // 传入1个String
g.setNames(); // 传入0个String
完全可以把可变参数改写为为String[] 类型：
class Group{
  private String[] names;

  public void setNames(String[] names){
    this.names = names;
  }
}

但是，调用方需要自己先构造String[]，比较麻烦。例如：

Group g = new Group();
g.setNames(new String[] {"Xiao Ming", "Xiao Hong", "Xiao Jun"}); // 传入1个String[]
另一个问题是，调用方可以传入null：

Group g = new Group();
g.setNames(null);
而可变参数可以保证无法传入null，因为传入0个参数时，接收到的实际值是一个空数组而不是null。

### 参数绑定

调用函数时把参数传递给实例方法时，调用时传递的值会按照参数位置一一绑定

#### 传递基础类型参数 和 引用参数区别

基本类型参数的传递，是调用方值的复制

引用类型参数的传递，调用方的变量，和接收方的参数变量，指向的是同一个对象。
双方任意一方对这个对象的修改，都会影响对方（因为指向同一个对象嘛）。

      Person p = new Person();
      String[] fullname = new String[] { "Homer", "Simpson" };
      p.setName(fullname); // 传入fullname数组
      System.out.println(p.getName()); // "Homer Simpson"
      fullname[0] = "Bart"; // fullname数组的第一个元素修改为"Bart"
      System.out.println(p.getName()); // 输出"Bart Simpson"

## 构造方法

创建实例时，经常需要同时初始化这个实例的字段
Person ming = new Person();
ming.setName("小明");
ming.setAge(12);
如果不嗲用setName() 或者 setAge() 则实例内部状态不正确

如何解决？
通过构造方法。在创建实例的时候 一次性传入name 和age, 完成初始化：

// 由于构造方法是如此特殊，所以构造方法的名称就是类名

构造方法的参数没有限制，在方法内部，也可以编写任意语句。
但是构造方法没有返回值（没有void）,调用构造方法，必须用new操作符。

### 默认构造方法
编译器自带一个默认构造方法 没有参数 没有执行语句

class Person{
    pulic Person(){}
}

注意如 自定义了一个构造方法，那么编译器不再自动创建默认构造方法

如想保留不带参数的构造方法，只能把两个构造方法都定义出

在创建对象实例时，1、会先初始化 类中定义的字段 ，例如，int age = 10;表示字段初始化为10
2、执行构造方法的代码

## 方法重载 （Overload）
一个类中可以定义多个方法，如果功能类似只是参数不同，则可以同一个命名 但是各自参数不同

## 继承
extends关键字实现继承
例：
class Person {
    private String name;
    private int age;

    public String getName() {...}
    public void setName(String name) {...}
    public int getAge() {...}
    public void setAge(int age) {...}
}

class Student extends Person {
    // 不要重复name和age字段/方法,
    // 只需要定义新增score字段/方法:
    private int score;

    public int getScore() { … }
    public void setScore(int score) { … }
}

** 注意
** 子类自动获得了父类的所有字段，严禁定义与父类重名的字段！

// 我们在定义Person的时候，没有写extends。在Java中，没有明确写extends的类，编译器会自动加上extends Object。所以，任何类，除了Object，都会继承自某个类。 下图是Person、Student的继承树
       ┌───────────┐
       │  Object   │
       └───────────┘
             ▲
             │
       ┌───────────┐
       │  Person   │
       └───────────┘
          ▲     ▲
          │     │
          │     │
┌───────────┐ ┌───────────┐
│  Student  │ │  Teacher  │
└───────────┘ └───────────┘
Java只允许一个class继承自一个类，因此，一个类有且仅有一个父类。只有Object特殊，它没有父类。

### protected
继承有个特点，就是子类无法访问父类的private字段或者private方法。例如，Student类就无法访问Person类的name和age字段：

class Person {
    private String name;
    private int age;
}

class Student extends Person {
    public String hello() {
        return "Hello, " + name; // 编译错误：无法访问name字段
    }
}

这使得继承的作用被削弱了。

为了让子类可以访问父类的字段，我们需要把private改为protected。

用protected修饰的字段可以被子类访问：

class Person {
    protected String name;
    protected int age;
}

class Student extends Person {
    public String hello() {
        return "Hello, " + name; // OK!
    }
}

因此，protected关键字可以把字段和方法的访问权限控制在继承树内部，
一个protected字段和方法可以被其子类，以及子类的子类所访问

### super
super关键字表示父类（超类）。子类引用父类的字段时，可以用super.fieldName。例如：

  class Student extends Person {
    public String hello() {
        return "Hello, " + super.name;
    }
  }
实际上，这里使用super.name，或者this.name，或者name，效果都是一样的。
编译器会自动定位到父类的name字段。

但是，在某些时候，就必须使用super。我们来看一个例子：

  public class Main {
    public static void main(String[] args) {
        Student s = new Student("Xiao Ming", 12, 89);
    }
  }


  class Person {
    protected String name;
    protected int age;
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
  }


  class Student extends Person {
    protected int score;
    public Student(String name, int age, int score) {
        this.score = score;
    }
  }

运行上面的代码，会得到一个编译错误，大意是在Student的构造方法中，无法调用Person的构造方法。

这是因为在Java中，任何class的构造方法，第一行语句必须是调用父类的构造方法。

如果没有明确地调用父类的构造方法，编译器会帮我们自动加一句super();

所以，Student类的构造方法实际上是这样：

  class Student extends Person {
    protected int score;
    public Student(String name, int age, int score) {
        super(); // 自动调用父类的构造方法
        this.score = score;
    }
  }

但是，Person类并没有无参数的构造方法，因此，编译失败。

解决方法是调用Person类存在的某个构造方法。例如：

  class Student extends Person {
    protected int score;
    public Student(String name, int age, int score) {
        super(name, age); // 调用父类的构造方法Person(String, int)
        this.score = score;
    }
  }

这样就可以正常编译了！

因此我们得出结论：如果父类没有默认的构造方法，子类就必须显式调用super() 

并给出参数以便让编译器定位到父类的一个合适的构造方法。

这里还顺带引出了另一个问题：即子类 <b>不会继承</b>任何父类的构造方法。

子类默认的构造方法是编译器自动生成的，不是继承的。

### 向上转型

如果一个引用变量的类型是Student，那么它可以指向一个Student类型的实例：

Student s = new Student();

如果一个引用类型的变量是Person，那么它可以指向一个Person类型的实例：

Person p = new Person();

那么Person p = new Student()是向上转型

因为Student继承自Person，因此，它拥有Person的全部功能。

Person类型的变量，如果指向Student类型的实例，对它进行操作，是没有问题的！

这种把一个子类类型安全地变为父类类型的赋值，被称为向上转型（upcasting）。

向上转型实际上是把一个子类型安全地变为更加抽象的父类型：

Student s = new Student();
Person p = s; // upcasting, ok
Object o1 = p; // upcasting, ok
Object o2 = s; // upcasting, ok

注意到继承树是Student > Person > Object.
所以，可以把Student类型转型为Person，或者更高层次的Object。

### 向下转型

把一个父类强制转型为子类类型，就是向下转型（donwcasting)

Person p1 = new Student(); // upcasting, ok
Person p2 = new Person();
Student s1 = (Student) p1; // ok   --> 实际创建的类型是Student类 拥有其各种方法
Student s2 = (Student) p2; // runtime error! ClassCastException!  失败 实际创建的类型是Person类 没有子类的各种方法


### 多态
子类定义了一个与父类方法签名完全相同的方法，被称为覆写（Override）
在 Person类中 ，定义run（）方法

class Student extends Person{
    public void run(){
      sysout("person run");
    }
}

在子类 Student中，覆写这个run()方法
class Student extends Person{
  @Override
  public void run(){
    sout("student.run");
  }
}

Override和Overload不同的是 如果方法签名不同，就是overload Overload方法是一个新方法；如果方法签名相同，并且返回值相同 就是Override。


如果子类覆写父类的方法：
// override
public class Main {
    public static void main(String[] args) {
        Person p = new Student();
        p.run(); // 应该打印Person.run还是Student.run?
    }
}

class Person {
    public void run() {
        System.out.println("Person.run");
    }
}

class Student extends Person {
    @Override
    public void run() {
        System.out.println("Student.run");
    }
}

实际是打印Student.run
Java的实例方法调用是基于运行时的实际类型的动态调用，而非变量的声明类型。

#### 多态
针对某个类型的方法调用，真正执行方法取决与运行时期实际类型的方法，例：
Person p = new Student();
p.run();

比如一个人的收入 可以有多种收入来源

生成一个收入大类 其中有兼职收入、国家补贴收入、特殊收入、津贴收入的子类

每个收入均有不一样的税费要扣除 而扣除之后才是实际的总收入

// Polymorphic
public class Main {
    public static void main(String[] args) {
        // 给一个有普通收入、工资收入和享受国务院特殊津贴的小伙伴算税:
        Income[] incomes = new Income[] {
            new Income(3000),
            new Salary(7500),
            new StateCouncilSpecialAllowance(15000)
        };
        System.out.println(totalTax(incomes));
    }

    public static double totalTax(Income... incomes) {
        double total = 0;
        for (Income income: incomes) {
            total = total + income.getTax();
        }
        return total;
    }
}

class Income {
    protected double income;

    public Income(double income) {
        this.income = income;
    }

    public double getTax() {
        return income * 0.1; // 税率10%
    }
}

class Salary extends Income {
    public Salary(double income) {
        super(income);
    }

    @Override
    public double getTax() {
        if (income <= 5000) {
            return 0;
        }
        return (income - 5000) * 0.2;
    }
}

class StateCouncilSpecialAllowance extends Income {
    public StateCouncilSpecialAllowance(double income) {
        super(income);
    }

    @Override
    public double getTax() {
        return 0;
    }
}

通过多态的方法 将每个收入子类都覆写一份子类的税费计算方法 而这些方法 都是同一个名称getTax()

对于收入大类而言 都是一个方法getTax() ,甚至不需要知道各个收入子类的存在


** 观察totalTax()方法：利用多态，totalTax()方法只需要和Income打交道，它完全不需要知道Salary和StateCouncilSpecialAllowance的存在，就可以正确计算出总的税。如果我们要新增一种稿费收入，只需要从Income派生，然后正确覆写getTax()方法就可以。把新的类型传入totalTax()，不需要修改任何代码。

### 覆写Object方法
因为所有的class 最终都继承自Object，而Object定义了几个重要的方法：
 toString(): 把instance输出为String;
 equals() : 判断两个instance是否逻辑相等;
 hashCode(): 计算一个instance的哈希值。
 必要的情况下，我们可以覆写Object的这个方法例：
 
class Person {
    ...
    // 显示更有意义的字符串:
    @Override
    public String toString() {
        return "Person:name=" + name;
    }

    // 比较是否相等:
    @Override
    public boolean equals(Object o) {
        // 当且仅当o为Person类型:
        if (o instanceof Person) {
            Person p = (Person) o;
            // 并且name字段相同时，返回true:
            return this.name.equals(p.name);
        }
        return false;
    }

    // 计算hash:
    @Override
    public int hashCode() {
        return this.name.hashCode();
    }
}

### 调用super
在子类的覆写方法中，如果要调用父类的被覆写的方法，可以通过super来调用。 例：

class Person {
    protected String name;
    public String hello() {
        return "Hello, " + name;
    }
}

class Student extends Person {
    @Override
    public String hello() {
        // 调用父类的hello()方法:
        return super.hello() + "!";
    }
}

### final
继承可以运行子类覆写父类的方法。
如果一个父类不允许子类对它某个方法进行覆写，可以把该方法标记为final
用final修饰的方法不能被Override：

class Person {
    protected String name;
    public final String hello() {
        return "Hello, " + name;
    }
}

class Student extends Person {
    // compile error: 不允许覆写
    @Override
    public String hello() {
    }
}

如果一个类不想被任何其他类继承 可以标记为final final修饰的类不能被继承：

class Person {
    protected String name;
    public final String hello() {
        return "Hello, " + name;
    }
}

class Student extends Person {
    // compile error: 不允许覆写
    @Override
    public String hello() {
    }
}

对于一个类的实例字段，同样可以用 final 修饰。修饰的字段在初始化后不能被修改。

class Person {
    public final String name = "Unamed";
}

对final字段重新赋值会报错：

Person p = new Person();
p.name = "New Name"; // compile error!

可以在构造方法中初始化final字段：

class Person {
    public final String name;
    public Person(String name) {
        this.name = name;
    }
}

这种方法更为常用，因为可以保证实例一旦创建，其final字段就不可修改。



## 静态字段和静态方法

class 中定义的字段，被称之为实例字段。实例字段的特点是，每个实例都有独立的字段，各个实例的同名字段互相不影响。

还有一种字段，使用static修饰的字段，称为静态字段：static field。

实例字段在每个实例中都有一个独立“空间”，但是静态字段只有一个共享“空间”，所有的实例都是共享某个字段

class Person{

  public String name;

  public static int number;

}


对于静态字段，无论修改哪个实例的静态字段，效果都是一样的：所有实例的静态字段都被修改了，原因是静态字段并不属于实例：

        ┌──────────────────┐
ming ──▶│Person instance   │
        ├──────────────────┤
        │name = "Xiao Ming"│
        │age = 12          │
        │number ───────────┼──┐    ┌─────────────┐
        └──────────────────┘  │    │Person class │
                              │    ├─────────────┤
                              ├───▶│number = 99  │
        ┌──────────────────┐  │    └─────────────┘
hong ──▶│Person instance   │  │
        ├──────────────────┤  │
        │name = "Xiao Hong"│  │
        │age = 15          │  │
        │number ───────────┼──┘
        └──────────────────┘

实际指向的都是Person class的静态字段。因此不推荐使用 实例变量.静态字段 去访问静态方法。

因为在运行中 实例对下并没有静态字段，而是由于编译器可以根据实例类型自动转换为 类名.静态字段 来访问静态对象。

推荐使用类名访问静态字段，这样可以理解为这个类本身具有字段。

### 静态方法
与静态字段对应，有静态方法。用static修饰的方法--静态方法

调用实例方法必须通过一个实例变量，而调用静态方法则不需要实例变量，通过类名就可以调用。

// static method
public class Main{
  public static void main(String[] args){
    Person.setNumber(99);
    Sout(Person.number);
  }
}

class Person{
  public static int number;

  public static int setNumber(int value){
      number = value;
  }
}

因为静态方法属于class 而不属于实例。因此，静态方法内部，无法访问this变量，也无法访问实例字段，他只能访问静态字段。

通过实例变量也可以调用静态方法，但这只是编译器自动转写为类名调用。

通常情况下，通过实例变量访问静态字段和静态方法，会出现一个编译警告。

静态方法经常用于工具类。例如：

Arrays.sort();
Math.random();

### 接口的静态字段
接口不能定义实例字段，但interface是可以有静态字段的，且静态字段必须为final类型：

public interface Person{
    public static final int MALE = 1;
    public static final int FEMALE = 2;
}

实际上，因为interface的字段只能是public static final类型，所以我们可以把这些修饰符都去掉，上述代码可以简写为：

public interface Person {
    // 编译器会自动加上public static final:
    int MALE = 1;
    int FEMALE = 2;
}

编译器会自动把该字段变为public static final类型。

## 作用域

public、protected、private

### public

定义为public的class、interface可以被其他任何类访问：

package abc;

public class Hello {
    public void hi() {
    }
}

Hello是public 因此可以被其他包的类访问：
package xxx;
class Main{
  void foo(){
    Hello h = new Hello();
  }
}

定义为public 的 field、method可以被其他类访问，前提是首先有访问class的权限

### private

定义为private的field、method无法被其他类访问：

package abc;

public class Hello {
    // 不能被其他类调用:
    private void hi() {
    }

    public void hello() {
        this.hi();
    }
}

实际上，private访问权限被限定在class的内部，而且与方法声明顺序无关。推荐把private方法放在后面，因为public方法定义了对外提供的功能，阅读代码时，应该优先关注public方法


由于JAVA支持嵌套类，如果一个类的内部还定义了一个嵌套类，那么嵌套类拥有访问private的权限：

// private
public class Main {
    public static void main(String[] args) {
        Inner i = new Inner();
        i.hi();
    }

    // private方法:
    private static void hello() {
        System.out.println("private hello!");
    }

    // 静态内部类:
    static class Inner {
        public void hi() {
            Main.hello();
        }
    }
}

定义在一个class内部的class称为嵌套类（nested class）

### protected
protected 作用于继承关系。定义为protected的字段和方法可以被子类访问，以及子类的子类：

package abc;

public class Hello {
    // protected方法:
    protected void hi() {
    }
}

上面的protect方法可以被继承的类访问：

package xyz;

class Main extends Hello {
    void foo() {
        // 可以访问protected方法:
        hi();
    }
}

### package
最后，包作用域是指一个类允许访问同一个package的没有public、private修饰的class，以及没有public、protected、private修饰的字段和方法。

package abc;
// package权限的类:
class Hello {
    // package权限的方法:
    void hi() {
    }
}

只要在同一个包，就可以访问package权限的class、field和method

### 局部变量
在方法内部定义的变量称之为局部变量，局部变量作用域从变量声明处开始到对应的块结束。方法参数也是局部变量。

package abc;

public class Hello {
    void hi(String name) { // 1
        String s = name.toLowerCase(); // 2
        int len = s.length(); // 3
        if (len < 10) { // 4
            int p = 10 - len; // 5
            for (int i=0; i<10; i++) { // 6
                System.out.println(); // 7
            } // 8
        } // 9
    } // 10
}

我们观察上面的hi()方法代码：

方法参数name是局部变量，它的作用域是整个方法，即1 ~ 10；

变量s的作用域是定义处到方法结束，即2 ~ 10；

变量len的作用域是定义处到方法结束，即3 ~ 10；

变量p的作用域是定义处到if块结束，即5 ~ 9；

变量i的作用域是for循环，即6 ~ 8。

使用局部变量时，应该尽可能把局部变量的作用域缩小，尽可能延后声明局部变量。

### final

final与访问权限不冲突，有很多作用。

用final修饰class可以阻止被继承：

package abc;

// 无法被继承:
public final class Hello {
    private int n = 0;
    protected void hi(int t) {
        long i = t;
    }
}

用final 修饰method可以阻止被子类覆写

package abc;

public class Hello {
    // 无法被覆写:
    protected final void hi() {
    }
}

用final修饰field可以阻止被重新赋值：

package abc;
public class Hello{
  private final int n = 0;
  protected void hi(){
    this.n = 1;
  }
}

用final修饰局部变量可以阻止被重新赋值：
package abc;

public class Hello {
    protected void hi(final int t) {
        t = 1; // error!
    }
}

### biji

如果不确定是否需要public，就不声明为public，即尽可能少地暴露对外的字段和方法。

把方法定义为package权限有助于测试，因为测试类和被测试类只要位于同一个package，测试代码就可以访问被测试类的package权限方法。

一个.java文件只能包含一个public类，但可以包含多个非public类。如果有public类，文件名必须和public类的名字相同。

## 内部类

通常情况下，把不同的类组织在不同的包下面，对于一个包下面的类来说，他们是同一层次，没有父子关系。

java.lang
├── Math
├── Runnable
├── String
└── ...

还有一种类，它被定义在另一个类的内部，所以称为内部类（NestedClass）。

Java的内部类分为好几种，通常情况用得不多，但也需要了解

### Inner Class
如果一个类定义在另一个类的内部，这个类就是innerClass：
class Outer {
    class Inner {
        // 定义了一个Inner Class
    }
}

上述定义的Outer是一个普通类，而Inner是一个Inner class，它与普通类有个最大的不同，就是Ineer class的实例不能单独存在，必须依附于一个Outer Class的实例。实例代码如下：

// inner class
public class Main {
    public static void main(String[] args) {
        Outer outer = new Outer("Nested"); // 实例化一个Outer
        Outer.Inner inner = outer.new Inner(); // 实例化一个Inner
        inner.hello();
    }
}

class Outer {
    private String name;

    Outer(String name) {
        this.name = name;
    }

    class Inner {
        void hello() {
            System.out.println("Hello, " + Outer.this.name);
        }
    }
}

观察上述代码，要实例化一个Inner，我们必须要先创建一个Outer的实例，然后调用Outer实例的new来创建Inner实例：

Outer.Inner inner = Outer.new Inner();

这是因为Inner class除了有一个this指向自己，还隐含地持有一个Outer Class实例，可以用Outer.this 访问这个实例。所以实例化一个Inner class不能脱离Outer实例。

Inner Class和普通Class相比，除了能引用Outer实例外，还有一个额外的“特权”，也就是可以修改Outer class的private字段 因为Innerclass的作用域在Outerclass内部，所以能访问Outerclass的private方法和字段。

观察Java编译器编译后的.class 文件可以发现，Outer类被编译为Outer.class,而Inner类被编译为Outer$Inner.class

### Anonymous Class
还有一种定义Inner class的方法，它不需要在Outer class中明确定义这个Class，而是在方法内部，通过匿名类（Anonymous Class）来定义。示例下：

// Anonymous Class
public class Main {
    public static void main(String[] args) {
        Outer outer = new Outer("Nested");
        outer.asyncHello();
    }
}

class Outer {
    private String name;

    Outer(String name) {
        this.name = name;
    }

    void asyncHello() {
        Runnable r = new Runnable() {
            @Override
            public void run() {
                System.out.println("Hello, " + Outer.this.name);
            }
        };
        new Thread(r).start();
    }
}

观察asycHello（）方法 ，我们在内部实例化了一个Runnable。Runnable本身是接口，接口时不能实例化，所以这里实际上是定义了一个实现Runnable接口的匿名类，并通过new实例化该匿名类，转型为Runnable。在定义匿名类的时候就必须实例化它，定义匿名类的写法如下：

Runnable r = new Runnable(){

    // 实现必要的抽象方法...
};

匿名类核Inner class一样 可以访问Outer class的private 字段和方法。之所以我们要定义匿名类，是因为我们在这里通常不关心类名，比直接定义Inner class可以少写很多代码。

观察JAVA编译器编译后的.class 文件可以发现，Outer类被编译为Outer.class 如果有多个匿名类，Java编译器会将每个匿名类依次命名为Outer$1、Outer$2、Outer$3····

除了接口外，匿名类也完全可以继承自普通类。观察一下代码：

// Anonymous Class
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        HashMap<String, String> map1 = new HashMap<>();
        HashMap<String, String> map2 = new HashMap<>() {}; // 匿名类!
        HashMap<String, String> map3 = new HashMap<>() {
            {
                put("A", "1");
                put("B", "2");
            }
        };
        System.out.println(map3.get("A"));
    }
}

map1 是一个普通的HashMap实例，但map2是一个匿名类实例，只是该匿名类继承子HashMap。map3也是继承自一个Hashmap的匿名类实例，并且添加了static 代码块来初始化数据。观察编译输出可发下Main$1.class和Main$2.class两个匿名类文件。

### Static Nested Class

最后一种内部类和Inner class类似，但是使用了static修饰 称为静态内部类（static nested class）：

// Static Nested Class
public class Main {
    public static void main(String[] args) {
        Outer.StaticNested sn = new Outer.StaticNested();
        sn.hello();
    }
}

class Outer {
    private static String NAME = "OUTER";

    private String name;

    Outer(String name) {
        this.name = name;
    }

    static class StaticNested {
        void hello() {
            System.out.println("Hello, " + Outer.NAME);
        }
    }
}

用Static修饰的内部类和Innerclass有很大不同，它不再依附于Outer的实例，而是一个完全独立的类，因此无法引用Outer.this，但它可以访问Outer的private静态字段和静态方法。如果把StaticNested移到Outer之外，就失去了访问private的权限。

## class版本

JDK版本 也就是JVM版本，更准确地说是java.exe程序的版本

低版本可以再高版本上运行 但是高版本不能再低版本运行

但是可以在高版本的环境中指定输出一个兼容低版本的文件

指定编译输出有两种方式，一种是在javac命令行中用参数--release设置：
$javac --release 11 Main.java
参数--release 11表示源码兼容Java 11，编译的class输出版本为Java 11兼容，即class版本55。

第二种方式是用参数--source指定源码版本，用参数--target指定class版本：
$javac --source 9 --target 11 Main.java
上述命令如果使用Java 17的JDK编译，它会把源码视为Java 9兼容版本，并输出class为Java 11兼容版本。注意--release参数和--source --target参数只能二选一，不能同时设置。


## 模块

.class 文件时JVM看到的最小可执行文件，而一个大型程序需要编写很多的class，并生成一堆.class文件，很不便于管理，所以，jar文件就是class文件的容器。

在Java 9 之前，一个大型java程序会生成自己的jar文件，同时引用依赖的第三方jar文件，而JVM自带的java标准库实际也是以jar文件形式存放的，这个文件交rt.jar

如是自己开发的程序，除了自己的app.jar之外，还需要第三方的jar包，运行一个java程序，一般来说

java -cp app.jar:a.jar:b.jar:c.jar com.liaoxuefeng.sample.Main

如果漏写了某个运行时需要用到的jar，那么在运行期极有可能抛出ClassNotFoundException。

所以，jar只是用于存放class的容器，它并不关心class之间的依赖。

从java 9 之后,为了解决依赖的问题 引入module 以.jmod拆分rt.jar

这些.jmod文件每一个都是一个模块，模块名就是文件名。例如：模块java.base对应的文件就是java.base.jmod。

模块之间的依赖关系已经被写入到模块内的module-info.class文件了。

所有的模块都直接或间接地依赖java.base模块，只有java.base模块不依赖任何模块，它可以被看作是“根模块”，好比所有的类都是从Object直接或间接继承而来。

把一堆class封装为jar仅仅是一个打包的过程，而把一堆class封装为模块则不但需要打包，还需要写入依赖关系，并且还可以包含二进制代码（通常是JNI扩展）。

此外，模块支持多版本，即在同一个模块中可以为不同的JVM提供不同的版本。

### 编写模块
首先创建模块和原有创建java项目是完全一样的，以oop-module工程为例，目录结构如下：
oop-module
├── bin
├── build.sh
└── src
    ├── com
    │   └── itranswarp
    │       └── sample
    │           ├── Greeting.java
    │           └── Main.java
    └── module-info.java

  其中，bin目录存放编译后的class文件，src目录存放源码，按包名的目录结构存放，仅仅在src目录下多一个module-info.java这个文件，这就是模块的描述文件。

module hello.world {
	requires java.base; // 可不写，任何模块都会自动引入java.base
	requires java.xml;
}

其中，module是关键字，后面的hello.world是模块名称 它的命名规范与包一致。花括号的requires xxx;表示这个模块需要引用的其他模块名称。

除了java.base可以被自动映入外，这里我们引入了一个java.xml模块。

当我们使用模块声明了依赖关系后，才能使用引入的模块。例如  Main.java 代码如下：

package com.itranswarp.sample;

// 必须引入java.xml模块后才能使用其中的类:
import javax.xml.XMLConstants;

public class Main {
	public static void main(String[] args) {
		Greeting g = new Greeting();
		System.out.println(g.hello(XMLConstants.XML_NS_PREFIX));
	}
}

如果把requires java.xml从module-info中去掉则会报错


































































































































