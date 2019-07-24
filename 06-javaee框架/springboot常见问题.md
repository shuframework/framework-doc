

## 关于springmvc时request的getReader()和getInputStream()只能调用一次的解决办法

链接 <https://www.cnblogs.com/ocean-sky/p/6899613.html>

原理是重写，缓存body的值



## IDEA启动Springboot时，解决报错 “java.lang.NoClassDefFoundError: javax/servlet/Filter”

如下所示，将spring-boot-starter-tomcat依赖中的<scope>provided</scope>注释掉

<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-tomcat</artifactId>
   <!--<scope>provided</scope>-->
</dependency>

或者设置idea 启动时，支持provided 环境

![1558947138127](..\imgmd\1558947138127.png)