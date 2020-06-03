# BUPTACststem

# 个人收集的教程：

#### 如何使用github简易教程

1. 下载安装git软件

2. 点击fork本仓库，创建一个分支。本仓库为master分支。

3. 在以你的用户名为前缀的仓库的分支页面进行git clone。

4. 更新自己的代码到master分支和从master分支更新最新的代码的方法：

   https://blog.csdn.net/whq19890827/article/details/75802717

### qt通信教程：

https://blog.csdn.net/u014695839/article/details/70041771

## 1、消息格式是所有通信格式样例

## 2、用户消息格式是小组讨论后的用户客户端和服务器通信的格式

## 3、Project文件夹中是新建好的3个QT工程

### 3.1 ACsystemServer 服务器

### 3.2 HotelCilent 前台 经理 管理员统一的客户端

### 3.3 BUPTACsystem/CustomerCilent 用户客户端

工程有2个文件因为大于50m无法上传，我百度了下说是vs的日志和报错处理文件，有没有没有差别。如果有因为没有这两个文件导致运行失败请找我我发给你们。

**大前提：**

1. **所有需要大组内统一的量应该用define或其它形式定义，方便修改，比如计费规则，温度变化规则，时间片长短等等。**
2. **客户端尽量不负责计算，应该只有UI和通信和其它模块。**

## 4、用户客户端的工作流程（验收组内统一）

前提：服务器不知道房间当前环境温度，环境温度开始默认是25度。

1. 从UI界面手动输入房间号
2. 开机，发送开机请求。
3. 开机后发送请求服务器实时更新费用的请求包，只在开机时附带发送一次。
4. 接收服务器的ACK，告知当前服务状态和默认风速和默认温度。UI界面应该告知当前服务状态，默认风速和默认温度。
5. 若收到消息处于服务状态或转变为服务状态，首先客户端回回一个ACK501包说明现在的环境温度，然后服务器会定期发送总费用和服务器根据温度变化规则计算得到的房间环境温度发给客户端，客户端修改UI界面上的环境温度和费用信息（房间的总费用）。
6. 若处于等待状态，服务器会告知等待时间，等待转为服务状态。
7. 用户点击UI界面上的关闭按钮，发送关闭请求，关闭后启动回温程序。

### 4.1回温程序

回温程序指在默认情况下模拟房间室温的自动变化过程。在房间关闭空调或者房间处于等待队列中，经过讨论无论冬夏都是默认回到24度。默认是1分钟回1度，等待小组内统一。


   ## 5、其它客户端和服务器的逻辑

和我们自己设计的一致即可。

## 6、酒店客户端的UI

可以一个界面是3个用户的面板，也可以是根据用户切换面板。

## 7、分工

每个人基本会被分到2-3个任务，分到2个任务的基本都有一个量比较大的任务，后面再看任务比较少的可以分配写文档的任务。

- 程年智 服务器的逻辑代码部分和UI部分。
- 李玉慧 酒店客户端的UI（经理和管理员），酒店客户端对应经理的逻辑部分。
- 李卓 酒店客户端的对应管理员的逻辑部分，酒店客户端的通信部分，用户客户端的通信部分。
- 刘凡 用户客户端的UI部分， 酒店客户端的UI（前台），用户客户端的逻辑部分。
- 高进 酒店客户端的对应前台的逻辑部分，服务器的通信和数据库部分。

周四（6.4）前负责逻辑部分成员需要建立好所有的类和方法的空壳并上传。周末大家多花点时间尽量早点完成。

