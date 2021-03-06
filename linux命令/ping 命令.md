# ping 命令

---

利用 `ICMP`,

向对端主机发送会送请求的信息(`ICMP Echo Request Message 8`)

接收对端主机发回来的回送应答消息(`ICMP Echo Reply Message 0`).

### 简介

ping 使用的是ICMP协议,它发送icmp回送请求消息给目的主机.ICMP协议规定:目的主机必须返回ICMP回送应答消息给源主机.如果源主机在一定时间内收到应答,则认为主机可达.

### 工作过程

Ping命令会构建一个固定格式的ICMP请求数据包,然后由ICMP协议将这个数据包连同地址"xxx.xxx.xx.xx"一起交给IP层协议,IP层协议将以地址"xxx.xxx.xx.xx"作为目的地址,本机IP地址作为源地址,加上一些其他的控制信息,构建一个IP数据包,并在一个映射表中查找出IP地址"xxx.xxx.xx.xx"所对应的物理地址,一并交给数据链路层。后者构建一个数据帧,目的地址是IP层传过来的物理地址,源地址则是本机的物理地址,还要附加上一些控制信息,依据以太网的介质访问规则,将它们传送出去.

主机B收到这个数据帧后,先检查它的目的地,，并和本机的物理地址对比,如符合,则接收;否则丢弃.接收后检查该数据帧,将IP数据包从帧中提取出来,交给本机的IP层协议.同样,IP层检查后,将有用的信息提取后交给ICMP协议,后者处理后,马上构建一个ICMP应答包,发送给主机A,其过程和主机A发送ICMP请求包到主机B一模一样.

即先由IP地址,在网络层传输,然后再根据mac地址由数据链路层传送到目的主机.