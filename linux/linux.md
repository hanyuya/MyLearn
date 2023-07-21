# Linux

## VM与Linux的安装

详见：[VM与Linux的安装](.\file\linux)

## Linux文件与目录结构

### Linux文件

Linux系统中一切皆文件。
###  Linux目录结构
![目录](.\picture\linux\文件与目录结构1.png)

![目录结构](D:\Typora笔记\笔记\linux\picture\linux\文件与目录结构2.png)

![目录结构1](D:\Typora笔记\笔记\linux\picture\linux\文件与目录结构3.png)

![目录结构2](D:\Typora笔记\笔记\linux\picture\linux\文件与目录结构4.png)

![目录结构3](D:\Typora笔记\笔记\linux\picture\linux\文件与目录结构5.png)

![目录结构4](D:\Typora笔记\笔记\linux\picture\linux\文件与目录结构6.png)

![目录结构5](D:\Typora笔记\笔记\linux\picture\linux\文件与目录结构7.png)

## VI/VIM编辑器

### vim是什么

VI是Unix操作系统和类Unix操作系统中最通用的文本编辑器。

VIM编辑器是从VI发展出来的一个性能更强大的文本编辑器。可以主动的以字体颜色辨别语法的正确性，方便程序设计。VIM与VI编辑器完全兼容。

### 一般模式
以vim打开一个档案就直接进入一般模式了（这是默认的模式）。在这个模式中， 你可以使用『上下左右』按键来移动光标，你可以使用『删除字符』或『删除整行』来处理档案内容， 也可以使用『复制、贴上』来处理你的文件数据。

**常用语法：**

|语法|功能描述|
|--|--|
|yy|复制光标当前一行|
|y数字y|复制一段（从第几行到第几行）|
|p|箭头移动到目的行粘贴|
|u|撤销上一步|
|dd|删除光标当前行|
|d数字d|删除光标（含）后多少行|
|x|删除一个字母，相当于del，向后删|
|X|删除一个字母，相当于Backspace，向前删|
|yw|复制一个词|
|dw|删除一个词|
|shift+^|移动到行头|
|shift+$|移动到行尾|
|gg或者1+G|移动到页头|
|G|移动到页尾|
|数字+G（先输入数字，在按G）|移动到目标行|
|[Ctrl] + [f]|屏幕『向下』移动一页，相当于 [Page Down]按键 (常用)|
|[Ctrl] + [b]|屏幕『向上』移动一页，相当于 [Page Up] 按键 (常用)|
|[Ctrl] + [d]|屏幕『向下』移动半页|
|[Ctrl] + [u]|屏幕『向上』移动半页|

### 编辑模式
 - **在一般模式中可以进行删除、复制、粘贴等的动作，但是无法编辑文件内容！**要等到你按下『`i, I, o, O, a, A, r,`
   `R`』等任何一个字母之后才会进入编辑模式。
 - 通常在Linux中，按下这些按键时，在**画面的左下方会出现『INSERT或 REPLACE』**的字样，此时才可以进行编辑。而如果要回到一般模式时， 则必须要按下『`Esc`』这个按键即可退出编辑模式。
 - 进入编辑模式:

 **常用语法**

|按键|功能|
|--|--|
|i|当前光标前|
|a|当前光标后|
|o|当前光标行的下一行|
|O|当前光标行的上一行|
|I|光标所在行最前|
|A|光标所在行最后|

 - 退出编辑模式
 按『`Esc`』键

### 指令模式

 - 在一般模式当中，输入『 `: / ?`』3个中的任何一个按钮，就可以将光标移动到最底下那一行。
 - 在这个模式当中， 可以提供你『搜寻资料』的动作，而读取、存盘、大量取代字符、离开 vi 、显示行号等动作是在此模式中达成的！

**基本语法**

|命令|功能|
|--|--|
|:w|保存|
|:q|退出|
|:!|强制执行|
|/ 要查找的词|n 查找下一个，向光标之下寻找，N 往上查找|
|? 要查找的词|n是查找上一个，向光标之上寻找，N是往下查找|
|:set nu|显示行号|
|:set nonu|关闭行号|
|ZZ（shift+zz）|没有修改文件直接退出，如果修改了文件保存后退出|
|:nohl|取消高亮|

### 三种模式之间的转换
![在这里插入图片描述](D:\Typora笔记\笔记\linux\picture\linux\三种模式之间的转换.png)

## 网络配置和系统管理操作

### 1 查看网络IP和网关

1. 查看虚拟网络编辑器

![查看虚拟网络编辑器](.\picture\linux\查看虚拟网络编辑器.png)

2. 修改ip地址

 ![修改ip地址](.\picture\linux\修改ip地址.png)

3. 查看网关

![查看网关](.\picture\linux\查看网关.png)

4. 查看windows环境的中VMnet8网络配置，如图1-98所示

![VMnet8](.\picture\linux\查看VMnet8.png)

![2](.\picture\linux\查看VMnet82.png)

![3](.\picture\linux\查看VMnet83.png)

![4](.\picture\linux\查看VMnet84.png)

![5](.\picture\linux\查看VMnet85.png)

### 2 配置网络ip地址

#### 2.1 ifconfig 配置网络接口

`ifconfig` :network interfaces configuring网络接口配置

1. 基本语法

`ifconfig`     （功能描述：显示所有网络接口的配置信息）

2. 案例实操

​    （1）查看当前网络ip

```powershell
[root@hadoop100 桌面]# ifconfig
```

#### 2.2 ping 测试主机之间网络连通性

1. 基本语法

​    `ping 目的主机`   （功能描述：测试当前服务器是否可以连接目的主机）

2. 案例实操

​    （1）测试当前服务器是否可以连接百度

```powershell
[root@hadoop100 桌面]# ping [www.baidu.com](http://www.baidu.com)
```

#### 2.3 修改IP地址

1. 修改IP地址

```powershell
[root@hadoop100 桌面]#vim /etc/sysconfig/network-scripts/ifcfg-eth0
```

![修改ip](.\picture\linux\修改ip.png)

以下标红的项必须修改，有值的按照下面的值修改，没有该项的要增加。

```
DEVICE=eth0                #接口名（设备,网卡）
HWADDR=00:0C:2x:6x:0x:xx   #MAC地址 
TYPE=Ethernet               #网络类型（通常是Ethemet）
UUID=926a57ba-92c6-4231-bacb-f27e5e6a9f44  #随机id
#系统启动的时候网络接口是否有效（yes/no）
ONBOOT=yes                
# IP的配置方法[none|static|bootp|dhcp]（引导时不使用协议|静态分配IP|BOOTP协议|DHCP协议）
BOOTPROTO=static      
#IP地址
IPADDR=192.168.1.100   
#网关  
GATEWAY=192.168.1.2      
#域名解析器
DNS1=114.114.114.114
DNS2=8.8.8.8
```

​    修改后，如图1-100所示

![修改配置文件](.\picture\linux\修改ip配置文件.png)

IP修改后

![](.\picture\linux\IP修改后.png)

`:wq` 保存退出

2. 执行,重启网络

   ```powershell
   service network restart
   ```


 ![重启网络](.\picture\linux\重启网络.png)

3. 如果报错，reboot，重启虚拟机

4. **使用ifconfig命令查看修改完成**

![](.\picture\linux\使用ifconfig命令查看修改完成.png)

![](.\picture\linux\打开自动连接.png)

### 3 配置主机名

#### 3.1 hostname 显示和设置系统的主机名称

1. 基本语法

`hostname`    （功能描述：查看当前服务器的主机名称）

2. 案例实操

​    （1）查看当前服务器主机名称

```powershell
[root@hadoop100 桌面]# hostname
```

#### 3.2 修改主机名称

1. 修改linux的主机映射文件（hosts文件）

（1）进入Linux系统查看本机的主机名。通过hostname命令查看

```powershell
[root@hadoop100 桌面]# hostname

hadoop100
```

（2）如果感觉此主机名不合适，我们可以进行修改。通过编辑/etc/sysconfig/network文件

```powershell
[root@hadoop100 桌面]# vi /etc/sysconfig/network

文件中内容

NETWORKING=yes

NETWORKING_IPV6=no

HOSTNAME= hadoop100
```

**注意：主机名称不要有“_”下划线**

（3）打开此文件后，可以看到主机名。修改此主机名为我们想要修改的主机名hadoop100。

（4）保存退出。

（5）打开/etc/hosts

```powershell
[root@hadoop100 桌面]# vim /etc/hosts

添加如下内容

192.168.1.100 hadoop100

192.168.1.101 hadoop101

192.168.1.102 hadoop102

192.168.1.103 hadoop103

192.168.1.104 hadoop104

192.168.1.105 hadoop105

192.168.1.106 hadoop106

192.168.1.107 hadoop107

192.168.1.108 hadoop108
```

（6）并重启设备，重启后，查看主机名，已经修改成功

2. 修改window7的主机映射文件（hosts文件）

​    （1）进入**C:\Windows\System32\drivers\etc**路径

​    （2）打开hosts文件并添加如下内容

```
192.168.1.100 hadoop100

192.168.1.101 hadoop101

192.168.1.102 hadoop102

192.168.1.103 hadoop103

192.168.1.104 hadoop104

192.168.1.105 hadoop105

192.168.1.106 hadoop106

192.168.1.107 hadoop107

192.168.1.108 hadoop108
```

3. 修改window10的主机映射文件（hosts文件）

（1）进入**C:\Windows\System32\drivers\etc**路径

（2）拷贝hosts文件到桌面

（3）打开桌面hosts文件并添加如下内容

```
192.168.1.100 hadoop100

192.168.1.101 hadoop101

192.168.1.102 hadoop102

192.168.1.103 hadoop103

192.168.1.104 hadoop104

192.168.1.105 hadoop105

192.168.1.106 hadoop106

192.168.1.107 hadoop107

192.168.1.108 hadoop108
```

（4）将桌面hosts文件覆盖**C:\Windows\System32\drivers\etc**路径hosts文件

### 4 关闭防火墙

#### 4.1 service 后台服务管理

1. **基本语法**

`service 服务名 start`         （功能描述：开启服务）

`service 服务名 stop`         （功能描述：关闭服务）

`service 服务名 restart`       （功能描述：重新启动服务）

`service 服务名 status`        （功能描述：查看服务状态）

2. 经验技巧

​    查看服务的方法：`/etc/init.d/服务名`

```powershell
[root@hadoop100 init.d]# pwd

/etc/init.d

[root@hadoop100 init.d]# ls -al
```

3. 案例实操

（1）查看网络服务的状态

```powershell
[root@hadoop100 桌面]#service network status
```

（2）停止网络服务

```powershell
[root@hadoop100 桌面]#service network stop
```

（3）启动网络服务

```powershell
[root@hadoop100 桌面]#service network start
```

（4）重启网络服务

```powershell
[root@hadoop100 桌面]#service network restart
```

（5）查看系统中所有的后台服务

```powershell
[root@hadoop100 桌面]#service --status-all
```

#### 4.2 chkconfig 设置后台服务的自启配置

1. **基本语法**

`chkconfig`           （功能描述：查看所有服务器自启配置）

`chkconfig 服务名 off`  （功能描述：关掉指定服务的自动启动）

`chkconfig 服务名 on`  （功能描述：开启指定服务的自动启动）

`chkconfig 服务名 --list` （功能描述：查看服务开机启动状态）

2. 案例实操

（1）关闭iptables服务的自动启动

```powershell
[root@hadoop100 桌面]#chkconfig iptables off
```

（2）开启iptables服务的自动启动

```powershell
[root@hadoop100 桌面]#chkconfig iptables on
```

#### 4.3 进程运行级别

Linux进程运行级别

![进程级别](.\picture\linux\linux进程运行级别.png)

#### 4.4 关闭防火墙

1. 临时关闭防火墙

（1）查看防火墙状态

```powershell
[root@hadoop100桌面]# service iptables status
```

（2）临时关闭防火墙

```powershell
[root@hadoop100桌面]# service iptables stop
```

2．开机启动时关闭防火墙

（1）查看防火墙开机启动状态

```powershell
[root@hadoop100桌面]#chkconfig iptables --list 
```

（2）设置开机时关闭防火墙

```powershell
[root@hadoop100桌面]#chkconfig iptables off
```

### 5 关机重启命令

​		在linux领域内大多用在服务器上，很少遇到关机的操作。毕竟服务器上跑一个服务是永无止境的，除非特殊情况下，不得已才会关机。

**正确的关机流程为**：`sync` > `shutdown` > `reboot` > `halt`

1. 基本语法

​    （1）`sync`          （功能描述：将数据由内存同步到硬盘中）

​	（2）`halt`          （功能描述：关闭系统，等同于`shutdown -h now` 和 `poweroff`）

​	（3）`reboot`         （功能描述：就是重启，等同于 `shutdown -r now`）

​    （4）`shutdown [选项] 时间` 

表1-4

| 选项 | 功能          |
| ---- | ------------- |
| -h   | -h=halt关机   |
| -r   | -r=reboot重启 |

表1-5

| 参数 | 功能                                   |
| ---- | -------------------------------------- |
| now  | 立刻关机                               |
| 时间 | 等待多久后关机（时间单位是**分钟**）。 |

2. **经验技巧**

​    Linux系统中为了提高磁盘的读写效率，对磁盘采取了 “预读迟写”操作方式。当用户保存文件时，Linux核心并不一定立即将保存数据写入物理磁盘中，而是将数据保存在缓冲区中，等缓冲区满时再写入磁盘，这种方式可以极大的提高磁盘写入数据的效率。但是，也带来了安全隐患，如果数据还未写入磁盘时，系统掉电或者其他严重问题出现，则将导致数据丢失。使用`sync`指令可以立即将缓冲区的数据写入磁盘。

3．案例实操

（1）将数据由内存同步到硬盘中

```powershell
[root@hadoop100桌面]#sync  
```

（2）重启

```powershell
[root@hadoop100桌面]# reboot 
```

（3）关机

```powershell
[root@hadoop100桌面]#halt 
```

（4）计算机将在1分钟后关机，并且会显示在登录用户的当前屏幕中

```powershell
[root@hadoop100桌面]#shutdown -h 1 ‘This server will shutdown after 1 mins’
```

（5）立马关机（等同于 halt）

```powershell
[root@hadoop100桌面]# shutdown -h now 
```

（6）系统立马重启（等同于 reboot）

```powershell
[root@hadoop100桌面]# shutdown -r now
```

### 6 找回root密码

 详见root密码破解[1.0版].pdf文件 

### 7 克隆虚拟机

 1. 关闭要被克隆的虚拟机

 2. 找到克隆选项
    ![克隆](D:\Typora笔记\笔记\linux\picture\linux\找到克隆选项.png)

 3. 欢迎页面

 ![欢迎向导](D:\Typora笔记\笔记\linux\picture\linux\欢迎页面.png)

 4. 克隆虚拟机

  ![克隆](D:\Typora笔记\笔记\linux\picture\linux\克隆虚拟机.png)

 5. 设置创建完整克隆

  ![设置创建完整克隆](D:\Typora笔记\笔记\linux\picture\linux\设置创建完整克隆.png)

 6. 设置克隆的虚拟机名称和存储位置

  ![设置克隆的虚拟机名称和存储位置](D:\Typora笔记\笔记\linux\picture\linux\设置克隆的虚拟机名称和存储位置.png)

 7. 等待完成后关闭窗口，完成克隆

  ![完成](D:\Typora笔记\笔记\linux\picture\linux\等待完成后关闭窗口完成克隆.png)

 8. 修改克隆后虚拟机的ip

```powershell
[root@hadoop101 /]#vim /etc/udev/rules.d/70-persistent-net.rules
```
进入如下页面，删除eth0该行；将eth1修改为eth0，同时复制物理ip地址。
![修改ip](D:\Typora笔记\笔记\linux\picture\linux\修改克隆后虚拟机的ip.png)

 9. 修改IP地址

```powershell
[root@hadoop101 /]#vim /etc/sysconfig/network-scripts/ifcfg-eth0
```
（1）把复制的物理ip地址更新
	HWADDR=00:0C:2x:6x:0x:xx   #MAC地址 
（2）修改成你想要的ip
	IPADDR=192.168.1.101      #IP地址

 10. 修改主机名称
参考：3.2
  
 11. reboot重新启动即可
 12. 完成
![完成1](https://img-blog.csdnimg.cn/20200223223319248.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwMzk0Nzky,size_16,color_FFFFFF,t_70)

### 克隆完之后，第二种方法（较第一种简单）
 8. 修改克隆后虚拟机的ip

```powershell
[root@hadoop101 /]#vim /etc/udev/rules.d/70-persistent-net.rules
```
可以将其中的内容删掉。
![删掉](https://img-blog.csdnimg.cn/20200223222725707.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwMzk0Nzky,size_16,color_FFFFFF,t_70)

 9. 修改IP地址

```powershell
[root@hadoop101 /]#vim /etc/sysconfig/network-scripts/ifcfg-eth0
```
![修改ip地址](https://img-blog.csdnimg.cn/20200223223020863.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwMzk0Nzky,size_16,color_FFFFFF,t_70)

 10. 修改主机名称

     参考：3.2

 11. reboot重新启动即可
 12. 完成
     ![完成](https://img-blog.csdnimg.cn/20200223223257668.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwMzk0Nzky,size_16,color_FFFFFF,t_70)

## 常用基本命令

### 帮助命令

#### man 获得帮助信息

1. **基本语法**
	`man [命令或配置文件]`		（功能描述：获得帮助信息）

2. **显示说明**
	
| 信息        | 功能                     |
| ----------- | ------------------------ |
| NAME        | 命令的名称和单行描述     |
| SYNOPSIS    | 怎样使用命令             |
| DESCRIPTION | 命令功能的深入讨论       |
| EXAMPLES    | 怎样使用命令的例子       |
| SEE ALSO    | 相关主题（通常是手册页） |
|?查找 |向前查找，如 ?and ，将会搜索含有“and”的行|
|/查找|向后查找，如 /and ，将会向后搜索“and”的行|
|N或者n|查找上一个和下一个|
|q|退出|

3. **man章节**

	1.用户命令
	2.系统调用
	3.C库调用
	4.设备文件及特殊文件
	5.配置文件格式
	6.游戏
	7.杂项
	8.管理类命令
	9.linux内核api
	
	帮助文档放在：/usr/share/man中
	
4. **查看man帮助在那些man章节号**
	`whatis` 命令
	使用：
```powershell
[root@hadoop100 ~]# whatis date
date                 (1)  - print or set the system date and time
date                 (1p)  - write the date and time
[root@hadoop100 ~]# whatis cd
cd                   (1p)  - change the working directory
cd [builtins]        (1)  - bash built-in commands, see bash(1)
cd-drive             (1)  - manual page for cd-drive
cd-info              (1)  - manual page for cd-info
cd-paranoia 9.8 (Paranoia release III via libcdio) [cd-paranoia] (1)  - an audio CD reading utility which includes extra data verification features
cd-read              (1)  - manual page for cd-read version 0.81
```

```powershell
[root@hadoop100 ~]# man 1 date //man 章节号 命令
```

```powershell
[root@hadoop100 ~]# whatis password
password-auth-ac [system-auth-ac] (5)  - Common configuration files for PAMified services written by authconfig(8)
[root@hadoop100 ~]# man 5 password //查看password文件的格式

```

`which 命令`
：查看路径，都有情况下显示按PATH显示，找到后不搜索
**`which -a 命令`**
：所有路径下的全显示

```powershell
[root@hadoop100 ~]# which -a ls
alias ls='ls --color=auto'
	/bin/ls

```

`where is 命令`
显示路径和man帮助的文档路径

5. 案例
	（1）查看ls命令的帮助信息
```powershell
[root@hadoop101 ~]# man ls
```

#### help获得shell内置命令的帮助信息
1. 基本语法
	`help 命令`	（功能描述：获得shell内置命令的帮助信息）
	
2. help 列出所有内部命令的用法
	加上*的是禁用的
	

```powershell
[root@hadoop100 ~]# help
GNU bash, version 4.1.2(1)-release (x86_64-redhat-linux-gnu)
These shell commands are defined internally.  Type `help' to see this list.
Type `help name' to find out more about the function `name'.
Use `info bash' to find out more about the shell in general.
Use `man -k' or `info' to find out more about commands not in this list.

A star (*) next to a name means that the command is disabled.

 job_spec [&]                                                                                   history [-c] [-d offset] [n] or history -anrw [filename] or history -ps arg [arg...]
 (( expression ))                                                                               if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... [ else COMMANDS; ] fi
 . filename [arguments]                                                                         jobs [-lnprs] [jobspec ...] or jobs -x command [args]
 :                                                                                              kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
 [ arg... ]                                                                                     let arg [arg ...]
 [[ expression ]]                                                                               local [option] name[=value] ...
 alias [-p] [name[=value] ... ]                                                                 logout [n]
 bg [job_spec ...]                                                                              mapfile [-n count] [-O origin] [-s count] [-t] [-u fd] [-C callback] [-c quantum] [array]
 bind [-lpvsPVS] [-m keymap] [-f filename] [-q name] [-u name] [-r keyseq] [-x keyseq:shell-c>  popd [-n] [+N | -N]
 break [n]                                                                                      printf [-v var] format [arguments]
 builtin [shell-builtin [arg ...]]                                                              pushd [-n] [+N | -N | dir]
 caller [expr]                                                                                  pwd [-LP]
 case WORD in [PATTERN [| PATTERN]...) COMMANDS ;;]... esac                                     read [-ers] [-a array] [-d delim] [-i text] [-n nchars] [-N nchars] [-p prompt] [-t timeout>
 cd [-L|-P] [dir]                                                                               readarray [-n count] [-O origin] [-s count] [-t] [-u fd] [-C callback] [-c quantum] [array]>
 command [-pVv] command [arg ...]                                                               readonly [-af] [name[=value] ...] or readonly -p
 compgen [-abcdefgjksuv] [-o option]  [-A action] [-G globpat] [-W wordlist]  [-F function] [>  return [n]
 complete [-abcdefgjksuv] [-pr] [-DE] [-o option] [-A action] [-G globpat] [-W wordlist]  [-F>  select NAME [in WORDS ... ;] do COMMANDS; done
 compopt [-o|+o option] [-DE] [name ...]                                                        set [--abefhkmnptuvxBCHP] [-o option-name] [arg ...]
 continue [n]                                                                                   shift [n]
 coproc [NAME] command [redirections]                                                           shopt [-pqsu] [-o] [optname ...]
 declare [-aAfFilrtux] [-p] [name[=value] ...]                                                  source filename [arguments]
 dirs [-clpv] [+N] [-N]                                                                         suspend [-f]
 disown [-h] [-ar] [jobspec ...]                                                                test [expr]
 echo [-neE] [arg ...]                                                                          time [-p] pipeline
 enable [-a] [-dnps] [-f filename] [name ...]                                                   times
 eval [arg ...]                                                                                 trap [-lp] [[arg] signal_spec ...]
 exec [-cl] [-a name] [command [arguments ...]] [redirection ...]                               true
 exit [n]                                                                                       type [-afptP] name [name ...]
 export [-fn] [name[=value] ...] or export -p                                                   typeset [-aAfFilrtux] [-p] name[=value] ...
 false                                                                                          ulimit [-SHacdefilmnpqrstuvx] [limit]
 fc [-e ename] [-lnr] [first] [last] or fc -s [pat=rep] [command]                               umask [-p] [-S] [mode]
 fg [job_spec]                                                                                  unalias [-a] name [name ...]
 for NAME [in WORDS ... ] ; do COMMANDS; done                                                   unset [-f] [-v] [name ...]
 for (( exp1; exp2; exp3 )); do COMMANDS; done                                                  until COMMANDS; do COMMANDS; done
 function name { COMMANDS ; } or name () { COMMANDS ; }                                         variables - Names and meanings of some shell variables
 getopts optstring name [arg]                                                                   wait [id]
 hash [-lr] [-p pathname] [-dt] [name ...]                                                      while COMMANDS; do COMMANDS; done
 help [-dms] [pattern ...]                                 
```
**禁用命令：**

- `enable -n 命令` ：禁用命令
- `enable` 可以进行查看，禁用后不显示
- `enable 命令`：启用内部命令

```powershell
[root@hadoop100 ~]# enable
enable .
enable :
enable [
enable alias
enable bg
enable bind
enable break
enable builtin
enable caller
enable cd
enable command
enable compgen
enable complete
enable compopt
enable continue
enable declare
enable dirs
enable disown
enable echo
enable enable
enable eval
enable exec
enable exit
enable export
enable false
enable fc
enable fg
enable getopts
enable hash
enable help
enable history
enable jobs
enable kill
enable let
enable local
enable logout
enable mapfile
enable popd
enable printf
enable pushd
enable pwd
enable read
enable readarray
enable readonly
enable return
enable set
enable shift
enable shopt
enable source
enable suspend
enable test
enable times
enable trap
enable true
enable type
enable typeset
enable ulimit
enable umask
enable unalias
enable unset
enable wait

```

3. 案例
	（1）查看cd命令的帮助信息
```powershell
[root@hadoop101 ~]# help cd
```
#### 获得外部命令的帮助信息
1. 基本语法
`命令 --help/h` ：列出命令的帮助
2. 实例

```powershell
[root@hadoop100 ~]# date --help
```


#### 判断内部命令和外部命令
`type 命令`

```powershell
[root@hadoop100 ~]# type date 
date is hashed (/bin/date) //有存储位置的命令为外部命令
[root@hadoop100 ~]# type cd
cd is a shell builtin //内部命令嵌入在linux的shell中
```
#### 别名
`alias`：查看所有别名列表

```powershell
[root@hadoop100 ~]# alias
alias cp='cp -i'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'

```
==优先级：别名>内部命令>外部命令==

`which --skip-alias 命令`：只显示一条路径，不显示别名信息

```powershell
[root@hadoop100 ~]# which --skip-alias ls
/bin/ls
[root@hadoop100 ~]# which ls
alias ls='ls --color=auto'
	/bin/ls
```

路径，如:`/bin/ls`：不想使用别名，执行原始命令，仅使用于外部命令
```powershell
[root@hadoop100 ~]# which ls
alias ls='ls --color=auto'
	/bin/ls
[root@hadoop100 ~]# /bin/ls
anaconda-ks.cfg      install.log.syslog  模板  文档  桌面
forlearnsmartd.conf  learndir		 视频  下载
install.log	     公共的		 图片  音乐
```
'命令' 或者 \命令 或者"命令" command 命令
:执行原始命令

`unalias 别名`：删除别名

在**.bashrc** 写上`alias 别名="命令"`即可，但不会立即生效，使用：`./source  文件`，**读取文件放到内存中使其生效**。
**/etc/bashrc**:放在此文件中，别名对所有用户都生效，但一般不这样做；

#### 常用快捷键
| 常用快捷键  | 功能                         |
| ----------- | ---------------------------- |
| ctrl + c    | 停止进程                     |
| ctrl+l      | 清屏；彻底清屏是：reset      |
| ctrl + q    | 退出                         |
| 善于用tab键 | 补全(更重要的是可以防止敲错) |
| 上下键      | 查找执行过的命令             |
| ctrl +alt   | linux和Windows之间切换       |

### 文件目录类

#### pwd 显示当前工作目录的绝对路径

`pwd`:print working directory 打印工作目录

1. 基本语法
`pwd`		（功能描述：显示当前工作目录的绝对路径）
2. 案例实操
	（1）显示当前工作目录的绝对路径
	
	```powershell
	[root@hadoop101 ~]# pwd
	/root
	```
#### ls 列出目录的内容
`ls`:list 列出目录内容

1. 基本语法
`ls [选项] [目录或是文件]`
2. 选项说明
	
|选项|功能                                                   |
|--|--                                                       |
|-a|全部的文件，连同隐藏档( 开头为 . 的文件) 一起列出来(常用)|
|-l|长数据串列出，包含文件的属性与权限等等数据；(常用)|
3. 显示说明

  每行列出的信息依次是： **文件类型与权限 链接数 文件属主 文件属组 文件大小用byte来表示 建立或最近修改的时间 名字** 

4. 案例实操

  （1）查看当前目录的所有内容信息

```powershell
[root@hadoop100 ~]# ls
anaconda-ks.cfg      install.log.syslog  模板  文档  桌面
forlearnsmartd.conf  learndir            视频  下载
install.log          公共的              图片  音乐
[root@hadoop100 ~]# ll
总用量 108
-rw-------. 1 root root  1248 2月  23 08:16 anaconda-ks.cfg
-rw-r--r--. 1 root root  6745 2月  23 14:40 forlearnsmartd.conf
-rw-r--r--. 1 root root 41954 2月  23 08:15 install.log
-rw-r--r--. 1 root root  9154 2月  23 08:11 install.log.syslog
drwxr-xr-x. 3 root root  4096 2月  24 10:39 learndir
drwxr-xr-x. 2 root root  4096 2月  23 00:28 公共的
drwxr-xr-x. 2 root root  4096 2月  23 00:28 模板
drwxr-xr-x. 2 root root  4096 2月  23 00:28 视频
drwxr-xr-x. 2 root root  4096 2月  23 00:28 图片
drwxr-xr-x. 2 root root  4096 2月  23 00:28 文档
drwxr-xr-x. 2 root root  4096 2月  23 00:28 下载
drwxr-xr-x. 2 root root  4096 2月  23 00:28 音乐
drwxr-xr-x. 3 root root  4096 2月  23 18:23 桌面

```
#### cd 切换目录
`cd`:Change Directory切换路径

1. 基本语法
	`cd  [参数]`
2. 参数说明

|参数|功能                                 |
|--|--                                     |
|cd 绝对路径|切换路径                      |
|cd相对路径|切换路径                       |
|cd ~或者cd|回到自己的家目录               |
|cd -|回到上一次所在目录                   |
|cd ..|回到当前目录的上一级目录            |
|cd -P|跳转到实际物理路径，而非快捷方式路径|
3．案例实操

（1）使用绝对路径切换到root目录

```powershell
[root@hadoop101 ~]# cd /root/
```

（2）使用相对路径切换到“公共的”目录

```powershell
[root@hadoop101 ~]# cd 公共的/
```

（3）表示回到自己的家目录，亦即是 /root 这个目录

```powershell
[root@hadoop101 公共的]# cd ~
```

（4）cd- 回到上一次所在目录

```powershell
[root@hadoop101 ~]# cd -
```

（5）表示回到当前目录的上一级目录，亦即是 “/root/公共的”的上一级目录的意思；

```powershell
[root@hadoop101 公共的]# cd ..
```
#### mkdir 创建一个新的目录
`mkdir`:Make directory 建立目录

1. 基本语法
	
	`mkdir [选项] 要创建的目录`
	
2. 选项说明

|选项|功能      |
|--|--          |
|-p|创建多层目录|

3. 案例实操
（1）创建一个目录

```powershell
[root@hadoop101 ~]# mkdir xiyou
[root@hadoop101 ~]# mkdir xiyou/mingjie
```

（2）创建一个多级目录

```powershell
[root@hadoop101 ~]# mkdir -p xiyou/dssz/meihouwang
```
#### rmdir 删除一个空的目录
`rmdir`:Remove directory 移动目录

1. 基本语法：
	
	`rmdir 要删除的空目录`
	
2. 案例实操

  （1）删除一个空的文件夹
```powershell
[root@hadoop101 ~]# rmdir xiyou/dssz/meihouwang
```
####  touch 创建空文件
1. 基本语法
	
	`touch 文件名称`
	
2. 案例实操

```powershell
[root@hadoop101 ~]# touch xiyou/dssz/sunwukong.txt
```
#### cp 复制文件或目录
1. 基本语法

  `cp [选项] source dest` 				（功能描述：复制source文件到dest）

2. 选项说明

|选项|功能            |
|--|--                |
|-r|递归复制整个文件夹|

3. 参数说明

|参数|功能    |
|--|--        |
|source|源文件|
|dest|目标文件|
4. 经验技巧
	
	强制覆盖不提示的方法：\cp
	
5. 案例实操
    （1）复制文件

```powershell
 [root@hadoop101 ~]# cp xiyou/dssz/suwukong.txt xiyou/mingjie/
```

（2）递归复制整个文件夹

```powershell
 [root@hadoop101 ~]# cp -r xiyou/dssz/ ./
 
```
#### rm 移除文件或目录
1. 基本语法
`rm [选项] deleteFile`			（功能描述：递归删除目录中所有内容）
2. 选项说明

|选项|功能                                  |
|--|--                                      |
|-r|递归删除目录中所有内容                  |
|-f|强制执行删除操作，而不提示用于进行确认。|
|-v|显示指令的详细执行过程|
3. 案例实操
（1）删除目录中的内容

```powershell
[root@hadoop101 ~]# rm xiyou/mingjie/sunwukong.txt
```

（2）递归删除目录中所有内容

```powershell
[root@hadoop101 ~]# rm -rf dssz/
```
#### mv 移动文件与目录或重命名
1. 基本语法
	（1）`mv oldNameFile newNameFile`	（功能描述：重命名）
	（2）`mv /temp/movefile /targetFolder`	（功能描述：移动文件）
	
2. 案例实操

  （1）重命名

```powershell
[root@hadoop101 ~]# mv xiyou/dssz/suwukong.txt xiyou/dssz/houge.txt
```

​	（2）移动文件

```powershell
[root@hadoop101 ~]# mv xiyou/dssz/houge.txt ./
```
#### cat 查看文件内容
查看文件内容，从第一行开始显示。
1. 基本语法
	
	`cat  [选项] 要查看的文件`
	
2. 选项说明

|选项|功能描述                  |
|--|--                          |
|-n|显示所有行的行号，包括空行。|
3. 经验技巧

  **一般查看比较小的文件，一屏幕能显示全的。**

4. 案例实操

  （1）查看文件内容并显示行号
```powershell
[atguigu@hadoop101 ~]$ cat -n houge.txt 
```
#### more 文件内容分屏查看器
more指令是一个基于VI编辑器的文本过滤器，它以全屏幕的方式按页显示文本文件的内容。more指令中内置了若干快捷键，详见操作说明。
1. 基本语法
	`more 要查看的文件`
2. 操作说明

|操作|功能说明                             |
|--|--                                     |
|空白键 (space)|代表向下翻一页；           |
|Enter|代表向下翻『一行』；                |
|q|代表立刻离开 more ，不再显示该文件内容。|
|Ctrl+F|向下滚动一屏        |
|Ctrl+B|返回上一屏          |
|=|输出当前行的行号         |
|:f|输出文件名和当前行的行号|
3．案例实操

（1）采用more查看文件

```powershell
[root@hadoop101 ~]# more smartd.conf
```
####  less 分屏显示文件内容
less指令用来分屏查看文件内容，它的功能与more指令类似，但是**比more指令更加强大**，支持各种显示终端。less指令在显示文件内容时，并不是一次将整个文件加载之后才显示，而是根据显示需要加载内容，对于显示大型文件具有较高的效率。
1. 基本语法
	
	`less 要查看的文件`
	
2. 操作说明

|操作|功能说明                                           |
|--|--                                                   |
|空白键|向下翻动一页；                                   |
|[pagedown]|向下翻动一页                                 |
|[pageup]|向上翻动一页；                                 |
|/字串|向下搜寻『字串』的功能；n：向下查找；N：向上查找；|
|?字串|向上搜寻『字串』的功能；n：向上查找；N：向下查找；|
|q  |离开 less 这个程序；|
4．案例实操
	（1）采用less查看文件
```powershell
[root@hadoop101 ~]# less smartd.conf
```
#### echo
echo输出内容到控制台
1.	基本语法
		`echo [选项] [输出内容]`
选项： 
    `-e`：  支持反斜线控制的字符转换

控制字符|作用 
--|--
\\ |输出\本身
\n|换行符
\t |制表符，也就是Tab键
2.	案例实操

```powershell
[atguigu@hadoop101 ~]$ echo "hello\tworld"
hello\tworld
[atguigu@hadoop101 ~]$ echo -e "hello\tworld"
hello		world
```
查看当前的shell

```powershell
[root@hadoop100 ~]# echo $SHELL
/bin/bash
```
查看shell的类型，直接输入即可执行

```powershell
[root@hadoop100 ~]# cat /etc/shells
/bin/sh
/bin/bash
/sbin/nologin
/bin/dash
/bin/tcsh
/bin/csh
[root@hadoop100 ~]# /bin/bash

```
显示10-20之间的数，+2递增

```powershell
[root@hadoop100 ~]# echo {10..20..2}
10 12 14 16 18 20

```

```powershell
[root@hadoop100 ~]# echo file{a,b,c}
filea fileb filec
```
笛卡尔积显示

```powershell
[root@hadoop100 ~]# echo file{a,b,c}.{log,txt}
filea.log filea.txt fileb.log fileb.txt filec.log filec.txt

```
创建笛卡尔积中的所有文件

```powershell
[root@hadoop100 ~]# touch file{a,b,c}.{log,txt}
```

#### 修改提示符
提示符的格式，PS1变量名
```powershell
[root@hadoop100 ~]# echo $PS1
[\u@\h \W]\$
```
提示符的格式，你可以在bash中查找：

```powershell
[root@hadoop100 ~]# man bash
```
找到这里，**查找PROMPTING**
```powershell
       PS1    The  value  of  this  parameter  is expanded (see
              PROMPTING below) and used as the  primary  prompt
              string.  The default value is ‘‘\s-\v\$ ’’.
       PS2    The  value  of this parameter is expanded as with
              PS1 and used as the secondary prompt string.  The
              default is ‘‘> ’’.
       PS3    The value of this parameter is used as the prompt
              for the select command (see SHELL GRAMMAR above).
       PS4    The  value  of this parameter is expanded as with
              PS1 and the value is printed before each  command
              bash  displays  during  an  execution trace.  The
              first character of  PS4  is  replicated  multiple
              times,  as necessary, to indicate multiple levels
              of indirection.  The default is ‘‘+ ’’.
       SHELL  The full pathname to the shell is  kept  in  this
              environment  variable.  If it is not set when the
              shell starts, bash assigns to it the  full  path-
              name of the current user’s login shell.
       TIMEFORMAT
              The  value  of this parameter is used as a format
              string specifying how the timing information  for
              pipelines  prefixed  with  the time reserved word
              should be displayed.  The % character  introduces
              an  escape  sequence  that  is expanded to a time
              value or other information.  The escape sequences
              and  their  meanings  are  as follows; the braces
              denote optional portions.
              %%        A literal %.
              %[p][l]R  The elapsed time in seconds.
/PROMPTING
```
找到，介绍了格式

```powershell
PROMPTING
       When  executing interactively, bash displays the primary
       prompt PS1 when it is ready to read a command,  and  the
       secondary  prompt  PS2  when it needs more input to com-
       plete a command.  Bash allows these prompt strings to be
       customized  by  inserting  a number of backslash-escaped
       special characters that are decoded as follows:
              \a     an ASCII bell character (07)
              \d     the date in "Weekday  Month  Date"  format
                     (e.g., "Tue May 26")
              \D{format}
                     the  format  is  passed to strftime(3) and
                     the result is  inserted  into  the  prompt
                     string;  an  empty  format  results  in  a
                     locale-specific time representation.   The
                     braces are required
              \e     an ASCII escape character (033)
              \h     the hostname up to the first ‘.’
              \H     the hostname
              \j     the  number  of  jobs currently managed by
                     the shell
              \l     the  basename  of  the  shell’s   terminal
                     device name
              \n     newline
              \r     carriage return
              \s     the  name of the shell, the basename of $0
                     (the portion following the final slash)
              \t     the current time in 24-hour HH:MM:SS  for-
                     mat
:
```

`PS1="{}"`:修改提示符

在 **/etc/profile.d/env.sh**文件中
加入：`PS1="{}"`
：**永久修改提示符，写入到文件中；**


#### head 显示文件头部内容
head用于显示文件的开头部分内容，默认情况下head指令显示文件的前10行内容。
1.	基本语法
`head 文件`	      （功能描述：查看文件头10行内容）
`head -n 5 文件`      （功能描述：查看文件头5行内容，5可以是任意行数）
2. 选项说明

|选项|功能                       |
|--|--                           |
|-n <行数>|指定显示头部内容的行数|
3. 案例实操
	（1）查看文件的头2行
```powershell
[root@hadoop101 ~]# head -n 2 smartd.conf
```

#### tail 输出文件尾部内容
tail用于输出文件中尾部的内容，默认情况下tail指令显示文件的后10行内容。
1.	基本语法
（1）`tail  文件` 			（功能描述：查看文件后10行内容）
（2）`tail  -n 5 文件` 		（功能描述：查看文件后5行内容，5可以是任意行数）
（3）`tail  -f  文件`		（功能描述：实时追踪该文档的所有更新）
2. 选项说明

|选项|功能                              |
|--|--                                  |
|-n<行数>|输出文件尾部n行内容           |
|-f|显示文件最新追加的内容，监视文件变化|
3．案例实操
（1）查看文件尾1行内容

```powershell
[root@hadoop101 ~]# tail -n 1 smartd.conf 
```

（2）实时追踪该档的所有更新

```powershell
[root@hadoop101 ~]# tail -f houge.txt
```
#### > 覆盖 和 >> 追加
1. 基本语法
（1）`ll >文件`		（功能描述：列表的内容写入文件a.txt中（覆盖写））
（2）`ll >>文件`		（功能描述：列表的内容追加到文件aa.txt的末尾）
（3）`cat 文件1 > 文件2`	（功能描述：将文件1的内容覆盖到文件2）
（4）`echo “内容” >> 文件`
2. 案例实操
（1）将ls查看信息写入到文件中

```powershell
[root@hadoop101 ~]# ls -l>houge.txt
```

（2）将ls查看信息追加到文件中

```powershell
[root@hadoop101 ~]# ls -l>>houge.txt
```

（3）采用echo将hello单词追加到文件中

```powershell
[root@hadoop101 ~]# echo hello>>houge.txt
```
#### `cat << EOF << file`

通过cat配合重定向能够生成文件并追加操作,在它之前先熟悉几个特殊符号:

- `<` :输入重定向
- `>` :输出重定向
- `\>>`:输出重定向,进行追加,不会覆盖之前内容
- `<<`:标准输入来自命令行的一对分隔号的中间内容.

“`<< EOF EOF`”的作用是在命令执行过程中用户自定义输入，它**类似于起到一个临时文件的作用**，只是比使用文件更方便灵活。

```shell
# 向文件test.sh里输入内容。
[root@slave-server opt]# cat << EOF >test.sh 
> 123123123
> 3452354345
> asdfasdfs
> EOF
[root@slave-server opt]# cat test.sh 
123123123
3452354345
asdfasdfs

# 追加内容
[root@slave-server opt]# cat << EOF >>test.sh 
> 7777
> 8888
> EOF
[root@slave-server opt]# cat test.sh 
123123123
3452354345
asdfasdfs
7777
8888
```



#### ln 软链接

软链接也称为符号链接，**类似于windows里的快捷方式**，**有自己的数据块，主要存放了链接其他文件的路径。**
1. 基本语法
`ln -s [原文件或目录] [软链接名]`		（功能描述：给原文件创建一个软链接）
2. 经验技巧
删除软链接： `rm -rf 软链接名`，而不是rm -rf 软链接名/
查询：通过`ll`就可以查看，**列表属性第1位是l，尾部会有位置指向**。
3. 案例实操
	（1）创建软连接
```powershell
[root@hadoop101 ~]# mv houge.txt xiyou/dssz/
[root@hadoop101 ~]# ln -s xiyou/dssz/houge.txt ./houzi
[root@hadoop101 ~]# ll
lrwxrwxrwx. 1 root    root      20 6月  17 12:56 houzi -> xiyou/dssz/houge.txt
```

（2）删除软连接

```powershell
[root@hadoop101 ~]# rm -rf houzi
```

（3）进入软连接实际物理路径

```powershell
[root@hadoop101 ~]# ln -s xiyou/dssz/ ./dssz
[root@hadoop101 ~]# cd -P dssz/
```
#### history 查看已经执行过历史命令
1. 基本语法
	`history`						（功能描述：查看已经执行过历史命令）
2. 案例实操
	（1）查看已经执行过的历史命令
```powershell
[root@hadoop101 test1]# history
```

补充：
`history`：列出所有执行的命令，**只记录最近的一千条历史，在`HISTSIZE`变量中**
`HISTSIZE` 变量在**/etc/prifile**中，可以修改。

|命令|执行                                                            |
|--|--                                                                |
|！+历史命令编号|重新执行命令                                         |
|！-编号|执行倒数第编号条命令                                         |
|ctrl+p+回车|执行前一条命令                                           |
|!+字符串|重复前一个以字符串开头的命令                                |
|！？+字符串|包含字符串的命令                                         |
|！+字符串：p|仅打印，并不执行                                        |
|!$:p|打印输出！$(上一条命令的最后一个参数）的内容                    |
|！*：p|打印输出！*（上一条命令的所有参数）的内容                     |
|^+字符串|删除上一条命令中的第一个字符串                              |
|^+字符串1+（shift+6）字符串2|将上一条命令的第一个字符串1替换为字符串2|
|！：gs/字符串/字符串2|将上一条命令中所有字符串1替换为字符串2|
|history -d 12|删除编号为12的命令历史                        |
|history -a|将内存中的命令写到文件中                         |
| history -r|将文件中的内容写到内存中                        |
| history -w|将当前新命令追加到文件中                        |
| history -n|将新增加的历史增加到历史列表中                  |
| history -p +"command" "command"|执行命令但不写到历史中     |
| history -s + "string"|伪造历史，但并不执行                 |

==执行时历史命令放在内存中，退出系统后，将内存中历史命令写进文件中==，命令存放在磁盘中**用户家目录中的.bash_history隐藏文件**中，当==用户登录时，从此文件中加载到内存中==，而执行`history -c`后是**清除内存中的命令历史**，从而用户退出时上一次的命令历史就被清掉，无法加载到文件中去

1）`rm .bash_history`
2）`history -c`
:删除历史文件，同时清除内存中的历史记录，执行顺序很重要，否则会暴露删除文件命令，在重新生成的.bash_history文件中。

**修改历史格式**
修改历史格式，想要永久更改，需要写入配置文件**/etc/profile.d/env.sh**文件中
命令历史相关的环境变量：
`HISTSIZE`:命令历史记录的条数
`HISTFILE`:指定历史文件，默认为~/.bash_history
`HISTFILESIZE`:命令历史文件记录历史的条数
`HISTTIMEFORMAT="%F %T "`：显示时间
`HISTIGNORE="STR1:STR2*..."`忽略str1命令，str2开头的历史

`HISTCONTROL=`
	`ignorespace`:忽略所有以空格开头的命令
	`ignoredups`：忽略重复的命令，连续相同为重复
	`ignoreboth`：相当于`ignoredups`和`ignorespace`的组合
	`erasedups`：删除重复命令，可以不连续的
系统的配置文件**/etc/profile**文件中

例如：`HISTTIMEFORMAT="%F %T "`修改历史格式

### 时间日期类
1. 基本语法
`date [OPTION]... [+FORMAT]`

2. 选项说明

| 选项           | 功能                                           |
| -------------- | ---------------------------------------------- |
| -d<时间字符串> | 显示指定的“时间字符串”表示的时间，而非当前时间 |
| -s<日期时间>   | 设置系统日期时间                               |

3. 参数说明

| 参数            | 功能                         |
| --------------- | ---------------------------- |
| <+日期时间格式> | 指定显示时使用的日期时间格式 |
#### date 显示当前时间
1. 基本语法
	（1）`date`								（功能描述：显示当前时间）
	（2）`date +%Y`							（功能描述：显示当前年份）
（3）`date +%m`							（功能描述：显示当前月份）
（4）`date +%d`							（功能描述：显示当前是哪一天）
	（5）`date "+%Y-%m-%d %H:%M:%S"`		（功能描述：显示年月日时分秒）
2. 案例实操
（1）显示当前时间信息

```powershell
[root@hadoop100 ~]# date
2020年 02月 24日 星期一 13:35:56 CST
```

（2）显示当前时间年月日

```powershell
[root@hadoop100 ~]# date +%Y%m%d
20200224
```

（3）显示当前时间年月日时分秒

```powershell
[root@hadoop100 ~]# date "+%Y-%m-%d %H:%M:%S"
2020-02-24 13:36:34
```
#### date 显示非当前时间
1. 基本语法
    （1）`date -d '1 days ago'`			（功能描述：显示前一天时间）
    （2）`date -d '-1 days ago'`			（功能描述：显示明天时间）
    （3）`date -d '1 day'`			（功能描述：显示明天时间）
    （4）`date -d '-1 day'`			（功能描述：显示昨天时间）

2. 案例实操

  （1）显示前一天

```powershell
[root@hadoop100 ~]# date -d '1 days ago'
2020年 02月 23日 星期日 13:38:03 CST
```

​	（2）使用day以年月日显示两天前的时间
​		`%F`:年-月-日
​		`%T`:小时：分：秒
​		系统时间格式：月日小时分年.秒

```powershell
[root@hadoop100 ~]# date -d "-2 day" +%F
2020-02-22
```
**补充（包含修改系统时间）：**
| 命令                     | 功能                                    |
| ------------------------ | --------------------------------------- |
| date                     | 系统时间，内核时间                      |
| clock                    | 主板时间                                |
| date "月日几点几分年.秒" | 更改系统时间                            |
| clock -s                 | 以硬件时间覆盖系统时间                  |
| clock -w                 | 以系统时间覆盖硬件时间                  |
| ntpdate ip地址           | 使系统时间与ip的实践一样                |
| date +%s                 | 1970.1.1到现在的时间秒数，linux诞生元年 |
| date -d @秒              | 把秒显示格式转换成系统时间格式          |
| date +%F                 | 显示当前时间的年月日                    |

`/etc/localtime`:记录时区时间，但不是文本文件

#### date 设置系统时间
1．基本语法
	`date -s 字符串时间`

2．案例实操
	（1）设置系统当前时间

```powershell
[root@hadoop101 ~]# date -s "2017-06-19 20:52:18"
```
#### cal 查看日历
1. 基本语法
`cal [选项]`			（功能描述：不加选项，显示本月日历）
2. 选项说明

| 选项       | 功能             |
| ---------- | ---------------- |
| 具体某一年 | 显示这一年的日历 |

3. 案例实操
（1）查看当前月的日历

```powershell
[root@hadoop100 ~]# cal
      二月 2020     
日 一 二 三 四 五 六
                   1
 2  3  4  5  6  7  8
 9 10 11 12 13 14 15
16 17 18 19 20 21 22
23 24 25 26 27 28 29

```

（2）查看2021年的日历

```powershell
[root@hadoop100 ~]# cal 2021
```


### bash快捷键
| 快捷键                  | 作用                                   |
| ----------------------- | -------------------------------------- |
| ctrl + l = clear        | 清屏                                   |
| ctrl + o                | 执行当前命令，并重新显示本命令         |
| ctrl + s                | 锁屏                                   |
| ctrl + q                | 允许屏幕输出                           |
| ctrl + c                | 终止命令                               |
| ctrl + z                | 挂起命令                               |
| ctrl + a                | 光标跳到行首                           |
| ctrl + e                | 光标跳至行尾                           |
| ctrl + f                | 光标向右移动一个字符                   |
| ctrl + b                | 光标想左移动一个字符                   |
| ctrl + xx               | 光标在命令行首和贯标之间移动           |
| ctrl + u                | 从光标处删除至行首                     |
| ctrl + k                | 从光标处删除至行尾                     |
| ctrl + w                | 从光标向左删除至单词首                 |
| alt + d                 | 从光标向右删除至单词尾                 |
| ctrl + d                | 删除光标处的一个字符                   |
| ctrl + h                | 删除光标前的一个字符                   |
| ctrl + y                | 将删除的字符粘贴至光标后               |
| alt + c                 | 光标处开始向右更改为首字母大写的单词   |
| alt + u                 | 从光标处开始，将右边一个单词更改为大写 |
| alt + l                 | 从光标处开始，将右边一个单词更改为小写 |
| ctrl + t                | 交换光标处和之前的字符的位置           |
| alt + t                 | 交换光标处和之前单词的位置             |
| alt + N（数字）+ string | 提示输入指定字符后，重复显示该字符N次  |
| alt + r                 | 删除当前行                             |
| alt + f                 | 光标向右移动一个单词尾                 |
| alt + b                 | 光标向左移动一个单词首                 |

### 用户管理命令

#### useradd 添加新用户

1. 基本语法
	`useradd 用户名`			（功能描述：添加新用户）
	`useradd -g 组名 用户名`	（功能描述：添加新用户到某个组）
2. 案例实操
	（1）添加一个用户
```powershell
[root@hadoop100 ~]# useradd why
[root@hadoop100 ~]# id why
uid=500(why) gid=500(why) 组=500(why)
[root@hadoop100 ~]# cd /home
[root@hadoop100 home]# ll
总用量 4
drwx------. 4 why why 4096 2月  24 13:53 why

```

**`passwd` 设置用户密码**

1. 基本语法
	`passwd 用户名`	（功能描述：设置用户密码）
2. 案例实操
	（1）设置用户的密码
```powershell
[root@hadoop100 home]# passwd why
更改用户 why 的密码 。
新的 密码：
无效的密码： 过于简单化/系统化
无效的密码： 过于简单
重新输入新的 密码：
passwd： 所有的身份验证令牌已经成功更新
```

#### id 查看用户是否存在

1. 基本语法
	`id 用户名`
2. 案例实操
	（1）查看用户是否存在
```powershell
[root@hadoop100 ~]# id why
uid=500(why) gid=500(why) 组=500(why)

```

#### cat /etc/passwd 查看创建了哪些用户

1）基本语法

```powershell
[root@hadoop100 home]# cat /etc/passwd

```
在文件的最后一行：

```powershell
why:x:500:500::/home/why:/bin/bash 
/* /etc/passwd文件 */
```
#### su 切换用户

`su`: swith user 切换用户

1. 基本语法
`su 用户名称`   （功能描述：切换用户，只能**获得用户的执行权限，不能获得环境变量**）
`su - 用户名称`		（功能描述：切换到用户并**获得该用户的环境变量及执行权限**）
2. 案例实操
	（1）切换用户
```powershell
[root@hadoop100 ~]# su why
[why@hadoop100 root]$ echo $PATH
/usr/lib64/qt-3.3/bin:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin
[why@hadoop100 root]$ su root
密码：
[root@hadoop100 ~]# su - why
[why@hadoop100 ~]$ echo $PATH
/usr/lib64/qt-3.3/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/why/bin

```

#### userdel 删除用户

1. 基本语法
	（1）`userdel  用户名`		（功能描述：**删除用户但保存用户主目录**）
（2）`userdel -r 用户名`		（功能描述：**用户和用户主目录，都删除**）
2. 选项说明

|选项|功能                                    |
|--|--                                        |
|-r|删除用户的同时，删除与用户相关的所有文件。|
3. 案例实操
（1）删除用户但保存用户主目录

```powershell
[root@hadoop100 why]# useradd why2
[root@hadoop100 why]# useradd why2
useradd：用户“why2”已存在
[root@hadoop100 why]# id why2
uid=501(why2) gid=501(why2) 组=501(why2)
[root@hadoop100 why]# userdel why2
[root@hadoop100 why]# id why2
id: why2：无此用户
[root@hadoop100 ~]# ll /home
总用量 8
drwx------. 5 why why    4096 2月  24 14:03 why
drwx------. 4 501 group1 4096 2月  24 14:00 why2
```

（2）删除用户和用户主目录，都删除

```powershell
[root@hadoop101 ~]#useradd zhubajie
[root@hadoop101 ~]#ll /home/
[root@hadoop101 ~]#userdel -r zhubajie
[root@hadoop101 ~]#ll /home/
```

#### who 查看登录用户信息

1. 基本语法
	（1）`whoami`			（功能描述：显示自身用户名称）
（2）`who am i`		（功能描述：显示登录用户的用户名）
2. 案例实操
	（1）显示自身用户名称
（2）显示登录用户的用户名

```powershell
[root@hadoop100 why]# whoami
root
[root@hadoop100 why]# who am i
root     pts/1        2020-02-24 09:41 (192.168.1.10)
[root@hadoop100 why]# su why
[why@hadoop100 ~]$ whoami
why
[why@hadoop100 ~]$ who am i
root     pts/1        2020-02-24 09:41 (192.168.1.10)

```

#### sudo 设置普通用户具有root权限
可以看到，why用户权限不够，无法创建目录
```powershell
[root@hadoop100 ~]# su why
[why@hadoop100 root]$ mkdir learn
mkdir: 无法创建目录"learn": 权限不够
```
**修改配置文件**

```powershell
[root@hadoop100 ~]# vim /etc/sudoers
```

修改 **/etc/sudoers** 文件，找到下面一行(91行)，在root下面添加一行，如下所示：
#### Allow root to run any commands anywhere
```
root    ALL=(ALL)     ALL
why   ALL=(ALL)     ALL
```

或者配置成采用sudo命令时，不需要输入密码

#### Allow root to run any commands anywhere
```
root      ALL=(ALL)     ALL
why   ALL=(ALL)     NOPASSWD:ALL
```

**修改完毕，现在可以用why帐号登录，然后用命令 sudo ，即可获得root权限进行操作。**

3．案例实操
	（1）用普通用户在/opt目录下创建一个文件夹

```powershell
[root@hadoop100 ~]# su why
[why@hadoop100 root]$ sudo mkdir learn
[why@hadoop100 root]$ sudo ls -l
总用量 112
-rw-------. 1 root root  1248 2月  23 08:16 anaconda-ks.cfg
-rw-r--r--. 1 root root  6745 2月  23 14:40 forlearnsmartd.conf
-rw-r--r--. 1 root root 41954 2月  23 08:15 install.log
-rw-r--r--. 1 root root  9154 2月  23 08:11 install.log.syslog
drwxr-xr-x. 2 root root  4096 2月  24 14:11 learn
drwxr-xr-x. 3 root root  4096 2月  24 10:39 learndir
drwxr-xr-x. 2 root root  4096 2月  23 00:28 公共的
drwxr-xr-x. 2 root root  4096 2月  23 00:28 模板
drwxr-xr-x. 2 root root  4096 2月  23 00:28 视频
drwxr-xr-x. 2 root root  4096 2月  23 00:28 图片
drwxr-xr-x. 2 root root  4096 2月  23 00:28 文档
drwxr-xr-x. 2 root root  4096 2月  23 00:28 下载
drwxr-xr-x. 2 root root  4096 2月  23 00:28 音乐
drwxr-xr-x. 3 root root  4096 2月  23 18:23 桌面
```

#### usermod 修改用户

1. 基本语法
`usermod -g 用户组 用户名`
2. 选项说明

|选项|功能                                |
|--|--                                    |
|-g|修改用户的初始登录组，给定的组必须存在|
3．案例实操

（1）将用户加入到用户组

```powershell
[root@hadoop100 ~]# id why
uid=500(why) gid=500(why) 组=500(why)
[root@hadoop100 ~]# usermod -g root why
[root@hadoop100 ~]# id why
uid=500(why) gid=0(root) 组=0(root)
```

### 用户组管理命令

每个用户都有一个用户组，系统可以对一个用户组中的所有用户进行集中管理。不同Linux 系统对用户组的规定有所不同，如**Linux下的用户属于与它同名的用户组，这个用户组在创建用户时同时创建**。用户组的管理涉及用户组的添加、删除和修改。组的增加、删除和修改实际上就是对/etc/group文件的更新。

#### groupadd 新增组

1. 基本语法
`groupadd 组名`
2. 案例实操
	（1）添加一个why2组
```powershell
[root@hadoop100 ~]# groupadd why2
```
#### groupmod 修改组
1. 基本语法
`groupmod -n 新组名 老组名`
2. 选项说明

|选项|功能描述                |
|--|--                        |
|-n<新组名>|指定工作组的新组名|
3．案例实操
	（1）修改why2组名称为why1
```powershell
[root@hadoop100 ~]# groupmod -n why1 why2
```

#### groupdel 删除组
1. 基本语法
`groupdel 组名`
2. 案例实操
	（1）删除why1组
```powershell
[root@hadoop100 ~]# groupdel why1
```

#### cat /etc/group 查看创建了哪些组

1. 基本操作

```powershell
[root@hadoop100 ~]# groupdel why1
[root@hadoop100 ~]# groupadd group1
[root@hadoop100 ~]# cat /etc/group
```
在`/etc/group`文件的最后几行，以上创建的why组合group1都存在，why存在是因为创建了why用户，它属于why组：

```powershell
why:x:500:
group1:x:501:
```

### 文件权限类

#### 文件属性

Linux系统是一种典型的多用户系统，不同的用户处于不同的地位，拥有不同的权限。为了保护系统的安全性，Linux系统对不同的用户访问同一文件（包括目录文件）的权限做了不同的规定。在Linux中我们可以使用ll或者`ls -l`命令来显示一个文件的属性以及文件所属的用户和组。

1. 从左到右的10个字符表示，如图所示：

![图1-154 文件属性](D:\Typora笔记\笔记\linux\picture\linux\文件属性.png)

如果没有权限，就会出现减号[ `-` ]而已。从左至右用0-9这些数字来表示:

（1）0首位表示类型

​	在Linux中第一个字符代表这个文件是目录、文件或链接文件等等

- `-`代表文件
- `d` 代表目录
- `l` 链接文档(link file)

（2）第1-3位确定属主（该文件的所有者）拥有该文件的权限。---User

（3）第4-6位确定属组（所有者的同组用户）拥有该文件的权限，---Group

（4）第7-9位确定其他用户拥有该文件的权限 ---Other

2. `rxw`作用文件和目录的不同解释

（1）作用到文件：

 - [ `r` ]代表可读(read): 可以读取，查看
 - [ `w` ]代表可写(write):
   可以修改，但是**不代表可以删除该文件，删除一个文件的前提条件是对该文件所在的目录有写权限，才能删除该文件**.
 - [ `x` ]代表可执行(execute):可以被系统执行

（2）作用到目录：

 - [ `r` ]代表可读(read): 可以读取，`ls`查看目录内容
 - [ `w` ]代表可写(write): 可以修改，目录内创建+删除+重命名目录
 - [ `x` ]代表可执行(execute):可以进入该目录

3．案例实操

```powershell
[root@hadoop101 ~]# ll
总用量 104
-rw-------. 1 root root  1248 1月   8 17:36 anaconda-ks.cfg
drwxr-xr-x. 2 root root  4096 1月  12 14:02 dssz
lrwxrwxrwx. 1 root root    20 1月  12 14:32 houzi -> xiyou/dssz/houge.tx
```

文件基本属性介绍，如图所示：

![图1-155 文件基本属性介绍](D:\Typora笔记\笔记\linux\picture\linux\文件基本属性介绍.png)

（1）如果查看到是文件：链接数指的是硬链接个数。创建硬链接方法

`ln [原文件] [目标文件]`	 

```powershell
[root@hadoop101 ~]# ln xiyou/dssz/houge.txt ./hg.txt
```

（2）**如果查看的是文件夹：链接数指的是子文件夹个数。**

```powershell
[root@hadoop101 ~]# ls -al xiyou/
总用量 16
drwxr-xr-x.  4 root root 4096 1月  12 14:00 .
dr-xr-x---. 29 root root 4096 1月  12 14:32 ..
drwxr-xr-x.  2 root root 4096 1月  12 14:30 dssz
drwxr-xr-x.  2 root root 4096 1月  12 14:04 mingjie
```

#### chmod 改变权限

1. 基本语法

如图所示

![图1-156 基本语法](D:\Typora笔记\笔记\linux\picture\linux\权限.png)

- **第一种方式变更权限**
  `chmod  [{ugoa}{+-=}{rwx}] 文件或目录`
- **第二种方式变更权限**
  `chmod  [mode=421 ]  [文件或目录]`

2. 经验技巧
	

==u:所有者  g:所有组  o:其他人  a:所有人(u、g、o的总和)==

	==r=4 w=2 x=1        rwx=4+2+1=7==

3. 案例实操

  （1）修改文件使其所属主用户具有执行权限

```powershell
[root@hadoop101 ~]# cp xiyou/dssz/houge.txt ./
[root@hadoop101 ~]# chmod u+x houge.txt
```

（2）修改文件使其所属组用户具有执行权限

```powershell
[root@hadoop101 ~]# chmod g+x houge.txt
```

（3）修改文件所属主用户执行权限,并使其他用户具有执行权限

```powershell
[root@hadoop101 ~]# chmod u-x,o+x houge.txt
```

（4）采用数字的方式，设置文件所有者、所属组、其他用户都具有可读可写可执行权限。

```powershell
[root@hadoop101 ~]# chmod 777 houge.txt
```

（5）修改整个文件夹里面的所有文件的所有者、所属组、其他用户都具有可读可写可执行权限。

```powershell
[root@hadoop101 ~]# chmod -R 777 xiyou/
```

#### chown 改变所有者

1. 基本语法

  `chown [选项] [最终用户] [文件或目录]`		（功能描述：改变文件或者目录的所有者）

2. 选项说明

|选项|功能  |
|--|--      |
|-R|递归操作|

3. 案例实操
	
	（1）修改文件所有者
```powershell
[root@hadoop100 ~]# ll
总用量 112
-rw-------. 1 root root  1248 2月  23 08:16 anaconda-ks.cfg
-rw-r--r--. 1 root root  6745 2月  23 14:40 forlearnsmartd.conf
-rw-r--r--. 1 root root 41954 2月  23 08:15 install.log
-rw-r--r--. 1 root root  9154 2月  23 08:11 install.log.syslog
drwxr-xr-x. 2 root root  4096 2月  24 15:06 learn
drwxr-xr-x. 3 root root  4096 2月  24 10:39 learndir
drwxr-xr-x. 2 root root  4096 2月  23 00:28 公共的
drwxr-xr-x. 2 root root  4096 2月  23 00:28 模板
drwxr-xr-x. 2 root root  4096 2月  23 00:28 视频
drwxr-xr-x. 2 root root  4096 2月  23 00:28 图片
drwxr-xr-x. 2 root root  4096 2月  23 00:28 文档
drwxr-xr-x. 2 root root  4096 2月  23 00:28 下载
drwxr-xr-x. 2 root root  4096 2月  23 00:28 音乐
drwxr-xr-x. 3 root root  4096 2月  23 18:23 桌面
[root@hadoop100 ~]# chown why learn
[root@hadoop100 ~]# ll
总用量 112
-rw-------. 1 root root  1248 2月  23 08:16 anaconda-ks.cfg
-rw-r--r--. 1 root root  6745 2月  23 14:40 forlearnsmartd.conf
-rw-r--r--. 1 root root 41954 2月  23 08:15 install.log
-rw-r--r--. 1 root root  9154 2月  23 08:11 install.log.syslog
drwxr-xr-x. 2 why  root  4096 2月  24 15:06 learn
drwxr-xr-x. 3 root root  4096 2月  24 10:39 learndir
drwxr-xr-x. 2 root root  4096 2月  23 00:28 公共的
drwxr-xr-x. 2 root root  4096 2月  23 00:28 模板
drwxr-xr-x. 2 root root  4096 2月  23 00:28 视频
drwxr-xr-x. 2 root root  4096 2月  23 00:28 图片
drwxr-xr-x. 2 root root  4096 2月  23 00:28 文档
drwxr-xr-x. 2 root root  4096 2月  23 00:28 下载
drwxr-xr-x. 2 root root  4096 2月  23 00:28 音乐
drwxr-xr-x. 3 root root  4096 2月  23 18:23 桌面

```

（2）递归改变文件所有者和所有组

```powershell
[root@hadoop100 ~]# chown -R why learndir
[root@hadoop100 ~]# ll
总用量 112
-rw-------. 1 root root  1248 2月  23 08:16 anaconda-ks.cfg
-rw-r--r--. 1 root root  6745 2月  23 14:40 forlearnsmartd.conf
-rw-r--r--. 1 root root 41954 2月  23 08:15 install.log
-rw-r--r--. 1 root root  9154 2月  23 08:11 install.log.syslog
drwxr-xr-x. 2 why  root  4096 2月  24 15:06 learn
drwxr-xr-x. 3 why  root  4096 2月  24 10:39 learndir
drwxr-xr-x. 2 root root  4096 2月  23 00:28 公共的
drwxr-xr-x. 2 root root  4096 2月  23 00:28 模板
drwxr-xr-x. 2 root root  4096 2月  23 00:28 视频
drwxr-xr-x. 2 root root  4096 2月  23 00:28 图片
drwxr-xr-x. 2 root root  4096 2月  23 00:28 文档
drwxr-xr-x. 2 root root  4096 2月  23 00:28 下载
drwxr-xr-x. 2 root root  4096 2月  23 00:28 音乐
drwxr-xr-x. 3 root root  4096 2月  23 18:23 桌面
[root@hadoop100 ~]# cd learndir
[root@hadoop100 learndir]# ll
总用量 4
drwxr-xr-x. 2 why root 4096 2月  24 10:43 beijing
[root@hadoop100 learndir]# cd beijing/
[root@hadoop100 beijing]# ll
总用量 4
-rw-r--r--. 1 why root 735 2月  24 10:43 learn.txt
```

#### chgrp 改变所属组

1. 基本语法
	
	`chgrp [最终用户组] [文件或目录]`	（功能描述：改变文件或者目录的所属组）
	
2. 案例实操

  （1）递归修改文件的所属组
```powershell
[root@hadoop100 ~]# chgrp -R why learndir
[root@hadoop100 ~]# ll
总用量 112
-rw-------. 1 root root  1248 2月  23 08:16 anaconda-ks.cfg
-rw-r--r--. 1 root root  6745 2月  23 14:40 forlearnsmartd.conf
-rw-r--r--. 1 root root 41954 2月  23 08:15 install.log
-rw-r--r--. 1 root root  9154 2月  23 08:11 install.log.syslog
drwxr-xr-x. 2 why  root  4096 2月  24 15:06 learn
drwxr-xr-x. 3 why  why   4096 2月  24 10:39 learndir
drwxr-xr-x. 2 root root  4096 2月  23 00:28 公共的
drwxr-xr-x. 2 root root  4096 2月  23 00:28 模板
drwxr-xr-x. 2 root root  4096 2月  23 00:28 视频
drwxr-xr-x. 2 root root  4096 2月  23 00:28 图片
drwxr-xr-x. 2 root root  4096 2月  23 00:28 文档
drwxr-xr-x. 2 root root  4096 2月  23 00:28 下载
drwxr-xr-x. 2 root root  4096 2月  23 00:28 音乐
drwxr-xr-x. 3 root root  4096 2月  23 18:23 桌面
[root@hadoop100 ~]# cd learndir
[root@hadoop100 learndir]# ll
总用量 4
drwxr-xr-x. 2 why why 4096 2月  24 10:43 beijing
[root@hadoop100 learndir]# cd beijing/
[root@hadoop100 beijing]# ll
总用量 4
-rw-r--r--. 1 why why 735 2月  24 10:43 learn.txt

```
### 搜索查找类

#### find 查找文件或者目录

find指令将从指定目录向下**递归地遍历其各个子目录**，将满足条件的文件显示在终端。
1. 基本语法
	
	`find [搜索范围] [选项]`
	
2. 选项说明

|选项|功能                                       |
|--|--                                           |
|-name<查询方式>|按照指定的文件名查找模式查找文件|
|-user<用户名>|查找属于指定用户名所有文件    |
|-size<文件大小>|按照指定的文件大小查找文件。|
3. 案例实操

  （1）按文件名：根据名称查找/目录下的filename.txt文件。

```powershell
[root@hadoop101 ~]# find xiyou/ -name “*.txt”
```

​	（2）按拥有者：查找/opt目录下，用户名称为atguigu的文件

```powershell
[root@hadoop101 ~]# find xiyou/ -user atguigu
```
​	（3）按文件大小：在/home目录下查找大于200m的文件（+n 大于  -n小于   n等于）
```powershell
[root@hadoop101 ~]find /home -size +204800
```

#### grep 过滤查找及“|”管道符

**管道符，“`|`”，表示将前一个命令的处理结果输出传递给后面的命令处理**

1. 基本语法

  `grep 选项 查找内容 源文件`

2. 选项说明

|选项|功能            |
|--|--                |
|-n|显示匹配行及行号。|
3. 案例实操
	（1）查找某文件在第几行
```powershell
[root@hadoop100 ~]# ll
总用量 112
-rw-r--r--. 1 root root     0 2月  24 15:47 73
-rw-------. 1 root root  1248 2月  23 08:16 anaconda-ks.cfg
-rw-r--r--. 1 root root  6745 2月  23 14:40 forlearnsmartd.conf
-rw-r--r--. 1 root root 41954 2月  23 08:15 install.log
-rw-r--r--. 1 root root  9154 2月  23 08:11 install.log.syslog
drwxr-xr-x. 2 why  root  4096 2月  24 15:06 learn
drwxr-xr-x. 3 why  why   4096 2月  24 10:39 learndir
drwxr-xr-x. 2 root root  4096 2月  23 00:28 公共的
drwxr-xr-x. 2 root root  4096 2月  23 00:28 模板
drwxr-xr-x. 2 root root  4096 2月  23 00:28 视频
drwxr-xr-x. 2 root root  4096 2月  23 00:28 图片
drwxr-xr-x. 2 root root  4096 2月  23 00:28 文档
drwxr-xr-x. 2 root root  4096 2月  23 00:28 下载
drwxr-xr-x. 2 root root  4096 2月  23 00:28 音乐
drwxr-xr-x. 3 root root  4096 2月  23 18:23 桌面
[root@hadoop100 ~]# ll | grep -n learn
4:-rw-r--r--. 1 root root  6745 2月  23 14:40 forlearnsmartd.conf
7:drwxr-xr-x. 2 why  root  4096 2月  24 15:06 learn
8:drwxr-xr-x. 3 why  why   4096 2月  24 10:39 learndir

```

#### which 查找命令

查找命令在那个目录下
1. 基本语法

  `which 命令`

2. 案例实操

```powershell
[root@hadoop100 ~]# which ls
alias ls='ls --color=auto'
	/bin/ls
```
### 压缩和解压类

#### gzip/gunzip 压缩

1. 基本语法

  `gzip 文件`		（功能描述：压缩文件，只能将文件压缩为***.gz**文件）

  `gunzip 文件.gz`	（功能描述：解压缩文件命令）

2. 经验技巧

  （1）**只能压缩文件不能压缩目录**

  （2）**不保留原来的文件**

3. 案例实操

  （1）gzip压缩

  ```powershell
  [root@hadoop101 ~]# ls
  honge.java
  [root@hadoop101 ~]# gzip houge.txt
  [root@hadoop101 ~]# ls
  houge.txt.gz
  ```
  （2）gunzip解压缩文件

  ```powershell
  [root@hadoop101 ~]# gunzip houge.txt.gz 
  [root@hadoop101 ~]# ls
  houge.txt
  ```

#### zip/unzip 压缩

1. 基本语法

  `zip  [选项] XXX.zip  将要压缩的内容` 		（功能描述：压缩**文件和目录**的命令）

  `unzip [选项] XXX.zip`						（功能描述：解压缩文件）

2. 选项说明

zip选项|功能
--|--
-r|压缩目录
-d<目录>|指定解压后文件的存放目录
3. 经验技巧

  zip 压缩命令在window/linux都通用，**可以压缩目录且保留源文件**。

4. 案例实操

  （1）压缩 1.txt 和2.txt，压缩后的名称为12.zip 

```powershell
[root@hadoop100 testzip]# touch 1.txt 2.txt
[root@hadoop100 testzip]# ls
1.txt  2.txt
[root@hadoop100 testzip]# zip 12.zip 1.txt 2.txt
  adding: 1.txt (stored 0%)
  adding: 2.txt (stored 0%)
[root@hadoop100 testzip]# ls
12.zip  1.txt  2.txt

```

（2）解压 12.zip,并替换当前目录下的1.txt和2.txt

```powershell
[root@hadoop100 testzip]# unzip 12.zip 
Archive:  12.zip
replace 1.txt? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
 extracting: 1.txt                   
replace 2.txt? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
 extracting: 2.txt                   
[root@hadoop100 testzip]# ll
总用量 4
-rw-r--r--. 1 root root 298 2月  24 16:26 12.zip
-rw-r--r--. 1 root root   0 2月  24 16:25 1.txt
-rw-r--r--. 1 root root   0 2月  24 16:25 2.txt

```

（3）解压12.zip到指定目录-d

```powershell
[root@hadoop100 testzip]# unzip 12.zip -d 12
Archive:  12.zip
 extracting: 12/1.txt                
 extracting: 12/2.txt                
[root@hadoop100 testzip]# ls
12  12.zip  1.txt  2.txt
[root@hadoop100 testzip]# cd 12
[root@hadoop100 12]# ll
总用量 0
-rw-r--r--. 1 root root 0 2月  24 16:25 1.txt
-rw-r--r--. 1 root root 0 2月  24 16:25 2.txt

```

#### tar 打包

1. 基本语法

  `tar  [选项]  XXX.tar.gz  将要打包进去的内容`		（功能描述：打包目录，压缩后的文件格式.tar.gz）

2. 选项说明

选项|功能
--|--
-z|打包同时压缩
-c|产生.tar打包文件
-v|显示详细信息
-f|指定压缩后的文件名
-x|解包.tar文件
3．案例实操
（1）压缩多个文件

```powershell
[root@hadoop100 testtar]# touch 1.txt 2.txt
[root@hadoop100 testtar]# ll
总用量 0
-rw-r--r--. 1 root root 0 2月  24 16:31 1.txt
-rw-r--r--. 1 root root 0 2月  24 16:31 2.txt
[root@hadoop100 testtar]# tar -zcvf 12.tar.gz 1.txt 2.txt
1.txt
2.txt
[root@hadoop100 testtar]# ll
总用量 4
-rw-r--r--. 1 root root 116 2月  24 16:31 12.tar.gz
-rw-r--r--. 1 root root   0 2月  24 16:31 1.txt
-rw-r--r--. 1 root root   0 2月  24 16:31 2.txt

```

（2）压缩目录

```powershell
[root@hadoop100 testtar]# mkdir testtar
[root@hadoop100 testtar]# ll
总用量 8
-rw-r--r--. 1 root root  116 2月  24 16:31 12.tar.gz
-rw-r--r--. 1 root root    0 2月  24 16:31 1.txt
-rw-r--r--. 1 root root    0 2月  24 16:31 2.txt
drwxr-xr-x. 2 root root 4096 2月  24 16:32 testtar
[root@hadoop100 testtar]# tar -zcvf testtar.tar.gz .
./
./testtar/
./12.tar.gz
./1.txt
./2.txt
tar: .: 在我们读入文件时文件发生了变化
[root@hadoop100 testtar]# ll
总用量 12
-rw-r--r--. 1 root root  116 2月  24 16:31 12.tar.gz
-rw-r--r--. 1 root root    0 2月  24 16:31 1.txt
-rw-r--r--. 1 root root    0 2月  24 16:31 2.txt
drwxr-xr-x. 2 root root 4096 2月  24 16:32 testtar
-rw-r--r--. 1 root root  357 2月  24 16:33 testtar.tar.gz

```

（3）解压到当前目录

```powershell
[root@hadoop100 testtar]# tar -zxvf testtar.tar.gz
```

（4）解压到指定目录

```powershell
[root@hadoop100 testtar]# tar -zxvf testtar.tar.gz -C ./testtar
./
./testtar/
./12.tar.gz
./1.txt
./2.txt
[root@hadoop100 testtar]# cd testtar
[root@hadoop100 testtar]# ll
总用量 8
-rw-r--r--. 1 root root  116 2月  24 16:31 12.tar.gz
-rw-r--r--. 1 root root    0 2月  24 16:31 1.txt
-rw-r--r--. 1 root root    0 2月  24 16:31 2.txt
drwxr-xr-x. 2 root root 4096 2月  24 16:32 testtar

```

### 磁盘分区类

#### df 查看磁盘空间使用情况

`df`: disk free 空余硬盘

1. 基本语法
	
	`df  选项`	（功能描述：列出文件系统的整体磁盘使用量，检查文件系统的磁盘空间占用情况）
	
2. 选项说明

选项|功能
--|--
-h|以人们较易阅读的 GBytes, MBytes, KBytes 等格式自行显示；
3．案例实操
	（1）查看磁盘使用情况
```powershell
[root@hadoop100 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        15G  3.3G   11G  24% /
tmpfs           996M   72K  996M   1% /dev/shm
/dev/sda1       190M   39M  142M  22% /boot
/dev/sr0        3.7G  3.7G     0 100% /mnt/cdrom
.host:/          82G   14G   69G  17% /mnt/hgfs

```

#### fdisk 查看分区

1. 基本语法
	
	`fdisk -l`			（功能描述：查看磁盘分区详情）
	
2. 选项说明

选项|功能
--|--
-l|显示所有硬盘的分区列表
3. 经验技巧

  **该命令必须在root用户下才能使用**

4. 功能说明

  **Linux分区:**
  		Device：分区序列
  		Boot：引导
  		Start：从X磁柱开始
  		End：到Y磁柱结束
  		Blocks：容量
  		Id：分区类型ID
  		System：分区类型

5. 案例实操
   
    （1）查看系统分区情况
```powershell
[root@hadoop100 ~]# fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00085b2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        1984    15728640   83  Linux
/dev/sda3            1984        2611     5037056   82  Linux swap / Solaris

```

#### mount/umount 挂载/卸载

- 对于Linux用户来讲，不论有几个分区，分别分给哪一个目录使用，它总归就是一个根目录、一个独立且唯一的文件结构。
- Linux中每个分区都是用来组成整个文件系统的一部分，它在用一种叫做“挂载”的处理方法，它整个文件系统中包含了一整套的文件和目录，并将一个分区和一个目录联系起来，要载入的那个分区将使它的存储空间在这个目录下获得。

1. 挂载前准备（必须要有光盘或者已经连接镜像文件）

  ![挂载前准备](D:\Typora笔记\笔记\linux\picture\linux\挂载前准备.png)

2. 基本语法

  `mount [-t vfstype] [-o options] device dir`	（功能描述：挂载设备）

  `umount 设备文件名或挂载点`			（功能描述：卸载设备）

3. 参数说明

 参数       | 功能                                                         
 ---------- | ------------------------------------------------------------ 
 -t vfstype | vfstype	指定文件系统的类型，通常不必指定。mount 会自动选择正确的类型。<br/>**常用类型有：**<br/>光盘或光盘镜像：iso9660<br/>DOS fat16文件系统：msdos<br/>Windows 9x fat32文件系统：vfat<br/>Windows NT ntfs文件系统：ntfs<br/>Mount Windows文件网络共享：smbfs<br/>UNIX(LINUX) 文件网络共享：nfs 
 -o options | 主要用来描述设备或档案的挂接方式。<br/>常用的参数有：<br/>loop：用来把一个文件当成硬盘分区挂接上系统<br/>ro：采用只读方式挂接设备<br/>rw：采用读写方式挂接设备<br/>iocharset：指定访问文件系统所用字符集 
 device     | 要挂接(mount)的设备                                          
 dir        | 设备在系统上的挂接点(mount point)                            
4．案例实操

（1）挂载光盘镜像文件

```powershell
#建立挂载点
[root@hadoop101 ~]# mkdir /mnt/cdrom/

# 设备: /dev/cdrom挂载到 挂载点 ： /mnt/cdrom中
[root@hadoop101 ~]# mount -t iso9660 /dev/cdrom /mnt/cdrom/	

[root@hadoop100 ~]# ll /mnt/cdrom/
总用量 558
-r--r--r--. 2 root root     14 5月  22 2016 CentOS_BuildTag
dr-xr-xr-x. 3 root root   2048 5月  22 2016 EFI
-r--r--r--. 2 root root    212 11月 27 2013 EULA
-r--r--r--. 2 root root  18009 11月 27 2013 GPL
dr-xr-xr-x. 3 root root   2048 5月  23 2016 images
dr-xr-xr-x. 2 root root   2048 5月  22 2016 isolinux
dr-xr-xr-x. 2 root root 528384 5月  23 2016 Packages
-r--r--r--. 2 root root   1359 5月  22 2016 RELEASE-NOTES-en-US.html
dr-xr-xr-x. 2 root root   4096 5月  23 2016 repodata
-r--r--r--. 2 root root   1706 11月 27 2013 RPM-GPG-KEY-CentOS-6
-r--r--r--. 2 root root   1730 11月 27 2013 RPM-GPG-KEY-CentOS-Debug-6
-r--r--r--. 2 root root   1730 11月 27 2013 RPM-GPG-KEY-CentOS-Security-6
-r--r--r--. 2 root root   1734 11月 27 2013 RPM-GPG-KEY-CentOS-Testing-6
-r--r--r--. 1 root root   3380 5月  23 2016 TRANS.TBL
```

（2）卸载光盘镜像文件

```powershell
[root@hadoop101 ~]# umount /mnt/cdrom
```

5．设置开机自动挂载

```powershell
[root@hadoop101 ~]# vim /etc/fstab
```
添加红框中内容，保存退出,重启即可生效。

![在这里插入图片描述](D:\Typora笔记\笔记\linux\picture\linux\开机自动挂载.png)

### 进程线程类
进程是正在执行的一个程序或命令，每一个进程都是一个运行的实体，都有自己的地址空间，并占用一定的系统资源。
#### ps 查看当前系统进程状态
`ps`:process status 进程状态

1. 基本语法
	
	`ps aux | grep xxx`		（功能描述：查看系统中所有进程）
	
	`ps -ef | grep xxx`		（功能描述：可以查看子父进程之间的关系）
	
2. 选项说明

选项|功能
--|--
-a|选择所有进程
-u|显示所有用户的所有进程
-x|显示没有终端的进程
3. 功能说明
	

（1）`ps aux`显示信息说明

​	USER：该进程是由哪个用户产生的
​	**PID：进程的ID号**
​	**%CPU：该进程占用CPU资源的百分比，占用越高，进程越耗费资源；**
​	**%MEM：该进程占用物理内存的百分比，占用越高，进程越耗费资源；**
​	VSZ：该进程占用虚拟内存的大小，单位KB；
​	RSS：该进程占用实际物理内存的大小，单位KB；
​	TTY：该进程是在哪个终端中运行的。其中tty1-tty7代表本地控制台终端，tty1-tty6是本地的字符界面终端，tty7是图形终端。pts/0-255代表虚拟终端。
​	STAT：进程状态。常见的状态有：R：运行、S：睡眠、T：停止状态、s：包含子进程、+：位于后台
​	START：该进程的启动时间
​	TIME：该进程占用CPU的运算时间，注意不是系统时间
​	COMMAND：产生此进程的命令名

（2）`ps -ef`显示信息说明
	**UID：用户ID 
	PID：进程ID 
	PPID：父进程ID** 
	C：CPU用于计算执行优先级的因子。数值越大，表明进程是CPU密集型运算，执行优先级会降低；数值越小，表明进程是I/O密集型运算，执行优先级会提高 
	STIME：进程启动的时间 
	TTY：完整的终端名称 
		TIME：CPU时间 
		CMD：启动进程所用的命令和参数
	
4. 经验技巧

  **如果想查看进程的CPU占用率和内存占用率，可以使用aux;**

  **如果想查看进程的父进程ID可以使用ef;**

5. 案例实操

  查看进程的CPU占用率和内存占用率
```powershell
[root@hadoop100 ~]# ps aux
USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root          1  0.1  0.0  19344  1548 ?        Ss   17:29   0:05 /sbin/init
root          2  0.0  0.0      0     0 ?        S    17:29   0:00 [kthreadd]
root          3  0.0  0.0      0     0 ?        S    17:29   0:00 [migration/0]
root          4  0.0  0.0      0     0 ?        S    17:29   0:02 [ksoftirqd/0]
root          5  0.0  0.0      0     0 ?        S    17:29   0:00 [stopper/0]
root          6  0.0  0.0      0     0 ?        S    17:29   0:00 [watchdog/0]
root          7  0.0  0.0      0     0 ?        S    17:29   0:00 [migration/1]
```
查看进程的父进程ID

```powershell
[root@hadoop100 ~]# ps -ef
UID         PID   PPID  C STIME TTY          TIME CMD
root          1      0  0 17:29 ?        00:00:05 /sbin/init
root          2      0  0 17:29 ?        00:00:00 [kthreadd]
root          3      2  0 17:29 ?        00:00:00 [migration/0]
root          4      2  0 17:29 ?        00:00:02 [ksoftirqd/0]
root          5      2  0 17:29 ?        00:00:00 [stopper/0]
root          6      2  0 17:29 ?        00:00:00 [watchdog/0]

```

#### kill 终止进程
1. 基本语法
	
	`kill  [选项] 进程号`		（功能描述：通过进程号杀死进程）
	
	`killall 进程名称`			（功能描述：通过进程名称杀死进程，也支持通配符，这在系统因负载过大而变得很慢时很有用）	
	
2. 选项说明

选项|功能
--|-
-9|表示强迫进程立即停止

3. 案例实操
	
	（1）杀死浏览器进程
```powershell
[root@hadoop101 桌面]# kill -9 5102
```
	（2）通过进程名称杀死进程
```powershell
[root@hadoop101 桌面]# killall firefox
```

#### pstree 查看进程树
1. 基本语法
	
	`pstree [选项]`
	
2. 选项说明

选项|功能
--|--
-p|显示进程的PID 
-u|显示进程的所属用户

3. 案例实操

  （1）显示进程pid
```powershell
[root@hadoop100 ~]# pstree -p
init(1)─┬─ManagementAgent(1818)─┬─{ManagementAgen}(1834)
        │                       └─{ManagementAgen}(1835)
        ├─NetworkManager(2161)
        ├─VGAuthService(1706)
        ├─abrtd(2559)
        ├─acpid(2258)
        ├─atd(2586)
        ├─auditd(2060)───{auditd}(2061)
        ├─bonobo-activati(2747)───{bonobo-activat}(2748)
        ├─console-kit-dae(2645)─┬─{console-kit-da}(2646)
        │                       ├─{console-kit-da}(2647)
        │                       ├─{console-kit-da}(2648)

```
（2）显示进程所属用户
```powershell
[root@hadoop100 ~]# pstree -u
init─┬─ManagementAgent───2*[{ManagementAgen}]
     ├─NetworkManager
     ├─VGAuthService
     ├─abrtd
     ├─acpid
     ├─atd
     ├─auditd───{auditd}
     ├─bonobo-activati(gdm)───{bonobo-activat}
     ├─console-kit-dae───63*[{console-kit-da}]
     ├─crond
     ├─cupsd
     ├─dbus-daemon(gdm)───{dbus-daemon}
     ├─dbus-daemon(dbus)───{dbus-daemon}
     ├─dbus-launch(gdm)
     ├─devkit-power-da

```

#### top 查看系统健康状态
1. 基本命令
	
	`top [选项]`	
	
2. 选项说明

选项|功能
--|--
-d|秒数	指定top命令每隔几秒更新。默认是3秒在top命令的交互模式当中可以执行的命令：
-i|使top不显示任何闲置或者僵死进程。
-p|通过指定监控进程ID来仅仅监控某个进程的状态。
3. 操作说明

操作|功能
--|--
P|以CPU使用率排序，默认就是此项 
M|以内存的使用率排序
N|以PID排序
q|退出top

4. 查询结果字段解释

  第一行信息为任务队列信息

内容|说明
--|--
12:26:46|系统当前时间
up 1 day, 13:32|系统的运行时间，本机已经运行1天13小时32分钟
2 users|当前登录了两个用户
load  average:  0.00, 0.00, 0.00|系统在之前1分钟，5分钟，15分钟的平均负载。一般认为小于1时，负载较小。如果大于1，系统已经超出负荷。
​	第二行为进程信息
内容|说明
--|--
Tasks:|95 total	系统中的进程总数
1 running|正在运行的进程数
94 sleeping|睡眠的进程
0 stopped|正在停止的进程
0 zombie|僵尸进程。如果不是0，需要手工检查僵尸进程

​	第三行为CPU信息
内容|说明
--|--
Cpu(s):  0.1%us|用户模式占用的CPU百分比
0.1%sy|系统模式占用的CPU百分比
0.0%ni|改变过优先级的用户进程占用的CPU百分比
99.7%id|空闲CPU的CPU百分比
0.1%wa|等待输入/输出的进程的占用CPU百分比
0.0%hi|硬中断请求服务占用的CPU百分比
0.1%si|软中断请求服务占用的CPU百分比
0.0%st|st（Steal  time）虚拟时间百分比。就是当有虚拟机时，虚拟CPU等待实际CPU的时间百分比。
​	第四行为物理内存信息
内容|说明
--|--
Mem|625344k total	物理内存的总量，单位KB
571504k used|已经使用的物理内存数量
53840k free|空闲的物理内存数量，我们使用的是虚拟机，总共只分配了628MB内存，所以只有53MB的空闲内存了
65800k buffers|作为缓冲的内存数量
​	第五行为交换分区（swap）信息
内容|说明
--|--
Swap|524280k total	交换分区（虚拟内存）的总大小
0k used|已经使用的交互分区的大小
524280k free|空闲交换分区的大小
409280k cached|作为缓存的交互分区的大小
5．案例实操

```powershell
[root@hadoop100 ~]# top -d 10
top - 18:29:06 up 59 min,  1 user,  load average: 0.16, 0.18, 0.21
Tasks: 160 total,   1 running, 159 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.1%us,  0.3%sy,  0.0%ni, 99.2%id,  0.3%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   2038376k total,   385272k used,  1653104k free,    21232k buffers
Swap:  5037052k total,        0k used,  5037052k free,   150020k cached

   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                          
    22 root      20   0     0    0    0 S  1.9  0.0   0:13.41 events/3                          
  2882 root      20   0 15028 1176  848 R  1.9  0.1   0:00.01 top                               
     1 root      20   0 19344 1548 1232 S  0.0  0.1   0:05.43 init                              
     2 root      20   0     0    0    0 S  0.0  0.0   0:00.04 kthreadd                          
     3 root      RT   0     0    0    0 S  0.0  0.0   0:00.23 migration/0                       
     4 root      20   0     0    0    0 S  0.0  0.0   0:02.79 ksoftirqd/0                       
     5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 stopper/0                         
     6 root      RT   0     0    0    0 S  0.0  0.0   0:00.36 watchdog/0                        
     7 root      RT   0     0    0    0 S  0.0  0.0   0:00.24 migration/1    
```

执行上述命令后，可以按P、M、N对查询出的进程结果进行排序。
#### netstat 显示网络统计信息和端口占用情况
1. 基本语法
	
	`netstat -anp | grep 进程号`	（功能描述：查看该进程网络信息）
	
	`netstat -nlp | grep 端口号`	（功能描述：查看网络端口号占用情况）
	
2. 选项说明

选项|功能
--|--
-n|拒绝显示别名，能显示数字的全部转化成数字
-l|仅列出有在listen（监听）的服务状态
-p|表示显示哪个进程在调用
3．案例实操
（1）通过进程号查看该进程的网络信息

```powershell
[root@hadoop100 ~]# netstat -nlp | grep 2747
unix  2      [ ACC ]     STREAM     LISTENING     17368  2747/bonobo-activat /tmp/orbit-gdm/linc-abb-0-2b237ae35f6
```

（2）查看某端口号是否被占用

```powershell
[root@hadoop100 ~]# netstat -nlp | grep 17368
unix  2      [ ACC ]     STREAM     LISTENING     17368  2747/bonobo-activat /tmp/orbit-gdm/linc-abb-0-2b237ae35f6
```

### crond 系统定时任务

#### crond 服务管理

1. 重新启动crond服务

```powershell
[root@hadoop101 ~]# service crond restart
```

#### crontab 定时任务设置
1. 基本语法

  `crontab [选项]`

2. 选项说明

选项|功能
--|--
-e|编辑crontab定时任务
-l|查询crontab任务
-r|删除当前用户所有的crontab任务
3. 参数说明

```powershell
[root@hadoop101 ~]# crontab -e 
```

（1）进入crontab编辑界面。会打开vim编辑你的工作。

```powershell
*  *  *  *  *  执行的任务
```

项目|含义|范围
--|--|--
第一个*|一小时当中的第几分钟|0-59
第二个*|一天当中的第几小时|0-23
第三个*|一个月当中的第几天|1-31
第四个*|一年当中的第几月|1-12
第五个*|一周当中的星期几|0-7（0和7都代表星期日）
（2）特殊符号

特殊符号|含义
--|--
*|代表任何时间。比如第一个“*”就代表一小时中每分钟都执行一次的意思。
,|代表不连续的时间。比如“0 8,12,16 * * * 命令”，就代表在每天的8点0分，12点0分，16点0分都执行一次命令
-|代表连续的时间范围。比如“0 5  *  *  1-6命令”，代表在周一到周六的凌晨5点0分执行命令
*/n|代表每隔多久执行一次。比如“*/10  *  *  *  *  命令”，代表每隔10分钟就执行一遍命令
（3）特定时间执行命令

时间 |含义
--|--
45 22 *  *   * 命令|在22点45分执行命令
0 17  *  *  1 命令|每周1 的17点0分执行命令
0 5 1,15  *  *  命令|每月1号和15号的凌晨5点0分执行命令
40 4  *  *  1-5 命令|每周一到周五的凌晨4点40分执行命令
*/10 4  *  *  *  命令|每天的凌晨4点，每隔10分钟执行一次命令
0 0 1,15 * 1 命令|每月1号和15号，每周1的0点0分都会执行命令。

**注意：星期几和几号最好不要同时出现，因为他们定义的都是天。非常容易让管理员混乱。**

4. 案例实操
	
	（1）每隔1分钟，向/root/learn/testcrontab.txt文件中添加一个“”Hello！的
```powershell
[root@hadoop100 learn]# crontab -e
no crontab for root - using an empty one
crontab: installing new crontab
[root@hadoop100 learn]# crontab -l
*/1 * * * * /bin/echo "Hello!" >> /root/learn/testcrontab.txt

```

```powershell
[root@hadoop100 learn]# tail -f testcrontab.txt 
Hello!
Hello!
Hello!
Hello!
^C
```

## 软件包管理

### RPM

#### RPM概述
RPM（RedHat Package Manager），RedHat软件包管理工具，类似windows里面的setup.exe，是Linux这系列操作系统里面的打包安装工具，它虽然是RedHat的标志，但理念是通用的。

RPM包的名称格式

Apache-1.3.23-11.i386.rpm

-	“apache” 软件名称
-	“1.3.23-11”软件的版本号，主版本和此版本
-	“i386”是软件所运行的硬件平台，Intel 32位微处理器的统称
-	“rpm”文件扩展名，代表RPM包
#### RPM查询命令（rpm -qa）
1. 基本语法

  `rpm -qa`				（功能描述：查询所安装的所有rpm软件包）

2. 经验技巧

  由于软件包比较多，一般都会采取过滤。`rpm -qa | grep rpm软件包`

3. 案例实操

  （1）查询firefox软件安装情况
```powershell
[root@hadoop101 Packages]# rpm -qa |grep firefox 
firefox-45.0.1-1.el6.centos.x86_64
```

#### RPM卸载命令（rpm -e）
1. 基本语法

  （1）`rpm -e RPM软件包`  

  （2） `rpm -e --nodeps 软件包`  

2. 选项说明

选项|功能
--|--
-e|卸载软件包
--nodeps|卸载软件时，不检查依赖。这样的话，那些使用该软件包的软件在此之后可能就不能正常工作了。
3. 案例实操
	
	（1）卸载firefox软件
```powershell
[root@hadoop101 Packages]# rpm -e firefox
```

#### RPM安装命令（rpm -ivh）
1. 基本语法
	
	`rpm -ivh RPM包全名`
	
2. 选项说明

选项|功能
--|--
-i|-i=install，安装
-v|-v=verbose，显示详细信息
-h|-h=hash，进度条
--nodeps|--nodeps，不检测依赖进度
3．案例实操

（1）安装firefox软件

```powershell
[root@hadoop101 Packages]# pwd
/media/CentOS_6.8_Final/Packages
[root@hadoop101 Packages]# rpm -ivh firefox-45.0.1-1.el6.centos.x86_64.rpm 
warning: firefox-45.0.1-1.el6.centos.x86_64.rpm: Header V3 RSA/SHA1 Signature, key ID c105b9de: NOKEY
Preparing...                ########################################### [100%]
```

### YUM仓库配置
#### YUM概述
YUM（全称为 Yellow dog Updater, Modified）是一个在Fedora和RedHat以及CentOS中的Shell前端软件包管理器。基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，**可以自动处理依赖性关系**，并且**一次安装所有依赖的软件包，无须繁琐地一次次下载**、安装，如图1-163所示

#### YUM的常用命令
1. 基本语法
	`yum [选项] [参数]`
2. 选项说明

选项|功能
--|--
-y|对所有提问都回答“yes”
3. 参数说明

参数|功能
--|--
install|安装rpm软件包
update|更新rpm软件包
check-update|检查是否有可用的更新rpm软件包
remove|删除指定的rpm软件包
list|显示软件包信息
clean|清理yum过期的缓存
deplist|显示yum软件包的所有依赖关系
4. 案例实操实操
	
	（1）采用yum方式安装firefox
```powershell
[root@hadoop101 ~]#yum -y install firefox.x86_64
```

#### 修改网络YUM源
**默认的系统YUM源，需要连接国外apache网站，网速比较慢，可以修改关联的网络YUM源为国内镜像的网站，比如网易163。**

1. 前期文件准备

  （1）前提条件linux系统必须可以联网

  （2）在Linux环境中访问该网络地址：http://mirrors.163.com/.help/centos.html，在使用说明中点击CentOS6->再点击保存


![保存](D:\Typora笔记\笔记\linux\picture\linux\修改网络YUM源1.png)

![在终端打开](D:\Typora笔记\笔记\linux\picture\linux\修改网络YUM源2.png)

2. 替换本地yum文件(在终端中执行）

  （1）把下载的文件移动到**/etc/yum.repos.d/**目录

  （2）进入到/etc/yum.repos.d/目录
```powershell
[root@hadoop100 下载]# mv CentOS6-Base-163.repo /etc/yum.repos.d/
[root@hadoop100 下载]# cd /etc/yum.repos.d/
[root@hadoop100 yum.repos.d]# ll
总用量 28
-rw-r--r--. 1 root root 2006 2月  24 20:48 CentOS6-Base-163.repo
-rw-r--r--. 1 root root 1991 5月  19 2016 CentOS-Base.repo
-rw-r--r--. 1 root root  647 5月  19 2016 CentOS-Debuginfo.repo
-rw-r--r--. 1 root root  289 5月  19 2016 CentOS-fasttrack.repo
-rw-r--r--. 1 root root  630 5月  19 2016 CentOS-Media.repo
-rw-r--r--. 1 root root 6259 5月  19 2016 CentOS-Vault.repo
```
（3）用CentOS6-Base-163.repo替换CentOS-Base.repo
```powershell
[root@hadoop100 yum.repos.d]# mv CentOS6-Base-163.repo CentOS-Base.repo 
mv：是否覆盖"CentOS-Base.repo"？ Y
[root@hadoop100 yum.repos.d]# ll
总用量 24
-rw-r--r--. 1 root root 2006 2月  24 20:48 CentOS-Base.repo
-rw-r--r--. 1 root root  647 5月  19 2016 CentOS-Debuginfo.repo
-rw-r--r--. 1 root root  289 5月  19 2016 CentOS-fasttrack.repo
-rw-r--r--. 1 root root  630 5月  19 2016 CentOS-Media.repo
-rw-r--r--. 1 root root 6259 5月  19 2016 CentOS-Vault.repo
```

3．安装命令

（1）[root@hadoop101 yum.repos.d]#`yum clean all`

（2）[root@hadoop101 yum.repos.d]#`yum makecache`

`yum makecache`就是把服务器的包信息下载到本地电脑缓存起来

```powershell
[root@hadoop100 yum.repos.d]# yum clean all
已加载插件：fastestmirror, refresh-packagekit, security
Cleaning repos: base extras updates
清理一切
Cleaning up list of fastest mirrors
[root@hadoop100 yum.repos.d]# yum makecache
已加载插件：fastestmirror, refresh-packagekit, security
Determining fastest mirrors
base                                                     | 3.7 kB     00:00     
base/group_gz                                            | 242 kB     00:00     
...
updates/other_db                                         | 377 kB     00:00     
元数据缓存已建立
```
4. 测试

```powershell
[root@hadoop100 yum.repos.d]# yum list | grep firefox
firefox.x86_64                             45.0.1-1.el6.centos           @anaconda-CentOS-201605220104.x86_64/6.8
firefox.i686                               68.5.0-2.el6.centos           updates
firefox.x86_64                             68.5.0-2.el6.centos           updates
```
5. 下载firefox

```powershell
[root@hadoop100 yum.repos.d]# yum -y install firefox.x86_64
已加载插件：fastestmirror, refresh-packagekit, security
设置安装进程
...
作为依赖被升级:
  nspr.x86_64 0:4.21.0-1.el6_10                                                 
  nss.x86_64 0:3.44.0-7.el6_10                                                  
  nss-softokn.x86_64 0:3.44.0-6.el6_10                                          
  nss-softokn-freebl.i686 0:3.44.0-6.el6_10                                     
  nss-softokn-freebl.x86_64 0:3.44.0-6.el6_10                                   
  nss-sysinit.x86_64 0:3.44.0-7.el6_10                                          
  nss-tools.x86_64 0:3.44.0-7.el6_10                                            
  nss-util.x86_64 0:3.44.0-1.el6_10                                             

完毕！
```
