一、OpenTSN简介
<<<<<<< HEAD
penTSN是基于FAST架构设计的TSN集成验证环境，主要设计目标包括
=======

OpenTSN是基于FAST架构设计的TSN集成验证环境，主要设计目标包括：	
（1）基于FPGA实现支持802.1AS 、802.1Qbv，802.1Qch，802.1Qci等TSN核心功能的交换机原型；
（2）基于FPGA实现支持802.1AS 、802.1Qbv，802.1Qci等功能的TSN接口适配器，同时为时间敏感应用提供编程接口；
（3）基于上述FPGA交换机和适配器原型，搭建TSN实验网络；
（4）实现TSN网络CNC控制器原型，支持对TSN网络的离线规划和配置；
（5）实现支持802.1AS 、802.1Qci和802.1Qbv的TSN测试仪原型，支持TSN数据流、Best Effort背景流的发送、接收和性能统计；
（6）实现TSN网络远程遥测功能，可微观观测TSN网络时间同步状态，交换机内部队列状态等，为TSN核心实现机制评估提供关键数据；
（7）实现TSN网络与IP网络的网关功能；
　　OpenTSN环境是包含6个TSN交换机的环形拓扑，以及连接在拓扑上的TSN测试仪，TSN CNC，TSN-Insigt，网络摄像头和TSN网关组成。


>>>>>>> 85cbe0f2ab09e664422371b4690667dba500827f
