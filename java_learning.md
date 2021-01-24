Java学习笔记
学习计划：本周内学完java基础
1.java执行过程：Hello.java -> Hello.class -> 机器码
		  编译器JDK(包含JVM)	虚拟机JVM

2.JDK包含JRE,JRE包含JVM。一个平台要运行java程序，必须安装JRE。

3.文件名必须和用public修饰的类名相同。

4.标识符命名规则：只有类名是首字母大写，变量名和方法名都遵循驼峰命名法。

5.代码注释：
单行注释 //
多行注释 /* ... */
文档注释 /** ... */

6.类包含属性（变量）和方法（函数）。方法中的变量称为局部变量，方法结束了变量就会被回收。

7.8个基本数据类型：整数4个，小数2个，布尔型，字符型。
整数：byte、short、int、long	小数：float、double	布尔型：boolean		字符型：char
默认值  0     0     0    0L            0.0f   0.0d               false                '\u0000' 
有无符号 有   有    有   有             有     有                  -                      无
长度    8位  16位  32位  64位          32位（有效精度为小数点后8位）   64位（有效精度为小数点后16位）                1位                    16位

字符用'', 字符串用""。L、f、d大小都可以。

8.整型都可以用二进制（0b开头）、八进制（0开头）、十进制、十六进制（0x开头）表示。

9.类型转换：占用内存小的可以自动转为占用内存大的，反之不然。若占用内存大的要转换成占用内存小的，需要强制转换。
byte、short、char进行数值运算时，会自动转换为int。

10.自动类型转换关系图：byte -> short -> int -> long -> float -> double
					^|
					char

11.包装类：将基本数据类型转换为引用数据类型。
Byte、Short、Integer、Long、Float、Double、Boolean、Character
可以通过包装类查看每种基本类型的占用空间（如Integer.SIZE）、最小值（如Integer.MIN_VALUE）、最大值（如Integer.MAX_VALUE）。
例子
Integer in = new Integer(100);
int i = in.intValue();
String s = new String("123");
int n = Integer.parseInt(s); //将字符串转换为整型
String s2 = Integer.toString(n); //将整型转为为字符串

12.String类的实例是一个不可变的对象，意味着对String的操作都会产生一个新的String对象。
例子，String有一个substring（）方法。
String str = "123456";
str.substring(3);
System.out.println(str); //输出123456
String str2 = str.substring(3)
System.out.println(str2); //输出456

13.获取控制台输入 
import java.util.Scanner;
Scanner scanner = new Scanner(System.in);
scanner读取不同的数据：int i = scanner.nextInt();
		       float f = scanner.nextFloat();
		       String str1 = scanner.next(); //读取字符串,字符串以空格或tab键结束
		       String str2 = scanner.nextLine(); //读取完整一行，即用户输入回车键之前的所有输入信息
		  scanner.close();
一个程序里只能有一个scanner。
scanner.readLine()是一个坑，当输入完其他类型的变量后，再输入readLine（）字符串，需要重复写一遍。
例子：
Scanner scanner = new Scanner(System.in);
int i = scanner.nextInt();

String rn = scanner.nextLine(); //一定要有
String s = scanner.nextLine();

scanner.close()


14.逻辑表达式
长路与、短路与（&、&&）  长路或、短路或（|、||）  true/false取反（!）  异或（^）  长路与、长路或一定会把整个表达式执行完，短路与、短路或若遇到前面表达式为false（or true），则不执行后面的表达式。
运算符==和!=适用于所有类型的值和变量。但==和!=作为关系运算符只能比较对象的引用。想要比较两个对象的实际内容，需要调用对象的equals()方法。
+优先级比==、!=都高，输出时用加号连接容易犯错误。
例子
if(str.equals("abcd")){}而不是if(str == "abcd"){}

15.位运算符：& | ~ ^        <<            >>                    >>>
		   异或  正负不变    高位补0或1，正负不变    高位补0，负数变正

16.三目运算符：booleanExpression ? valueWhenTrue : valueWhenFalse
例子， y = x >= 0 ? x : -x;
java整型相除，结果向下取整，依然为整型。
数组是一个固定长度，包含相同类型数据的容器。
访问数组长度：int[] a = new int[5]; System.out.print(a.length);
在数组初始化时赋值：int[] a = new int[]{22, 36, 56};
数组复制：System.arraycopy(src, srcPos, dest, destPos，length);
例子 System.arraycopy(a, 0, b, 3, 5); //数组a从下标0开始，将五个元素复制到数组b，数组b的下标从3开始

Arrays工具类，可以进行 排序，查找，复制填充等功能，大大提高了开发人员的工作效率。
复制。int[] b =Arrays.copyOfRange(int[] a, int from, int to)
// 第一个参数表示源数组
// 第二个参数表示开始位置(取得到)
// 第三个参数表示结束位置(取不到)

转换为字符串。Arrays.toString(int[] array)方法，直接把一个数组，转换为字符串，方便打印。
System.out.println(Arrays.toString(a));

排序,将结果保存在原数组。Arrays.sort(int[] array); 

搜索。使用binarySearch之前，必须先使用sort进行排序。
Arrays.sort(a); int index = Arrays.binarySearch(a, 62); //找出62这个数的索引

判断数组是否相同，返回true或false。boolean flag = Arrays.equals(a, b);

用同一个数填充数组。Arrays.fill(a, 5);

只有Arrays.sort()和Arrays.fill()不需要重新赋值。

17.forEach循环，例子
String[] sentences = {"hello","how are you","I am fine"};
for(String sentence : sentences){
	System.out.println(sentence);
}

18.switch表达式中的数据类型只能是byte、short、int、char、String、enum。

19.方法重载：方法名相同，输入参数不同。仅返回值不同可能造成错误，不能算是方法重载。

20.对象的引用变量和基本数据类型的变量存放在栈中，而对象本身存在堆中。

21.Java是值传递。当实际参数是基本类型的变量时，基本类型变量不会发生改变；当实际参数是引用类型的变量时，由于形参和实参指向同一个对象，方法结束后，对对象的修改将被保留下来。形参和实参指向同一个对象时，令形参为null，实参并不会为null，因为这只是切断了形参和对象的关联。方法结束后，这些变量（无论是基本类型还是引用类型，都存在栈中）会被销毁。

22.初始化块：{...} 会自动插入到每一个构造器中。

23.final修饰符：最终的，不能被修改。优势是高效。
final变量：常量，不能被再次赋值。必须赋初值。
final方法：能被继承，不能被子类重写。
final类：不能被继承。

24.static修饰符：类变量和类方法。
static变量：类变量，无论有多少对象，该变量只有一个，任何对象对该变量进行修改，其他对象的该变量也会跟着变。
static方法：类方法，只能操作类变量，调用类方法，不能引用this或super。

25.字符串格式化 String.format("...",variable)
int age = 24;
String hometown = "东莞";
System.out.println(String.format("我今年%d岁，来自%s",age,hometown));
或者
System.out.format("我今年%d岁，来自%s",age,hometown);

26.字符串操作：
截取：String.substring(beginIndex, endIndex); //返回beginIndex到endIndex-1的子串
      String.trim(); //把字符串前后空格都删除
替换：String.replace(oldChar,newChar); 
      String.replace(CharSequence target,CharSquence replacement); //String是CharSquence的子类，这里可以输入String类型的变量
查找：String.charAt(int index)、String.indexOf(String str, int fromIndex)、String.lastIndexOf(String str, int fromIndex)、String.startsWith(String str, int toffset)、String.endsWith(String str)、String.contains(String str)

27.StringBuffer类似于String，只是StringBuffer表示可变长和可修改的字符串序列，对StringBuffer对象操作时不生成新的对象，而是在原操作对象上进行。
常用方法：append(String str)、insert(int offset, String s)、delete(int start, int end)、replace(int start, int end, String s)、reverse()、toString()。

28.泛型，T,V必须为包装类。
例子
class Point<T,V>{
	private T x;
	private V y;
	public T getX(){return x;}
	public V getY(){return y;}
	public void setX(T x){this.x = x;}
	public void setY(V y){this.y = y;}
}

public class TestPoint{
	public static void main(String[] args){
		Point<Integer,Double> point = new Point<Integer,Double>();
		point.setX(2);
		point.setY(4.2);	
	}
}

29.List和数组的区别是List长度可变。
ArrayList基于数组实现，LinkedList基于链表实现。ArrayList和LinkedList都继承了List接口。
ArrayList的常用操作：add(...)、remove(...)。
常用定义方式：List<Long> ids = new ArrayList<Long>(); 或 List<Long> ids = new ArrayList<>();

30.Map接口的实现类是HashMap，HashMap的常用方法有put(key, value)、get(key)、remove(key)。
常用定义方法：Map<Long,Post> postMap = new HashMap<>();
获取键、值、键值对的集合：keySet()、values()、entrySet()。
遍历HashMap:
for (Map.entry<Long,Post> postEntry: postMap.entrySet()){
	Long id = postEntry.getkey();
	Post post = postEntry.getValue();
	...
}

31.Java的继承是单继承，即一个子类只能有一个父类。子类会继承父类中除构造器外所有的非private方法和变量。继承的关键字是extends。
生成子类对象时，会默认调用父类无参构造器一次。
this(variable); //调用自己具有相同变量的构造器
super(variable); //调用父类具有相同变量的构造器
方法重写：方法名相同，返回值相同，参数表相同。可以通过super.func()调用父类同名方法。

32.接口和抽象类都不能有实例。“有得有失”，抽象类没有实例，但是有抽象方法。抽象方法以;结束。
接口用public或不用修饰符修饰，接口中的方法默认用public修饰，可以不写。接口定义以Interface开头。
继承接口的类必须实现所有的接口中的所有方法。一个类可以继承多个接口，用implements连接。
抽象类可以提供方法的默认实现，接口则不行。
用接口定义变量，引用实现类的对象，使程序更具扩展性。
经验：使用接口、抽象类定义变量，指向实现类的实例。

33.异常处理
throws(系统自动抛出，抛出类)、throw(手动抛出，抛出异常实例)、try(系统自动抛出，抛出类)抛出异常，由catch抓住，finally代码块一定会执行，除非受保护代码块中包含System.exit(0)。一个try可以有多个catch，catch(Exception e)一定放在最后。自动抛出（throws、try）按顺序显示，手动抛出（throw）放最后。

例子
public class ExceptionTest{
	public static void foo() throws Exception{
		int x =5/0;
		System.out.println("x = " + x);	
	}
	public static void main(String[] args){
		try{
			foo(); //发生异常，跳到catch
			System.out.println("foo()运行结果"); //不会执行
		}catch(Exception e){
			e.printStackTrace();
		}finally{
			System.out.println("我会执行");
		}
		System.out.println(""正常执行);
	}
}

34.Java IO。字节流（InputStream、OutputStream抽象类）、字符流（Reader、Writer抽象类）、标准流（System.in、System.out、System.err）。
常见子类	FileInputStream FileOutputStream	   FileReader FileWriter	类型  InputStream PrintStream PrintStream
例子
        OutputStream os = null;
        InputStream is = null;
        try{
            String str = "我是第二名！";
            byte[] bytes = str.getBytes();
            os = new FileOutputStream("bytes.txt",true);
            for (int i = 0; i < bytes.length; i++){
                os.write(bytes[i]);
            }
            is = new FileInputStream("bytes.txt");
            byte[] buff = new byte[18];
            int length = 0;
            //is.read(buff)最多将buff.length个字节读入到buff中，返回类型是读取的字节数
            while ((length = is.read(buff)) != -1){ //当文件读取到末尾时返回-1，循环结束
                System.out.println(new String(buff,0,length));
            }
            //方法二
            System.out.print("方法二");
            is = new FileInputStream("bytes.txt");
            byte[] buff2 = new byte[is.available()];
            is.read(buff2);
            System.out.print(new String(buff2));
        } catch(Exception e){
            e.printStackTrace();
        } finally {
            try{
                os.close();
                is.close();
            }catch(IOException e){
                e.printStackTrace();
            }
        }

容易犯的错误
1.+优先级比==、!=都高，输出时用加号连接容易犯错误，如System.out.println("a == b ?" + a == b)，会判断a == b + a是否与b相等，会输出false。
2.输出char时，会将char转化为对应的ASSCI码，如char c = 65; System.out.println("c = " + c);会输出c = A。

未知
Java反射、多线程



