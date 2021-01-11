# Practical Skill

## 0. Linux Command

### 0.0 netstat(适用Windows)

#### 说明

`netstat`（network statistics）是在内核中访问**网络连接状态**及其相关信息的命令行程序，可以显示**路由表**、实际的网络连接和**网络接口**设备的状态信息，以及与 IP、TCP、UDP 和 ICMP 协议相关的统计数据，一般用于检验本机各端口的网络服务运行状况。

#### 命令选项

- `-t`、`-u`，分别为显示出 `TCP` 与 `UDP` 协议的套接字链接，可同`-a`一起使用
- `-n`,  禁用反向域名解析，加快查询速度

> 默认情况下 netstat 会通过**反向域名解析**查找每个 IP 地址对应的主机名，会降低查找速度。**n** 选项可以禁用此行为，并且用户 ID 和端口号也优先使用数字显示。

- `-l` 选项可以只列出正在监听的连接（不能和 `-a` 选项同时使用） 

- `-p` 选项可以查看进程ID与进程名信息（此时 **netstat** 应尽量运行在 **root** 权限之下，否则不能得到运行在 root 权限下的进程名）

#### 返回值详解

- **state**
  - CLOSING：在TCP四次挥手期间，主动关闭端发送了FIN包后，没有收到对应的ACK包，却收到对方的FIN包，此时，进入CLOSING状态。
  - SYN_RECV：在TCP三次握手期间，被动连接端收到SYN包时，进入SYN_RECV状态。

#### 相关文档

- [netstat state 详解](https://developer.aliyun.com/article/553406)

### 0.1 ps

#### 说明

Linux中的`ps`命令是Process Status的缩写。`ps`命令用来列出系统中当前运行的那些进程。ps命令列出的是当前那些进程的快照，就是执行ps命令的那个时刻的那些进程，如果想要动态的显示进程信息，就可以使用top命令。

#### 命令选项

- `-ef`，详细列出所有进程。标准语法
- `aux`，详细列出所有进程。BSD语法
- `-a`，select all processes except both session leaders and processes not associated with a terminal

