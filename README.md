2013年秋网络程序设计
课程目标和要求
本课程的主要目标是开拓学生视野、追踪网络技术前沿，能利用开源软件hostapd、Open vSwitch实现软件定义无线网络原型系统remoteapd.

本课程紧密追踪网络技术前沿，开拓学生视野，并紧密结合工程实验项目学以致用。课程以业界前沿的软件定义网络（SDN，Software Defined Networking）为主要领域范围，以设计实现软件定义WLAN网络系统为主要目标，期间会利用hostapd、Open vSwitch、mac80211等开源软件，可能会涉及OpenFlow协议、Linux程序设计技术、OpenWRT等，要求学生有较好的动手能力并以此为基础进一步强化动手能力和系统设计与构建能力。

课程将理论与实践紧密联系起来，探索采用教学和课程项目实验相融合的教学方法。

要求选修本课程的同学，即便是最优秀的学生，也必须保证每周课外投入的上机时间也不得少于10小时，无法保证时间投入切勿选修，最好结合工程实践项目选题，以便在课程项目的基础上继续做一些创新性的探索及原型系统。

课程安排
实验答疑：18-20周周二下午1:00-5:00 思贤楼318
具体目标
精读并将The Design Philosophy of the DARPA Internet Protocols 翻译为中文
分析Open vSwitch开源软件代码
精读并将Building Programmable Wireless Networks:An Architectural Survey 翻译为中文
分析hostapd开源软件代码
实现remoteapd软件定义无线网络原型系统并Demo
课程考核办法
平时表现占40%，实验占60%
平时表现包括课堂演讲参与情况及课后准备是否充分等，也包括日常突出表现的记录
实验成绩的评分两原则：以功劳为主，没有功劳记苦劳；强调质量不强调规模。
功劳如率先调通程序、某一模块程序做到极致的规范完善、经过仔细设计的测试代码、经过精心编辑的文档等主要产出结果和突出表现为评价依据
苦劳以github上的代码文档编写提交记录为主要评价标准，github以https://github.com/mengning/stream https://github.com/mengning/remoteapd https://github.com/mengning/agentapd 三个版本库及其fork的副本为数据来源。
以个人评分为主，以小组整体为辅，鼓励良好的团队协作
课程与实验内容
实验准备：
Linux操作系统，比如VMware+Ubuntu 10.04
下载编译安装Open vSwitch，熟悉其功能配置。
使用支持AP模式的无线网卡利用hostapd在linux上配置一个无线路由器，能够支持手机等station的认证关联和自动获取IP地址连接互联网。
Keshav, How to read a paper, ACM CCR 2007
【可选】推荐购买一块无线路由器开发板，根据OpenWRT支持的无线路由器型号http://wiki.openwrt.org/toh/start 选择购买一块无线路由器自己改装即可
WZR-HP-G300NH Rev：V1的板子（孟宁）
上海贝尔rg100a-aa（刘昊）和华为hg255d （陈立立）华为hg255d的链接http://item.taobao.com/item.htm?id=10026723226
也可以使用VMware运行OpenWRT(x86)但虚拟机不支持无线设备，不如实际的无线路由器开发板有实战的感觉。
互联网基础知识和关键机制简述
DNS Naming
IP Networking
L2 Switching
TCP Overview
TCP Understanding
hostapd和dhcp3-serveAP配置指南
任务-1：精读并将The Design Philosophy of the DARPA Internet Protocols 翻译为中文
统筹整理：赵骞理
12月2日各小组提交翻译稿发到赵骞理处 1513090500@qq.com
12月6日形成一个草稿发给我，我来通知各小组下一步的工作
12月10日前各小组修订批注草稿 互联网架构的设计哲学DraftV0.9.doc （至少要仔细严格地审校本小组负责的那部分，也可以全文审校），将小组修订版发到到赵骞理处 1513090500@qq.com
12月13日将各小组的修订版统一整理形成一个完整版发给我
互联网架构的设计哲学Beta
互联网架构的设计哲学V1.0
互联网架构设计的背后逻辑及其演进趋势
D. D. Clark, The Design Philosophy of the DARPA Internet Protocols, SIGCOMM 1988
refer to 笔记TheDesignPhilosophyOfTheInternetProtocols
我所理解的“软件定义的网络” 闵应骅 中国科学院计算技术研究所
McKeown, Nick, et al. OpenFlow: enabling innovation in campus networks. ACM SIGCOMM Computer Communication Review 38.2 (2008): 69-74.
OpenFlow Whitepaper:Software-Defined Networking:The New Norm for Networks
OpenFlow Switch Specification Version 1.4.0 (Wire Protocol 0x05) October 14, 2013
下一代网络热潮：软件定义网络SDN技术
SDN & Open vSwitch
OpenStack: OVS Deep Dive Slides - The focus is on how OVS is architected and hints about how to debug it as a component of a larger system.
任务-2：分析Open vSwitch开源软件代码 openvswitch-2.0.0.tar.gz
下载编译安装Open vSwitch，熟悉其功能配置。Build Open vSwitch
Open vSwitch Documentation
OpenvSwitch 代码分析
Open vSwitch网络部分代码https://github.com/mengning/stream
编译方法：source build.env;make clean;make
面向stream.h和poll-loop.h接口编写server和client代码，先利用stream.h实现server和client之间的通信（比如发送和回传hello world），然后再利用poll-loop.h接口实现server的并发处理。在Open vSwitch中使用stream.h的位置在vconn-stream.c中，编写server和client时可以参考。
stream目录下的部分需要剔除与Open vSwitch有关的include头文件，改造util和vlog等，总之使stream目录成为一个单纯的通用的网络模块代码库。
任务-3：精读并将Building Programmable Wireless Networks:An Architectural Survey 翻译为中文
The Road to SDN: An Intellectual History of Programmable Networks 这篇文章与我们要读的文章前半部分内容基本一致，可以互为参考。
统筹整理：郭志鹏 1096121002@qq.com
请大家务必在理解的基础上翻译，更多用意译，而非用字面翻译的方式，对于新的理解要回头重新审查翻译，有更新及时发送给郭志鹏。
12月25日前将翻译稿到 1096121002@qq.com
可编程无线网络架构文献综述V0.9.doc
特邀行业专题讲座：软件定义网络SDN在云计算中的应用
主讲人：张卫峰，盛科网络软件总监，《深度解析SDN——利益、战略、技术、实践》一书的作者，数据通信和芯片设计领域资深专家，有十几年的网络实践经验，对SDN、传统二三层交换机、数据传输设备（PTN和IPRAN），从管理面到协议控制面一直到芯片转发面，都有着深刻的理解
时间：2013年12月14日上午9:00 地点：苏州仁爱路166号明德楼242室
无线网络技术及WLAN
WLAN技术专题知识
以下文档可以通过http://ishare.iask.sina.com.cn/ 搜索下载
802.11-1999.pdf 1999年版
802.11-2007.pdf 2007年修订版(Revision of IEEE Std 802.11-1999)
802.11n-2009.pdf Amendment 5：Enhancements for Higher Throughput (MIMO)
802.11s-2011.pdf Amendment 10: Mesh Networking
802.11u-2011.pdf Amendment 9: Interworking with External Networks (HotSpot 2.0)
802.11-2012.pdf 2012年修订版(Revision of IEEE Std 802.11-2007)
802.11ad-2012.pdf Amendment 3: Enhancements for Very High Throughput in the 60 GHz Band
802.11ac_D2.0 for ISO.pdf（unapproved draft） Amendment 4: Enhancements for Very High Throughput for Operation in Bands below 6 GHz （俗称5G WiFi）
任务-4：分析hostapd开源软件代码http://hostap.epitest.fi/
以nl80211为驱动使用hostapd搭建一个无线路由器，AP配置指南
SetupHostapd
以driver_nl80211.c为重点分析hostapd源代码 hostapd nl80211源代码初步导读
TODO:确定小组任务分工及统筹整理负责人
课程实验：实现remoteapd软件定义无线网络原型系统并Demo
为hostapd增加增一个底层驱动driver_nl80211ext.c，内部实现一个网络服务器 https://github.com/mengning/remoteapd
基于driver_nl80211.c驱动写一个网络客户端程序 https://github.com/mengning/agentapd
在以上两点的基础上实现原有的hostapd功能。
合并之后的参考代码框架见https://github.com/mengning/cloudap
特邀专题讲座：创新的奥秘
主讲人：邹欣，现任微软互联网工程院研发总监, 负责必应客户端的项目. 从2007 年起在各高校讲授 <现代软件工程> 课程，著有《移山之道》 和《编程之美--微软技术面试心得》。
时间：2014年1月10日下午2:00 地点：苏州仁爱路166号明德楼242室
对本课程的一些评价
网络程序这门难忘的课程终于落下帷幕了。之所以说它难忘，是因为这门课有以下几个鲜明的特点：

没有老师枯燥无味的照本宣科，而是个小组通过presentation的方式集思广益，使得枯燥的技术因为这种互动交流的方式变得鲜活起来了。
老师没有强制性地定量布置作业，而是鼓励同学尽可能地去挖掘，去探索新的知识，并且把学到的东西和大家交流，这就使得学习新知识变得积极主动，而不是被动地陷入题海中。
课程虽然定位技术前沿，但没有像技术讲座一样，满篇理论，空话，大话，而是兼顾了理论和实践，鼓励大家通过结对编程，基于github工作流的迭代开发，是软件工程的最佳实践。
并没有通过考试这种一战定生死的考察方式，而是通过多纬度，多方面去考察每个人的功劳和苦劳，使得考察结果更加准确，信服。
以上评价来自team12
2013-2014学年《网络程序设计》课程总结
本年度《网络程序设计》课程第一次采用研讨课授课模式，以阅读翻译论文文献、阅读分析开源代码、邀请行业专家做报告和完成课程设计为主要手段进行授课。

具体的课程目标任务清单如下：
精读并将The Design Philosophy of the DARPA Internet Protocols 翻译为中文
分析Open vSwitch开源软件代码
精读并将Building Programmable Wireless Networks:An Architectural Survey 翻译为中文
分析hostapd开源软件代码
实现remoteapd软件定义无线网络原型系统并Demo
特邀行业专题讲座：软件定义网络SDN在云计算中的应用 主讲人：张卫峰，盛科网络软件总监，《深度解析SDN——利益、战略、技术、实践》一书的作者，数据通信和芯片设计领域资深专家，有十几年的网络实践经验，对SDN、传统二三层交换机、数据传输设备（PTN和IPRAN），从管理面到协议控制面一直到芯片转发面，都有着深刻的理解
特邀专题讲座：创新的奥秘 主讲人：邹欣，现任微软互联网工程院研发总监, 负责必应客户端的项目. 从2007 年起在各高校讲授 <现代软件工程> 课程，著有《移山之道》 和《编程之美--微软技术面试心得》。
课程考核办法：
采用开源社区开发模式以记录代码、文档等实际贡献为主要衡量标准，强调竞争性的原创和首创机制，在记录功劳的基础上适当考虑苦劳和学生自身的成长增量。
授课感想：
学生的潜力无穷的，要求的多收获的多，不管标准有多高总有学生能接近你定的标准；以Top前20%为授课对象定标准，其余80%学生的成长增量要比以80%的学生定标准带来的增量更多，背后的原因值得思考：通往高标准的阶梯比高标准本身更重要，没有什么比无从下手目标遥不可及更打击一个人的努力热情的了。
参考资料
[1]Vestin, Jonathan, Peter Dely, Andreas Kassler, Nico Bayer, Hans Einsiedler, and Christoph Peylo. Cloudmac: towards software defined WLANs. ACM SIGMOBILE Mobile Computing and Communications Review 16, no. 4 (2013): 42-45. 及涉嫌一稿多投的另外一篇文章[1+]Dely, Peter, Jonathan Vestin, Andreas Kassler, Nico Bayer, Hans Einsiedler, and Christoph Peylo. "CloudMAC—An OpenFlow based architecture for 802.11 MAC layer processing in the cloud." In Globecom Workshops (GC Wkshps), 2012 IEEE, pp. 186-191. IEEE, 2012.CloudMAC架构分析，CloudMAC实际上将无线网卡（即WTP）收到的frame通过隧道传输到服务端（即VAP）来进行处理，估计没有实现OpenFlow Switch的转发机制，只是在最简化的情况下测评网络性能。
[2]Suresh, Lalith, Julius Schulz-Zander, Ruben Merz, Anja Feldmann, and Teresa Vazao. Towards programmable enterprise WLANs with Odin. In Proceedings of the first workshop on Hot topics in software defined networks, pp. 115-120. ACM, 2012.Odin架构分析，Odin使用The Click Modular Router Project 来实现physical AP，即Odin Agent，使用the Floodlight OpenFlow controller 来实现Odin Master，在Odin系统下可以支持多Light Virtual AP (LVAP)。
[3]https://openwrt.org/
[4]http://www.openflow.org/
[5]http://hostap.epitest.fi/hostapd/
[6]http://conferences.sigcomm.org/sigcomm/2012/program.php
[7]http://conferences.sigcomm.org/sigcomm/2013/hotsdn.php
[8]http://conferences.sigcomm.org/sigcomm/2012/hotsdn.php
[9]http://conferences.sigcomm.org/sigcomm/2013/mcc.php
[10]http://conferences.sigcomm.org/sigcomm/2012/mcc.php
[11]http://conferences.sigcomm.org/sigcomm/2013/srif.php
[12]http://www.sigmobile.org/mobicom/2013/index.html
[13]http://dl.acm.org/citation.cfm?id=2436196&picked=prox&CFID=350918785&CFTOKEN=11448596
[14]Advanced Topics in Networking http://www.stanford.edu/class/cs244/2013/timetable.html
[15]Qadir, Junaid, Nadeem Ahmed, and Nauman Ahad. Building Programmable Wireless Networks:An Architectural Survey arXiv preprint arXiv:1310.0251 (2013).
[16]http://openvswitch.org/
[17]https://www.opennetworking.org
p393-vestin.pdf - CloudMAC - Towards Software Defined WLANs (150.1 kB) 孟宁 老师, 2013-09-11 12:16
Odin-sigcomm.pdf - Towards Programmable Enterprise WLANs with Odin (631.6 kB) 孟宁 老师, 2013-09-11 12:19
Odin-Towards-programmable-enterprise-wlans.pdf - ppt of Odin (2.3 MB) 孟宁 老师, 2013-09-11 12:20
C2012-12.pdf - CloudMAC without Openflow (857.5 kB) 孟宁 老师, 2013-09-11 12:23
L2Switching.ppt - L2 Switching Overview (371 kB) 孟宁 老师, 2013-09-16 10:40
HowIPNetworking.ppt - How IP Networking (899 kB) 孟宁 老师, 2013-09-16 10:40
TheDesignPhilosophyOfTheDARPAInternetProtocols.pdf - D. D. Clark, The Design Philosophy of the DARPA Internet Protocols, SIGCOMM 1988 (1006.8 kB) 孟宁 老师, 2013-11-06 16:13
Software_Defined_Networking.ppt - Software Defined Networking (541.5 kB) 孟宁 老师, 2013-11-06 17:33
6-DNS.ppt - naming DNS (328 kB) 孟宁 老师, 2013-11-19 09:16
7-TCP.ppt - TCP overview (957.5 kB) 孟宁 老师, 2013-11-19 09:20
TCPUnderstanding.ppt - TCP Understanding (649.5 kB) 孟宁 老师, 2013-11-19 09:21
CoursePlan2013Fall.ppt (180.5 kB) 孟宁 老师, 2013-11-22 11:03
hostpad安装配置指南.doc - hostpad安装配置指南.doc (34.5 kB) 孟宁 老师, 2013-11-22 12:26
互联网架构的设计哲学DraftV0.9.doc - 互联网架构的设计哲学DraftV0.9.doc (62 kB) 孟宁 老师, 2013-12-05 11:28
test_stream.tar.gz (58.3 kB) 孟宁 老师, 2013-12-06 10:57
互联网架构的设计哲学V0.99.0.pdf - 互联网架构的设计哲学V0.99.0.pdf (285.1 kB) 孟宁 老师, 2013-12-20 11:42
hostapd和dhcp3-serve.doc (32 kB) 孟宁 老师, 2013-12-23 17:19
Hostapd-driver_nl80211源代码分析.doc - Hostapd-driver_nl80211源代码分析.doc (26 kB) 孟宁 老师, 2013-12-24 11:29
可编程无线网络架构文献综述V0.9.doc - 可编程无线网络架构文献综述V0.9.doc (150.5 kB) 孟宁 老师, 2014-01-03 17:13
我所理解的“软件定义的网络”.pdf - 我所理解的“软件定义的网络” (1.6 MB) 孟宁 老师, 2014-01-17 17:11
hostapd和dhcp3-serveAP配置指南.doc - /attachments/709/hostapd和dhcp3-serveAP配置指南.doc (32 kB) 李 旦荣, 2015-12-13 19:31