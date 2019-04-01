

## 1. spring aop能做什么

日志log， 数据库事务，全局异常，数据源动态切换。一般实现是 一个注解+一个拦截器实现

特点是：大量重复的流程

aop将大量重复的流程抽取出来，给默认实现，只用关注改变的地方。这样可以优化代码（代码简单，可维护性高）



## 2. spring aop实现原理

有2种方式 jdk动态代理 和 cglib，默认是动态代理

```
可以通过以下注解强制改为cglib
@EnableAspectJAutoProxy(proxyTargetClass = true)
```

## 2.1 jdk动态代理原理

代理模式 有个代理对象去调用方法，必须基于接口，类似装饰者模式 进行功能增强

编译原理是 修改了java文件 然后翻译为class文件，增强功能是在生成java文件添加的


## 2.2 cglib原理

编译原理是 修改了class文件，基于继承关系







切点的应用

execution(* com.springboot.chapter4.*.printUser( . . )  &&  bean (’ userServiceimpl ’ ) 
表达式中 bean 中定义的字符串代表对 Spring Bean 名称的限定这样就限定具体的类了



## 多个切面的执行顺序（拦截器的执行顺序）

默认是没有顺序的

使用@Order后是 一去一回的形式类似 1before-2before-2after-1after （责任链模式）