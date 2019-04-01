

org.springframework.context.ApplicationContext







## 1. spring aop实现方式

基于javaconfig 



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

