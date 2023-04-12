---

layout: wiki

title: My Resume 2023

cate1: Tools

cate2: Editor

description: My Resume 2023

keywords: Resume

---

# Interview



配置资源管理亮点：

* 使用Redis作为缓存，减小数据库访问压力。
* Elasticsearch作为搜索引擎搭建搜索平台，支持对所有字段的搜索。
* 使用Kafka作为消息队列，来减小服务间耦合，填谷削峰。
* 资源权限控制、资源变更操作历史、资源关系topo、采集和监控、开放的模型管理。







Redis、唯一ID、乐观锁

Synchronic（偏向锁）：公平锁

ReEntrantLock（AQS）：非公平所

JMM：内存模型

Voltain关键字：共享变量可见性，有序性，禁之指令重排。

OOM、STW

内存泄漏

IO密集

abccba访问判断



网管gateway拦截器

Controller是单例？

Mysql慢查询排查过吗？

文件上传下载@注解是什么？

SpringBoot在项目中都使用到哪些注解？

feign调用涉及到哪些注解？

多线程如何异步回调获取结果？

Redis实现分布式锁？

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

Spring 中用到的设计模式有哪些？

了解和使用过反射吗？



MyBatis中引用对象如何查询，如何映射到对象上？多对多关系如何映射的？

GateWay登录流程？

Kafka多副本机制，以及可能存在的问题？

synchronize作用在方法上，创建两个对象调用该方法，会有线程安全问题吗？

SpringCloud各个组件使用过吗？

线程池核心线程数根据什么配置？





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





## 项目介绍/自我介绍

### My自我介绍

**配置资源监控平台**

您好，我叫xxx。20年毕业。目前在xxx公司，一直到现在。我所在的是数字化部研发组，负责的是 **资源管理与全栈监控** 业务。这块业务的目标是 支撑 IT、CT、IOT 相关资源的管理与监控，主要解决资源配置没有统一管理、监控问题。我个人在其中负责的是 配置资源管理 模块的产品，负责核心业务代码编写，负责带领指导新人。我的大致情况是这样。

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
* 平时加班情况？





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
* VMware、华为MO6、华为云FusionComputer、中兴云
  * VMware云、VMware虚拟机、物理机、虚拟磁盘网卡
* 运营商的5G消息、5G短信网关、骨干网、核心网
* 路由器、交换机、网络接口
* 小型机、机架服务器
* 平板电脑、打印机













