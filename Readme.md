# OpenTSN: Open source TSN

## This repository doesn't specify a license. 
## Without author's permission, this code is only for learning and cannot be used for other purposes. 

## This text is automatically translated from chinesse using automatic translation tool
#### Original Link : [https://gitee.com/opentsn/openTSN](https://gitee.com/opentsn/openTSN)


**Introduction to OpenTSN**: **OpenTSN** is a **TSN integrated verification environment** designed based on the FAST architecture. 
The main design goals include:
- (1) Based on FPGA, realize the prototype of the switch supporting TSN core functions such as 802.1AS, 802.1Qbv, 802.1Qch, 802.1Qci, etc.;
- (2) Implement TSN interface adapters that support 802.1AS, 802.1Qbv, 802.1Qci and other functions based on FPGA, and provide programming interfaces for time-sensitive applications;
- (3) Based on the above FPGA switch and adapter prototype, build a TSN experimental network;
- (4) Realize the prototype of TSN network CNC controller, support offline planning and configuration of TSN network; 
- (5) Realize the prototype of the TSN tester that supports 802.1AS, 802.1Qci and 802.1Qbv, and support the transmission, reception and performance statistics of TSN data stream and Best Effort background stream;
 - (6) Realize the TSN network remote telemetry function, which can micro-observe the time synchronization status of the TSN network, the internal queue status of the switch, etc., and provide key data for the evaluation of the TSN core implementation mechanism;
 - (7) Realize the gateway function of TSN network and IP network;

The OpenTSN environment is a ring topology that contains 6 TSN switches, as well as the TSN tester, TSN CNC, TSN-Insigt, webcam and TSN gateway connected to the topology.

**2. The OpenTSN directory structure is explained as follows.**

　　**1. bin directory** 
　　This directory is mainly used to store the files generated in the compilation of software and hardware codes. The files currently used in the OpenTSN environment are tsn_CNC, tsn_switch and tsn_insight. Users can refer to the topology diagram in the OpenTSN project introduction article for understanding:
 - **tsn_CNC**: Contains topology_info topology file and executable file tsn_CNC, used to configure the switch node, the executable file needs to be run on the Linux device, you can modify the value of sw_mac and host_mac in the topology file to control the mac and host of the switch mac to configure.
 - **Tsn_switch**: contains the firmware file BOOT.bin generated by the hardware code. Users only need to replace this file with the original BOOT.bin file in openbox to use it as a TSN switch node.
 - **Tsn_insight**: The executable file tsn_insight is stored, which needs to be run on the Linux device in the Qt environment to display the interface.

　　**2. doc directory**
This directory is mainly used to store documents, including operation manuals, design documents and configuration files: 
- **Design documents:** include design documents of software and hardware,    software includes design documents of tsc_CNC and tsn_insight, and hardware includes detailed design documents of FTS hardware.
- **Operation Manual:** Contains the OpenTSN operation manual, which introduces the architecture of the open source code so that users can quickly understand the structure of OpenTSN.
- **Configuration documents:** Contains OpenTSN configuration documents, introducing how to set up the environment, introducing how to configure the device, etc., which can help users build an OpenTSN environment.

　　**3. src directory**
 The src directory user stores the source code used to store software and hardware:
 - **Software code**: Contains the source code of tsn_CNC and tsn_insight. The tsn_CNC source code is implemented in C language and needs to be compiled in a Linux device to generate an executable file tsn_CNC.
   tsn_insight is implemented in C++, and it needs to be compiled to  generate an executable file tsn_insight in the Linux device where Qt  is installed. The executable files generated in the software code are all copied to the bin directory.
 - **Hardware code**: The hardware code contains the um logic code and bit stream file of the tsn switch node. The um code is the core part of the hardware of the tsn switch node, and it forms the entire FPGA hardware logic with FPGA-OS. The bit stream is a binary file generated by compiling the entire FPGA hardware logic, and the BOOT.bin used by the tsn switching node can be generated through the bit stream.

　　**4. Tool catalog**
Contain tools used in the OpenTSN environment, including ANT tester and flow analyzer.
- **ANT tester:** The operating platform is openbox. This tool is mainly used for packet sending and network delay. It can send TSN streams (the priority of VLAN header is 6/7), and it can also send bandwidth reservation streams (the priority of VLAN header is 3, 4,5), you can also send a best-effort forwarding stream. A loopback connection is needed to test the delay of the flow in the network. Users only need to replace BOOT.bin in the directory with BOOT.bin in the original openbox, and run the executable file ant to test the stream. The GUI is the interface of the tester, which can dynamically discount and  display the specific conditions of the flow delay. It needs to be run on a Linux device with Qt software installed.
 - **Traffic analyzer:** The operating platform is openbox. The function of this tool is to receive messages and analyze the messages, and then send the analysis results to tsn_insight through the socket. Different ports are used to distinguish received packets, such as beacon packets, and calculate the accuracy of time synchronization after receiving them, and then send them to tsn_insight. The user only needs to replace BOOT.bin in the directory with BOOT.bin in the original openbox, and then run tsn_NA.

　　**5. sys directory**
This item mainly stores system-related files, including the contents of the TF card used in the fast system and openbox devices: 
 - **Fast:** Contains the development files of the openbox device platform. Mainly include fast_lib and fast_os. FPGA OS implements platform-related FPGA processing logic, and provides basic services for user logic. Services include: 1) packet reception and transmission; 2) high-performance DMA support; 3) packet output control; 4) management control Pass control. FAST_LIB realizes the virtual exchange of packets between FAST UA and FAST pipeline modules. Shield the difference of hardware platform from FAST UA and provide programming API. Functions include: 1) FAST packet and SK_Buf conversion; 2) Kernel and user space communication; 3) FPGA OS  configuration management; 4) FAST pipeline configuration management, etc.
 - **TF card:** the files needed for standard openbox operation, users only need to replace the BOOT.bin file and restart to complete the replacement of the hardware logic.
