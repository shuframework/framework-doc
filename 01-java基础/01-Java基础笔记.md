基于jdk8

# 1. 基本语法

数组变量和数组元素是两回事，类比 对象变量和对象属性是两回事。即2块内存地址。



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









