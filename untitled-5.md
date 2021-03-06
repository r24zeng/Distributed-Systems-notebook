# 7.系统结构

## 集成结构

### 基础的用户服务器模型：

用户发送请求，等待 -&gt; 服务器接收请求，处理 -&gt; 服务器回应用户

### 多层集成结构：

* 一层：仅有终端的大型机器
* 两层：用户和服务器端
* 三层：每一层都分散在不同的机器上，例如客户端 -&gt; 应用的服务器 -&gt; 数据库服务器

  **非集成结构**

  两种类型：

* 垂直分布式：逻辑化地将请求处理的流程分成三部分（客户端，应用端，数据库），每层都有多台机器，它们都完成整个工作的一部分，这样这些机器就需要非常清楚下一步要把请求发给哪个机器。
* 平行分布式：这种更通用更简单一些。把一个大任务分解成小任务，平均分发给所有的机器，所有的机器都执行同样的的功能。但问题是**更新**非常麻烦，需要更新所有的机器。

### 平行式分布，哈希一致性使分布均匀

> 每个节点（机器）需要同时担任客户端和服务器

例1: Peer-to-Peer \(P2P\)

每个数据都有一个键值，通过哈希方程找到其位置，但不能保证分布均匀

例2：Chord

节点连成一个环形，通过一致性哈希将数据但键值存储到相应的物理节点上，或者离哈希过的虚拟节点最近的物理节点上，无论哪个物理节点接收了请求，每个物理节点通过finger table都能迅速找到键值应存储的节点（successor）。

添加物理节点：新进来一个节点u，找到这个节点的后继节点v，将自己插入到自己的前继节点和u之间，再修改以前指向v的到u即可。修改指向即修改finger table。

删除物理节点：通知它的前继节点和后继节点告知它的离开，然后将指向它的都转移到它的后继节点上。修改指向即修改finger table。

例3：非结构性P2P

每个节点都有自己的邻居清单。两种方式去找某个数据的键值所存储的位置：（1）如果此键值存储在自己这里，则回应请求，否则将这个键值发送给它的所有邻居；（2）如果此键值存储在自己这里，则回应请求，否则将这个键值随便发给另一个邻居。

例4：超级Peer网络

打破了P2P的对称性，有的机器表现为超级机器，他们之间有联系，然后集群部分普通机器。

## 混合结构

例1: 边缘服务器

例2: BitTorrent

