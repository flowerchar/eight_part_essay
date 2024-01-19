# 八股文

## 一、计算机网络

### 1.1 HTTP、HTTPS、DNS协议

#### 1.1.1 TCP、UDP属于什么层

1. 为什么要分层？

   分层设计：不同层实现不同功能   **类比**  函数设计：函数体不能太长![image-20240114164206578](README.assets/image-20240114164206578.png)

2. OSI七层作用![image-20240114164842182](README.assets/image-20240114164842182.png)

3. OSI七层与TCP/IP四层对应关系以及所用协议![image-20240114165212225](README.assets/image-20240114165212225.png)

4. 每一层的数据结构![image-20240114165555126](README.assets/image-20240114165555126.png)

5. 网络层特点![image-20240114170018905](README.assets/image-20240114170018905.png)

6. 传输层特点![image-20240114170511487](README.assets/image-20240114170511487.png)

7. 应用层特点![image-20240114170808622](README.assets/image-20240114170808622.png)

> 面试题
>
> ​	1.TCP、UDP、IP协议分别属于什么层
>
> ​	2.网络中传输层有什么作用？它有哪些协议

#### 1.1.2 HTTP1.0、1.1、2.0有什么区别

1. 各版本一些区别![image-20240114211129299](README.assets/image-20240114211129299.png)
2. keep-alive长连接的好处![image-20240114211528152](README.assets/image-20240114211528152.png)
3. HTTP2.0![image-20240114212159623](README.assets/image-20240114212159623.png)头部压缩通过哈夫曼编码和字典实现 ![image-20240114212535809](README.assets/image-20240114212535809.png)![image-20240114212811848](README.assets/image-20240114212811848.png)

> 1. 简述HTTP1.0，1.1，2.0的主要区别
> 2. HTTP头Connection:Keep-alive是什么意思？解决了什么问题？

#### 1.1.3 HTTP状态码

1. HTTP报文结构![image-20240114213711362](README.assets/image-20240114213711362.png)

>  比如一个场景
>
> GET https://www/baidu.com HTTP/1.1
>
> Accept-Encoding:gzip
>
> Accept-Language:zh-CN
>
> {
>
> ​	"page":1,
>
> ​	"pageSize":5
>
> }

2. HTTP请求方法![image-20240114214622447](README.assets/image-20240114214622447.png)![image-20240114214926779](README.assets/image-20240114214926779.png)![image-20240114215051551](README.assets/image-20240114215051551.png)

3. 幂等操作：指对同一资源的多次操作，其结果与执行一次操作的效果相同

   幂等函数：指对于相同的输入值，多次调用函数的结果与单次调用的结果相同

4. HTTP状态码![image-20240114215721734](README.assets/image-20240114215721734.png)
5. 一些常见的状态码![image-20240114215810839](README.assets/image-20240114215810839.png)![image-20240114220030539](README.assets/image-20240114220030539.png)![image-20240114220130937](README.assets/image-20240114220130937.png)![image-20240114220239960](README.assets/image-20240114220239960.png)
6. 网关分配资源![image-20240114220428802](README.assets/image-20240114220428802.png)

#### 1.1.4 对称加密和非对称加密

1. 一种安全传输模型![image-20240114221130988](README.assets/image-20240114221130988.png)
2. 古典密码学是通过一一映射的，但是可以通过频率统计出来
3. 对称加密![image-20240114221754553](README.assets/image-20240114221754553.png)
4. 非对称加密![image-20240114222011886](README.assets/image-20240114222011886.png)![image-20240114222213288](README.assets/image-20240114222213288.png)
5. 对比![image-20240114222241004](README.assets/image-20240114222241004.png)
6. 哈希散列不是加密算法，因为哈希是单向的，不具备解密能力。即使通过哈希函数将用户密码保存进数据库了，也有风险被黑客破解(时间暴力枚举等等)，这时可以在哈希之前**加盐**，加盐就是在进行哈希散列的时候自定义一个字符串，将该字符串和原密码拼接，最后将这个整体一起哈希散列，加大破译难度

#### 1.1.5 HTTPS加密认证--TLS技术

1. HTTP与HTTPS对比![image-20240115144611553](README.assets/image-20240115144611553.png)
2. TLS![image-20240115144735107](README.assets/image-20240115144735107.png)
3. 数字证书，类似身份证，使用非对称加密![image-20240115144959134](README.assets/image-20240115144959134.png)![image-20240115145346936](README.assets/image-20240115145346936.png)![image-20240115145617334](README.assets/image-20240115145617334.png)



#### 1.1.6 域名系统DNS

1. 进程服务：IP+端口，比如115.182.41.180:443，但是这样太难记住了，那么![image-20240115150112576](README.assets/image-20240115150112576.png)
2. 域名工作原理
   1. 域名由点、字母、数字组成
   2. 点分隔不同域
   3. 域名分为顶级域、二级域、三级域
   4. 比如 www.baidu.com，www是三级域、baidu是二级域、com是顶级域
3. 那么这些域就组成了一棵树![image-20240115151012491](README.assets/image-20240115151012491.png)
4. DNS会优先在本机hosts文件里查找是否有映射，然后通过迭代或者递归查询![image-20240115151714909](README.assets/image-20240115151714909.png)



#### 1.1.7 DNS攻击

1. 比如我们请求的url是www.baidu.com，但是经过DNS解析后返回的是www.twly.com，将正常站点解析到恶意页面(赚取游戏推广费等等)
2. DNS劫持![image-20240115152527297](README.assets/image-20240115152527297.png)
3. DNS欺骗![image-20240115152721244](README.assets/image-20240115152721244.png)
4. DDos攻击是大量请求DNS解析服务器，使得网络或者系统资源耗尽，让服务中断或者停止，这样其他用户就无法正常访问了，防范手段：
   1. DNS服务商角度：提高本机安全些
   2. 个人角度：选择更加权威的服务商



### 1.2 IP、TCP、UDP协议

#### 1.2.1 TCP、UDP的区别 

1. UDP协议 ![image-20240115164038894](README.assets/image-20240115164038894.png)
2. TCP协议![image-20240115164340063](README.assets/image-20240115164340063.png)![image-20240115164529052](README.assets/image-20240115164529052.png)![image-20240115164642844](README.assets/image-20240115164642844.png)![image-20240115164814225](README.assets/image-20240115164814225.png)![image-20240115164905416](README.assets/image-20240115164905416.png)
3. UDP vs TCP![image-20240115202208905](README.assets/image-20240115202208905.png)![image-20240115202530246](README.assets/image-20240115202530246.png)![image-20240115202623372](README.assets/image-20240115202623372.png)应用场景![image-20240115202854995](README.assets/image-20240115202854995.png)DNS通常处理大量的短期请求，而且这些请求的响应需要在短时间内迅速返回。UDP是无连接的，没有复杂的握手和确认过程，因此在速度和效率方面比TCP更合适。 DNS服务器通常面对的是大量的短暂请求，而非大量长连接。UDP在这种情境下更为适用，因为它允许更高的并发连接数量。



#### 1.2.2 TCP三次握手

1. 三次握手图解![image-20240115203844016](README.assets/image-20240115203844016.png)![image-20240115203952077](README.assets/image-20240115203952077.png)
2. 异常情况![image-20240115204115983](README.assets/image-20240115204115983.png)如果是两次握手，那么如果因为滞慢等原因没有及时传达，那就建立起两次连接，造成资源浪费![image-20240115204345703](README.assets/image-20240115204345703.png)如果是三次握手，就会保证建立的连接是可靠的、无差错的![image-20240115204513506](README.assets/image-20240115204513506.png)

#### 1.2.3 TCP四次挥手

1. TCP的释放![image-20240115205241565](README.assets/image-20240115205241565.png)![image-20240115205702419](README.assets/image-20240115205702419.png)
2. TIME-WAIT![image-20240115205849898](README.assets/image-20240115205849898.png)![image-20240115210155394](README.assets/image-20240115210155394.png)
3. TCP可靠运输-滑动窗口

4. 停止-等待协议![image-20240115210919135](README.assets/image-20240115210919135.png)![image-20240115210947631](README.assets/image-20240115210947631.png)
5. ARQ协议![image-20240115211043012](README.assets/image-20240115211043012.png)![image-20240115211944956](README.assets/image-20240115211944956.png)![image-20240115212008938](README.assets/image-20240115212008938.png)![image-20240115212040862](README.assets/image-20240115212040862.png)
6. 滑动窗口使得信息传递不再是串联，提高了速度![image-20240115212109616](README.assets/image-20240115212109616.png)



#### 1.2.4 TCP拥塞避免算法

1. 定义：![image-20240116145145135](README.assets/image-20240116145145135.png)拥塞是很多原因引发的，是一个全局问题
2. 慢开始与拥塞避免![image-20240116150643218](README.assets/image-20240116150643218.png)![image-20240116150914160](README.assets/image-20240116150914160.png)
3. 快重传与快恢复![image-20240116151118924](README.assets/image-20240116151118924.png)![image-20240116151242875](README.assets/image-20240116151242875.png)![image-20240116151431357](README.assets/image-20240116151431357.png)

#### 1.2.5 TCP粘包原理

1. 粘包并不是TCP协议造成的，而是应用层协议设计缺陷造成的
2. 应用层数据拆分
   1. 基于长度的标识
   2. 基于特殊分隔符
3. Nagle算法![image-20240116152757879](README.assets/image-20240116152757879.png)
4. 总结![image-20240116153111066](README.assets/image-20240116153111066.png)
5. TCP协议安全性
   1. SYN flood攻击，攻击方即是主动发送方![image-20240116153544531](README.assets/image-20240116153544531.png)
   2. 资源耗尽类攻击![image-20240116153742730](README.assets/image-20240116153742730.png)
   3. 协议特性漏洞攻击![image-20240116153858389](README.assets/image-20240116153858389.png)
   4. 防范手段![image-20240116154956937](README.assets/image-20240116154956937.png)

#### 1.2.6 虚拟专用网VPN

1. 场景
   1. 公司内网
   2. 校园网
   3. 工业专用网
2. 专用IP地址![image-20240116160517599](README.assets/image-20240116160517599.png)
3. 工作原理![image-20240116160816494](README.assets/image-20240116160816494.png)

## 二、操作系统

### 2.1 进程、线程和协程

#### 2.1.1 进程

1. 演进历史![image-20240116163731100](README.assets/image-20240116163731100.png)
2. 多道程序设计
   1. 在计算机内存中同时存放多个程序
   2. 在计算机的管理程序之下相互穿插运行 
   3. 用户无需面向硬件接口编程
   4. IO设备管理软件，提供读写接口
   5. 文件管理软件，提供操作文件接口
   6. **操作系统实现了对计算机硬件资源的管理和抽象**
3. 怎么隔离资源？调度程序？提高利用率？![image-20240116164341340](README.assets/image-20240116164341340.png)![image-20240116164928483](README.assets/image-20240116164928483.png)



#### 2.1.2 同步与异步

1. 五状态模型：创建、就绪、终止、阻塞、运行![image-20240116165226422](README.assets/image-20240116165226422.png)![image-20240116165313044](README.assets/image-20240116165313044.png)![image-20240116165339177](README.assets/image-20240116165339177.png)![image-20240116165511707](README.assets/image-20240116165511707.png)关系图如上，创建状态如下![image-20240116165637188](README.assets/image-20240116165637188.png)![image-20240116165715693](README.assets/image-20240116165715693.png)终止状态如上，完整关系图如下![image-20240116165754243](README.assets/image-20240116165754243.png)
2. 阻塞、非阻塞、同步、异步![image-20240116170247663](README.assets/image-20240116170247663.png)阻塞是由同步造成的![image-20240116170405771](README.assets/image-20240116170405771.png)一些常见的阻塞情况![image-20240116170535669](README.assets/image-20240116170535669.png)非阻塞的情况![image-20240116170639660](README.assets/image-20240116170639660.png)非阻塞就是通顺，是多路并行，是高效异步



#### 2.1.3  进程和线程的区别

1. 线程是什么![image-20240116183205748](README.assets/image-20240116183205748.png)![image-20240116183549081](README.assets/image-20240116183549081.png)线程共享进程资源![image-20240116183656089](README.assets/image-20240116183656089.png)二者对比![image-20240116183741616](README.assets/image-20240116183741616.png)多线程就可以充分利用CPU的资源![image-20240116183943097](README.assets/image-20240116183943097.png)



#### 2.1.4 用户态和内核态

1. 操作系统资源管理
   1. 处理器资源
   2. IO设备资源
   3. 存储器资源
   4. 文件资源
2. Linux设计
   1. 对不同操作赋予不同的执行等级
   2. 与系统相关的特别操作必须由最高权限完成
3. 内核态![image-20240116185043922](README.assets/image-20240116185043922.png)
4. 用户态![image-20240116185142731](README.assets/image-20240116185142731.png)
5. 二者切换的时机![image-20240116185521975](README.assets/image-20240116185521975.png)



#### 2.1.5 IO密集服务

1. 计算密集型![image-20240116190212859](README.assets/image-20240116190212859.png)
2. IO密集型![image-20240116190346968](README.assets/image-20240116190346968.png)
3. 对于计算密集型，应该使用多线程去充分利用CPU资源。对于IO密集，提升多线程效率已经没什么用了，但是可以提高硬盘读写速度
4. 服务部署![image-20240116191154618](README.assets/image-20240116191154618.png)



#### 2.1.6 协程

1. 上下文切换![image-20240116191918430](README.assets/image-20240116191918430.png)![image-20240116192024572](README.assets/image-20240116192024572.png)上下文切换势必有资源开销，那么进程与进程间的切换肯定是最大的![image-20240116192354852](README.assets/image-20240116192354852.png)
2. 协程![image-20240116192507037](README.assets/image-20240116192507037.png)协程的本质是用户级线程，一般的线程是内核级线程
3. 为什么协程叫做协作式线程？因为协程之间是相互让步、相互协作的。由用户自行调度，内核无法干涉。线程对协程是一对多
4. 协程优缺点![image-20240116193038369](README.assets/image-20240116193038369.png)![image-20240116193207653](README.assets/image-20240116193207653.png)

### 2.2 存储系统详解

#### 2.2.1 缓存

1. 层次结构![image-20240117144111314](README.assets/image-20240117144111314.png)
2. 局部性原理![image-20240117144139745](README.assets/image-20240117144139745.png)![image-20240117144257580](README.assets/image-20240117144257580.png)![image-20240117144449127](README.assets/image-20240117144449127.png)![image-20240117144531640](README.assets/image-20240117144531640.png)
3. 缓存的设计![image-20240117144838439](README.assets/image-20240117144838439.png)

#### 2.2.2 虚拟内存

1. 概述![image-20240117145225919](README.assets/image-20240117145225919.png)![image-20240117145306464](README.assets/image-20240117145306464.png)![image-20240117145546399](README.assets/image-20240117145546399.png)![image-20240117145813190](README.assets/image-20240117145813190.png)![image-20240117145922380](README.assets/image-20240117145922380.png)
2. 当缓存没有数据时![image-20240117150046494](README.assets/image-20240117150046494.png)
3. 当主存没有数据时![image-20240117150154608](README.assets/image-20240117150154608.png)
4. 总结![image-20240117150246179](README.assets/image-20240117150246179.png)

#### 2.2.3 缺页中断

1. 操作系统如何管理进程空间
2. 内存管理
   1. 页式存储管理
   2. 段氏存储管理
   3. 段页式存储管理
3. 页式存储管理![image-20240117150733780](README.assets/image-20240117150733780.png)![image-20240117150838780](README.assets/image-20240117150838780.png)![image-20240117151001416](README.assets/image-20240117151001416.png)![image-20240117151142749](README.assets/image-20240117151142749.png)![image-20240117151248972](README.assets/image-20240117151248972.png)
4. 段氏存储管理![image-20240117151347761](README.assets/image-20240117151347761.png)![image-20240117151517826](README.assets/image-20240117151517826.png)
5. 段页式存储管理![image-20240117151557250](README.assets/image-20240117151557250.png)![image-20240117151643189](README.assets/image-20240117151643189.png)![image-20240117151730254](README.assets/image-20240117151730254.png)
6. 缺页中断![image-20240117152021305](README.assets/image-20240117152021305.png)系统调用属于内核态

#### 2.2.4 页面置换算法

1. 页面置换时机![image-20240117152343829](README.assets/image-20240117152343829.png)
2. 缓存置换算法
   1. 先进先出 FIFO
   2. 最近最少使用 LRU
   3. 最不经常使用 LFU
3. 先进先出，类似队列![image-20240117152756402](README.assets/image-20240117152756402.png)
4. 最不经常使用 ![image-20240117152929094](README.assets/image-20240117152929094.png)![image-20240117153010386](README.assets/image-20240117153010386.png)![image-20240117153107778](README.assets/image-20240117153107778.png)
5. 最近最少使用![image-20240117153135926](README.assets/image-20240117153135926.png)![image-20240117153345148](README.assets/image-20240117153345148.png)跟FIFO类似，但FIFO是严格的队列。而LRU是会“插队”的  



#### 2.2.5 软链接与硬链接

1. 常见文件系统![image-20240117153632232](README.assets/image-20240117153632232.png)
2. FAT![image-20240117153803559](README.assets/image-20240117153803559.png)![image-20240117153927688](README.assets/image-20240117153927688.png)
3. NTFS![image-20240117154012553](README.assets/image-20240117154012553.png)
4. EXT![image-20240117154042291](README.assets/image-20240117154042291.png)![image-20240117154145678](README.assets/image-20240117154145678.png)![image-20240117154206851](README.assets/image-20240117154206851.png)![image-20240117154232871](README.assets/image-20240117154232871.png)![image-20240117154256178](README.assets/image-20240117154256178.png)![image-20240117154419043](README.assets/image-20240117154419043.png)![image-20240117154447630](README.assets/image-20240117154447630.png)![image-20240117154527305](README.assets/image-20240117154527305.png)![image-20240117154558633](README.assets/image-20240117154558633.png)![image-20240117154628189](README.assets/image-20240117154628189.png)
5. 软链接-硬链接![image-20240117154801762](README.assets/image-20240117154801762.png)![image-20240117154903736](README.assets/image-20240117154903736.png)![image-20240117154928309](README.assets/image-20240117154928309.png)

#### 2.2.6 磁盘冗余阵列

1. RAID是什么![image-20240117155212382](README.assets/image-20240117155212382.png)
2. RAID 0![image-20240117155327717](README.assets/image-20240117155327717.png)![image-20240117155420730](README.assets/image-20240117155420730.png)
3. RAID 1![image-20240117155537626](README.assets/image-20240117155537626.png)![image-20240117155630977](README.assets/image-20240117155630977.png)
4. RAID 5![image-20240117155655948](README.assets/image-20240117155655948.png)![image-20240117155837904](README.assets/image-20240117155837904.png)
5. RAID 10![image-20240117155907424](README.assets/image-20240117155907424.png)![image-20240117155934806](README.assets/image-20240117155934806.png)
6. 对比![image-20240117155954638](README.assets/image-20240117155954638.png)

##  三、计算机系统

### 3.1 锁、同步与通信

#### 3.1.1 死锁

1. 定义![image-20240117181512411](README.assets/image-20240117181512411.png)

2. 产生原因

   1. 竞争资源

      1. 共享资源资源数量不满足各个进程需求
      2. 各个进程之间发生资源竞争导致死锁![image-20240117181753133](README.assets/image-20240117181753133.png)

   2. 进程调度顺序不当![image-20240117181859904](README.assets/image-20240117181859904.png)

   3. 死锁的四个必要条件

      1. 互斥条件
         1. 进程对资源的使用是**排他性的使用**
         2. 某资源只能由一个进程使用，其他进程需要使用只能等待
      2. 请求保持条件
         1. 进程至少保持一个资源，又提出新的资源请求
         2. 新资源被占用，请求被阻塞
         3. 被阻塞的进程不释放自己保持的资源
      3. 不可剥夺条件
         1. 进程获得的资源在未完成使用前不能被剥夺
         2. 获得的资源只能由进程自身释放
      4. 环路等待条件![image-20240117182415356](README.assets/image-20240117182415356.png)
      5. 预防死锁方法，破坏以上原因(除开互斥)![image-20240117182616859](README.assets/image-20240117182616859.png)![image-20240117182632419](README.assets/image-20240117182632419.png)![image-20240117182738448](README.assets/image-20240117182738448.png)
      6. 银行家算法![image-20240117182901384](README.assets/image-20240117182901384.png)

#### 3.1.2 线程-进程同步问题

  1. 生产者-消费者问题![image-20240117183755020](README.assets/image-20240117183755020.png)![image-20240117183842749](README.assets/image-20240117183842749.png)![image-20240117184110616](README.assets/image-20240117184110616.png)
  2. 读者-写者问题![image-20240117184524253](README.assets/image-20240117184524253.png)![image-20240117184557267](README.assets/image-20240117184557267.png)
  3. 哲学家进餐问题![image-20240117184809397](README.assets/image-20240117184809397.png)![image-20240117184944327](README.assets/image-20240117184944327.png)
  4. 临界资源![image-20240117185128152](README.assets/image-20240117185128152.png)
  5. 原子性![image-20240117185220713](README.assets/image-20240117185220713.png)
     
      
#### 3.1.3 乐观锁、悲观锁与可重入锁

1. 特点![image-20240117185901201](README.assets/image-20240117185901201.png)![image-20240117190105231](README.assets/image-20240117190105231.png)这四个的重要性依次递增
2. 公平锁/非公平锁![image-20240117190240980](README.assets/image-20240117190240980.png)![image-20240117190348602](README.assets/image-20240117190348602.png)
3. 可重入锁/非可重入锁![image-20240117190505026](README.assets/image-20240117190505026.png)![image-20240117190556507](README.assets/image-20240117190556507.png)
4. 共享锁和排他锁![image-20240117190634806](README.assets/image-20240117190634806.png)![image-20240117190724721](README.assets/image-20240117190724721.png)读线程使用共享锁，写线程使用排他锁

​      



#### 3.1.4 线程间通信方式

1. 互斥锁![image-20240117191036226](README.assets/image-20240117191036226.png)![image-20240117191134613](README.assets/image-20240117191134613.png)![image-20240117191232828](README.assets/image-20240117191232828.png)
2. 自旋锁![image-20240117191320951](README.assets/image-20240117191320951.png)![image-20240117191355289](README.assets/image-20240117191355289.png)![image-20240117191604708](README.assets/image-20240117191604708.png)**会不会让出CPU是自旋锁与互斥锁的区别**，这样的好处是![image-20240117191654790](README.assets/image-20240117191654790.png)
3. 读写锁![image-20240117191822074](README.assets/image-20240117191822074.png)![image-20240117191915681](README.assets/image-20240117191915681.png)
4. 条件变量![image-20240117192027906](README.assets/image-20240117192027906.png)![image-20240117192122337](README.assets/image-20240117192122337.png)



#### 3.1.5 进程间通信

1. 进程与线程的区别![image-20240118122040388](README.assets/image-20240118122040388.png)因为进程间的资源是相互独立的，所以线程间通信方式不适用
2. 进程间通信的方法
   1. 管道![image-20240118122506124](README.assets/image-20240118122506124.png)![image-20240118122602502](README.assets/image-20240118122602502.png)
   2. 消息队列![image-20240118122723136](README.assets/image-20240118122723136.png)![image-20240118122812664](README.assets/image-20240118122812664.png)
   3. 共享内存![image-20240118122931583](README.assets/image-20240118122931583.png)![image-20240118123029185](README.assets/image-20240118123029185.png)
   4. 信号![image-20240118123133291](README.assets/image-20240118123133291.png)![image-20240118123212930](README.assets/image-20240118123212930.png)
   5. 套接字![image-20240118123331324](README.assets/image-20240118123331324.png)![image-20240118123408725](README.assets/image-20240118123408725.png)![image-20240118123520705](README.assets/image-20240118123520705.png)![image-20240118123601169](README.assets/image-20240118123601169.png)![image-20240118123652642](README.assets/image-20240118123652642.png)前者是server端，后者是client端



#### 3.1.6 CAS原理与无锁技术

1. 锁的弊端![image-20240118124012197](README.assets/image-20240118124012197.png)
2. CAS技术![image-20240118124132301](README.assets/image-20240118124132301.png)![image-20240118124257425](README.assets/image-20240118124257425.png)![image-20240118124337566](README.assets/image-20240118124337566.png)
3. CAS与无锁队列![image-20240118124519110](README.assets/image-20240118124519110.png)![image-20240118124634656](README.assets/image-20240118124634656.png)
4. CAS弊端![image-20240118124802618](README.assets/image-20240118124802618.png)![image-20240118124902874](README.assets/image-20240118124902874.png)解决方法：像Java一样增加一个版本号，如果发生改变那么就有变化





#### 3.1.7 分布式锁实现

1. 应用场景
   1. 订单系统，秒杀系统
   2. 积分系统，消费系统
   3. 消息中间件，服务中间件，数据发布-订阅
   4. 分布式部署：集群、微服务
   5. 服务节点之间需要通信
   6. 数据强一致要求，性能要求，并发量要求
2. redis![image-20240118125453761](README.assets/image-20240118125453761.png)![image-20240118125729734](README.assets/image-20240118125729734.png)
3. Zookeeper![image-20240118125830575](README.assets/image-20240118125830575.png)![image-20240118130130958](README.assets/image-20240118130130958.png)
4. MYSQL![image-20240118130337459](README.assets/image-20240118130337459.png)
5. 分布式锁框架![image-20240118130403787](README.assets/image-20240118130403787.png)





### 3.2 编程语言与运行原理

 #### 3.2.1 计算机层次结构

1. 一个复杂的系统应该有清洗明确的分层设计
2. 层次 ![image-20240118133809651](README.assets/image-20240118133809651.png)![image-20240118133924685](README.assets/image-20240118133924685.png)![image-20240118134023978](README.assets/image-20240118134023978.png)![image-20240118134116565](README.assets/image-20240118134116565.png)![image-20240118134213183](README.assets/image-20240118134213183.png)



#### 3.2.2 编译与解释

1. ![image-20240118135237273](README.assets/image-20240118135237273.png)
2. 编译型
   1. C/C++
   2. Object-C
   3. Golang
3. 解释型
   1. Python(像Java，不是纯粹的解释语言)
   2. Php
   3. Javascript
4. 虚拟机![image-20240118135557103](README.assets/image-20240118135557103.png)![image-20240118135746750](README.assets/image-20240118135746750.png)![image-20240118135926776](README.assets/image-20240118135926776.png)



#### 3.2.3 编译器原理

1. 编译器运行![image-20240118141507342](README.assets/image-20240118141507342.png)![image-20240118141701752](README.assets/image-20240118141701752.png)![image-20240118141811357](README.assets/image-20240118141811357.png)![image-20240118141907749](README.assets/image-20240118141907749.png)![image-20240118142024841](README.assets/image-20240118142024841.png)![image-20240118142109673](README.assets/image-20240118142109673.png)![image-20240118142226191](README.assets/image-20240118142226191.png)



#### 3.2.4 程序运行原理

1. CPU体系![image-20240118142920961](README.assets/image-20240118142920961.png)
2. 程序运行过程![image-20240118143148746](README.assets/image-20240118143148746.png)![image-20240118143228183](README.assets/image-20240118143228183.png)![image-20240118143313853](README.assets/image-20240118143313853.png)![image-20240118143354196](README.assets/image-20240118143354196.png)![image-20240118143507408](README.assets/image-20240118143507408.png)![image-20240118143934405](README.assets/image-20240118143934405.png)![image-20240118144032457](README.assets/image-20240118144032457.png)
3. JIT技术![image-20240118144207810](README.assets/image-20240118144207810.png)



#### 3.2.5 链接方式

1. 动态/静态链接![image-20240118150914773](README.assets/image-20240118150914773.png)![image-20240118151053519](README.assets/image-20240118151053519.png)

2. 目标文件![image-20240118151327733](README.assets/image-20240118151327733.png)

3. 静态链接![image-20240118151605961](README.assets/image-20240118151605961.png)

4. 动态链接![image-20240118151548514](README.assets/image-20240118151548514.png)

5. 动态链接与装载![image-20240118151740892](README.assets/image-20240118151740892.png)

6. 两者对比![image-20240118151815664](README.assets/image-20240118151815664.png)

   

## 四、算法与数据结构

### 4.1 链表、栈、队列与二叉树

#### 4.1.1 时间/空间复杂度

1. ![image-20240118153854728](README.assets/image-20240118153854728.png)
2. 取去掉系数的最高阶![image-20240118154019359](README.assets/image-20240118154019359.png)
3. ![image-20240118154225402](README.assets/image-20240118154225402.png)因为前者sum的空间就一个，只不过是经常变值而已
4. 空间跟时间相互驳斥![image-20240118154938341](README.assets/image-20240118154938341.png)



#### 4.1.2 链表

1. 定义![image-20240118155242138](README.assets/image-20240118155242138.png)
2. 链表
   1. 数据域
   2. 指针域 



#### 4.1.3 链表算法题

1. LeetCode 206.反转链表![image-20240118174203063](README.assets/image-20240118174203063.png)![image-20240118174320082](README.assets/image-20240118174320082.png)![image-20240118174331481](README.assets/image-20240118174331481.png)![image-20240118174418707](README.assets/image-20240118174418707.png)![image-20240118174426631](README.assets/image-20240118174426631.png)![image-20240118174512978](README.assets/image-20240118174512978.png)![image-20240118174542391](README.assets/image-20240118174542391.png)最后一步已经跳出循环了，但是最后一个还没有逆序
2. LeetCode 92![image-20240118180021458](README.assets/image-20240118180021458.png)TODO

## 五、数据库

### 5.1 DB、表、视图、事务与函数

#### 5.1.1 关系型数据库

1. ![image-20240118182159849](README.assets/image-20240118182159849.png)![image-20240118182408833](README.assets/image-20240118182408833.png)
2. NoSQL![image-20240118182553045](README.assets/image-20240118182553045.png)
3. key-value数据库![image-20240118182645729](README.assets/image-20240118182645729.png)
4. 文档数据库![image-20240118182916384](README.assets/image-20240118182916384.png)
5. 列存储数据库![image-20240118183005965](README.assets/image-20240118183005965.png)![image-20240118183211882](README.assets/image-20240118183211882.png)
6. 图数据库![image-20240118183306484](README.assets/image-20240118183306484.png)



#### 5.1.2 数据库设计、创建、维护

1. ![image-20240118183843236](README.assets/image-20240118183843236.png)
2. ![image-20240118184505428](README.assets/image-20240118184505428.png)
3. ![image-20240118184826881](README.assets/image-20240118184826881.png)



#### 5.1.3 数据表设计、创建、维护

1. 官方实例![image-20240118185043203](README.assets/image-20240118185043203.png)
2. ![image-20240118185247270](README.assets/image-20240118185301830.png)![image-20240118185317771](README.assets/image-20240118185317771.png)![image-20240118185541592](README.assets/image-20240118185541592.png)
3. ![image-20240118185958398](README.assets/image-20240118185958398.png)
4. ![image-20240118190233060](README.assets/image-20240118190233060.png)



#### 5.1.4 char、varchar和text

1. MYSQL类型![image-20240118191550509](README.assets/image-20240118191550509.png)
2. 数字类型![image-20240118192043075](README.assets/image-20240118192043075.png)
3. 日期类型![image-20240118192254369](README.assets/image-20240118192254369.png)
4. 字符串类型![image-20240118192329524](README.assets/image-20240118192329524.png)![image-20240118192642751](README.assets/image-20240118192642751.png)
5. JSON ![image-20240118193045305](README.assets/image-20240118193045305.png)

#### 5.1.5 数据库ACID

1. 定义![image-20240119141424236](README.assets/image-20240119141424236.png)
2. 事务处理![image-20240119141546163](README.assets/image-20240119141546163.png)
3. 原子性![image-20240119141812601](README.assets/image-20240119141812601.png)
4. 一致性![image-20240119141953303](README.assets/image-20240119141953303.png)
5. 隔离性![image-20240119142230335](README.assets/image-20240119142230335.png)
6. 持久性![image-20240119142400441](README.assets/image-20240119142400441.png)



#### 5.1.6 数据事务隔离级别

1. 级别![image-20240119142610311](README.assets/image-20240119142610311.png)
2. 脏读、不可重复读、幻读![image-20240119142816691](README.assets/image-20240119142816691.png)
3. 未提交读![image-20240119143058288](README.assets/image-20240119143058288.png)
4. 提交读![image-20240119143301665](README.assets/image-20240119143301665.png)
5. 可重复读![image-20240119143454421](README.assets/image-20240119143454421.png)
6. 串行读![image-20240119143611053](README.assets/image-20240119143611053.png)![image-20240119143654598](README.assets/image-20240119143654598.png)
7. 总结![image-20240119143728070](README.assets/image-20240119143728070.png)



### 5.2 索引、性能和安全

#### 5.2.1 MySQL索引

1. ![image-20240119144119016](README.assets/image-20240119144119016.png)
2. 二叉搜索树、多叉树![image-20240119144422792](README.assets/image-20240119144422792.png)![image-20240119144620378](README.assets/image-20240119144620378.png)![image-20240119144727329](README.assets/image-20240119144727329.png)
3. B、B+树![image-20240119144939491](README.assets/image-20240119144939491.png)![image-20240119145023517](README.assets/image-20240119145023517.png)
4. 为什么是B+树![image-20240119145148234](README.assets/image-20240119145148234.png)



#### 5.2.2  聚簇/非聚簇索引

1. 索引![image-20240119145439218](README.assets/image-20240119145439218.png)
2. 存储区层次![image-20240119145621940](README.assets/image-20240119145621940.png)
3. 聚簇索引![image-20240119145724283](README.assets/image-20240119145724283.png)![image-20240119145949291](README.assets/image-20240119145949291.png)
4. 非聚簇索引![image-20240119150106525](README.assets/image-20240119150106525.png)
5. InnoDB的聚簇与非聚簇![image-20240119150248855](README.assets/image-20240119150248855.png)![image-20240119150419926](README.assets/image-20240119150419926.png)![image-20240119150504673](README.assets/image-20240119150504673.png)
6. 聚簇优点![image-20240119150545624](README.assets/image-20240119150545624.png)
7. 注意事项![image-20240119151451391](README.assets/image-20240119151451391.png)



#### 5.2.3 联合索引原理

1. 定义![image-20240119152745909](README.assets/image-20240119152745909.png)![image-20240119153003086](README.assets/image-20240119153003086.png)
2. 联合索引使用与Where顺序无关![image-20240119154701285](README.assets/image-20240119154701285.png)



#### 5.2.4 MVCC原理

TODO

#### 5.2.5 MYSQL日志类型



#### 5.2.6 MySQL权限维护

1. 权限粒度![image-20240119155409671](README.assets/image-20240119155409671.png)![image-20240119155622804](README.assets/image-20240119155622804.png)
2. 创建用户并授权![image-20240119160107556](README.assets/image-20240119160107556.png)![image-20240119160223229](README.assets/image-20240119160223229.png)![image-20240119160325626](README.assets/image-20240119160325626.png)
3. 移除授权![image-20240119160406553](README.assets/image-20240119160406553.png)
4. 用户更改![image-20240119160434292](README.assets/image-20240119160434292.png)



## 六、编程能力

### 6.1 面向对象

#### 6.1.1 面向对象思想

1. 概念![image-20240119161024327](README.assets/image-20240119161024327.png)![image-20240119161351689](README.assets/image-20240119161351689.png)![image-20240119161516199](README.assets/image-20240119161516199.png)![image-20240119161654077](README.assets/image-20240119161654077.png)![image-20240119161935102](README.assets/image-20240119161935102.png)![image-20240119162027932](README.assets/image-20240119162027932.png)![image-20240119162130195](README.assets/image-20240119162130195.png)![image-20240119162311375](README.assets/image-20240119162311375.png)



#### 6.1.2 接口

1. 概念![image-20240119185839041](README.assets/image-20240119185839041.png)![image-20240119190134674](README.assets/image-20240119190134674.png)![image-20240119190219559](README.assets/image-20240119190219559.png)![image-20240119190339203](README.assets/image-20240119190339203.png)![image-20240119190444689](README.assets/image-20240119190444689.png)



#### 6.1.3 类的实现与继承

1. 概念![image-20240119190752143](README.assets/image-20240119190752143.png)![image-20240119190859296](README.assets/image-20240119190859296.png)![image-20240119191037756](README.assets/image-20240119191037756.png)方法重写如上，二者区别![image-20240119191139773](README.assets/image-20240119191139773.png)
2. super、this![image-20240119191309862](README.assets/image-20240119191309862.png)![image-20240119191506997](README.assets/image-20240119191506997.png)



#### 6.1.4 继承的使用原则

1. 概念![image-20240119191911421](README.assets/image-20240119191911421.png)![image-20240119192201521](README.assets/image-20240119192201521.png)![image-20240119192342700](README.assets/image-20240119192342700.png)

### 6.2 设计模式

#### 6.2.1 单例模式

1. 为什么需要单例模式![image-20240119192820393](README.assets/image-20240119192820393.png)要不然需要同步全部内容![image-20240119192909467](README.assets/image-20240119192909467.png)![image-20240119193048163](README.assets/image-20240119193048163.png)
2. 实现方式![image-20240119193427676](README.assets/image-20240119193427676.png)
3. 多线程安全问题![image-20240119193556287](README.assets/image-20240119193556287.png)
4. 懒汉模式![image-20240119193718292](README.assets/image-20240119193718292.png)
5. 饿汉模式![image-20240119193932250](README.assets/image-20240119193932250.png)



#### 6.2.2 建造者模式

1. 为什么需要建造者模式![image-20240119194146577](README.assets/image-20240119194146577.png)
2. 突破了数量、顺序的限制![image-20240119194808921](README.assets/image-20240119194808921.png)



#### 6.2.3 适配器模式

1. 为什么需要适配器![image-20240119195317079](README.assets/image-20240119195317079.png)两个类之间不能直接联系在一起，可以做一个适配器承上启下。比如插座跟手机之间不能直接充电，不可能直接给插座或者手机外接一个充电线，充电器就是中间的适配器
2. 适配器优劣![image-20240119195936063](README.assets/image-20240119195936063.png)![image-20240119200054386](README.assets/image-20240119200054386.png)



#### 6.2.4 装饰器模式

1. 为什么需要装饰器![image-20240119200215107](README.assets/image-20240119200215107.png)
2. 装饰器优劣![image-20240119200752045](README.assets/image-20240119200752045.png)





#### 6.2.5 代理模式

1. 为什么需要代理模式![image-20240119202623522](README.assets/image-20240119202623522.png)比如有五台服务器，那么就可以用一台代理控制五台机器，坐负载均衡等等事情![image-20240119203220091](README.assets/image-20240119203220091.png)![image-20240119203256248](README.assets/image-20240119203256248.png)



#### 6.2.6 设计模式原则

1. 开闭原则![image-20240119203709690](README.assets/image-20240119203709690.png)
2. 里氏替换原则![image-20240119203843028](README.assets/image-20240119203843028.png)
3. 依赖倒置原则![image-20240119204141484](README.assets/image-20240119204141484.png)
4. 单一职责原则![image-20240119204258281](README.assets/image-20240119204258281.png)
5. 接口隔离原则![image-20240119204352707](README.assets/image-20240119204352707.png)
6. 迪米特原则![image-20240119204554171](README.assets/image-20240119204554171.png)
7. 合成复用原则![image-20240119204712057](README.assets/image-20240119204712057.png)