---

layout: wiki

title: My Resume 2023

cate1: Tools

cate2: Editor

description: My Resume 2023

keywords: Resume

---

# Interview_Java_总结篇



### 资产监控项目

#### 产品亮点

CMDB配置资源管理亮点：

* 使用Redis作为缓存，减小数据库访问压力。
* Elasticsearch作为搜索引擎搭建搜索平台，支持对所有字段的搜索。
* 使用Kafka作为消息队列，来减小服务间耦合，填谷削峰。
* 资源采集和监控
* 自定义模型模版管理
* 资源关系topo，资源间关系的处理
* 资源权限管理、多租户管理
* 资源告警规则配置，资源变更通知
* 资源变更操作历史
*
* Eureka作为注册中心，Feign远程调用，Apollo作为配置中心
* 对标蓝鲸监控、Prometheus
* 前后端分离VUE

* CMSB-SDK，提供第三方集成工具SDK

*

低效无效资产清理：

IP地址管理：



#### 项目难点：

* 数据量大，使用Kafka作为消息队列。

* 数据量大，业务处理慢：
    * 优化业务逻辑，减少查询数据库，改为查询redis和es
    * 多线程处理
    * 增加ehcache缓存
    * 合并kafka消息
    *





#### 工作成就

解决OOM问题：

* 查询数据量过大，未分页导致OOM（查询资产名称，使用List接收，数据量大时导致OOM）
*

优化数据库查询：

* 联表查询，CQL查询数据量过大，增加查询条件
* CQL未使用索引，新建索引解决

提升系统整体性能

提高吞吐量

提高系统稳定性





### Interview

#### 面试真题

Redis可以用来做什么用：唯一ID、乐观锁

JMM：内存模型

Voltain关键字：共享变量可见性，有序性，禁之指令重排。

OOM、STW

内存泄漏

IO密集

abccba访问判断



网管gateway拦截器

Controller是单例？

Mysql慢查询排查过吗？



feign调用涉及到哪些注解？

多线程如何异步回调获取结果？

[Redis实现分布式锁？](#Redis实现分布式锁？)

Redis配置RDB和AOF命令

kafka如何保证消息有序？

集合中数据去重？

HAVING 和 GROUP BY区别？子查询需要 AS subQuery。

MyBatis原理和流程？

Docker常用命令？

MyBatis：

* #和$区别
* 一级二级缓存
* 分页方式有哪几种

Spring Bean注入方式

Java8新特性

Stream常用方法

如何对集合排序？如何使用stream对集合排序？

Spring 中 @Transaction 原理？

Equals 和 Hash，项目使用到重写Equals了吗？



了解和使用过反射吗？：扩展程序热加载Class文件

MyBatis中引用对象如何查询，如何映射到对象上？多对多关系如何映射的？

GateWay登录流程？

Kafka多副本机制，以及可能存在的问题？

Kafka自动提交和手动提交有什么区别？

Sentinel限流是怎么处理的？

MyBatis使用的基本步骤？

实际使用的代码自动生成工具？



##### Java

线程池核心线程数根据什么配置？

[Synchronized 修饰普通方法和静态方法有什么区别？](#Synchronized 修饰普通方法和静态方法有什么区别？)

[Java创建内部类的方式？](#Java创建内部类的方式？)



[synchronized和ReentrantLock有什么区别呢？](#synchronized和ReentrantLock有什么区别呢？)

[线程生命周期的不同状态？](#线程生命周期的不同状态？)

[什么情况下Java程序会产生死锁？如何定位、修复？](#什么情况下Java程序会产生死锁？如何定位、修复？)

[Java并发包提供了哪些并发工具类？](#Java并发包提供了哪些并发工具类？)

[为什么用线程池？解释下线程池参数？](#为什么用线程池？解释下线程池参数？)

[请介绍类加载过程，什么是双亲委派模型？](#请介绍类加载过程，什么是双亲委派模型？)

[谈谈JVM内存区域的划分，哪些区域可能发生OutOfMemoryError](#谈谈JVM内存区域的划分，哪些区域可能发生OutOfMemoryError)

[性能问题：内存持续上升，我该如何排查问题？](#性能问题：内存持续上升，我该如何排查问题？)





##### 设计模式与算法

[用到过哪些设计模式？](#用到过哪些设计模式？)





##### Spring

[@Transaction事务隔离级别传播特性，在项目中实际？](#@Transaction事务隔离级别传播特性，在项目中实际？)

[SpringBoot在项目中都使用到哪些注解？](#SpringBoot在项目中都使用到哪些注解？)

微服务化时如何对服务进行拆分？

SpringCloud各个组件使用过吗？

[Spring 中用到的设计模式有哪些？](#Spring 中用到的设计模式有哪些？)

[文件上传下载@注解是什么？](#文件上传下载@注解是什么？)

[Spring的基础机制IOC和AOP](#Spring的基础机制IOC和AOP)



##### 组件

[Eureka的CAP特性，服务宕机了怎么办？](#Eureka的CAP特性，服务宕机了怎么办？)

[Redis实际使用到哪些数据结构？](#Redis实际使用到哪些数据结构？)

[Redis与MySQL双写一致性如何保证？](#Redis与MySQL双写一致性如何保证？)

[ES常用关键字 match match_all，ES内置分词器？](#ES常用关键字 match match_all，ES内置分词器？)



##### MySQL

[MySQL组合索引的使用规则？](#MySQL组合索引的使用规则？)



[MySQL支持的事务隔离级别](#**MySQL支持的事务隔离级别**)



MySQL左外链接Left Join On，JOIN默认是内连接还是外链接？

查询总分大于100的学生和每一科都超过60分的学生





### MySQL 索引模型

InnoDB 使用了 B+ 树索引模型。



聚簇索引（clustered index）：主键索引的叶子节点存的是整行数据。在 InnoDB 里，主键索引也被称为聚簇索引（clustered index）。

二级索引（secondary index）：非主键索引的叶子节点内容是主键的值。在 InnoDB 里，非主键索引也被称为二级索引（secondary index）。



普通索引查询方式需要回表。



索引优化，如何避免回表?

* 覆盖索引可以减少树的搜索次数，显著提升查询性能



[04 深入浅出索引（上）](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/MySQL%E5%AE%9E%E6%88%9845%E8%AE%B2/04%20%20%E6%B7%B1%E5%85%A5%E6%B5%85%E5%87%BA%E7%B4%A2%E5%BC%95%EF%BC%88%E4%B8%8A%EF%BC%89.md)

[05 深入浅出索引（下）](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/MySQL%E5%AE%9E%E6%88%9845%E8%AE%B2/05%20%20%E6%B7%B1%E5%85%A5%E6%B5%85%E5%87%BA%E7%B4%A2%E5%BC%95%EF%BC%88%E4%B8%8B%EF%BC%89.md)





### Java IO 模型

BIO、NIO、NIO 2（AIO）。

BIO：传统的 java.io 包，它基于流模型实现。交互方式是同步、阻塞的方式，在读、写动作完成之前，线程会一直阻塞在那里。

NIO：可以构建多路复用的、同步非阻塞 IO 程序。

NIO 2：异步 IO 操作基于事件和回调机制。



[Java提供了哪些IO方式？ NIO如何实现多路复用？](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%20%E6%A0%B8%E5%BF%83%E6%8A%80%E6%9C%AF%E9%9D%A2%E8%AF%95%E7%B2%BE%E8%AE%B2/11%20%20Java%E6%8F%90%E4%BE%9B%E4%BA%86%E5%93%AA%E4%BA%9BIO%E6%96%B9%E5%BC%8F%EF%BC%9F%20NIO%E5%A6%82%E4%BD%95%E5%AE%9E%E7%8E%B0%E5%A4%9A%E8%B7%AF%E5%A4%8D%E7%94%A8%EF%BC%9F-%E6%9E%81%E5%AE%A2%E6%97%B6%E9%97%B4.md)



### Java反射机制和使用

[自己动手实现springboot运行时新增/更新外部接口](https://juejin.cn/post/6962828391116439565)





### Spring事务（4种特性、7种传播行为，5种隔离级别）

Spring事物传播特性、事物隔离级别？Spring事物传播特性？

#### 事务有四个特性：ACID

* 原子性（Atomicity）
* 一致性（Consistency）
* 隔离性（Isolation）
* 持久性（Durability）

####  传播行为（propagation behavior）

* PROPAGATION_REQUIRED
* PROPAGATION_SUPPORTS
* PROPAGATION_MANDATORY
* PROPAGATION_REQUIRED_NEW
* PROPAGATION_NOT_SUPPORTED
* PROPAGATION_NEVER
* PROPAGATION_NESTED

#### 隔离级别

* ISOLATION_READ_UNCOMMITTED
* ISOLATION_READ_COMMITTED
* ISOLATION_REPEATABLE_READ
* ISOLATION_SERIALIZABLE

> 脏读（Dirty reads）——脏读发生在一个事务读取了另一个事务改写但尚未提交的数据时。如果改写在稍后被回滚了，那么第一个事务获取的数据就是无效的。
> 不可重复读（Nonrepeatable read）——不可重复读发生在一个事务执行相同的查询两次或两次以上，但是每次都得到不同的数据时。这通常是因为另一个并发事务在两次查询期间进行了更新。
> 幻读（Phantom read）——幻读发生在一个事务（T1）读取了几行数据，接着另一个并发事务（T2）插入了一些数据时。在随后的查询中，第一个事务（T1）就会发现多了一些原本不存在的记录。



### 如何使用 Spring Boot 实现全局异常处理？

使用 `@ControllerAdvice` 和 `@ExceptionHandler` 注解处理全局异常。

```java
@ControllerAdvice
@ResponseBody
public class GlobalExceptionHandler {
    @ExceptionHandler(value = Exception.class)
    public ResponseEntity exceptionHandler(HttpServletRequest request, HttpServletResponse response, HandlerMethod handlerMethod, Exception e) {
      printStackTrace(request, handlerMethod, e);
        
        ResponseEntity<Object> resEnt = new ResponseEntity<>(HttpStatus.INTERNAL_SERVER_ERROR);
        return resEnt;
    }
}
```







SQL查询语句

学生成绩前三

```sql
select s.id, e.id
    from student s, exam e
    where s.eId = e.id 
    order by e.score  desc
    limit 3;
```

优化

```sql
select 
    s.id, e.id
from 
    student s
    left join exam e on s.eId = e.id
order by 
    e.score  desc
limit 3;
```





## 优化

反射

设计模式

VUE



## 八股文汇总

[Java核心技术面试精讲_time.geekbang](https://learn.lianglianglee.com/专栏/Java核心技术面试精讲)

[Java技术之高频面试题-v2023.2_atguigu](https://www.wolai.com/miG7fA1qKFy1r4UoRG54iG)







## Redis

五大数据类型：String、List、Set、ZSet、Hash

五大数据结构：整数数组、链表、Hash、压缩链表、跳表

Redis用途：

* 作为缓存

* 作为消息队列
    * 消息保序：使用List类型，LPUSH、RPOP（BRPOP阻塞式读取）
    * 重复消息：消息提供全局唯一的 ID 号
    * 可靠传输：List类型是如何保证消息可靠性，BRPOPLPUSH

* 大数据量：使用二级编码的方法，实现了用集合类型保存单值键值对，Redis 实例的内存空间消耗明显下降了



## Kafka

传输消息的格式: Kafka使用的是纯二进制的字节序列。

传输协议：

* 点对点模型
* 发布 / 订阅模型

术语：

* Client：生产者、消费组
* Server：Broker
* Topic：主题
* Partition：分区
* Replication：Replica副本
* Offset：位移（消息在分区中的位置信息）

持久化：Kafka 使用消息日志（Log）来保存数据。

```json
我来总结一下今天提到的所有名词术语：
消息：Record。Kafka 是消息引擎嘛，这里的消息就是指 Kafka 处理的主要对象。
主题：Topic。主题是承载消息的逻辑容器，在实际使用中多用来区分具体的业务。
分区：Partition。一个有序不变的消息序列。每个主题下可以有多个分区。
消息位移：Offset。表示分区中每条消息的位置信息，是一个单调递增且不变的值。
副本：Replica。Kafka 中同一条消息能够被拷贝到多个地方以提供数据冗余，这些地方就是所谓的副本。副本还分为领导者副本和追随者副本，各自有不同的角色划分。副本是在分区层级下的，即每个分区可配置多个副本实现高可用。
生产者：Producer。向主题发布新消息的应用程序。
消费者：Consumer。从主题订阅新消息的应用程序。
消费者位移：Consumer Offset。表征消费者消费进度，每个消费者都有自己的消费者位移。
消费者组：Consumer Group。多个消费者实例共同组成的一个组，同时消费多个分区以实现高吞吐。
重平衡：Rebalance。消费者组内某个消费者实例挂掉后，其他消费者实例自动重新分配订阅主题分区的过程。Rebalance 是 Kafka 消费者端实现高可用的重要手段。
```

Kafka 保证消息不丢失：

* Producer：使用带有回调通知的发送 API
* Consumer：不要开启自动提交位移，而是要应用程序手动提交位移

Kafka 保证消息准确性：

* Producer：开启幂等配置 enable.idempotence = true。

* Producer： 事务型 Producer
    * 开启 enable.idempotence = true。
    * 设置 Producer 端参数 transctional.id
    * Consumer 端设置 isolation.level=read_committed

Rebalance触发条件：

* 组成员数发生变更。
* 订阅主题数发生变更。
* 订阅主题的分区数发生变更。







## MySQL

MySQL 脏读、不可重复读、幻读： [MySQL中的幻读，你真的理解吗？](https://cloud.tencent.com/developer/article/1593481)



[查询总分大于100的学生和每一科都超过60分的学生](https://blog.csdn.net/qq_36004234/article/details/123522933)

![img](https://onecup-image.oss-cn-beijing.aliyuncs.com/imgs/typora/202311070847359.png)





## 项目介绍/自我介绍

### My自我介绍

**配置资源监控平台**

领导您好，我叫xxx。20年毕业。上家公司是在xxx公司，从事Java后端开发。最近做的项目是资源管理与全栈监控平台。这块业务的目标是 支撑 IT、CT、IOT 相关资源的管理与监控，主要解决资源资产没有统一采集、管理、监控、告警。平台基于SpringCloud搭建，使用到Eureka、Apollo、Kafka、Redis、ES等。我个人在其中负责的是 资源资产管理 模块的产品，负责核心业务代码编写，负责带领指导新人。我的大致情况是这样。



### My项目介绍

- 首先他要解决的问题是，资源资产配置管理与监控。公司的资产资源配置没有统一管理，统一监控。
- 复杂性在于系统间数据传输，大数据量采集处理。
- 最终的结果是，保证系统高可用。







## 有什么想问的

技术：

* 项目或产品中使用到的技术，是微服务吗
* 产品项目进度或所处阶段，以及未来1年的规划。
* 小组整体氛围，平时加班情况
* 有没有什么技术培训项目？贵公司的晋升机制是什么样的？贵公司业务及战略的未来发展？
* 公司文化是什么？
*

HR：

* 有13薪或年终奖吗？
* 公司规模或公司发展方向？
* 平时加班情况？加班车费报销？
* 假期福利





## 你的优点和缺点是什么？

优点：

* 热爱技术，喜欢思考，平时会通过视频和文章学习技术
* 喜欢分享，在线问题文档，Code Review，分享技术
* 追求效率，Jenkins构建部署

缺点：

* 性格不够外向
* 语言表达能力不够好





## 在这里工作你喜欢什么？

我从我所做的工作中获得了满足。

我喜欢与真正聪明，友好的同事合作。

尊重工程技术。



## 讲个笑话？

“Knock, knock. Who’s there? Hire. Hire who? Hire me！”



## 配置资源监控平台

IT资产：

* Linux、Windows、Tomcat、MySQL、Kafka、Redis
    * 资源信息：
        * Linux：CPU核数、内存总量、操作系统
        * 文件系统：挂载点、所属逻辑卷
    * 监控信息：
        * Linux：CPU利用率、内存利用率、Ping状态
        * MySQL：会话数、连接状态
* VMware、华为MO6、华为云、中兴云
    * VMware云、VMware虚拟机、物理机、虚拟磁盘网卡
* 运营商的5G消息、5G短信网关、骨干网、核心网
* 路由器、交换机、网络接口
* 小型机、机架服务器
* 平板电脑、打印机





## 面试题



#### Spring

##### Spring的基础机制IOC和AOP

Spring的基础机制：

- 控制反转（Inversion of Control），或者也叫依赖注入（Dependency Injection），广泛应用于Spring框架之中，可以有效地改善了模块之间的紧耦合问题。

从Bean创建过程可以看到，它的依赖关系都是由容器负责注入，具体实现方式包括带参数的构造函数、setter方法或者[AutoWired](https://docs.spring.io/spring-framework/docs/5.0.3.RELEASE/javadoc-api/org/springframework/beans/factory/annotation/Autowired.html)方式实现。

- AOP，Spring框架中的事务、安全、日志等功能都依赖于AOP技术。

切面编程落实到软件工程其实是为了更好地模块化，而不仅仅是为了减少重复代码。通过AOP等机制，我们可以把横跨多个不同模块的代码抽离出来，让模块本身变得更加内聚，进而业务开发者可以更加专注于业务逻辑本身。我们可以通过切面的方式进行修改或者新增功能。



##### SpringBoot在项目中都使用到哪些注解？

```Java
@PropertySource(value = {"firm-model.properties"}, encoding = "UTF-8", ignoreResourceNotFound = true)

```



##### 自定义注解

```java
// 定义注解
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.METHOD, ElementType.TYPE})
public @interface RedisLockAnnotation {
    String LOCK_KEY();
    int LOCK_TIME() default 1800;
    boolean NEED_UNLOCK() default false;}

// 通过AOP监听注解
@Aspect
public class RedisLockHander {
    @Pointcut("@annotation(com.ultra.cmdb.annotation.RedisLockAnnotation)")
    public void redisLock() {
    
    @Around("redisLock()")
    public Object lock(ProceedingJoinPoint pjp) throws Throwable {
            MethodSignature signature = (MethodSignature) pjp.getSignature();
            Method method = signature.getMethod();
            // 获取注解
            RedisLockAnnotation annotation = method.getAnnotation(RedisLockAnnotation.class);
            lockKey = annotation.LOCK_KEY();
                if (needUnlock) {              //需要锁
                  hasLock = redisLockUtil.lock(lockKey, 10 * 60);

    // 瞬时锁，如果获取不到锁 立刻返回获取锁失败
    public boolean lock(String key, int seconds) {
          String address = getIpAddress();
        String result = jedis.set(lockKey, address, new SetParams().nx().ex(seconds));

    // 同步所有厂商入库
    @RedisLockAnnotation(LOCK_KEY = "SYNCFIRMMODEL", LOCK_TIME = 24 * 60 * 60)
    public void sysAllFirm() {
```





##### Spring 中用到的设计模式有哪些？

- BeanFactory：工厂模式。
- 在Bean的创建中，Spring也为不同scope定义的对象，提供了单例和原型等模式实现。
- AOP：代理模式、装饰器模式、适配器模式等。
- 事件监听器：观察者模式
- JdbcTemplate：模板模式





##### @Transaction事务注解

@Transaction事务隔离级别传播特性，在项目中实际？

@Transactional的propagation参数解释

* 示例：@Transactional(propagation = Propagation.REQUIRED, rollbackFor = Exception.class)
* 传播行为（propagation behavior）
    * PROPAGATION_REQUIRED
    * PROPAGATION_SUPPORTS
    * PROPAGATION_MANDATORY
    * PROPAGATION_REQUIRED_NEW
    * PROPAGATION_NOT_SUPPORTED
    * PROPAGATION_NEVER
    * PROPAGATION_NESTED



##### 文件上传下载@注解是什么？

MultipartFile

```java
// 使用 MultipartFile 接收文件
@RequestParam("file") MultipartFile file,
// 将文件上传到服务器
orgFile.transferTo(toFile);
AttachFile attFile = new AttachFile();
// 由文件读出数据，处理
is = new FileInputStream(f);

/** 导入 **/
dataMaps = ImportUtil.getDataListFromExcel(is, pMap);
// 处理一个excel
XSSFWorkbook workbook = new XSSFWorkbook(is);
handleOneSheet(workbook, sheetNum, pMap) {
// 处理一个sheet
  Sheet sheet = workbook.getSheetAt(sheetNum);
  Row row = sheet.getRow(0);
  // 处理一个单元格
  Cell cell = row.getCell(colName);
  date = cell.getDateCellValue();
}
/** 导出 **/
ExportUtil.exportResFailsExcel(){
  workbook = new SXSSFWorkbook(rowAccessWindowSize);
  sheet = workbook.createSheet(sheetName);
  row = sheet.createRow(0);
  cell = row.createCell(i);
```



#### Java





##### Stream常用方法

map，filter，forEach，limit/skip，distinct

* 遍历操作(map)：.stream().map().collect()
* 过滤操作(filter)：.stream().filter() .collect()
* 循环操作(forEach): .stream().forEach()
* 返回特定的结果集合（limit/skip）：.stream().skip().limit().collect()
* 排序（sort/min/max/distinct）：.stream().distinct().collect()



##### Java创建内部类的方式？

非静态内部类

```java
public class Outerclass {
  public  class innerclass{
        public void  to() {
            System.out.println(name);
        }
    }
  public static void main(String[] args) {
        Outerclass q = new Outerclass();
        Outerclass.innerclass c = q.new innerclass();
        c.to();
    }
}
```



静态内部类

```java
public class Outerclass {
    public static  class innerclass {
        public void  to() {
            System.out.println(name);
        }
    }
    public static void main(String[] args) {
        innerclass q = new innerclass();
    }
 
}
```



##### Synchronized 修饰普通方法和静态方法有什么区别？

Synchronized修饰非静态方法，实际上是对调用该方法的对象加锁，俗称“对象锁”。

Synchronized修饰静态方法，实际上是对该类对象加锁，俗称“类锁”。



##### synchronized和ReentrantLock有什么区别呢？

synchronized：提供了互斥的语义和可见性，当一个线程已经获取当前锁时，其他试图获取的线程只能等待或者阻塞在那里。

ReentrantLock：再入锁，它是表示当一个线程试图获取一个它已经获取的锁时，这个获取动作就自动成功，这是对锁获取粒度的一个概念，也就是锁的持有是以线程为单位而不是基于调用次数。

ReentrantLock提供了很多实用的方法，比如可以控制fairness(公平性)，tryLock()（非阻塞式的获取锁操作），isLocked()，getOwner()。通过调用lock()方法获取，调用unlock()方法释放。



##### 线程生命周期的不同状态？

- 新建（NEW）
- 就绪（RUNNABLE）
- 阻塞（BLOCKED）
- 等待（WAITING），计时等待（TIMED_WAIT）

- 终止（TERMINATED）



##### 性能问题：内存持续上升，我该如何排查问题？

* top：查看CPU 使用率、内存使用率以及系统负载等信息。
* top -Hp pid： 查看具体线程使用系统资源情况
* jstat -gc pid：堆内存信息以及垃圾回收信息
* jstack pid：查看线程的堆栈信息。结合 top -Hp pid 查看具体线程的状态，排查一些死锁的异常
* jmap -dump:live,format=b,file=jmap-dump.phrof [pid]：把堆内存的使用情况 dump 到文件中



使用线程池时 workQueue 过大，任务堆积导致OOM：

- 避免任务堆积。前面我说过newFixedThreadPool是创建指定数目的线程，但是其工作队列是无界的，如果工作线程数目太少，导致处理跟不上入队的速度，这就很有可能占用大量系统内存，甚至是出现OOM。诊断时，你可以使用jmap之类的工具，查看是否有大量的任务对象入队。



##### 什么情况下Java程序会产生死锁？如何定位、修复？

基本上死锁的发生是因为：

- 互斥条件，类似Java中Monitor都是独占的，要么是我用，要么是你用。
- 互斥条件是长期持有的，在使用结束之前，自己不会释放，也不能被其他线程抢占。
- 循环依赖关系，两个或者多个个体之间出现了锁的链条环。

避免死锁的思路和方法:

* 尽量避免使用多个锁，并且只有需要时才持有锁。
* 如果必须使用多个锁，尽量设计好锁的获取顺序。
* 使用带超时的方法，Object.wait(…)或CountDownLatch.await(…)。
* 通过静态代码分析（如FindBugs）去查找固定的模式，进而定位可能的死锁或者竞争情况。



##### Java并发包提供了哪些并发工具类？

并发包也就是java.util.concurrent及其子包

- 提供了比synchronized更加高级的各种同步结构，包括CountDownLatch、CyclicBarrier、Semaphore等，可以实现更加丰富的多线程操作。
- 各种线程安全的容器，比如最常见的ConcurrentHashMap、有序的ConcurrentSkipListMap，或者通过类似快照机制，实现线程安全的动态数组CopyOnWriteArrayList等。
- 各种并发队列实现，如各种BlockingQueue实现，比较典型的ArrayBlockingQueue、 SynchronousQueue或针对特定场景的PriorityBlockingQueue等。
- 强大的Executor框架，可以创建各种不同类型的线程池，调度任务运行等，绝大部分情况下，不再需要自己从头实现线程池和任务调度器。

CountDownLatch:

- CountDownLatch，允许一个或多个线程等待某些操作完成。
- CountDownLatch的基本操作组合是countDown/await。调用await的线程阻塞等待countDown足够的次数，不管你是在一个线程还是多个线程里countDown，只要次数足够即可。
- CountDownLatch是不可以重置的，所以无法重用；

CopyOnWriteArrayList:

* CopyOnWrite到底是什么意思呢？它的原理是，任何修改操作，如add、set、remove，都会拷贝原数组，修改后替换原来的数组，通过这种防御性的方式，实现另类的线程安全。



##### 为什么用线程池？解释下线程池参数？

线程池参数：

* **corePoolSize**：代表核心线程数。

* **maxinumPoolSize**：代表的是最大线程数。
* **keepAliveTime 、 unit**：表示超出核心线程数之外的线程的空闲存活时间。

* **workQueue**：用来存放待执行的任务。

* **ThreadFactory**：实际上是一个线程工厂，一般我们会根据业务来制定不同的线程工厂。

* **Handler**：任务拒绝策略。

线程池大小的选择策略：

* CPU密集型：按照CPU核的数目N或者N+1。
* I/O密集型：线程数 = CPU核数 × 目标CPU利用率 ×（1 + 平均等待时间/平均工作时间）



##### 请介绍类加载过程，什么是双亲委派模型？

Java的类加载过程分为三个主要步骤：加载、链接、初始化:

* 加载阶段（Loading）:  Java将字节码数据从不同的数据源读取到JVM中
* 链接（Linking）:
    * 验证（Verification），这是虚拟机安全的重要保障，JVM需要核验字节信息是符合Java虚拟机规范的，否则就被认为是VerifyError，这样就防止了恶意信息或者不合规的信息危害JVM的运行，验证阶段有可能触发更多class的加载。
    * 准备（Preparation），创建类或接口中的静态变量，并初始化静态变量的初始值。但这里的“初始化”和下面的显式初始化阶段是有区别的，侧重点在于分配所需要的内存空间，不会去执行更进一步的JVM指令。
    * 解析（Resolution），在这一步会将常量池中的符号引用（symbolic reference）替换为直接引用。在[Java虚拟机规范](https://docs.oracle.com/javase/specs/jvms/se8/html/jvms-5.html#jvms-5.4.3)中，详细介绍了类、接口、方法和字段等各个方面的解析。

* 初始化阶段（initialization）: 执行类初始化的代码逻辑，包括静态字段赋值，执行静态初始化块内的逻辑。

双亲委派模型：简单说就是当类加载器（Class-Loader）试图加载某个类型的时候，除非父加载器找不到相应类型，否则尽量将这个任务代理给当前加载器的父加载器去做。使用委派模型的目的是避免重复加载Java类型。

类加载器的结构：

* 启动类加载器（Bootstrap Class-Loader）
* 扩展类加载器（Extension or Ext Class-Loader）
* 应用类加载器（Application or App Class-Loader）
* 用户自定义类加载器



##### 谈谈JVM内存区域的划分，哪些区域可能发生OutOfMemoryError

JVM内存区域的划分

* **程序计数器**: 程序计数器会存储当前线程正在执行的Java方法的JVM指令地址

* **Java虚拟机栈**: 每个线程在创建时都会创建一个虚拟机栈，每个栈帧对应着一次次的Java方法调用。

* **堆**（Heap）：它是Java内存管理的核心区域，用来放置Java对象实例，几乎所有创建的Java对象实例都是被直接分配在堆上。堆被所有的线程共享，在虚拟机启动时，我们指定的“Xmx”之类参数就是用来指定最大堆空间等指标。堆被垃圾收集器进行进一步的细分为新生代、老年代。

* **方法区**：用于存储类结构信息，以及对应的运行时常量池、字段、方法代码等。

* **运行时常量池**：编译期生成的各种字面量，运行时决定的符号引用等。

* **本地方法栈**。它和Java虚拟机栈是非常相似的，支持对本地方法的调用。

哪些区域可能发生OutOfMemoryError：

* 堆内存不足，抛出的错误信息是“java.lang.OutOfMemoryError:Java heap space”，原因可能存在内存泄漏问题
* 程序不断的进行递归调用，而且没有退出条件，JVM实际会抛出StackOverFlowError，如果JVM试图去扩展栈空间的的时候失败，则会抛出OutOfMemoryError。



#### MySQL

##### MySQL支持的事务隔离级别

MySQL事务隔离级别分为四个不同层次：

- 读未提交（Read uncommitted），就是一个事务能够看到其他事务尚未提交的修改，这是最低的隔离水平，允许[脏读](https://en.wikipedia.org/wiki/Isolation_(database_systems)#Dirty_reads)出现。
- 读已提交（Read committed），事务能够看到的数据都是其他事务已经提交的修改，也就是保证不会看到任何中间性状态，当然脏读也不会出现。读已提交仍然是比较低级别的隔离，并不保证再次读取时能够获取同样的数据，也就是允许其他事务并发修改数据，允许不可重复读和幻象读（Phantom Read）出现。
- 可重复读（Repeatable reads），保证同一个事务中多次读取的数据是一致的，这是MySQL InnoDB引擎的默认隔离级别，但是和一些其他数据库实现不同的是，可以简单认为MySQL在可重复读级别不会出现幻象读。
- 串行化（Serializable），并发事务之间是串行化的，通常意味着读取需要获取共享读锁，更新需要获取排他写锁。



##### MySQL组合索引的使用规则？

mysql (a,b,c) 索引生效 请问哪些索引生效（）

生效的规则是：从前往后依次使用生效，如果中间某个索引没有使用，那么断点前面的索引部分起作用，断点后面的索引没有起作用； 比如:

```sql
-- 
where a=3 and b=45 and c=5 .... 这种三个索引顺序使用中间没有断点，全部发挥作用；
where a=3 and c=5... 这种情况下b就是断点，a发挥了效果，c没有效果
where b=3 and c=4... 这种情况下a就是断点，在a后面的索引都没有发挥作用，这种写法联合索引没有发挥任何效果；
where b=45 and a=3 and c=5 .... 这个跟第一个一样，全部发挥作用，abc只要用上了就行，跟写的顺序无关

-- 
(6)    select * from mytable where a=3 order by b;
a用到了索引，b在结果排序中也用到了索引的效果，前面说了，a下面任意一段的b是排好序的
(8)    select * from mytable where b=3 order by a;
b没有用到索引，排序中a也没有发挥索引效果
```





#### 设计模式

##### 用到过哪些设计模式？

单例模式

```json
纯Java项目中（CMDB SDK）：
1. redis消息订阅（MsgSubscriManager extends JedisPubSub），使用单例模式
2. 读取Apollo中配置，使用单例模式
```

策略模式

[设计模式之----匹配器处理器模式（Matcher-Handler）的理解](https://blog.csdn.net/ws9029/article/details/117229616)

```json
策略模式的升级版（matcher-handler）,Matcher-Handler模式也是属于略模式的一种.
isMatcher()
prcoess()
@Autowired
private List<IResMsgHandle> resHandlers;
```

代理模式

```json
// 接口实例工厂，这里主要是用于提供接口的实例对象
public class ServiceFactory<T> implements FactoryBean<T> {
    @Override
    public T getObject() throws Exception {
        //这里主要是创建接口对应的实例，便于注入到spring容器中
        InvocationHandler handler = new ServiceProxy<>(interfaceType);
        return (T) Proxy.newProxyInstance(interfaceType.getClassLoader(),
                new Class[]{interfaceType}, handler);

// 用于Spring动态注入自定义接口
public class ServiceBeanDefinitionRegistry implements BeanDefinitionRegistryPostProcessor, ResourceLoaderAware, ApplicationContextAware {
      @Override
    public void postProcessBeanDefinitionRegistry(BeanDefinitionRegistry registry)
            //这里一般我们是通过反射获取需要代理的接口的clazz列表
        //比如判断包下面的类，或者通过某注解标注的类等等
        Set<Class<?>> beanClazzs = scannerPackages("com.ultra.cmdb.dao");
				definition.setBeanClass(ServiceFactory.class);

// 动态代理，需要注意的是，这里用到的是JDK自带的动态代理，代理对象只能是接口，不能是类
public class ServiceProxy<T> implements InvocationHandler {
    @Override
    public Object invoke(Object proxy, Method method, Object[] args)
        Class<?> returnType = method.getReturnType();
        Query annotation = method.getAnnotation(Query.class);
```





#### 数据结构与算法



##### 冒泡排序

每次遍历时都对相邻两个元素排序





#### 组件



#### Redis

##### Redis实际使用到哪些数据结构？

* string

  ```java
  // 对String操作的命令: set(key, value)：给数据库中名称为key的string赋予值value
  jedisCluster.set(key, value);
  ```



##### Redis作为消息队列使用

* 消息队列

  ```java
  // 发送Redis消息
  sendMsg(data, objType, opType);
    jedis.publish(preFix + ChannelName.FROM_CMDB.name(), opObj.toString());
  
  // 订阅消息
  public class MsgSubscriber extends JedisPubSub implements ApplicationRunner{
            // 订阅信道
            jedis.subscribe(sub, channelName);
   
    @Override
    public void onMessage(String channel, String message) {
        hdlMng.handleMsg(message);
    }
  ```



##### Redis与MySQL双写一致性如何保证？

* 延时双删策略

    * 在写库前后都进行redis.del(key)操作，并且设定合理的超时时间。具体步骤是：

    * 1）先删除缓存

    * 2）再写数据库

    * 3）休眠500毫秒（根据具体的业务时间来定）

    * 4）再次删除缓存。

* 设置缓存的过期时间

* 如何写完数据库后，再次删除缓存成功？

    * （1）更新数据库数据；

      （2）数据库会将操作信息写入binlog日志当中；

      （3）订阅程序提取出所需要的数据以及key；

      （4）另起一段非业务代码，获得该信息；

      （5）尝试删除缓存操作，发现删除失败；

      （6）将这些信息发送至消息队列；

      （7）重新从消息队列中获得该数据，重试操作。



##### Redis实现分布式锁？

参考：[基于Redis的分布式锁实现](https://juejin.cn/post/6844903830442737671)

```java
@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface RedisLock {
    // 业务键
    String key();
    // 锁的过期秒数,默认是5秒
    int expire() default 5;
    // 尝试加锁，最多等待时间
    long waitTime() default Long.MIN_VALUE;
    // 锁的超时时间单位
    TimeUnit timeUnit() default TimeUnit.SECONDS;
}


/** 在AOP中我们去执行获取分布式锁和释放分布式锁的逻辑 **/
@Aspect
@Component
public class LockMethodAspect {
    @Around("@annotation(com.redis.lock.annotation.RedisLock)")
    public Object around(ProceedingJoinPoint joinPoint) {
        Method method = signature.getMethod();
        RedisLock redisLock = method.getAnnotation(RedisLock.class);
        String value = UUID.randomUUID().toString();
        String key = redisLock.key();
        try {
            final boolean islock = redisLockHelper.lock(jedis,key, value, redisLock.expire(), redisLock.timeUnit());
          return joinPoint.proceed();
        }  finally {
          // 释放锁
            redisLockHelper.unlock(jedis,key, value);
            jedis.close();
        }
    }
}


/** Redis实现分布式锁核心类 **/
@Component
public class RedisLockHelper {
    // 在Redis的2.6.12及以后中,使用 set key value [NX] [EX] 命令
    public boolean lock(Jedis jedis,String key, String value, int timeout, TimeUnit timeUnit) {
        long seconds = timeUnit.toSeconds(timeout);
        return "OK".equals(jedis.set(key, value, "NX", "EX", seconds));
    }

    // 使用Lua脚本进行解锁操纵，解锁的时候验证value值
    public boolean unlock(Jedis jedis,String key,String value) {
        String luaScript = "if redis.call('get',KEYS[1]) == ARGV[1] then " +
                "return redis.call('del',KEYS[1]) else return 0 end";
        return jedis.eval(luaScript, Collections.singletonList(key), Collections.singletonList(value)).equals(1L);
    }
}


/** 定义一个TestController来测试我们实现的分布式锁 **/
public class TestController {
    @RedisLock(key = "redis_lock")
    @GetMapping("/index")
    public String index() {

```



#### Eureka

##### Eureka的CAP特性，服务宕机了怎么办？

CAP 定理

* 一致性（Consistency）：在分布式系统中的所有数据备份，在同一时刻是否同样的值。（等同于所有节点访问同一份最新的数据副本）（意思是，写操作之后的读操作，必须返回该值。）

* 可用性（Availability）：在集群中一部分节点故障后，集群整体是否还能响应客户端的读写请求。（对数据更新具备高可用性）（意思是只要收到用户的请求，服务器就必须给出回应。）

* 分区容错性（Partition tolerance）：以实际效果而言，分区相当于对通信的时限要求。系统如果不能在时限内达成数据一致性，就意味着发生了分区的情况，必须就当前操作在C和A之间做出选择。（意思是，区间通信可能失败。）

Eureka是满足`AP`的：

* 优先保证可用性

- 各个节点都是平等的，几个节点挂掉不会影响正常节点的工作，剩余的节点依然可以提供注册和查询服务
- 在向某个Eureka注册时如果发现连接失败，则会自动切换至其它节点，只要有一台Eureka还在，就能保证注册服务可用(保证可用性)，只不过查到的信息可能不是最新的(不保证强一致性)

Eureka服务宕机了怎么办：

* Eureka Server可以运行多个实例来构建集群，解决单点问题。如果某台Eureka Server宕机，Eureka Client的请求会自动切换到新的Eureka Server节点，当宕机的服务器重新恢复后，Eureka会再次将其纳入到服务器集群管理之中。

参考：[2021升级版微服务教程3—Eureka完全使用指南](https://www.cnblogs.com/bingyang-py/p/14255298.html)





#### ElasticSearch

##### ES常用关键字 match match_all，ES内置分词器？

关键字

* `match_all`表示查询所有的数据

* 在字段中搜索特定字词，可以使用`match`; 如下语句将查询address 字段中包含 mill 或者 lane的数据

  ```bash
  GET /bank/_search
  {
    "query": { "match": { "address": "mill lane" } }
  }
  ```

* 查询段落匹配：match_phrase

  如果我们希望查询的条件是 address字段中包含 “mill lane”，则可以使用`match_phrase`

  ```bash
  match_phrase还是分词后去搜的，目标文档需要包含分词后的所有词，目标文档还要保持这些词的相对顺序和文档中的一致
  
  GET /bank/_search
  {
    "query": { "match_phrase": { "address": "mill lane" } }
  }
  ```

* 使用`bool`查询来组合多个查询条件。

* `must`, `should`, `must_not` 和 `filter` 都是`bool`查询的子句。那么`filter`和上述`query`子句有啥区别呢？

* 查询条件：query or filter，query 上下文的条件是用来给文档打分的，匹配越好 _score 越高；filter 的条件只产生两种结果：符合与不符合，后者被过滤掉。

* 聚合查询：Aggregation。aggs，avg

* 模糊匹配：fuzzy

* Term查询：term是代表完全匹配，也就是精确查询，搜索前不会再对搜索词进行分词拆解。

  ```json
  // 查询不到  "title": "love China",
  {
    "query": {
      "term": {
        "title": "love China"
      }
    }
  }
  // 执行发现无数据，从概念上看，term属于精确匹配，只能查单个词
  ```

完整语句参考

* ```json
  "query": {
    "bool": {
      "must": [
        "match": {
            "state": "ND"
        "filter": [
          "term": {
            "age": "40"
        "range": {
          "balance": {
          "gte": 20000, "lte": 30000
  ```



Elasticsearch的内置分词器

- Standard Analyzer - 默认分词器，按词切分，小写处理
- Simple Analyzer - 按照非字母切分(符号被过滤), 小写处理
- Whitespace Analyzer - 按照空格切分，不转小写
- Keyword Analyzer - 不分词，直接将输入当作输出
- Patter Analyzer - 正则表达式，默认\W+(非字符分割)
- Customer Analyzer 自定义分词器

