---

layout: wiki

title: My Resume 2023

cate1: Tools

cate2: Editor

description: My Resume 2023

keywords: Resume

---





# My Resume 2023 Interview

# Interview



配置资源管理亮点：

* 使用Redis作为缓存，减小数据库访问压力。
* Elasticsearch作为搜索引擎搭建搜索平台，支持对所有字段的搜索。
* 使用Kafka作为消息队列，来减小服务间耦合，填谷削峰。
* 资源权限控制、资源变更操作历史、资源关系topo、采集和监控、开放的模型管理

Mysql索引：B+树

Redis、唯一ID、乐观锁

Synchronic（偏向锁）：公平锁

ReEntrantLock（AQS）：非公平所

JMM：内存模型

Voltain关键字：通过总键监听，共享变量可见性，有序性，禁之指令重排。

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



MyBatis中引用对象如何查询，如何映射到对象上？

GateWay登录流程？

Java IO 模型？

Kafka多副本机制，以及可能存在的问题？

Java反射机制和使用？



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

* 作为缓冲

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





## 项目/自我介绍

### 崔光浩项目介绍

- 首先他要解决的问题是，资源资产配置管理与监控。公司的资产资源配置没有统一管理，统一监控。
- 复杂性在于系统间数据传输，大数据量采集处理。
- 最终的结果是，保证系统高可用。



### 崔光浩自我介绍

**配置资源监控平台**

您好，我叫崔光浩。20年毕业。目前在神州泰岳公司，一直到现在。我所在的是数字化部研发组，负责的是 **资源管理与全栈监控** 业务。这块业务的目标是 支撑IT相关资源的管理与监控，主要解决资源配置孤岛，资源统一管理问题，同时配合对资源采集与监控。我个人在其中负责的是 配置资源管理 模块的产品，负责核心业务代码编写，负责带领指导新人。我的大致情况是这样。





## 有什么想问的

技术

* 产品项目进度或所处阶段，以及未来1年的规划。

* 平时加班情况？

* 项目或产品中使用到的技术？

HR

* 有13薪吗？
* 公司规模？







2.6 你的缺点是什么

答:

不擅长讲解和用户打交道,社交焦虑症.

稳重负责、追求效率(提高电脑性能、多个显示器)、喜欢思考.



