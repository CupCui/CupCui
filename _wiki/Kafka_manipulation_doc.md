---

layout: wiki

title: Kafka常用操作

cate1: Tools

cate2: Editor

description: Kafka常用操作

keywords: Kafka

---





# Kafka操作文档



### 查看指定消费者的Lag值

```sh
# 查看指定消费者的Lag值
./kafka-consumer-groups.sh --bootstrap-server <Kafka broker 连接信息 > --describe --group <group 名称 >

# 举例
./kafka-consumer-groups.sh --bootstrap-server 192.168.95.114:59092 --describe --group bit_matrix_191
```



### 创建 Kafka 主题

```sh
# 创建 Kafka 主题
bin/kafka-topics.sh --bootstrap-server broker_host:port --create --topic my_topic_name  --partitions 1 --replication-factor 1

# 举例
bin/kafka-topics.sh --bootstrap-server 192.168.95.114:59092 --create --topic topic_test_20221221  --partitions 1 --replication-factor 1
```



### 修改主题分区

```sh
# 修改主题分区
bin/kafka-topics.sh --bootstrap-server broker_host:port --alter --topic <topic_name> --partitions < 新分区数 >
```



### 设置主题级别参数 max.message.bytes

```sh
# 设置主题级别参数 max.message.bytes
bin/kafka-configs.sh --zookeeper zookeeper_host:port --entity-type topics --entity-name <topic_name> --alter --add-config max.message.bytes=10485760
```



### 删除主题

```sh
# 删除主题
bin/kafka-topics.sh --bootstrap-server broker_host:port --delete  --topic <topic_name>
```





### 配置动态 Broker 参数 unclean.leader.election.enable

```sh
# 在集群层面设置全局值(即设置 cluster-wide 范围值)
$ bin/kafka-configs.sh --bootstrap-server kafka-host:port --entity-type brokers --entity-default --alter --add-config unclean.leader.election.enable=true
Completed updating default config for brokers in the cluster,

# 查看配置
$ bin/kafka-configs.sh --bootstrap-server kafka-host:port --entity-type brokers --entity-default --describe
Default config for brokers in the cluster are:
  unclean.leader.election.enable=true sensitive=false synonyms={DYNAMIC_DEFAULT_BROKER_CONFIG:unclean.leader.election.enable=true}

```



### 配置动态设置 per-broker 范围参数

```sh
# 设置 per-broker 范围参数
$ bin/kafka-configs.sh --bootstrap-server kafka-host:port --entity-type brokers --entity-name 1 --alter --add-config unclean.leader.election.enable=false
Completed updating config for broker: 1.

# 查看配置
$ bin/kafka-configs.sh --bootstrap-server kafka-host:port --entity-type brokers --entity-name 1 --describe
Configs for broker 1 are:
  unclean.leader.election.enable=false sensitive=false synonyms={DYNAMIC_BROKER_CONFIG:unclean.leader.election.enable=false, DYNAMIC_DEFAULT_BROKER_CONFIG:unclean.leader.election.enable=true, DEFAULT_CONFIG:unclean.leader.election.enable=false}

```



### 删除 cluster-wide 范围参数或 per-broker 范围参数

```sh
# 删除 cluster-wide 范围参数
$ bin/kafka-configs.sh --bootstrap-server kafka-host:port --entity-type brokers --entity-default --alter --delete-config unclean.leader.election.enable
Completed updating default config for brokers in the cluster,
# 删除 per-broker 范围参数
$ bin/kafka-configs.sh --bootstrap-server kafka-host:port --entity-type brokers --entity-name 1 --alter --delete-config unclean.leader.election.enable
Completed updating config for broker: 1.
```





### 查看 kafka 版本

```sh
# 查看 kafka 版本
./kafka-topics.sh --version
```



