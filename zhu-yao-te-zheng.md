# 2.主要特征

## 规模化的技术

1. 隐藏延迟
   * 同步通讯
   * 分别处理请求
   * 问题：不是所有情况适用
2. 在不同的机器上分开存储和处理数据
   * 转移计算到客户端
   * 分散_server_ （DNS）
   * 分散信息系统 （www）
3. 复制和缓存
   * 复制文件和数据库
   * 镜像网站
   * 浏览器和代理服务器中缓存网站
   * 缓存文件在客户和服务端
   * 问题：把资源复制在不同的地方容易引起不一致性，如果想要使同步化，则需要规模化解决方案同步每次变化

## 分布式系统的几大误区

1. 网络是绝对可靠的
2. 网络是绝对安全的
3. 拓扑结构永远不会改变
4. 零延迟
5. 带宽是无限的
6. 传输耗费为0
7. 只有一个域名（管理中心）
