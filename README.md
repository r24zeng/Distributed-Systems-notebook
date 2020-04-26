# 1.介绍

> 定义：自主计算元素的集合，对外看起来像单个耦合系统

特征：

* 自主计算的元素：也被称为_node_，可以是硬件设备或者软件进程
* 单个耦合系统：用户体感知面对的是一个系统，意味着需要_node_间的协作

每个_node_都是独立的，因此不存在**全局时钟**，**同步**和**协作**是整个系统要面对的问题。

### 节点间的组合形式

覆盖网络 \(overlay network\)

特征：_node_只跟其邻居群沟通

例子： P2P网络 \(peer-to-peer system\)

类型：有组织的（知道自己的邻居群，有任务直接处理或者知道将任务传递给谁）；无组织的（只知道某个邻居，有任务直接处理或者传给自己的邻居）

### 耦合系统

定义：很多个_node_，但看起来像一个系统一样的行为，一致性，专业术语叫“distribution tranparency”

分布式的系统的某部分可能会出故障，隐藏这种故障和恢复都是非常困难的

### 分布式系统的中间层

定义：包含应用层和硬件间通用的功能模块

## 分布式系统的目的

### 1. 共享资源

云端文件存储；P2P媒体流；邮件服务；网站服务

### 2. 分布的透明度（隐藏）

* 访问：底层到底如何让用户访问
* 位置：从不同的终端或位置访问
* 迁移：将文件从一个_server_迁移到另一个_server_
* 重定向：将一个链接重定向到另一个链接
* 复制：后台对文件的复制防止一个点挂掉文件完全丢失
* 并发：多个用户同时共享、竞争同一个资源
* 故障：一个点故障，迅速恢复

**分布的透明度（不可能完全隐藏）**

* 隐藏沟通延迟
* 100%隐藏故障
* 隐藏会以牺牲表现为代价（例如想要确保数据随时更新，为防止数据丢失，每次都要更新数据到硬盘中而非内存中，这样就会导致花费更多的时间和重载代价）

另一种说法：暴露分布系统可能是好事，因为这样可以让更近的系统来处理任务，减少长距离导致的响应延迟；一旦哪个部分没响应或者非常缓慢就知道哪个出问题了。

### 3. 开放性

无论任何环境下，接口开放，易于另一个开放系统接上。

易交互，易合作，易与API接上，功能易扩展。

### 4. 规模化

* 用户数量或者进程规模化
  * 被CPU限制的计算能力
  * 包括CPU和_disk_间的传输速率在内的存储能力
  * 中心和用户间的网络
* 地理上规模化（两个_node_间最大距离）
  * **Scale up:** 增加更多资源时需要更多的存储空间，因此可以增加更多的机器，同时增加了响应延迟
  * **Scale out:** 距离太长了，需要加入更多的机器一起工作，同时增加了延迟
* 域名数量规模化
  * 不同域名间的资源分享更贵
  * 跨域名的控制、管理和合作更难（例如更新数据）
  * 例外（P2P系统）：BitTorrent \(文件系统\)；Skypte\(通信系统\);Sptify（音频媒体）

目前大多数实现了用户数量的规模化，只要增加_server_并行处理即可，所以遇到的最大挑战依然是地理上和域名数量的规模化。

