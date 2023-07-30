# Docker

参考：
Docker容器学习笔记二（狂神说Java）：https://blog.csdn.net/qq_41822345/article/details/107123141
学习docker：https://www.runoob.com/docker/docker-tutorial.html
使用docker：https://labs.play-with-docker.com/

## 一、Docker概述

### 1.Docker为什么会出现？

- 一款产品： 开发–上线 两套环境！应用环境，应用配置！
- 开发 — 运维。 问题：我在我的电脑上可以允许！版本更新，导致服务不可用！对于运维来说考验十分
  大？
- 环境配置是十分的麻烦，每一个机器都要部署环境(集群Redis、ES、Hadoop…) !费事费力。
- 发布一个项目( jar + (Redis MySQL JDK ES) )，项目能不能带上环境安装打包！
- 之前在服务器配置一个应用的环境 Redis MySQL JDK ES Hadoop 配置超麻烦了，不能够跨平台。
- 开发环境Windows，最后发布到Linux！
- 传统：开发jar，运维来做！
- 现在：开发打包部署上线，一套流程做完！
- 安卓流程：java — apk —发布（应用商店）一 张三使用apk一安装即可用！
- docker流程： java-jar（环境） — 打包项目帯上环境（镜像） — ( Docker仓库：商店）----- 下载我们发布的镜像 ----直接运行即可
- Docker给以上的问题，提出了解决方案！

<img src=".\picture\docker.png" style="zoom: 67%;" />

- Docker的思想就来自于集装箱！
- JRE – 多个应用(端口冲突) – 原来都是交叉的！
- 隔离：Docker核心思想！打包装箱！每个箱子是互相隔离的。
- Docker通过隔离机制，可以将服务器利用到极致！
- 本质：所有的技术都是因为出现了一些问题，我们需要去解决，才去学习！

### 2.Dcoker的历史

- 2010年，几个的年轻人，就在美国成立了一家公司 dotcloud，做一些pass的云计算服务！
- LXC（Linux Container容器）有关的容器技术！Linux Container容器是一种内核虚拟化技术，可以提供轻量级的虚拟化，以便隔离进程和资源。他们将自己的技术（容器化技术）命名就是 Docker。
- Docker刚刚延生的时候，没有引起行业的注意！dotCloud，就活不下去！
- 开源，2013年，Docker开源！
- 越来越多的人发现docker的优点！火了。Docker每个月都会更新一个版本！
- 2014年4月9日，Docker1.0发布！
- docker为什么这么火？十分的轻巧！
  - 在容器技术出来之前，我们都是使用虚拟机技术！
  - 虚拟机：在window中装一个VMware，通过这个软件我们可以虚拟出来一台或者多台电脑！笨重！
  - 虚拟机也属于虚拟化技术，Docker容器技术，也是一种虚拟化技术！

```shelll
vm : linux centos 原生镜像（一个电脑！） 隔离、需要开启多个虚拟机！ 几个G 几分钟
docker: 隔离，镜像（最核心的环境 4m + jdk + mysql）十分的小巧，运行镜像就可以了！小巧！
几个M 秒级启动！
```

**聊聊docker：**

- Docker基于Go语言开发的！开源项目！
- docker官网：https://www.docker.com/
- 文档：https://docs.docker.com/ Docker的文档是超级详细的！
- 仓库：https://hub.docker.com

### 3.Docker能做什么？

> 之前的虚拟机技术
>
> <img src=".\picture\之前的虚拟机技术.png" style="zoom:80%;" />
>
> **虚拟机技术缺点**：
>
> 1. 资源占用十分多
> 2. 冗余步骤多
> 3. 启动很慢

> 容器化技术
>
> 容器化技术不是模拟一个完整的操作系统
>
> <img src=".\picture\容器化技术.png" style="zoom:80%;" />

比较Docker和虚拟机技术的不同：

- 传统虚拟机，虚拟出一条硬件，运行一个完整的操作系统，然后在这个系统上安装和运行软件
- 容器内的应用直接运行在宿主机的内容，容器是没有自己的内核的，也没有虚拟我们的硬件，所以就轻便了
- 每个容器间是互相隔离，**每个容器内都有一个属于自己的文件系统**，互不影响

==DevOps（开发、运维）==

- **应用更快速的交付和部署**
  - 传统：一对帮助文档，安装程序。
  - Docker：打包镜像发布测试一键运行。
- **更便捷的升级和扩缩容**
  - 使用了 Docker之后，我们部署应用就和搭积木一样
  - 项目打包为一个镜像，扩展服务器A！服务器B
- **更简单的系统运维**
- **更高效的计算资源利用**
  - Docker是**内核级别的虚拟化**，可以在一个物理机上可以运行很多的容器实例！服务器的性能可以被压榨
    到极致。

## Docker安装

### Docker的基本组成

<img src=".\picture\Docker的基本组成.png" style="zoom:80%;" />

**镜像（image)**：

- docker镜像就好比是一个目标，可以通过这个目标来创建容器服务，tomcat镜像=== > run == >容器（提供服务器），通过这个镜像可以创建多个容器（最终服务运行或者项目运行就是在容器中的）。

**容器(container)**：

- Docker利用容器技术，独立运行一个或者一组应用，通过镜像来创建的.
- 启动，停止，删除，基本命令
- 目前就可以把这个容器理解为就是一个简易的 Linux系统。

**仓库(repository)**：

- 仓库就是存放镜像的地方！
- 仓库分为公有仓库和私有仓库。(很类似git)
- Docker Hub是国外的。
- 阿里云…都有容器服务器(**配置镜像加速!**)

### 安装Docker

**环境准备**

1.Linux要求内核3.0以上

2.CentOS 7

```shell
[root@iz2zeak7sgj6i7hrb2g862z ~]# uname -r
3.10.0-514.26.2.el7.x86_64	# 要求3.0以上
[root@iz2zeak7sgj6i7hrb2g862z ~]# cat /etc/os-release 
NAME="CentOS Linux"
VERSION="7 (Core)"
ID="centos"
ID_LIKE="rhel fedora"
VERSION_ID="7"
PRETTY_NAME="CentOS Linux 7 (Core)"
ANSI_COLOR="0;31"
CPE_NAME="cpe:/o:centos:centos:7"
HOME_URL="https://www.centos.org/"
BUG_REPORT_URL="https://bugs.centos.org/"

CENTOS_MANTISBT_PROJECT="CentOS-7"
CENTOS_MANTISBT_PROJECT_VERSION="7"
REDHAT_SUPPORT_PRODUCT="centos"
REDHAT_SUPPORT_PRODUCT_VERSION="7"
```

安装

帮助文档：https://docs.docker.com/engine/install/

卸载与安装

```powershell
#1.卸载旧版本
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
#2.需要的安装包
yum install -y yum-utils

#3.设置镜像的仓库
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
#上述方法默认是从国外的，不推荐

#推荐使用国内的
yum-config-manager \
    --add-repo \
    https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
    
#更新yum软件包索引
yum makecache fast

#4.安装docker相关的 docker-ce 社区版 而ee是企业版
yum install docker-ce docker-ce-cli containerd.io # 这里我们使用社区版即可

#5.启动docker
systemctl start docker

#6. 使用docker version查看是否按照成功
docker version

#7. 测试
docker run hello-world
```

```powershell
#8.查看已经下载的镜像(从这里可以查看已有镜像的id)
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker images
REPOSITORY            TAG                 IMAGE ID            CREATED             SIZE
hello-world           latest              bf756fb1ae65        4 months ago      13.3kB
```

卸载docker

```powershell
#1. 卸载依赖
yum remove docker-ce docker-ce-cli containerd.io
#2. 删除资源
rm -rf /var/lib/docker
# /var/lib/docker 是docker的默认工作路径！
```

### 阿里云镜像加速

#### 1、登录阿里云找到容器服务

![](.\picture\登录阿里云找到容器服务.png)

#### 2、找到镜像加速器

![](.\picture\找到镜像加速器.png)

#### 3、配置使用

```powershell
#1.创建一个目录
sudo mkdir -p /etc/docker

#2.编写配置文件
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://t2wwyxhb.mirror.aliyuncs.com"]
}
EOF

#3.重启服务
sudo systemctl daemon-reload
sudo systemctl restart docker
```

### 回顾HelloWorld流程

![](.\picture\回顾HelloWorld流程.png)

**docker run 流程图**

<img src=".\picture\docker run 流程图.png" style="zoom:80%;" />

### 底层原理

Docker是怎么工作的？

- Docker是一个Client-Server结构的系统，Docker的守护进程运行在主机上。通过Socket从客户端访问！
- Docker-Server接收到Docker-Client的指令，就会执行这个命令！

![]([./picture/docker%E5%BA%95%E5%B1%82%E5%8E%9F%E7%90%86.jpg))

为什么Docker比Vm快

1. docker有着比虚拟机更少的抽象层。由于docker不需要**Hypervisor**实现硬件资源虚拟化,运行在docker容器上的程序直接使用的都是实际物理机的硬件资源。因此在CPU、内存利用率上docker将会在效率上有明显优势。

2. docker利用的是宿主机的内核,而不需要Guest OS。

   ```
   GuestOS： VM（虚拟机）里的的系统（OS）
   
   HostOS：物理机里的系统（OS）
   ```

![]([./picture/docker%E4%B8%8Evm.png))

- 因此,当新建一个容器时,docker不需要和虚拟机一样重新加载一个操作系统内核。因而避免引导、加载操作系统内核返个比较费时费资源的过程,当新建一个虚拟机时,虚拟机软件需要加载GuestOS,返个新建过程是分钟级别的。而docker由于直接利用宿主机的操作系统,则省略了这个复杂的过程,因此新建一个docker容器只需要几秒钟。

## Docker的常用命令

### 帮助命令

```dockerfile
docker version    #显示docker的版本信息。
docker info       #显示docker的系统信息，包括镜像和容器的数量
docker 命令 --help #帮助命令
```

帮助文档的地址：https://docs.docker.com/engine/reference/commandline/build/

### 镜像命令

```dockerfile
docker images #查看所有本地主机上的镜像 可以使用docker image ls代替

docker search #搜索镜像

docker pull #下载镜像 docker image pull

docker rmi #删除镜像 docker image rm
```

#### docker images查看所有本地的主机上的镜像

```shell
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker images
REPOSITORY            TAG                 IMAGE ID            CREATED           SIZE
hello-world           latest              bf756fb1ae65        4 months ago     13.3kB
mysql                 5.7                 b84d68d0a7db        6 days ago       448MB

# 解释
#REPOSITORY			# 镜像的仓库源
#TAG				# 镜像的标签(版本)		---lastest 表示最新版本
#IMAGE ID			# 镜像的id
#CREATED			# 镜像的创建时间
#SIZE				# 镜像的大小

# 可选项
Options:
  -a, --all         Show all images (default hides intermediate images) #列出所有镜像
  -q, --quiet       Only show numeric IDs # 只显示镜像的id
  
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker images -a  #列出所有镜像详细信息
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker images -aq #列出所有镜像的id
d5f28a0bb0d0
f19c56ce92a8
1b6b1fe7261e
1b6b1fe7261e
```

#### docker search 搜索镜像

```shell
[root@centos101 ~]# docker search mysql
NAME                              DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
mysql                             MySQL is a widely used, open-source relation…   10876     [OK]       
mariadb                           MariaDB Server is a high performing open sou…   4102      [OK]       
mysql/mysql-server                Optimized MySQL Server Docker images. Create…   808                  [OK]

# --filter=STARS=3000 #过滤，搜索出来的镜像收藏STARS数量大于3000的
Options:
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print search using a Go template
      --limit int       Max number of search results (default 25)
      --no-trunc        Don't truncate output

[root@centos101 ~]# docker search mysql --filter=STARS=3000
NAME      DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
mysql     MySQL is a widely used, open-source relation…   10876     [OK]       
mariadb   MariaDB Server is a high performing open sou…   4102      [OK]
```

#### docker pull 下载镜像

```shell
# 下载镜像 docker pull 镜像名[:tag]
[root@AlibabaECS ~]# docker pull mysql
Using default tag: latest # 如果不写tag,默认就是latest
latest: Pulling from library/mysql 
bf5952930446: Pull complete # 分层下载，docker image的核心 联合文件系统
8254623a9871: Pull complete 
938e3e06dac4: Pull complete 
ea28ebf28884: Pull complete 
f3cef38785c2: Pull complete 
894f9792565a: Pull complete 
1d8a57523420: Pull complete 
6c676912929f: Pull complete 
ff39fdb566b4: Pull complete 
fff872988aba: Pull complete 
4d34e365ae68: Pull complete 
7886ee20621e: Pull complete 
Digest: sha256:c358e72e100ab493a0304bda35e6f239db2ec8c9bb836d8a427ac34307d074ed # 签名
Status: Downloaded newer image for mysql:latest
docker.io/library/mysql:latest # 真实地址

# 两条命令等价
docker pull mysql
docker.io/library/mysql:latest

# 指定版本下载
docker pull mysql:5.7

[root@AlibabaECS ~]# docker pull mysql:5.7
5.7: Pulling from library/mysql
bf5952930446: Already exists 
8254623a9871: Already exists 
938e3e06dac4: Already exists 
ea28ebf28884: Already exists 
f3cef38785c2: Already exists 
894f9792565a: Already exists 
1d8a57523420: Already exists 
5f09bf1d31c1: Pull complete 
1b6ff254abe7: Pull complete 
74310a0bf42d: Pull complete 
d398726627fd: Pull complete 
Digest: sha256:da58f943b94721d46e87d5de208dc07302a8b13e638cd1d24285d222376d6d84
Status: Downloaded newer image for mysql:5.7
docker.io/library/mysql:5.7
```

查看已安装的镜像

```shell
[root@centos101 ~]# docker images
REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
mysql        5.7       2c9028880e58   3 days ago   447MB
```

#### docker rmi 删除镜像

```shell
[root@AlibabaECS ~]# docker rmi -f 容器id                # 删除指定的容器
[root@AlibabaECS ~]# docker rmi -f  容器id 容器id 容器id  # 删除多个容器
[root@AlibabaECS ~]# docker rmi -f $(docker images -aq) # 删除全部容器
```

### 容器命令

**说明：我们有了镜像才可以创建容器，linux，下载一个centos镜像来测试学习**

```
docker pull centos
```

#### 新建容器并启动

```shell
docker run [可选参数] image

# 参数说明
--name = "Name"    容器名字  tomcat01，tomcat02,用来区分容器
-d                 后台方式运行
-it                使用交互方式运行，进入容器查看区分
-p                 指定容器的端口 -p 8080：8080
    -p ip:主机端口：容器端口
    -p 主机端口：容器端口(常用)
    -p 容器端口
    容器端口
-p                 随机指定端口

# 测试，启动并进入容器
[root@AlibabaECS bin]# docker run -it centos /bin/bash
[root@94d468db18da /]# ls  # 查看容器内的centos，基础版本，很多命令都是不完善的！
bin  etc   lib    lost+found  mnt  proc  run   srv  tmp  var
dev  home  lib64  media       opt  root  sbin  sys  usr


# 从容器中退回主机
[root@94d468db18da /]# exit


```

#### 列出所有的运行的容器

```shell
# docker ps 命令
	   # 列出当前正在运行的容器
  -a   # 列出当前正在运行的容器+带出历史运行过的容器
  -n=? # 显示最近创建的容器
  -q   # 只显示容器的编号
  
[root@centos101 ~]# docker ps 
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@centos101 ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                      PORTS     NAMES
2dd89afd3141   centos    "/bin/bash"   24 seconds ago   Exited (0) 15 seconds ago             friendly_feistel
[root@centos101 ~]# docker ps -aq
2dd89afd3141
```

#### 退出容器

```shell
exit            # 直接容器停止并退出
Ctrl + P + Q    # 容器不停止退出


```

#### 删除容器

```shell
docker rm 容器id                  # 删除指定容器，不能删除正在运行的容器，如果要强制删除 rm -f
docker rm -f $(docker ps -aq)    # 删除所有的容器
docker ps -aq|xargs docker rm    # 删除所有的容器
```

#### 启动和停止容器的操作

```shell
docker start 容器id        # 启动容器
docker restart 容器id      # 重启容器
docker stop 容器id         # 停止当前正在运行的容器
docker kill 容器id         # 强制停止当前容器
```

### 常用其他命令

#### 后台启动容器

```shell
# 命令 docker run -d 镜像名
[root@AlibabaECS /]# docker run -d centos

# 问题docker ps, 发现 centos 停止了

# 常见的坑, docker容器使用后台运行，就必须要有一个前台进程，docker发现没有应用，就会自动停止
# nginx,容器启动后，发现自己没有提供服务，就会立刻停止，就是没有程序了
```

#### 查看日志

```shell
docker logs --help
Options:
      --details        Show extra details provided to logs 
*  -f, --follow         Follow log output
      --since string   Show logs since timestamp (e.g. 2013-01-02T13:23:37) or relative (e.g. 42m for 42 minutes)
*      --tail string    Number of lines to show from the end of the logs (default "all")
*  -t, --timestamps     Show timestamps
      --until string   Show logs before a timestamp (e.g. 2013-01-02T13:23:37) or relative (e.g. 42m for 42 minutes)

docker run -d centos /bin/sh -c "while true;do echo 6666;sleep 1;done" #模拟日志      

#显示日志
-tf		#显示日志信息（一直更新）
--tail number #需要显示日志条数
docker logs -t --tail n 容器id #查看n行日志
docker logs -ft 容器id #跟着日志

docker logs -f -t --tail 容器，没有日志

# 自己编写一段shell脚本
[root@AlibabaECS /]# docker run -d centos /bin/sh -c "while true;do echo kuangshen;sleep 1;done"

# 显示日志
-tf                # 显示日志
--tail number      # 要显示的日志条数

[root@AlibabaECS /]# docker logs -ft --tail 10 f1178d5b0bd8
```

#### 查看容器中进程信息ps

```shell
# 命令 docker top 容器id

[root@AlibabaECS /]# docker top f1178d5b0bd8
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                21626               21609               0                   while true;do echo kuangshen;sleep 1;done
root                27492               21626               0                   13:15               ?                   00:00:00            
```

#### 查看镜像元数据

```shell
# 命令
docker inspect 容器id

#测试
[root@AlibabaECS /]# docker inspect 55321bcae33d
[
    {
        "Id": "55321bcae33d15da8280bcac1d2bc1141d213bcc8f8e792edfd832ff61ae5066",
        "Created": "2020-05-15T05:22:05.515909071Z",
        "Path": "/bin/sh",
        "Args": [
            "-c",
            "while true;do echo 6666;sleep 1;done"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 22973,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2020-05-15T05:22:06.165904633Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:470671670cac686c7cf0081e0b37da2e9f4f768ddc5f6a26102ccd1c6954c1ee",
        "ResolvConfPath": "/var/lib/docker/containers/55321bcae33d15da8280bcac1d2bc1141d213bcc8f8e792edfd832ff61ae5066/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/55321bcae33d15da8280bcac1d2bc1141d213bcc8f8e792edfd832ff61ae5066/hostname",
        "HostsPath": "/var/lib/docker/containers/55321bcae33d15da8280bcac1d2bc1141d213bcc8f8e792edfd832ff61ae5066/hosts",
        "LogPath": "/var/lib/docker/containers/55321bcae33d15da8280bcac1d2bc1141d213bcc8f8e792edfd832ff61ae5066/55321bcae33d15da8280bcac1d2bc1141d213bcc8f8e792edfd832ff61ae5066-json.log",
        "Name": "/bold_bell",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "docker-default",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "Capabilities": null,
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/1f347949ba49c4dbee70cea9ff3af39a14e602bc8fac8331c46347bf6708757a-init/diff:/var/lib/docker/overlay2/5afcd8220c51854a847a36f52775b4ed0acb16fe6cfaec3bd2e5df59863835ba/diff",
                "MergedDir": "/var/lib/docker/overlay2/1f347949ba49c4dbee70cea9ff3af39a14e602bc8fac8331c46347bf6708757a/merged",
                "UpperDir": "/var/lib/docker/overlay2/1f347949ba49c4dbee70cea9ff3af39a14e602bc8fac8331c46347bf6708757a/diff",
                "WorkDir": "/var/lib/docker/overlay2/1f347949ba49c4dbee70cea9ff3af39a14e602bc8fac8331c46347bf6708757a/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "55321bcae33d",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/sh",
                "-c",
                "while true;do echo 6666;sleep 1;done"
            ],
            "Image": "centos",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.label-schema.build-date": "20200114",
                "org.label-schema.license": "GPLv2",
                "org.label-schema.name": "CentOS Base Image",
                "org.label-schema.schema-version": "1.0",
                "org.label-schema.vendor": "CentOS",
                "org.opencontainers.image.created": "2020-01-14 00:00:00-08:00",
                "org.opencontainers.image.licenses": "GPL-2.0-only",
                "org.opencontainers.image.title": "CentOS Base Image",
                "org.opencontainers.image.vendor": "CentOS"
            }
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "63ed0c837f35c12453bae9661859f37a08541a0749afb86e881869bf6fd9031b",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {},
            "SandboxKey": "/var/run/docker/netns/63ed0c837f35",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "b129d9a5a2cbb92722a2101244bd81a9e3d8af034e83f338c13790a1a94552a1",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.4",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:04",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "ad5ada6a106f5ba3dda9ce4bc1475a4bb593bf5f7fbead72196e66515e8ac36a",
                    "EndpointID": "b129d9a5a2cbb92722a2101244bd81a9e3d8af034e83f338c13790a1a94552a1",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.4",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:04",
                    "DriverOpts": null
                }
            }
        }
    }
]
```

#### 进入当前正在运行的容器

```shell
# 我们通常都是使用后台方式运行的，需要进入容器，修改一些配置

# 命令
docker exec -it 容器id baseShell

# 测试
[root@AlibabaECS ~]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
f1178d5b0bd8        centos              "/bin/sh -c 'while t…"   2 hours ago         Up 2 hours                              stupefied_colden
[root@AlibabaECS ~]# docker exec -it f1178d5b0bd8 /bin/bash
[root@f1178d5b0bd8 /]# ls
bin  etc   lib    lost+found  mnt  proc  run   srv  tmp  var
dev  home  lib64  media       opt  root  sbin  sys  usr
[root@f1178d5b0bd8 /]# ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 05:10 ?        00:00:02 /bin/sh -c while true;do echo kuangshen;sleep 1;done
root      8869     0  0 07:38 pts/0    00:00:00 /bin/bash
root      8887     1  0 07:38 ?        00:00:00 /usr/bin/coreutils --coreutils-prog-shebang=sleep /usr/bin/
root      8888  8869  0 07:38 pts/0    00:00:00 ps -ef

# 方式二
docker attach 容器id

# 测试
[root@AlibabaECS ~]# docker attach f1178d5b0bd8
正在执行当前的代码...

# docker exec        # 进入容器后开启一个新的终端，可以在里面操作(常用)
# docker attach      # 进入容器正在执行的终端，不会启动新的进程
```

#### 从容器内拷贝到主机上

```shell
# 命令
docker cp [r] 容器id :容器内路径 目的地主机路径
# 参数r : 递归拷贝

# 测试
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker ps
CONTAINER ID     IMAGE    COMMAND     CREATED         STATUS       PORTS      NAMES
56a5583b25b4     centos   "/bin/bash" 7seconds ago    Up 6 seconds      

#1. 进入docker容器内部
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker exec -it 56a5583b25b4 /bin/bash
[root@55321bcae33d /]# ls
bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

#2. 新建一个文件
[root@55321bcae33d /]# echo "hello" > java.java
[root@55321bcae33d /]# cat hello.java 
hello
[root@55321bcae33d /]# exit
exit

#2. hello.java拷贝到home文件加下
[root@iz2zeak7sgj6i7hrb2g862z /]# docker cp 56a5583b25b4:/hello.java /home 
[root@iz2zeak7sgj6i7hrb2g862z /]# cd /home
[root@iz2zeak7sgj6i7hrb2g862z home]# ls -l	#可以看见java.java存在
total 8
-rw-r--r-- 1 root root    0 May 19 22:09 haust.java
-rw-r--r-- 1 root root    6 May 22 11:12 java.java
drwx------ 3 www  www  4096 May  8 12:14 www

# 拷贝是一个手动的过程，未来我们使用 -v 卷的技术，可以实现，自动同步 容器：/home 主机：/home
```

### 小结

![](.\picture\docker命令.jpg)

```shell
  attach      Attach local standard input, output, and error streams to a running container
  #当前shell下 attach连接指定运行的镜像
  build       Build an image from a Dockerfile # 通过Dockerfile定制镜像
  commit      Create a new image from a container's changes #提交当前容器为新的镜像
  cp          Copy files/folders between a container and the local filesystem #拷贝文件
  create      Create a new container #创建一个新的容器
  diff        Inspect changes to files or directories on a container's filesystem #查看docker容器的变化
  events      Get real time events from the server # 从服务获取容器实时时间
  exec        Run a command in a running container # 在运行中的容器上运行命令
  export      Export a container's filesystem as a tar archive #导出容器文件系统作为一个tar归档文件[对应import]
  history     Show the history of an image # 展示一个镜像形成历史
  images      List images #列出系统当前的镜像
  import      Import the contents from a tarball to create a filesystem image #从tar包中导入内容创建一个文件系统镜像
  info        Display system-wide information # 显示全系统信息
  inspect     Return low-level information on Docker objects #查看容器详细信息
  kill        Kill one or more running containers # kill指定docker容器
  load        Load an image from a tar archive or STDIN #从一个tar包或标准输入中加载一个镜像[对应save]
  login       Log in to a Docker registry #注册或登录一个docker源服务器
  logout      Log out from a Docker registry #从当前Docker registry推出
  logs        Fetch the logs of a container #输出当前容器日志信息
  pause       Pause all processes within one or more containers #暂停容器
  port        List port mappings or a specific mapping for the container #查看映射端口对应的容器内部源端口
  ps          List containers #列出容器列表
  pull        Pull an image or a repository from a registry #从docker源镜像服务器拉去制定的镜像或者库镜像
  push        Push an image or a repository to a registry #推送制定镜像或者库镜像至docker源服务器
  rename      Rename a container #
  restart     Restart one or more containers #重启运行的容器
  rm          Remove one or more containers # 移除一个或者多个容器
  rmi         Remove one or more images # 移除一个或者多个镜像【五容器使用该镜像才可以删除，否则需删除相关容器才可继续或-f强制删除】
  run         Run a command in a new container # 创建一个新的容器并运行一个命令
  save        Save one or more images to a tar archive (streamed to STDOUT by default) #曹村一个镜像为一个tar包【对应load】
  search      Search the Docker Hub for images # 在docker hub 中搜索镜像
  start       Start one or more stopped containers # 启动容器
  stats       Display a live stream of container(s) resource usage statistics # 
  stop        Stop one or more running containers # 停止容器
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE 给源镜像打标签
  top         Display the running processes of a container # 查看容器中运行的进程信息
  unpause     Unpause all processes within one or more containers # 取消暂停容器
  update      Update configuration of one or more containers
  version     Show the Docker version information # 查看docker版本号
  wait        Block until one or more containers stop, then print their exit codes # 截取容器停止时的推出状态
```

## 作业练习

### 作业一：Docker 安装Nginx

```shell
#1. 搜索镜像 search 建议大家去docker搜索，可以看到帮助文档
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker search nginx

#2. 拉取下载镜像 pull
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker pull nginx

#3. 查看是否下载成功镜像
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker images

#3. 运行测试
# -d 后台运行
# --name 给容器命名
# -p 宿主机端口：容器内部端口
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker run -d --name nginx01 -p 3344:80 nginx
aa664b0c8ed98f532453ce1c599be823bcc1f3c9209e5078615af416ccb454c2

#4. 查看正在启动的镜像
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
75943663c116        nginx               "nginx -g 'daemon of…"   41 seconds ago      Up 40 seconds       0.0.0.0:82->80/tcp   nginx00

# 本机自测
[root@AlibabaECS home]# curl localhost:3344

#5. 进入容器
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker exec -it nginx01 /bin/bash #进入
root@aa664b0c8ed9:/# whereis nginx	#找到nginx位置
nginx: /usr/sbin/nginx /usr/lib/nginx /etc/nginx /usr/share/nginx
root@aa664b0c8ed9:/# cd /etc/nginx/
root@aa664b0c8ed9:/etc/nginx# ls
conf.d	fastcgi_params	koi-utf  koi-win  mime.types  modules  nginx.conf  scgi_params	uwsgi_params  win-utf

#6. 退出容器
root@aa664b0c8ed9:/etc/nginx# exit
exit

#7. 停止容器
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
aa664b0c8ed9        nginx               "nginx -g 'daemon of…"   10 minutes ago      Up 10 minutes       0.0.0.0:3344->80/tcp   nginx01
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker stop aa664b0c8ed9
```

**宿主机端口** 和 **容器内部端口** 以及端口暴露：

![](.\picture\宿主机端口和容器内部端口.jpg)

**问题：**我们每次改动nginx配置文件，都需要进入容器内部？十分麻烦，我要是可以在容器外部提供一个映射路径，达到在容器外部修改文件名，容器内部就可以自动修改？-v 数据卷技术！

### 作业二：用docker 来装一个tomcat

```shell
# 下载 tomcat9.0
# 之前的启动都是后台，停止了容器，容器还是可以查到， docker run -it --rm 镜像名 一般是用来测试，用完就删除
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker run -it --rm tomcat:9.0

--rm       Automatically remove the container when it exits 用完即删

#下载 最新版
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker pull tomcat

#查看下载的镜像
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker images

#以后台方式，暴露端口方式，启动运行
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker run -d -p 8080:8080 --name tomcat01 tomcat

#测试访问有没有问题
curl localhost:8080

#根据容器id进入tomcat容器
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker exec -it 645596565d3f /bin/bash
root@645596565d3f:/usr/local/tomcat# 
#查看tomcat容器内部内容：
root@645596565d3f:/usr/local/tomcat# ls -l
total 152
-rw-r--r-- 1 root root 18982 May  5 20:40 BUILDING.txt
-rw-r--r-- 1 root root  5409 May  5 20:40 CONTRIBUTING.md
-rw-r--r-- 1 root root 57092 May  5 20:40 LICENSE
-rw-r--r-- 1 root root  2333 May  5 20:40 NOTICE
-rw-r--r-- 1 root root  3255 May  5 20:40 README.md
-rw-r--r-- 1 root root  6898 May  5 20:40 RELEASE-NOTES
-rw-r--r-- 1 root root 16262 May  5 20:40 RUNNING.txt
drwxr-xr-x 2 root root  4096 May 16 12:05 bin
drwxr-xr-x 1 root root  4096 May 21 11:04 conf
drwxr-xr-x 2 root root  4096 May 16 12:05 lib
drwxrwxrwx 1 root root  4096 May 21 11:04 logs
drwxr-xr-x 2 root root  4096 May 16 12:05 native-jni-lib
drwxrwxrwx 2 root root  4096 May 16 12:05 temp
drwxr-xr-x 2 root root  4096 May 16 12:05 webapps
drwxr-xr-x 7 root root  4096 May  5 20:37 webapps.dist
drwxrwxrwx 2 root root  4096 May  5 20:36 work
root@645596565d3f:/usr/local/tomcat# 
#进入webapps目录
root@645596565d3f:/usr/local/tomcat# cd webapps
root@645596565d3f:/usr/local/tomcat/webapps# ls
root@645596565d3f:/usr/local/tomcat/webapps# 
# 发现问题：1、linux命令少了。 2.webapps目录为空 
# 原因：阿里云镜像的原因，阿里云默认是最小的镜像，所以不必要的都剔除掉
# 保证最小可运行的环境！
# 解决方案：
# 将webapps.dist下的文件都拷贝到webapps下即可
root@645596565d3f:/usr/local/tomcat# ls # 找到webapps.dist
BUILDING.txt	 LICENSE  README.md	 RUNNING.txt  conf  logs  temp     webapps.dist
CONTRIBUTING.md  NOTICE   RELEASE-NOTES  bin   lib   native-jni-lib  webapps  work

root@645596565d3f:/usr/local/tomcat# cd webapps.dist/ # 进入webapps.dist 
root@645596565d3f:/usr/local/tomcat/webapps.dist# ls # 查看内容
ROOT  docs  examples  host-manager  manager

root@645596565d3f:/usr/local/tomcat/webapps.dist# cd ..
root@645596565d3f:/usr/local/tomcat# cp -r webapps.dist/* webapps # 拷贝webapps.dist 内容给webapps
root@645596565d3f:/usr/local/tomcat# cd webapps #进入webapps
root@645596565d3f:/usr/local/tomcat/webapps# ls #查看拷贝结果
ROOT  docs  examples  host-manager  manager
```

这样docker部署tomcat就可以访问了

![](.\picture\tomcat可以访问.png)

**问题**:我们以后要部署项目，如果每次都要进入容器是不是十分麻烦？要是可以在容器外部提供一个映射路径，比如webapps，我们在外部放置项目，就自动同步内部就好了！

### 作业三：部署elasticsearch+kibana

```shell
# es 暴露的端口很多！
# es 十分耗内存
# es 的数据一般需要放置到安全目录！挂载
# docker run -d --name elasticsearch --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" 
# --net somenetwork ? 网络配置 

# 下载启动elasticsearch
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.6.2

# 启动了 linux就卡住了

# 查看docker容器使用内存情况
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker stats  

# 测试一下es是否成功启动
[root@iz2zeak7sgj6i7hrb2g862z ~]# curl localhost:9200
{
  "name" : "d73ad2f22dd3",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "atFKgANxS8CzgIyCB8PGxA",
  "version" : {
    "number" : "7.6.2",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "ef48eb35cf30adf4db14086e8aabd07ef6fb113f",
    "build_date" : "2020-03-26T06:34:37.794943Z",
    "build_snapshot" : false,
    "lucene_version" : "8.4.0",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}

#测试成功就关掉elasticSearch，防止耗内存
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker stop d834ce2bd306
d834ce2bd306

[root@iz2zeak7sgj6i7hrb2g862z ~]# docker stats  # 查看docker容器使用内存情况
```

```shell
#关闭，添加内存的限制，修改配置文件 -e 环境配置修改
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker rm -f d73ad2f22dd3    # stop命令也行                                              
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e ES_JAVA_OPTS="-Xms64m -Xmx512m" elasticsearch:7.6.2

[root@iz2zeak7sgj6i7hrb2g862z ~]# curl localhost:9200
{
  "name" : "b72c9847ec48",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "yNAK0EORSvq3Wtaqe2QqAg",
  "version" : {
    "number" : "7.6.2",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "ef48eb35cf30adf4db14086e8aabd07ef6fb113f",
    "build_date" : "2020-03-26T06:34:37.794943Z",
    "build_snapshot" : false,
    "lucene_version" : "8.4.0",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}
```

作业三：使用kibana连接es (elasticSearch)？思考网络如何才能连接

容器内部互相隔离

![](.\picture\使用kibana连接es.jpg)

## 可视化

### Portainer 可视化面板安装

- portainer(先用这个)

```shell
# 运行如下命令即可 打开可视化服务
docker run -d -p 8080:9000 \
--restart=always -v /var/run/docker.sock:/var/run/docker.sock --privileged=true portainer/portainer
```

- Rancher(CI/CD再用)

**什么是portainer？**

Docker图形化界面管理工具！提供一个后台面板供我们操作！

```shell
# 安装命令
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker run -d -p 8080:9000 \
> --restart=always -v /var/run/docker.sock:/var/run/docker.sock --privileged=true portainer/portainer

Unable to find image 'portainer/portainer:latest' locally
latest: Pulling from portainer/portainer
d1e017099d17: Pull complete 
a7dca5b5a9e8: Pull complete 
Digest: sha256:4ae7f14330b56ffc8728e63d355bc4bc7381417fa45ba0597e5dd32682901080
Status: Downloaded newer image for portainer/portainer:latest
81753869c4fd438cec0e31659cbed0d112ad22bbcfcb9605483b126ee8ff306d
```

测试访问： 外网：8080 ：http://123.56.247.59:8080/

![](.\picture\portainer访问.png)

进入之后的面板

![](.\picture\portainer进入面板.png)

## Docker镜像讲解

### 镜像是什么

镜像是一种轻量级、**可执行的独立软件包**，用来打包软件运行环境和基于运行环境开发的软件，他包含运行某个软件所需的所有内容，包括代码、运行时库、环境变量和配置文件。

所有的应用，直接打包docker镜像，就可以直接跑起来！

如何得到镜像：

- 从远程仓库下载
- 拷贝
- 自己制作一个镜像 DockerFile

### Docker镜像加载原理

**UnionFs （联合文件系统)**

- UnionFs（联合文件系统）：Union文件系统（UnionFs）是一种分层、轻量级并且高性能的文件系统，他支持**对文件系统的修改作为一次提交来一层层的叠加**，同时可以将不同目录挂载到同一个虚拟文件系统下（ unite several directories into a single virtual filesystem)。Union文件系统是 Docker镜像的基础。镜像可以通过分层来进行继承，基于基础镜像（没有父镜像），可以制作各种具体的应用镜像
- 特性：一次同时加载多个文件系统，但从外面看起来，只能看到一个文件系统，联合加载会把各层文件系统叠加起来，这样最终的文件系统会包含所有底层的文件和目录

**Docker镜像加载原理**

- docker的镜像实际上由一层一层的文件系统组成，这种层级的文件系统UnionFS。
  **bootfs**(**boot file system**系统启动需要引导加载）主要包含 **bootloader**和 **Kernel**, bootloader主要是引导加 **kernel**, Linux刚启动时会加载**bootfs**文件系统，在 Docker镜像的最底层是 bootfs。这一层与我们典型的Linux/Unix系统是一样的，包含boot加载器和内核。当boot加载完成之后整个内核就都在内存中了，此时内存的使用权已由 bootfs转交给内核，此时系统也会卸载bootfs。

  ![](.\picture\Docker镜像加载原理.jpg)

- **rootfs**（**root file system**),在 bootfs之上。包含的就是典型 Linux系统中的/dev,/proc,/bin,/etc等标准目录和文件。 rootfs就是各种不同的操作系统发行版，比如 Ubuntu, Centos等等。

- 平时我们安装进虚拟机的CentOS都是好几个G，为什么Docker这里才200M？

  ![](.\picture\docker的centos大小.jpg)

- 对于一个精简的OS,**rootfs**可以很小，只需要包含最基本的命令，工具和程序库就可以了，因为==底层直接用Host的kernel，自己只需要提供rootfs就可以了==，**由此可见对于不同的Linux发行版， boots基本是一致的， rootfs会有差別，因此不同的发行版可以公用bootfs.**
- ==虚拟机是分钟级别，容器是秒级！==

### 分层理解

**分层的镜像**

- 我们可以去下载一个镜像，注意观察下载的日志输出，可以看到是一层层的在下载

  ![](.\picture\镜像分层下载.jpg)

思考：

为什么Docker镜像要采用这种分层的结构呢？

- 最大的好处，我觉得莫过于资源共享了！比如有多个镜像都从相同的Base镜像构建而来，那么宿主机只需在磁盘上保留一份base镜像，同时内存中也只需要加载一份base镜像，这样就可以为所有的容器服务了，而且镜像的每一层都可以被共享。

- 查看镜像分层的方式可以通过`docker image inspect name`命令

  ![](.\picture\镜像的分层.jpg)

理解：

- **所有的 Docker镜像都起始于一个基础镜像层，当进行修改或培加新的内容时，就会在当前镜像层之上，创建新的镜像层。**

- 举一个简单的例子，假如基于 Ubuntu 76543 Linux16.04创建一个新的镜像，这就是新镜像的第一层；如果在该镜像中添加 Python包，就会在基础镜像层之上创建第二个镜像层；如果继续添加一个安全补丁，就会创健第三个镜像层

- 该镜像当前已经包含3个镜像层，如下图所示（这只是一个用于演示的很简单的例子）。

  ![](.\picture\3个镜像层.jpg)

- **在添加额外的镜像层的同时，镜像始终保持是当前所有镜像的组合**，理解这一点非常重要。下图中举了一个简单的例子，每个镜像层包含3个文件，而镜像包含了来自两个镜像层的6个文件。

  ![](.\picture\2个镜像层.jpg)

- 上图中的镜像层跟之前图中的略有区別，主要目的是便于展示文件

- 下图中展示了一个稍微复杂的三层镜像，在外部看来整个镜像只有6个文件，这是因为最上层中的文件7是文件5的一个更新版

  ![](.\picture\在已有的镜像中添加新层.jpg)

- 这种情況下，上层镜像层中的文件覆盖了底层镜像层中的文件。这样就使得文件的更新版本作为一个新镜像层添加到镜像当中

- Docker通过存储引擎（新版本采用快照机制）的方式来实现镜像层堆栈，并保证多镜像层对外展示为统一的文件系统

- **Linux上可用的存储引擎有AUFS、 Overlay2、 Device Mapper、Btrfs以及ZFS**。顾名思义，**每种存储引擎都基于 Linux中对应的件系统或者块设备技术，井且每种存储引擎都有其独有的性能特点。**

- **Docker在 Windows上仅支持 windowsfilter 一种存储引擎，该引擎基于NTFS文件系统之上实现了分层和CoW [1]。**

- 下图展示了与系统显示相同的三层镜像。所有镜像层堆并合井，对外提供统一的视图

  ![](.\picture\全部三层镜像视图.jpg)

**特点**

- ==**Docker 镜像都是只读的**，当容器启动时，一个新的可写层加载到镜像的顶部！==
- 这一层就是我们通常说的容器层，容器之下的都叫镜像层！

![](.\picture\镜像与容器.jpg)

### commit镜像

```shell
docker commit 提交容器成为一个新的副本

# 命令和git原理类似
docker commit -m="描述信息" -a="作者" 容器id 目标镜像名:[TAG]
```

**实战测试:**

```shell
# 1、启动一个默认的tomcat
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker run -d -p 8080:8080 tomcat
de57d0ace5716d27d0e3a7341503d07ed4695ffc266aef78e0a855b270c4064e

# 2、发现这个默认的tomcat 是没有webapps应用，官方的镜像默认webapps下面是没有文件的！
#docker exec -it 容器id /bin/bash
[root@iz2zeak7sgj6i7hrb2g862z ~]# docker exec -it de57d0ace571 /bin/bash
root@de57d0ace571:/usr/local/tomcat# 

# 3、从webapps.dist拷贝文件进去webapp
root@de57d0ace571:/usr/local/tomcat# cp -r webapps.dist/* webapps
root@de57d0ace571:/usr/local/tomcat# cd webapps
root@de57d0ace571:/usr/local/tomcat/webapps# ls
ROOT  docs  examples  host-manager  manager

# 4、将操作过的容器通过commit调教为一个镜像！我们以后就使用我们修改过的镜像即可，而不需要每次都重新拷贝webapps.dist下的文件到webapps了，这就是我们自己的一个修改的镜像。
docker commit -m="描述信息" -a="作者" 容器id 目标镜像名:[TAG]
docker commit -a="kuangshen" -m="add webapps app" 容器id tomcat02:1.0

[root@iz2zeak7sgj6i7hrb2g862z ~]# docker commit -a="csp提交的" -m="add webapps app" de57d0ace571 tomcat02.1.0
sha256:d5f28a0bb0d0b6522fdcb56f100d11298377b2b7c51b9a9e621379b01cf1487e

[root@iz2zeak7sgj6i7hrb2g862z ~]# docker images
REPOSITORY            TAG                 IMAGE ID            CREATED             SIZE
tomcat02.1.0          latest              d5f28a0bb0d0        14 seconds ago      652MB
tomcat                latest              1b6b1fe7261e        5 days ago          647MB
nginx                 latest              9beeba249f3e        5 days ago          127MB
mysql                 5.7                 b84d68d0a7db        5 days ago          448MB
elasticsearch         7.6.2               f29a1ee41030        8 weeks ago         791MB
portainer/portainer   latest              2869fc110bf7        2 months ago        78.6MB
centos                latest              470671670cac        4 months ago        237MB
hello-world           latest              bf756fb1ae65        4 months ago        13.3kB
```

![](.\picture\commit镜像.jpg)

如果你想要保存当前容器的状态，就可以通过commit来提交，获得一个镜像，就好比我们我们使用虚拟机的快照。

## 容器数据卷

### 什么是容器数据卷

docker的理念回顾

- 将应用和环境打包成一个镜像！
- 数据？如果数据都在容器中，那么我们容器删除，数据就会丢失！需求：数据可以持久化
- MySQL，容器删除了，删库跑路！需求：MySQL数据可以存储在本地！

容器之间可以有一个数据共享的技术！Docker容器中产生的数据，同步到本地！

这就是卷技术！目录的挂载，将我们容器内的目录，挂载到Linux上面！

<img src=".\picture\卷技术.jpg" style="zoom:80%;" />

**总结一句话：容器的持久化和同步操作！容器间也是可以数据共享的！**

### 使用数据卷

方式一 ：直接使用命令挂载 -v

```shell
-v, --volume list                    Bind mount a volume

docker run -it -v 主机目录:容器内目录  -p 主机端口:容器内端口
# /home/ceshi：主机home目录下的ceshi文件夹  映射：centos容器中的/home
[root@iz2zeak7 home]# docker run -it -v /home/ceshi:/home centos /bin/bash
#这时候主机的/home/ceshi文件夹就和容器的/home文件夹关联了,二者可以实现文件或数据同步了

#通过 docker inspect 容器id 查看
[root@iz2zeak7sgj6i7hrb2g862z home]# docker inspect 6064c490c371
```

![](.\picture\挂载.jpg)

```shell
#将宿主机的/root/test挂载到tomcat的/home目录
[root@CZP ~]# docker run -d -p 9999:8080 -v /root/test:/home --name="tomcat01"  1b6b1fe7261e
015001911b67f5e357b93c6bb05ebaf07aebe4f3abc455f9aa439afd83b9af78
[root@CZP ~]# docker ps
CONTAINER ID        IMAGE                 COMMAND                  CREATED             STATUS              PORTS                                            NAMES
015001911b67        1b6b1fe7261e          "catalina.sh run"        16 seconds ago      Up 15 seconds       0.0.0.0:9999->8080/tcp                           tomcat01
db186da947d7        portainer/portainer   "/portainer"             17 hours ago        Up 17 hours         0.0.0.0:8088->9000/tcp                           interesting_shockley
bd4094db247f        elasticsearch:7.6.2   "/usr/local/bin/dock…"   18 hours ago        Up 17 hours         0.0.0.0:9200->9200/tcp, 0.0.0.0:9300->9300/tcp   elasticsearch
94b00b6f6172        tomcat:9.0            "catalina.sh run"        18 hours ago        Up 18 hours         0.0.0.0:8080->8080/tcp                           tomcat
d458bc50a808        nginx                 "/docker-entrypoint.…"   18 hours ago        Up 18 hours         0.0.0.0:80->80/tcp                               nginx01
63d4c4115212        36304d3b4540          "docker-entrypoint.s…"   22 hours ago        Up 22 hours         0.0.0.0:6379->6379/tcp                           redis

#进入tomcat内部
[root@CZP test]# docker exec -it tomcat01 /bin/bash
root@015001911b67:/usr/local/tomcat# cd /home
#在home目录创建b.java
root@015001911b67:/home# touch b.java
root@015001911b67:/home# read escape sequence
[root@CZP test]# cd /root/test
[root@CZP test]# ll
total 0
-rw-r--r-- 1 root root 0 Jun 11 11:03 b.java #b.java显示挂载成功
```

测试文件的同步

![](.\picture\测试文件的同步.jpg)

再来测试;

1. 停止容器

2. 宿主机上修改文件

3. 容器启动

   ```shell
   docker attach 容器id
   ```

4. 容器内的数据依旧是同步的

   ![](.\picture\测试文件同步2.jpg)

==好处：我们以后修改只需要在本地修改即可，容器内会自动同步！==

### 实战：安装MySQL

思考：MySQL的数据持久化问题

```shell
# 获取镜像
[root@AlibabaECS home]# docker pull mysql:5.7

# 运行容器,需要做数据挂载！ # 安装启动mysql, 需要配置密码的，这是要注意的点！
# 参考官网hub 
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag

# 启动我们的
-d 后台运行
-p 端口映射
-v 卷挂载
-e 环境配置
--name 容器名字

[root@AlibabaECS home]# docker run -d -p 3310:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 --name mysql01 mysql:5.7

# 启动成功之后，我们使用本地Navicat连接测试
# sqlyog-连接到服务器的3310 ---- 和容器内的3306映射 

# 在本地测试创建一个数据库，查看一下我们映射的路径是否ok！
```

**测试连接**：注意3310端口要在阿里云服务器的安全组中打开，否则无法连接。

当我们在本地用SQLyog新建名称为test的数据库时候，容器容器也会创建

![](.\picture\在sqlyog中创建test数据库后.jpg)

假设我们将包含mysql的容器删除时，发现，**我们挂载到本地的数据卷依旧没有丢失，这就实现了容器数据持久化功能**。

![](.\picture\删除mysql容器后.jpg)

### 具名和匿名挂载

```shell
# 匿名挂载
-v 容器内路径!
$ docker run -d -P --name nginx01 -v /etc/nginx nginx

# 查看所有的volume(卷)的情况
$ docker volume ls    
DRIVER              VOLUME NAME # 容器内的卷名(匿名卷挂载)
local               21159a8518abd468728cdbe8594a75b204a10c26be6c36090cde1ee88965f0d0
local               b17f52d38f528893dd5720899f555caf22b31bf50b0680e7c6d5431dbda2802c
         
# 这里发现，这种就是匿名挂载，我们在 -v只写了容器内的路径，没有写容器外的路径！

# 具名挂载 -P:表示随机映射端口
$ docker run -d -P --name nginx02 -v juming-nginx:/etc/nginx nginx
9663cfcb1e5a9a1548867481bfddab9fd7824a6dc4c778bf438a040fe891f0ee

# 查看所有的volume(卷)的情况
$ docker volume ls                  
DRIVER              VOLUME NAME
local               21159a8518abd468728cdbe8594a75b204a10c26be6c36090cde1ee88965f0d0
local               b17f52d38f528893dd5720899f555caf22b31bf50b0680e7c6d5431dbda2802c
local               juming-nginx #多了一个名字


# 通过 -v 卷名：查看容器内路径
# 查看一下这个卷
$ docker volume inspect juming-nginx
[
    {
        "CreatedAt": "2020-05-23T13:55:34+08:00",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/juming-nginx/_data", #默认目录
        "Name": "juming-nginx",
        "Options": null,
        "Scope": "local"
    }
]
```

![](.\picture\具名和匿名挂载.jpg)

所有的docker容器内的卷,没有指定目录的情况下都是在**/var/lib/docker/volumes/卷名/_data**

![](.\picture\columes目录.jpg)

我们通过具名挂载可以方便的找到一个卷,大多数情况在使用的’具名挂载’

```shell
# 如何确定是具名挂载还是匿名挂载,还是指定路径挂载
-v 容器内路径 #匿名挂载
-v 卷名:容器内路径 #具名挂载
-v /宿主机路径 : 容器内路径 #指定路径挂载
```

扩展:

```shell
#通过 -v  容器内路径: ro rw 改变读写权限
ro read only
rw read and write

#一旦设置了容器权限,容器对挂载出来的内容就有限定了!
docker -run -P -name nginx01 -v /etc/nginx:ro nginx
docker -run -P -name nginx01 -v /etc/nginx:rw nginx
ro : 只要看到ro就说明这个路径只能通过宿主机来改变,容器内部无法操作，readonly，默认rw
```

**初始Dockerfile**

Dockerfile就是用来构建Dockerfile镜像的文件! 命令脚本!

```shell
# 创建一个dockerfile文件,名字可以随机 建议 dockerfile
# 文件中的内容

FROM centos

VOLUME ["volume01","volume02"]

CMD echo "---end---"
CMD /bin/hash

#这里的每个命令，就是镜像的一层！
```

生成了我们自己的镜像

```shell
# 构建出这个镜像 
-f dockerfile1 			# f代表file，指这个当前文件的地址(这里是当前目录下的dockerfile1)
-t kuangshen/centos 	# t就代表target，指目标目录(注意kuangshen镜像名前不能加斜杠‘/’)，生成狂神版的centos
. 						# 表示生成在当前目录下
```

![](.\picture\具名和匿名挂载2.jpg)

启动自己写的容器

![](.\picture\具名和匿名挂载3.jpg)

通过dockerfile生成的目录，这个卷和外部一定有一个同步的目录

![](.\picture\匿名挂载.jpg)

使用`docker inspect id`查看一下卷挂载的路径

![](.\picture\生成的匿名挂载卷.jpg)

测试一下刚才的文件是否同步出去了

这种方式我们未来使用的十分多,因为我们通常会构建自己的镜像!

假设构建镜像时没有挂载卷,要手动镜像挂载 `-v 卷名: 容器内路径`

### 数据卷容器

- 多个容器之间共享数据

**多个MySQL同步数据**！

命名的容器挂载数据卷！

![](.\picture\数据卷容器.jpg)

启动三个容器，通过我们刚才自己的写镜像启动

![](.\picture\启动docker01.jpg)

**启动docker02继承docker01**

![](.\picture\启动docker02继承docker01.jpg)

docker01创建的内容同步到了docker02上

![](.\picture\docker01创建的内容同步到了docker02上.jpg)

```shell
# 测试：可以删除docker01，查看一下docker02和docker03是否可以访问这个文件
# 测试依旧可以访问
```

![](.\picture\docker0123拷贝共享卷.jpg)

多个mysql实现数据共享

```shell
$ docker run -d -p 3306:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 --name mysql01 mysql:5.7
$ docker run -d -p 3307:3306 -e MYSQL_ROOT_PASSWORD=123456 --name mysql02 --volumes-from mysql01  mysql:5.7
# 这个时候，可以实现两个容器数据同步！因为mysql02与mysql01目录是相同的，所以可以不用写 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql
```

**结论：**

==容器之间的配置信息的传递，数据卷容器的生命周期一直持续到没有容器使用为止。==

==但是一旦你持久化到了本地，这个时候，本地的数据是不会删除的！==

## DockerFile

### DockerFile介绍

dockerfile是用来构建docker镜像的文件！命令参数脚本！

构建步骤：

1、 编写一个dockerfile文件

2、 `docker build` 构建称为一个镜像

3、 `docker run`运行镜像

4、 `docker push`发布镜像（DockerHub 、阿里云仓库)

![](.\picture\dockerhub.png)

点击后跳到一个Dockerfile

![](.\picture\Dockerfile.png)

很多官方镜像都是基础包，很多功能没有，我们通常会自己搭建自己的镜像！

官方既然可以制作镜像，那我们也可以！

### DockerFile构建过程

**基础知识**：

1、每个保留关键字(指令）都是必须是大写字母

2、执行从上到下顺序

3、`#`表示注释

4、**每一个指令都会创建提交一个新的镜像层**，并提交！

<img src=".\picture\dockerfile层.png" style="zoom: 80%;" />

Dockerfile是面向开发的，我们以后要发布项目，做镜像，就需要编写dockerfile文件，这个文件十分简单！

Docker镜像逐渐成企业交付的标准，必须要掌握！

- DockerFile：构建文件，定义了一切的步骤，源代码
- ==DockerImages：通过DockerFile构建生成的镜像，最终发布和运行产品。==
- ==Docker容器：容器就是镜像运行起来提供服务==

### DockerFile的指令

以前的话我们是使用的别人的,现在我们知道了这些指令后,我们来练习自己写一个镜像!

```shell
FROM				# from:基础镜像，一切从这里开始构建 例如；centos
MAINTAINER			# maintainer:镜像是谁写的， 姓名+邮箱
RUN					# run:镜像构建的时候需要运行的命令
ADD					# add:步骤，tomcat镜像，这个tomcat压缩包！添加内容 添加同目录
WORKDIR				# workdir:镜像的工作目录
VOLUME				# volume:挂载的目录
EXPOSE				# expose:暴露端口配置
CMD					# cmd:指定这个容器启动的时候要运行的命令，只有最后一个会生效，可被替代
ENTRYPOINT			# entrypoint:指定这个容器启动的时候要运行的命令，可以追加命令
ONBUILD				# onbuild:当构建一个被继承DockerFile这个时候就会运行onbuild的指令，触发指令
COPY				# copy:类似ADD，将我们文件拷贝到镜像中
ENV					# env:构建的时候设置环境变量！
```

![](.\picture\dockerfile命令.jpg)

### 实战测试

**Docker Hub 中99%镜像都是从centos基础镜像FROM scratch过来的,然后配置需要的软件**

```dockerfile
FROM scratch
ADD centos-7-x86_64-docker.tar.xz /

LABEL \
    org.label-schema.schema-version="1.0" \
    org.label-schema.name="CentOS Base Image" \
    org.label-schema.vendor="CentOS" \
    org.label-schema.license="GPLv2" \
    org.label-schema.build-date="20200504" \
    org.opencontainers.image.title="CentOS Base Image" \
    org.opencontainers.image.vendor="CentOS" \
    org.opencontainers.image.licenses="GPL-2.0-only" \
    org.opencontainers.image.created="2020-05-04 00:00:00+01:00"

CMD ["/bin/bash"]
```

![](.\picture\官方dockerfile文件.png)

创建一个自己的centos

```dockerfile
# 1 编写一个DOckerfile的文件
# 从centos开始，centos可以看上边的截图，默认是没有那么多的配置的，我们之后可以在其基础之上添加功能
FROM centos

MAINTAINER czp<2432688105@qq.com>

ENV MYPATH /usr/local

WORKDIR $MYPATH

RUN yum -y  install vim
RUN yum -y install net-tools

EXPOSE 80

CMD echo $MYPATH
CMD echo "---end---"
```

```shell
# 2. 通过这个文件构建镜像
# 命令 docker build -f dockerfile文件路径 -t 目标镜像:[版本号] .
# docker build -f mydockerfile-centos -t mycentos:0.1 .
Successfully built 5ebc296aad5a
Successfully tagged mycentos:1.0

# 3. 测试运行
```

原生的centos

![](.\picture\测试原生的centos.jpg)

增强之后的镜像

![](.\picture\自己的centos.jpg)

我们可以列出本地进程的历史，`docker history id`可以查看当前镜像是怎么构建起来的

![](.\picture\查看列出本地进程的历史.jpg)

我们平时拿到一个镜像,可以研究一下它是怎么做的

**`CMD` 和`ENTRYPOINT`的区别**

```shell
CMD # 指定这个容器启动的时候要运行的命令,只有最后一个会生效,可被替代
ENTRYPOINT # 指定这个容器启动的时候要运行的命令,可以追加命令
```

测试cmd命令

```shell

# 编写
[root@CZP dockerfile]# cat dockerfile-centos-test 
FROM centos
CMD ["ls","-a"]


# 构建镜像
[root@CZP dockerfile]# docker build -f dockerfile-centos-test -t centostest .

# 运行
# docker run id

# 想要追加一个命令 -l  ls -al 我们期待的是返回ls -al，但是，我们-l是替换了ls -a，所以报错
# docker run id -l
docker: Error response from daemon: OCI runtime create failed: container_linux.go:349: starting container process caused "exec: \"-l\": executable file not found in $PATH": unknown.
ERRO[0000] error waiting for container: context canceled 

# cmd的情况下 替换了CMD["ls","-a"]命令,-不是命令追加
```

**测试ENTRYPOINT**

```shell
# 编写dockerfile文件
$ vim dockerfile-test-entrypoint
FROM centos
ENTRYPOINT ["ls","-a"]

# 构建镜像
$ docker build  -f dockerfile-test-entrypoint -t cmd-test:0.1 .

# 运行镜像
$ docker run entrypoint-test:0.1
.
..
.dockerenv
bin
dev
etc
home
lib
lib64
lost+found ...

# 我们的命令，是直接拼接在我们得ENTRYPOINT命令后面的
$ docker run entrypoint-test:0.1 -l
total 56
drwxr-xr-x   1 root root 4096 May 16 06:32 .
drwxr-xr-x   1 root root 4096 May 16 06:32 ..
-rwxr-xr-x   1 root root    0 May 16 06:32 .dockerenv
lrwxrwxrwx   1 root root    7 May 11  2019 bin -> usr/bin
drwxr-xr-x   5 root root  340 May 16 06:32 dev
drwxr-xr-x   1 root root 4096 May 16 06:32 etc
drwxr-xr-x   2 root root 4096 May 11  2019 home
lrwxrwxrwx   1 root root    7 May 11  2019 lib -> usr/lib
lrwxrwxrwx   1 root root    9 May 11  2019 lib64 -> usr/lib64 ....
```

Dockerfile中很多命令都十分的相似，我们需要了解它们的区别，我们最好的学习就是对比他们然后测试效果！

### 实战：Tomcat镜像

1、准备镜像文件 tomcat压缩包，jdk压缩包

![](.\picture\tomcat镜像准备的压缩文件.jpg)

2、编写dockerfile文件，官方命名==Dockerfile==，`build`会自动寻找这个文件，就不需要`-f`指定了！

```dockerfile
FROM centos
MAINTAINER czp<2432688105@qq.com>

COPY readme.txt /usr/local/readme.txt

#ADD命令会自动解压
ADD apache-tomcat-9.0.33.tar.gz /usr/local/
ADD jdk-8u221-linux-x64.rpm /usr/local/

RUN yum -y install vim
 
ENV MYPATH /usr/local
 
WORKDIR $MYPATH
 
ENV JAVA_HOME /usr/local/jdk1.8.0_11
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

ENV CATALINA_HOME /usr/local/apache-tomcat-9.0.33
ENV CATALINA_BASH /usr/local/apache-tomcat-9.0.33

# 配置环境变量
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/lib:/CATALINA_HOME/bin

EXPOSE 8080

CMD /usr/local/apache-tomcat-9.0.33/bin/startup.sh && tail -F /usr/local/apache-tomcat-9.0.33/bin/logs/catalina.out
```

4、构建镜像

```shell
# 因为dockerfile命名使用默认命名 因此不用使用-f 指定文件
[root@AlibabaECS tomcat]# docker build -t diytomcat .
```

5、run镜像

```shell
[root@AlibabaECS tomcat]# docker run -d -p 9090:8080 --name kuangshentomcat -v /home/deng/build/tomcat/test:/url/local/apache-tomcat-9.0.37/webapps/test -v /home/deng/build/tomcat/tomcatlogs/:/usr/local/apache-tomcat-9.0.37/logs diytomcat
```

6、访问测试

```shell
$ docker exec -it 自定义容器的id /bin/bash

#返回容器外
$ cul localhost:9090
```

7、发布项目

(由于做了卷挂载，我们直接在本地编写项目就可以发布了！)

发现：项目部署成功，可以直接访问！

我们以后开发的步骤：需要掌握Dockerfile的编写！我们之后的一切都是使用docker镜像来发布运行！

### 发布自己的镜像

**发布到 Docker Hub**

1、地址 https://hub.docker.com/

2、确定这个账号可以登录

3、登录

```shell
$ docker login --help
Usage:  docker login [OPTIONS] [SERVER]

Log in to a Docker registry.
If no server is specified, the default is defined by the daemon.

Options:
  -p, --password string   Password
      --password-stdin    Take the password from stdin
  -u, --username string   Username

$ docker login -u 你的用户名 -p 你的密码
```

4、登录完毕就可以提交镜像了,就是一步 `docker push`

```shell
# push自己的镜像到服务器上一定要带上人/镜像名:版本号
[root@CZP ~]# docker push czp/centos:1.0

# docker tag [id] [tag] 为容器添加一个版本
# docker tag id kuangshen/tomcat:1.0

# 会发现push不上去，因为如果没有前缀的话默认是push到 官方的library
# 解决方法：
# 第一种 build的时候添加你的dockerhub用户名，然后在push就可以放到自己的仓库了
$ docker build -t kuangshen/mytomcat:0.1 .

# 第二种 使用docker tag #然后再次push
$ docker tag 容器id kuangshen/mytomcat:1.0 #然后再次push
$ docker push kuangshen/mytomcat:1.0
```

发布到阿里云镜像服务上

看官网 很详细https://cr.console.aliyun.com/repository/

1、登录阿里云

2、找到容器镜像服务

3、创建命名空间

![](.\picture\创建命名空间.png)

4、创建容器镜像

![](.\picture\创建容器镜像.png)

5、浏览阿里云

![](.\picture\浏览阿里云.png)

```shell
$ sudo docker login --username=zchengx registry.cn-shenzhen.aliyuncs.com
$ sudo docker tag [ImageId] registry.cn-shenzhen.aliyuncs.com/dsadxzc/cheng:[镜像版本号]

# 修改id 和 版本
sudo docker tag a5ef1f32aaae registry.cn-shenzhen.aliyuncs.com/dsadxzc/cheng:1.0
# 修改版本
$ sudo docker push registry.cn-shenzhen.aliyuncs.com/dsadxzc/cheng:[镜像版本号]
```

### 小结

```shell
# 可以本地化的保存和加载镜像
# docker save 路径
# docker load 路径
```

<img src=".\picture\docker小结.png" style="zoom: 67%;" />

## Docker网络

### 理解Docker0

清空所有环境

测试

![](.\picture\ip addr.jpg)

三个网络

#问题: docker 是如何处理容器网络访问的?

![](.\picture\如何网络访问.jpg)

```shell
# 测试  运行一个tomcat
$ docker run -d -P --name tomcat01 tomcat

# 直接查看容器内部网络地址
$ docker exec -it 容器id ip addr

# 发现容器启动的时候会得到一个 eth0@if91 ip地址，docker分配！
$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
261: eth0@if91: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ac:12:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.18.0.2/16 brd 172.18.255.255 scope global eth0
       valid_lft forever preferred_lft forever

# 思考？ linux能不能ping通容器内部！ 可以 容器内部可以ping通外界吗？ 可以！
$ ping 172.18.0.2
PING 172.18.0.2 (172.18.0.2) 56(84) bytes of data.
64 bytes from 172.18.0.2: icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from 172.18.0.2: icmp_seq=2 ttl=64 time=0.074 ms
#linux可以ping通容器内部
```

**原理**

1、我们每启动一个docker容器，docker就会给docker容器分配一个ip，我们只要按照了docker，就会有一个docker0**桥接模式**，使用的技术是**veth-pair**技术！

https://www.cnblogs.com/bakari/p/10613710.html

在主机中再次测试 `ip addr`，多了一个网卡，和容器内部的ip是相同的

![](.\picture\再次测试ip addr.jpg)

2 、再启动一个容器测试，发现又多了一对网络

![](.\picture\再启动一个容器发现又多了一对网络.jpg)

```shell
# 我们发现这个容器带来网卡，都是一对对的
# veth-pair 就是一对的虚拟设备接口，他们都是成对出现的，一端连着协议，一端彼此相连
# 正因为有这个特性 veth-pair 充当一个桥梁，连接各种虚拟网络设备的
# OpenStac,Docker容器之间的连接，OVS的连接，都是使用evth-pair技术
```

3、我们来测试下tomcat01和tomcat02是否可以ping通

```shell
# 获取tomcat01的ip 172.17.0.2
# docker exec -it tomcat01 ip addr  
550: eth0@if551: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.17.0.2/16 brd 172.17.255.255 scope global eth0
       valid_lft forever preferred_lft forever

# 让tomcat02 ping tomcat01       
# docker exec -it tomcat02 ping 172.17.0.2
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.098 ms
64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.071 ms

# 结论：容器和容器之间是可以互相ping通
```

**网络模型图**

![](.\picture\网络模型图.jpg)

结论：tomcat01和tomcat02公用一个路由器，docker0。

所有的容器不指定网络的情况下，都是docker0路由的，docker会给我们的容器分配一个默认的可用ip。

**小结**

Docker使用的是Linux的桥接，宿主机是一个Docker容器的网桥 docker0

<img src=".\picture\网络小结.jpg" style="zoom:80%;" />

Docker中所有网络接口都是虚拟的，虚拟的转发效率高（内网传递文件）

**只要容器删除，对应的网桥一对就没了！**

![](.\picture\docker network ls.jpg)

![](.\picture\通过network inspect id查看网络.jpg)

### --link

思考一个场景：**我们编写了一个微服务，database url=ip: 项目不重启，数据ip换了，我们希望可以处理这个问题，可以通过名字来进行访问容器**？

```shell
[root@CZP ~]# docker exec -it tomcat02 ping tomcat01
ping: tomcat01: Name or service not known

# 如何可以解决呢?


# 通过 --link 就可以解决网络问题
# docker run -d -P --name tomcat03 --link tomcat02 tomcat
# docker exec -it tomcat03 ping tomcat02

[root@CZP ~]# docker exec -it tomcat03 --link ping tomcat02
PING tomcat02 (172.18.0.4) 56(84) bytes of data.
64 bytes from tomcat02 (172.18.0.4): icmp_seq=1 ttl=64 time=0.128 ms
64 bytes from tomcat02 (172.18.0.4): icmp_seq=2 ttl=64 time=0.097 ms
64 bytes from tomcat02 (172.18.0.4): icmp_seq=3 ttl=64 time=0.091 ms
64 bytes from tomcat02 (172.18.0.4): icmp_seq=4 ttl=64 time=0.109 ms
64 bytes from tomcat02 (172.18.0.4): icmp_seq=5 ttl=64 time=0.097 ms
64 bytes from tomcat02 (172.18.0.4): icmp_seq=6 ttl=64 time=0.096 ms
64 bytes from tomcat02 (172.18.0.4): icmp_seq=7 ttl=64 time=0.092 ms
64 bytes from tomcat02 (172.18.0.4): icmp_seq=8 ttl=64 time=0.094 ms
64 bytes from tomcat02 (172.18.0.4): icmp_seq=9 ttl=64 time=0.102 ms
^C
--- tomcat02 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 1007ms
rtt min/avg/max/mdev = 0.091/0.100/0.128/0.015 ms

# 反向是否可以ping通吗,如果没有配置，反向是不可以ping通的
[root@CZP ~]# docker exec -it tomcat02 ping tomcat03
```

探究：inspect！

```shell
# 可以查看当前的网络信息
# docker network ls

# 查看某一个docker网络的详细信息
# docker network inspect networkid
```

![](.\picture\通过network inspect id查看网络2.jpg)

查看tomcat03就是在在本地配置了tomcat02的配置

```shell
# 查看hosts 配置，在这里原理发现
[root@AlibabaECS ~]# docker exec -it tomcat03 cat /etc/hosts
127.0.0.1       localhost
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
172.17.0.3      tomcat02 c2e5a8a29151
172.17.0.4      50b163f99e32
```

==`–link` 本质就是在hosts配置中添加映射==

**现在使用Docker已经不建议使用`–link`了！**

自定义网络，不适用docker0！

docker0问题：**不支持容器名连接访问！**

### 自定义网络

```shell
# docker network
connect     -- Connect a container to a network
create      -- Creates a new network with a name specified by the
disconnect  -- Disconnects a container from a network
inspect     -- Displays detailed information on a network
ls          -- Lists all the networks created by the user
prune       -- Remove all unused networks
rm          -- Deletes one or more networks
```

查看所有的docker网络

![](.\picture\查看所有网络和移除网络.jpg)

**网络模式**

**bridge** : 桥接 docker 大桥（默认）

**none**: 不配置网络

**host**: 和宿主机共享网络

**container**: 容器内网络联通!（用的少，局限很大）

**测试**

```shell
# 直接启动的命令 --net brodge,默认docker0
docker run -d -P --name tomcat01 tomcat
docker run -d -P --name tomcat01 --net bridge tomcat # 默认方式

# docker0的特点: 默认的,域名是不能访问的, --link可以打通连接

[root@CZP ~]# docker network create --help

Usage:	docker network create [OPTIONS] NETWORK

Create a network

Options:
      --attachable           Enable manual container attachment
      --aux-address map      Auxiliary IPv4 or IPv6 addresses used by Network driver (default map[])
      --config-from string   The network from which copying the configuration
      --config-only          Create a configuration only network
  -d, --driver string        Driver to manage the Network (default "bridge")
      --gateway strings      IPv4 or IPv6 Gateway for the master subnet
      --ingress              Create swarm routing-mesh network
      --internal             Restrict external access to the network
      --ip-range strings     Allocate container ip from a sub-range
      --ipam-driver string   IP Address Management Driver (default "default")
      --ipam-opt map         Set IPAM driver specific options (default map[])
      --ipv6                 Enable IPv6 networking
      --label list           Set metadata on a network
  -o, --opt map              Set driver specific options (default map[])
      --scope string         Control the network's scope
      --subnet strings       Subnet in CIDR format that represents a network segment
# 我们可以自定义一个网络
# --driver bridge 
# --subnet 192.168.0.0/16    子网
# --gateway 192.168.0.1      网关
[root@CZP ~]# docker network create --driver bridge --subnet 192.168.0.0/16 --gateway 192.168.0.1 mynet
677fae13a48c634dc03c56641b9ba31354846d31a196fdcb92c9ef6ddff73150
[root@CZP ~]# docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
228826a97a0b        bridge              bridge              local
c3b4884cd4db        host                host                local
677fae13a48c        mynet               bridge              local # 创建的自定义网络
35885200f93d        none                null                local
```

我们自己的网络就创建好了

![](.\picture\自定义网络.jpg)

```shell
# 使用自己的网络
[root@CZP ~]#  docker run -d -P --name tomcat-net-01 --net mynet tomcat:9.0
336dd072ca17ac1adf514c44c8dcbd3358146d6d60667f3a0f99dbbb3e305f09
[root@CZP ~]#  docker run -d -P --name tomcat-net-02 --net mynet tomcat:9.0
2cea3bb29350ae99ce26c1bf6f8d1f2dcfb25bf8042193263ce275308e9eb42d
[root@CZP ~]# docker network inspect mynet
[
   {
       "Name": "mynet",
       "Id": "677fae13a48c634dc03c56641b9ba31354846d31a196fdcb92c9ef6ddff73150",
       "Created": "2020-06-14T16:49:14.554786193+08:00",
       "Scope": "local",
       "Driver": "bridge",
       "EnableIPv6": false,
       "IPAM": {
           "Driver": "default",
           "Options": {},
           "Config": [
               {
                   "Subnet": "192.168.0.0/16",
                   "Gateway": "192.168.0.1"
               }
           ]
       },
       "Internal": false,
       "Attachable": false,
       "Ingress": false,
       "ConfigFrom": {
           "Network": ""
       },
       "ConfigOnly": false,
       "Containers": {
           "2cea3bb29350ae99ce26c1bf6f8d1f2dcfb25bf8042193263ce275308e9eb42d": {
               "Name": "tomcat-net-02",
               "EndpointID": "ebff8e9ef22bd3d66d0de4229d1f3a3c610785b23005294f60f96f3089d52c3d",
               "MacAddress": "02:42:c0:a8:00:03",
               "IPv4Address": "192.168.0.3/16",
               "IPv6Address": ""
           },
           "336dd072ca17ac1adf514c44c8dcbd3358146d6d60667f3a0f99dbbb3e305f09": {
               "Name": "tomcat-net-01",
               "EndpointID": "69451bb0c95ed27d207cd2bade9c57fd2625c245b8b8cb3e5d0dea530a368683",
               "MacAddress": "02:42:c0:a8:00:02",
               "IPv4Address": "192.168.0.2/16",
               "IPv6Address": ""
           }
       },
       "Options": {},
       "Labels": {}
   }
]
```

现在不使用`–link`也可以ping名字了,推荐使用这种网络

```shell
[root@CZP ~]# docker exec tomcat-net-01 ping tomcat-net-02
PING tomcat-net-02 (192.168.0.3) 56(84) bytes of data.
64 bytes from tomcat-net-02.mynet (192.168.0.3): icmp_seq=1 ttl=64 time=0.080 ms
64 bytes from tomcat-net-02.mynet (192.168.0.3): icmp_seq=2 ttl=64 time=0.096 ms
64 bytes from tomcat-net-02.mynet (192.168.0.3): icmp_seq=3 ttl=64 time=0.086 ms
^C
[root@CZP ~]# 
```

我们自定义的网络docker当我们维护好了对应的关系，推荐我们平时这样使用网络！

好处：

- redis - 不同的集群使用不同的网络，保证集群是健康和安全的
- mysql - 不同的集群使用不同的网络，保证集群是健康安全的

![](.\picture\两个集群网络隔离.jpg)

### 网络连通

![](.\picture\打通两个网段.jpg)

![](.\picture\docker network connect.jpg)

```shell
# 测试打通 tomcat - mynet
[root@AlibabaECS ~]# docker network connect mynet tomcat01

# 连通之后就是将 tomcat01 放到了 mynet 网络下

# 一个容器两个ip地址
# 类似，阿里云服务：公网ip  私网ip
```

![](.\picture\将tomcat01加入到mynet中.jpg)

这样容器之间就可以ping通了

```shell
# 01连通ok
[root@AlibabaECS ~]# docker exec -it tomcat01 ping tomcat-net-01
PING tomcat-net-01 (192.168.0.2) 56(84) bytes of data.
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=1 ttl=64 time=0.098 ms
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=2 ttl=64 time=0.091 ms

# 02依旧是打不通的
[root@AlibabaECS ~]# docker exec -it tomcat02 ping tomcat-net-01
Error: No such container: tomcat02
```

结论：假设要跨网络操作别人，就需要使用`docker network connect` 连通！

### 实战：部署Redis集群

三主三从

![](.\picture\部署redis集群.jpg)

```shell
# 创建网卡
docker network create redis --subnet 172.38.0.0/16

# 通过脚本创建六个redis配置
for port in $(seq 1 6);\
do \
mkdir -p /mydata/redis/node-${port}/conf
touch /mydata/redis/node-${port}/conf/redis.conf
cat << EOF >> /mydata/redis/node-${port}/conf/redis.conf
port 6379
bind 0.0.0.0
cluster-enabled yes
cluster-config-file nodes.conf
cluster-node-timeout 5000
cluster-announce-ip 172.38.0.1${port}
cluster-announce-port 6379
cluster-announce-bus-port 16379
appendonly yes
EOF
done

# 通过脚本运行六个redis
for port in $(seq 1 6);\
docker run -p 637${port}:6379 -p 1667${port}:16379 --name redis-${port} \
-v /mydata/redis/node-${port}/data:/data \
-v /mydata/redis/node-${port}/conf/redis.conf:/etc/redis/redis.conf \
-d --net redis --ip 172.38.0.1${port} redis:5.0.9-alpine3.11 redis-server /etc/redis/redis.conf
docker exec -it redis-1 /bin/sh #redis默认没有bash
redis-cli --cluster create 172.38.0.11:6379 172.38.0.12:6379 172.38.0.13:6379 172.38.0.14:6379 172.38.0.15:6379 172.38.0.16:6379  --cluster-replicas 1
```

![](.\picture\创建集群的配置.png)

集群搭建成功

![](.\picture\redis集群.jpg)

```shell
# 停掉redis3
# docker stop redis-3
```

![](.\picture\选取新主机.jpg)

## SpringBoot微服务打包Docker镜像

1、构建SpringBoot项目

2、打包运行

```mvn
mvn package
```

3、编写dockerfile

```dockerfile
FROM java:8
COPY *.jar /app.jar
CMD ["--server.port=8080"]
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
```

4、构建镜像

```shell
# 1.复制jar和DockerFIle到服务器
# 2.构建镜像
$ docker build -t xxxxx:xx  .
```

![](.\picture\构建镜像.jpg)

5、发布运行

![](.\picture\运行项目生成的镜像.jpg)

以后我们使用了Docker之后，给别人交付就是一个镜像即可！
