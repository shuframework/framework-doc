基于jdk8

# 1. 基本语法

程序执行原理：CPU有个指令指示器，指向下一条要执行的指令，要么顺序执行，要么跳转执行。

数组变量和数组元素是两回事，类比 对象变量和对象属性是两回事。即2块内存地址，保存地址的部分分配在栈中，保存实际内容分配在堆中。



堆中的内存是被垃圾回收机制管理的，当没有变量指向对象的时候，Java系统会自动进行垃圾回收，从而释放这块空间。



编码转换改变了字符的二进制内容，但并没有改变字符看上去的样子。

出现乱码的原因：源码与解码编码类型没对上；将源码的编码格式搞错了然后进行转码。如原来是GB18030,被当成了GBK，然后将其转码为UTF-8，解析时用GB18030编码。





# 2. 常用类（常用API）

## String

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









