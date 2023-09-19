---
layout: default
title: Java基础
nav_order: 3
permalink: /Java基础
has_children: true
has_toc: false
---

# Java基础





# 《Java核心技术》

## 一、Java特性

### 简单性

### 面向对象

### 可移植性*

java是编译型语言和解释型的混合，初衷是可以适配多个平台。比如java中int永远是32位。

### 网络技能*

java是最先提出并发应对的，因此到后面java的服务端开发占优势。

### 健壮性*

没有c++中的指针，不用担心内存泄漏等。

### 安全性*

提出在沙盒中运行，具有一定的安全性。

### 解释型*

利用解释器讲java解释为字节码，再在JVM中运行。后期即时编译器可以把部分字节码直接翻译为机械码。

## 二、Java程序设计环境

JDK：Java开发工具包。

JRE：运行java程序的用户所需要的软件，只包含虚拟机，即运行环境。

SDK：过时的术语，描述1998-2006期间的JDK。

Javac：Java的编译器，编译语句为：javac Welcome.java，将java文件编译为.class文件。通过java Welcome运行该文件，即启动虚拟机执行类文件的字节码。

JShell：在终端输入jshell，提供一个“读取-计算-打印”的循环程序。

## 三、Java的基本程序设计结构

### Java应用程序

- Java区分大小写，比如main写为Main，编译不通过。
- 源代码文件的文件名必须和公共类的名称相同，一个源文件中只能有一个公共类。
- Java中所有函数都是某个类的方法，Main函数的默认类是shell。

#### main方法

每一个类都可以有一个main方法。可以用此进行独立测试。比如：

```
class Employee{
	public static void main(String[] args){
		// 测试内容
	}
}

// 然后运行java Employee进行测试
```





### 整型

- 整型的范围与Java代码的机器无关，同时Java没有任何无符号（unsigned）形式的int、long等。
- 从Java7开始，可以在数字字面量上加_，比如1_000_000，表示100万。增加易读性。

### 浮点类型

- 没有F后缀的浮点数，默认为double。
- 三个特殊的浮点数：正无穷大、负无穷大、NaN。
- 所有非数值的值都被认为是不同的。

```
if(x == Double.NaN) // is Never true

if(Double.isNaN(x))  // check whether x is "not a number"
```

### char类型

char类型用单括号引起来。

特殊的转义字符表。

#### unicode类型和char类型*

Unicode：不同国际使用不同的编码方法，比如美国ASCII、中国GB 18030和BIG-5（港台）。而Unicode是16位的，统一的世界编码语言。

UTF-16：现在16位的Unicode不能描述全部字符:，UTF-16可以表示所有Unicode码点。

> GBK是包含中日韩的统一编码方法。
>
> 码点：就是Unicode中的一个字的编码。

Char：Java的Char类型是根据UTF-16编码的，但是**不能完全描述Unicode中的值，推荐使用String描述。**

### 枚举类

```
public enum SizeEnum {
    SMALL(0,"S"),
    MEDIUM(1,"M"),
    LARGE(2,"L"),
    EXTRA_LARGE(3,"XL");
    private int Code;
    private String size;

    public int getCode() {
        return Code;
    }
    public String getSize() {
        return size;
    }
    SizeEnum(int code, String m) {
        size = m;
        Code = code;
    }
    public static int finCode(String Size){
        for( SizeEnum instance: SizeEnum.values()){
            if(instance.getSize().equals(Size)){
                return instance.getCode();
            }
        }
        return 0;
    }
}
```

1. Enum是一个类，可以有多个字段，可以有多个方法
2. 构造器一定是Private的
3. 所有枚举类型都是Enum的子类，可以用toString方法：SizeEnum.*EXTRA_LARGE*.toString()



### Boolean类型

整数和bool不能默认转换。

不同c++，Java不存在非0就是true的规则。

### 大数

BigInterger：实现任意精度的整数运算。

BigDecimal：实现任意精度的浮点数运算。

大数类没有运算符重载，使用add、multiply等方法。

> 如果BigDecimal除的商是一个无限循环小数，会报错。

### 变量、常量

#### null

基本类型的变量，有默认值，不可能是null。

### 运算符

“+” 除了运算符外，可以连接字符串。

### 字符串

1.字符串比较：== 和equals不一样，要用equals比较值是不是一样；==判断两个对象的地址。

2.字符串的比较应该为：常量.equals(变量)

3.String.format()，字符串格式化：

![image-20230905162231618](http://img.chenpoop.top/image/202309051622765.png)

### 输入输出

### 不可变类（基本类型）

不可变类：一旦被创建，就不可更改。其本质是在常量池中开辟常量，用引用变量引用。不可变类线程安全。

包括：String、基本类型的封装类、枚举、日期类（LocalDate、LocalTime）、BigDecimal、BigInteger等数值类。

## 四、对象和类

### 面向对象

#### 类

- 封装：把数据和行为组合在一个包里。封装的特性在于只能用对象的方法对数据进行交互，一个类可以修改数据的存储方法，而对其他对象没有影响。

- 继承：在一个类的基础上（有该类的全部方法和属性），拓展新的方法和属性。

  > 不要返回有更改器的对象。比如一个类的通过get方法，返回Date hireday字段。但是Date类型可以进行setTime修改。
  >
  > 如果一定要这样，使用clone()方法，返回一个克隆对象。

类和类之间的关系：

- 依赖（uses-a）：A类中的函数参数中有B类。
- 聚合（has-a）：A类中包含B类。
- 继承（is-a）：A类继承B类。

### 对象*

对象：

对象变量：对象变量没有包含一个变量，而是引用一个变量。类似C++中的指针。new 操作返回的也是一个引用，比如Date deadline = new Date()，是先new一个Date()，构造了一个对象，返回该对象的引用，然后定义一个变量Date deadline，用于存储该引用。

栈：里面放的是对象的引用、基本类型值。

堆：里面是实例出来的对象。

![image-20230808151658394](http://img.chenpoop.top/image/202308081516502.png)

### 预定义类

预定义类：不具备面向对象特性的Java类库（第三方类）中定义好的类，比如Math、Date等。

LocalDate类：相比Date，localDate是线程安全的。

#### 更改器和访问器方法

访问器方法：只访问对象，不修改对象。如有返回值，就返回一个新的对象，比如String.toUpperCase()，返回一个新的字符串，原字符串不变。

变更器方法：直接修改对象。比如日历类GreorianCalendar的add()方法。

### 类

#### 多源文件编译

可以用javac Employee*.java编译开头的文件。

在编译文件时，发现依赖其他文件，会自动编译所依赖的源文件。

#### 构造器

```
public class Employee{
	private String name;
	......
}

public Employee(String n,double s,...){
	String name = n;  // ERROR
	double salary = s;  // ERROR
}
```

构造器里的局部变量name，和该类的name**字段同名，会屏蔽覆盖**，导致字段赋值失败。

#### 隐式参数和显式参数

隐式参数：this，默认每个类的方法都有这个参数。

显式参数：括号里的参数。

#### final*

final修饰符：用于修饰字段是，字段只能被初始化一次，之后不再改变。

线程安全：final的线程安全时：**只有一个不可变类的对象被正确的构造出来后，就是线程安全的**。所以在构造过程中是线程不安全的。

#### Static*

静态方法：静态方法是没有隐式参数this的方法，不能在对象上执行操作。静态方法主要的使用场景：

- 方法不需要访问对象的状态。
- 方法只需要访问类的静态字段。

静态字段：有100个Employee类，则有100个id字段，但是**共享**一个nextId字段。即静态字段属于类，不属于对象。不一定线程安全。

```
class Employee{
	private static int nextId = 1;
	private int id;
	......
}
```

尽量不要用静态变量，应用静态常量，比如：

```
public class Math{
	public static final double PI = 3.14;
}
```

#### 深拷贝、浅拷贝

浅拷贝：不同引用，同一对象。

深拷贝：拷贝不同对象，同时生成不同引用。

### 方法参数

#### 按值调用、按引用调用*

按值调用：接收调用者的值。**Java总是按值调用的，传递的参数是一个副本。**

```
public static void tripleSalary(Employee x) // works
{
	x.raiseSalary(200);
}
harry = new Employee(...);
tripleSalary(harry);
```

具体的执行过程为，如图：

1.x初始化为 harry 值的一个副本，这里就是一个对象引用。
2.raiseSalary方法应用于这个对象引用。x和harry 同时引用的那个 Employee 对象的工资提高了200%。
3.方法结束后，参数变量x不再使用。当然，对象变量 harry 继续引用那个工资增至3倍的员工对象。

![image-20230810103510914](http://img.chenpoop.top/image/202308101035089.png)

按引用调用：接收调用者的引用。比如，以下代码是不能实现交换的：

```
public static void swap(Employee X, Employee y) // doesn't work{
	Employee temp = X;
	X=y;
	y = temp;
}
// 如果 Java 对对象采用的是按引用调用，那么这个方法就应该能够实现交换:
var a= new Employee("Alice",...);
var b = new Employee("Bob",...);
swap(a,b);
// 但实际上，这个方法交换的是两个副本。
```

#### 参数数量可变

```
public static double max(double... values){
	double largest = Double.Negative_infinity;
	for(double v : values) if(v > largest) largest = v;
	return largest;
}
```

...表示可以接收任意参数的对象。



### 对象构造

#### 重载

java的构造函数重载，是**以方法名、参数类型确定的**。也就是说，不能有两个名字相同、参数类型相同，当时返回值不同的构造函数，这会导致无法确定具体哪个构造函数。

#### 默认构造器

**仅当没有其他构造器时，默认会提供一个无参数的构造器**，赋值为默认值：数值为0、布尔为false、对象引用为null。如果至少有一个构造器，但是没有提供无参构造器，则不提供参数是非法的。比如：

```
public Employee(String n, double s, int year, int month, int day);
// 对于这个类，构造默认的员工就是不合法的。也就是说，调用以下
e= new Employee();
// 将会产生错误。
```

#### 构造器

java的构造器可以调用同类的另一个构造器。

### 包

包是为了将自己和别人的代码库进行分开管理，为了保证包名的唯一性，Java**采用域名的方式作为包名**。同时是逆序的形式。比如com.horstman.corejava。

#### import

通过import导入包下的类。*表示这个包下的所有类。

```
import java.util.*;
```

如果类名相同出现冲突情况，可以加上具体的类名来区别。

#### package

package表示把这个类放进对应的包中，如果没有写package，则放进一个默认的无名包里。**package包相当于类的逻辑集合**。

```
package com.horstman.corejava;

public class Employee{
	...
}
```

包不是封闭的实体，可能被第三方利用，往包里添加其他类。

#### Jar包

jar包就是把相关文件、文件夹进行归档压损为.jar文件。创建命令：

```
jav cvf jar包名称 文件1 文件2/目录
```

jar包中有个MANIFEST.MF文件，包括一些文件信息。

jar包可以根据不同的java版本的类。

#### JavaDoc

javadoc用于描述类或者方法的作用，由源文件自动生成一个HTML。

## 五、继承

父类、子类：继承用**extends**表示继承：

```
public class Manager extends Employee{
	...
}
```

子类覆盖父类字段，使用super调用父类字段。如果忽略super，会导致子类自己调用自己，最终奔溃。**super表示父类的**，也可以调用super的构造器。

```
public double getSalary{
	double baseSalary = super.getSalary();
	return baseSalaty + bouns;
}
```

Java支持单一继承

### 多态

java的多态包括：父子类的继承、方法的重写。即出现父类对象的任意地方都可以用子类对象替换。

不能将父类的引用赋值给子类变量。

```
// 出现父类对象的任意地方都可以用子类对象替换
Employee e;
e = new Employee();
e = new Manager();
```

### 阻止继承 Final

final：用于修饰类、方法时，说明该类、方法不能被继承！

### 抽象 abstract

1. 一个类被abstract修饰，这个类被称为抽象类；一个方法被abstract修饰，这个方法被称为抽象方法。抽象方法不用给出具体的实现
2. 抽象类不能实例化对象
3. 抽象方法不能被private、final和static修饰，因为抽象类要被子类实现
4. 抽象类有两种：子类中有部分抽象方法没有被定义，则一定要用abstract修饰子类；全部被定义，则不用
5. 要想使用抽象类，只能创建该抽象类的子类，然后让子类重写抽象类中的方法

### 受保护的 protected

 1.对本包和所有子类可访问

 2.本包指的是同一文件

### 所有的超类 Object

#### clone()

![image-20230905154226380](http://img.chenpoop.top/image/202309051542527.png)

clone()采用浅拷贝，比如house2=house1.clone()，浅拷贝会其他基本类型的值都复制过去；但是如果是引用类型，则复制的是引用。

#### equal()

equal()的判断是==，即如果是基本类型，判断值；如果是引用类型，判断地址。

#### hasCode()

返回的是对象的内存地址的整数表示。

### 泛型列表ArrayList

ArrayList：动态数组

1. 动态扩容：执行Add、AddRange、Insert、InsertRange等添加元素的方法，都会检查内部数组的容量是否不够了，如果是，它就会以当前容量的两倍来重新构建一个数组，将旧元素Copy到新数组中，然后丢弃旧数组。消耗性能。

### 包装器和拆箱、装箱

#### 包装器

为了把基础类型包装到变量中

![image-20230905160949537](http://img.chenpoop.top/image/202309051609614.png)

#### 拆箱、装箱

```
var list = new ArrayList<Integer>();
// 装箱，把int转换为Integer
list.add(3);
// 拆箱，把Integer转换为int
int n = list.get(0);
```

1. 拆箱和装箱是编译器的工作，并不是虚拟机的。

反射

## JavaWeb

### Servlet主要思想

![image-20230911105454840](http://img.chenpoop.top/image/202309111054975.png)

### servlet生命周期

![image-20230911141046322](http://img.chenpoop.top/image/202309111410408.png)

过滤器Filter：对请求或者响应进行过滤处理，可以用于校验等。

监听器Listener：对一些对象的生命周期或者执行过程进行监听，比如session、request等。

### JSP

- Jsp全称Java Server Pages，顾名思义就是运行在java服务器中的页面。由Sun 公司专门为了解决动态生成HTML文档的技术。

- Jsp能够以HTML页面的方式呈现数据，是一个可以嵌入Java代码的HTML。

- 其本质是当tomcat运行JSP时，先把JSP解析为一个servlet文件（解析出来的文件在tomcat的work文件夹下），把jsp中html部分。

  <%%>：在jsp中写java代码。

  <%=%>：将数据显示到页面，如同out.println

## SSM

SSM：即Spring、Spring MVC、mybatis

分为四层：

持久层：DAO层，使用mybatis进行数据库交互。

业务层：Service层，使用Spring进行业务处理。

表现层：控制层，Spring MVC，接口入口，调用业务层。

视图层：View层，使用前端架构或者jsp。

### Spring

### spring mvc

注解：

@RequestMapping：提供路由信息，将HTTP请求映射到对应函数。

@RestController：控制器注解，说明将响应结果直接返回客户端。

### Mybatis

mybatis和JDBC

1. mybatis基于JDBC，Java和数据库操作只能通过JDBC。
2. JDBC每次都要用connection，statement来操作数据库，比较繁琐。mybatis自动生成连接。
3. mybatis实现了ORM（对象关系映射），可以通过xml、注解的方法实现实体类和数据库列的映射。

注解：





## Springboot

springboot采用约定大于配置思想，简化spring的xml配置为注解。

springboot有自带的tomcat服务器。

对于使用了 `@ComponentScan`, `@ConfigurationPropertiesScan`, `@EntityScan` 或者 `@SpringBootApplication` 注解的Spring Boot程序，应该避免使用default包。

`@Entity` 类只有定义在启动类的子包下才能被扫描加载到。

spring-boot-devtools会在classpath上的文件发生变化时自动重启。





# 《Spring实战》

### 注解

@Component：将类标记为Spring组件。

@componentScan:默认扫描位于这个包以及子包下的component的注解，注入为bean。

@autowired：装配bean，可以用于属性和方法的注解。方法的话尝试装配。

第三方库的组件不能通过@Component和@autowired进行自动化装配，因此只能显式装配。





@Bean：通过这个方法，产生一个实例。引用第三方的类库，只能用Bean。

Starter是一系列开箱即用的依赖。

classpath：编译后的classes文件下的文件路径。



## 类和对象



## Java集合

接口：Collection、Map、Iterator

![image-20230728151834667](http://img.chenpoop.top/image/202307281518788.png)

实现类有：List、Set、Map

List：有序的，可重复的

Set：无顺序的，不可重复

Map：不可重复，无序的

泛型<>不能使用基本类型，所以是各基本类型的包装类

### List

ArrayList：基于数组，随机访问性能好

LinkedLIst：基于链表，插入删除性能好

### Set

迭代器：hasNext、Next方法

Set：hashSet、TreeSet

### Map

HashMap：哈希表，便于插入删除

TreeMap：红黑树，便于排序

### 线程安全

多线程进行集合操作是否会出问题

vector线程安全

ArrayList、LinkedList、HashMap、TreeMap都不是线程安全的

### 常用方法

comparable：比较方法

sort：升序

reverse：反转

min、max

### 多线程

线程是系统最小单元

同一进程下线程共享资源

使用场景：

tomcat内部采用多线程

后台任务

异步处理



实现方法：继承Thread、Runable接口

互斥和同步



synchronized

### 排序

Comparable ：单一的排序方法

Comparator ：可以定义多种排序方法

# IDEA快捷键

Getter和Setter方法的快捷键：右键greater



# 其他

## MAVEN

Maven是为JAVA项目提供管理和构建的工具。

### 项目结构

![image-20230915151456198](http://img.chenpoop.top/image/202309151514301.png)

maven的pom主要为：

```
<project ...>
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.itranswarp.learnjava</groupId>
	<artifactId>hello</artifactId>
	<version>1.0</version>
	<packaging>jar</packaging>
	<properties>
        ...
	</properties>
	<dependencies>
        <dependency>
            <groupId>commons-logging</groupId>
            <artifactId>commons-logging</artifactId>
            <version>1.2</version>
        </dependency>
	</dependencies>
</project>
```

maven通过groupId，artifactId和version确定唯一的第三方包。groupId是组织，artifactId是包名，version是版本。

使用`<dependency>`声明一个依赖后，Maven就会自动下载这个依赖包并把它放到classpath中。

### 依赖

maven解决了jar包复杂依赖关系的问题，同时提供了几种包的依赖scope：

![image-20230915152010040](http://img.chenpoop.top/image/202309151520118.png)

#### Maven镜像

可以在用户的.m2目录下，setting.xml中配置文件，设置镜像信息。

```
<settings>
    <mirrors>
        <mirror>
            <id>aliyun</id>
            <name>aliyun</name>
            <mirrorOf>central</mirrorOf>
            <!-- 国内推荐阿里云的Maven镜像 -->
            <url>https://maven.aliyun.com/repository/central</url>
        </mirror>
    </mirrors>
</settings>
```

### 构建

maven的构建分为：lifecycle、phase和goal。分别对应生命周期，步骤，步骤中的方法。lifecycle中由多个phase组成，phase由多个goal组成。goal是最小任务单位。

goal类似于：tomcat:run

maven的phase是从开始，执行到某一phase为止。比如clear，就是从开始到clear执行完成为止。

### 插件

maven的phase其实是通过插件实现了，maven去找对应名称的插件，并执行。可以使用自定义插件，在package周期中添加插件。

```
<project>
    ...
	<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-shade-plugin</artifactId>
                <version>3.2.1</version>
				<executions>
					<execution>
						<phase>package</phase>
						<goals>
							<goal>shade</goal>
						</goals>
						<configuration>
                            ...
						</configuration>
					</execution>
				</executions>
			</plugin>
		</plugins>
	</build>
</project>
```

### 模块管理

maven可以把多个项目通过模块进行管理。其中parent的pom部分表示子pom中有相同的依赖或者属性。

模块和模块之间也可以通过dependency进行依赖管理。

### mvnw

mvnw：是为了让项目选择指定的maven版本，而不是系统版本。

```
-- 下载指定的mvnw
mvn -N io.takari:maven:0.7.6:wrapper
```

然后这个项目的mvn指令都用mvnw。