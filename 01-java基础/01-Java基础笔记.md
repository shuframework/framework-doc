基于jdk8

# 1. 基本语法

数组变量和数组元素是两回事，类比 对象变量和对象属性是两回事。即2块内存地址。

程序执行原理：CPU有个指令指示器，指向下一条要执行的指令，要么顺序执行，要么跳转执行。



栈空间没有变量指向堆地址的时候，Java系统会自动进行垃圾回收，从而释放这块空间。





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









