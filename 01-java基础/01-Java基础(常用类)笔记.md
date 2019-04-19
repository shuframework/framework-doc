基于jdk8

# 1. 基本语法

程序执行原理：CPU有个指令指示器，指向下一条要执行的指令，要么顺序执行，要么跳转执行。

数组变量和数组元素是两回事，类比 对象变量和对象属性是两回事。即2块内存地址，保存地址的部分分配在栈中，保存实际内容分配在堆中。

堆中的内存是被垃圾回收机制管理的，当没有变量指向对象的时候，Java系统会自动进行垃圾回收，从而释放这块空间。

栈存放函数的局部变量，堆存放动态分配的对象，内存区(方法区)存放类的信息，



编码转换改变了字符的二进制内容，但并没有改变字符看上去的样子。

出现乱码的原因：源码与解码编码类型没对上；将源码的编码格式搞错了然后进行转码。如原来是GB18030,被当成了GBK，然后将其转码为UTF-8，解析时用GB18030编码。





# 2. 常用类（常用API）

## 1. StringUtil工具类

**String 、StringBuild、StringBuffer都用final 修饰了，即不可变性、不可继承**

String 的常用方法有  equals，charAt，indexOf，substring，contains，startsWith，endsWith，toLowerCase，toUpperCase，replace，trim，compareTo

### 1.1 获得后缀

String getSuffix(String str)
String getSuffixHasPoint(String str)

### 1.2 重命名

String getNewFileName(String oldFileName)   放在SystemUtil类了，因为需要日期戳配合String 

```
添加/移除 前缀或后缀
String renameByAdd(String oldFileName, String addName, String type)
String renameByRemove(String oldFileName, String removeName, String type)
```

### 1.3 拼接或连接字符串

```
String append(String... str)
String appendHasTrim(String... str)
```

```
String join(final Object[] array)
String join(final Object[] array, String separator)
String join(final Object[] array, String separator, int startIndex, int endIndex)
String join(final Collection<?> collection)
String join(final Collection<?> collection, final String separator)
```

### 1.4 处理空

boolean isEmpty(String str) 判断是否为null或空串（去空格了），是返回 true

String parseEmpty(String str, String num)	转换空串

### 1.5 单词处理

```
String capitalize(String str)	首字母大写,其它字母不变
String capitalizeFully(String str)  首字母大写,其它字母小写
String capitalizeFully(String str, final char... delimiters) 
String uncapitalize(String str)	首字母小写,其它字母不变
String uncapitalize(Class<?> clazz)
```

### 1.6 其他

String fillLeftZero(int num, int length)	对数字补零



## 2. BigDecimalUtil工具类

小数计算  加（add）， 减（subtract）， 乘（multiply）， 除（divide）



## 3. DateUtil工具类

### 3.1 获得年，月，日等信息

```
int getYear(Date date)
int getMonth(Date date)
int getDayOfMonth(Date date)	获取日期的天数(月份的第几天)
int getDayOfYear(Date date)		年份的第几天
int getMaxDaysOfMonth(Date date)  该月最大天数
int getWeek(Date date)	
int getWeek2Zh(Date date)
boolean isWeekend(Date date) 
int getWeekOfYear(Date date)
int getWeekOfYear2Zh(Date date)
```

### 3.2 年，月，日 加减

addXX

### 3.3 获得开始，结束时间

```
Date getStartTime()
Date getStartTime(Date date)
Date getStartTime(Date date, int addDays)
Date getEndTime()
Date getEndTime(Date date)
Date getEndTime(Date date, int addDays)
Date getFirstDayOfWeek2zh(Date date)
Date getFirstDayOfYear(Date date)

Date getFirstDayOfMonth(Date date)
Date getFirstDayOfMonth(Date date, int specifiedMonth)
Date getFirstDayOfMonth(int specifiedMonth)
Date getLastDayOfMonth(Date date)
Date getLastDayOfMonth(int specifiedMonth)
```



## 包装类

包装类中的数值类型都继承 java.lang.Number

不可变性 都用final 修饰了，即不能被继承。

设计为 不可变的类 是为了防止数据意外被串改，以及多线程环境下安全。

包装类的 valueOf() 方法有缓存值，建议使用该方法创建，这样共享的设计模式是 享元模式。

