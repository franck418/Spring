# Spring 

标签（空格分隔）： spring aop di ioc 依赖注入 面向切面

 
#### 一.了解Spring
    Q：什么是spring？
    A：spring是一个轻量级java开发框架。已经成为j2ee的业界开发标准了。现在已经发展为spring的一个生态系统了。为了更方便，更快捷地进行企业应用开发
       
    
    Q：为什么要用spring？spring带来什么好处？
    A：最终达到的目的是：更简单，更快速地开发强大的JAVA应用程序！  
       通过解耦；使用配置文件的方式来管理对象与对象之间的依赖关系
        1. 轻量级，代码污染率（侵入率）低；开发的时候，程序代码并不依赖spring的类。
        2. 扩展性强，可以与绝大多数的框架无缝整合。
        3. 源代码本身就是一份可以深入研究的绝好资料
        4. spring 编写的程序容易测试
        5. 强制使用接口编程，有利于养成良好的编程习惯
        6. **将多种技术的异常(hibernate jdbc)翻译成一致的** 没用过
        

    
    Q:spring用于哪些程序？
    A：
    
    Q：spring的架构是怎么样的？
    A：
    
    Q：spring的核心有哪些？如何使用？
    A：

#### 二.Spring容器
    Q:什么是Spring容器？有什么用？
    A:Spring容器是spring的核心，控制和管理所有bean。实现DI和IOC
 
    Q:有哪些容器，怎么使用？
    A:BeanFactory , ApplicationContext
 
    ApplicationContext 是BeanFactory的更高级的实现。
    一些轻量级的，小的应用程序里面可以使用BeanFactory,一般使用ApplicationContext。
    这两个都是接口，这两个接口下面都有相关的实现.
    
    BeanFactory
    是最简单的容器，提供了DI支持
    常用的实现：XmlBeanFactory
    
    ApplicationContext
    常用的实现：
    FileSystemXmlApplicationContext  需要提供配置文件的完整路径
    ClassPathXmlApplicationContext   提供配置文件的CLASSPATH下的路径
    WebXmlApplicationContext         会在WEB应用范围内加载配置文件
    
#### 三.Bean
    Q:Bean是什么？有什么用?
    A:
    
    Q:
    A:
    
    Bean的作用域
    bean的作用于都是基于本个容器的
    编辑bean的时候，可以使用scope来指定bean的作用域，
    例：<bean id="msg" class="xxx.xxx.xx" scope="singleton" ></bean>


|作用域	|描述
| --------   | -----:  | 
| singleton  | 将bean的定义限制为一个springIoc容器只存在一个，即单例(默认) | 
| prototype  | 每次使用bean的时候都会新建   |   


#### 1. Bean的生命周期

Q:Bean的生命周期有哪些?是怎么样的？
A:Bean的生命周期主要有2个时间点，1初始化的时候，2销毁的时候；（其他周期后续深入研究）

Q:怎么进行初始化和销毁？
A:初始化和销毁都可以通过2种方法来实现
1 初始化直接在Bean实现InitailazingBean接口；销毁直接在Bean实现DestroyAble接口
2 在配置文件内使用 init-method 和 destroy-method 来指定初始化和销毁方法。

Q:两种指定初始化和销毁方法的方式，有哪些区别?
A:



如果多个bean有相同的初始化和销毁方法， 可以使用default-init-method和default-destroy-method来指定；
如下：

``` xml
 <?xml version="1.0" encoding="UTF-8"?>
 
 <beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd"

       default-init-method="init"
       default-destroy-method="destroy"
 >
 </beans>
```

    
    
#### 2. Bean的后置处理器(这个还是一个比较模糊的概念，认识不够深入和清晰)
Q：Bean后置处理器是什么？有什么用？
A：可以在bean初始化前后调用某些特定的方法进行bean的操作

Q: 为什么要有Bean后置处理器？
A:提供更加完善的bean的操作和控制

Q: Bean处理器怎么使用？
A: 实现BeanPostProcessor接口。。。。。




####3. Bean定义继承

Q:Bean的继承和java类的继承的关系？
A:Bean定义的继承和java类的继承没有关系，但概念是一样的。通过使用继承，子bean可以继承父bean的配置。

Q:Bean怎么定义继承？
A:通过指定bean的parent属性值来指定bean的父bean
```
    <beans>
        <bean id='parentBean' class='xxx.xxx.xxx' > </bean> 这里是父bean的定义
        <bean id='sonBean' class='xxx.xxx.xxx' parent='parentBean'> </bean>  通过指定parent属性来指定sonBean的配置继承自parentBean
    </beans>
```

另外还可以定义一个bean模板来让各个bean继承，模板不能指定class，并且abstract=true
```
    <beans>
        <bean id="tempBean" abstract="true"><property name="xx" value="xx"></property></bean>
        <bean id="sonBean" parent="tempBean"></bean>
    </beans>
```
模板只能被继承，充当抽象类使用

## 四.依赖注入 ##
#### 1.DI , IOC
    什么是DI，什么是IOC？
    为什么要使用，有什么好处？
    如何使用？
    spring是怎么实现的？


## 五.面向切面编程 ##
#### .AOP ####
    什么是AOP？
    为什么要使用，有什么好处？
    如何使用？
    spring是怎么实现的？



 
 

