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

##  三、计算机系统

## 四、算法与数据结构

## 五、数据库

## 六、编程能力