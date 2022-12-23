---

layout: wiki

title: Redis常用操作

cate1: Tools

cate2: Editor

description: Redis常用操作

keywords: Redis

---



# Redis操作文档



## 常用

### 连接redis集群 ./redis-cli

```sh
# 连接redis集群
./redis-cli -c -h 192.168.95.111 -p 45050 -a fsm2003
```



### 查看集群信息

```sh
# 查看集群信息
> cluster info
```



### 查看集群中节点情况

```sh
# 查看集群中节点信息
> cluster nodes
```





## 不常用

### 查看指定key对应的slot

```sh
# 查看指定key对应的slot
> cluster keyslot 9218474373890186868
```

