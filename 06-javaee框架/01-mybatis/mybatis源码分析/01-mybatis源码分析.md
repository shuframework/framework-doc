mybatis源码 4大对象

```
SqlSession	SqlSessionFactory 入口
Executor			sql执行器
StatementHandler	sql解析（对sql的预处理）
ParameterHandler	拼接参数
ResultSetHandler	处理返回结果
```



 mybatis3.4支持日期 



## 1. mybatis源码分析

## 1.1 过程加载





## 1. mybatisplus启动注入sql原理

xml中不配置crud的sql也能实现功能的`原因是` 项目启动时自动注入sql， 调用执行时通过动态代理 执行了相应的方法对应的sql。

表象分析
```
1. SysUserMapper 的本质 org.apache.ibatis.binding.MapperProxy（代理对象）
2. MapperProxy 中 sqlSession –> SqlSessionFactory
3. SqlSessionFacotry 中 Configuration -> MappedStatements
  每一个 mappedStatement都表示 Mapper接口中的一个方法与 Mapper映射文件中的一个SQL。MP 在启动就会挨个分析 xxxMapper中的方法，并且将对应的SQL语句处理好，保存到 configuration 对象中的 mappedStatements 中
```

本质是 通过 MapperBuilderAssistant 将每一个 mappedStatement添加到 configuration 中的 mappedstatements 中
```
Configuration： MyBatis 或者 MP 全局配置对象；

MappedStatement：一个 MappedStatement 对象对应 Mapper 配置文件中的一个
select/update/insert/delete 节点，主要描述的是一条 SQL 语句；

SqlMethod : 枚举对象 ，MP 支持的 SQL 方法；
TableInfo：数据库表反射信息 ，可以获取到数据库表相关的信息；
SqlSource: SQL 语句处理对象；
MapperBuilderAssistant： 用于缓存、SQL 参数、查询方剂结果集处理等；
```



## 2. 插件机制

## 2.1 分页插件

mybatis-plus 的一个分页插件
com.baomidou.mybatisplus.plugins.PaginationInterceptor

（实现原理类似MyBatisPagePlugin.java）其原理是 implements org.apache.ibatis.plugin.Interceptor  拦截了sql，然后计算 count，拼接分页语句


## 2.1 乐观锁插件

mybatis-plus 的一个乐观锁插件
com.baomidou.mybatisplus.plugins.OptimisticLockerInterceptor

乐观锁的实现原理:
    取出记录时，获取当前 version 2 
    更新时，带上这个 version 2 
    执行更新时， set version = yourVersion+1 where version = yourVersion
    如果 version 不对，就更新失败



