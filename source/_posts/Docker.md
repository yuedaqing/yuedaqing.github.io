title: docker部署
---
## docker与VM区别
1. 由于docker不需要虚拟机实现硬件资源虚拟化，运行在docker容器上的程序直接使用的都是实际物理机的硬件资源。因此在CPU、内存利用率上docker将会在效率上有明显优势
2. docker利用的是宿主机的内核，不需要加载操作系统OS内核
3. 当新建一个容器时，docker不需要和虚拟机一样重新加载一个操作系统内核。避免引寻、加载操作系统内核返回等比较费时费资源的过程。
4. 当新建一个虚拟机时，虚拟机软件需要加载OS，返回新建过程是分钟级别的。而docker由于直接利用宿主机的操作系统，省略了返回过程，因此新建一个docker容器只需要几秒钟
```
https://blog.csdn.net/qq_50854662/article/details/127788452
```
## docker命令

1. -i ：以交互模式运行容器
2. -t：为容器重新分配一个伪终端
3. -it  启动交互式容器
4. -P 大写：随机端口映射
5. -p:小写：指定端口映射
6. -d：后台运行容器并返回容器Id，启动守护式容器
## docker安装（Centos7安装Docker）

-  
```
#依次运行以下命令添加yum源
yum update -y

#安装依赖
yum install epel-release -y
yum install yum-utils device-mapper-persistent-data lvm2 -y

#配置yum源 使用国内的
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

#查看版本
yum list docker-ce --showduplicates | sort -r

#1. 安装docker
yum -y install docker-ce-20.10.10-3.el7

#2. 查看docker版本
docker -v

#3. 启动docker
systemctl start docker

#4. 查看docker 启动状态
systemctl status docker

#检查安装结果。
docker info

启动使用Docker
systemctl start docker     #运行Docker守护进程
systemctl stop docker      #停止Docker守护进程
systemctl restart docker   #重启Docker守护进程

#查看容器
docker ps
#停止容器
docker stop 容器ID

#注意：不使用1.13.1版本，该版本在jenkins使用docker命令时会说找不到配置文件！
```
 

-  
```
#修改镜像仓库
vim /etc/docker/daemon.json

#改为下面内容，然后重启docker
{
"debug":true,"experimental":true,
"registry-mirrors":["https://pb5bklzr.mirror.aliyuncs.com","https://hub-mirror.c.163.com","https://docker.mirrors.ustc.edu.cn"]
}

#重启Docker守护进程
systemctl restart docker

#查看信息
docker info
```
 
# docker——安装redis
```
```shell
centos 7 安装独立环境 tcp6占用80端口解决方法
解决方法:

1、打开/etc/sysctl.conf
2、添加如下三条设置
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
3、保存修改
4、执行：
sudo sysctl -p
5、查看状态：
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
显示应该是1
6、结束
```
```
docker run -itd --name shop_redis -p 8000:6379 --restart=always -v /mydata/redis/data:/data redis:6.2.4 --requirepass hrbtiegu
```
## docker拉取redis镜像 
```
docker search redis 搜索
docker pull redis  拉取最新redis
docker pull redis:6.  拉取指定版本

docker run -d --privileged=true -p 6379:6379 --restart always -v /usr/local/redis/conf/redis.conf:/etc/redis.conf -v /root/usr/local/redis/data:/data  --name redisStudy redis redis-server /etc/redis.conf
```

## docker——redis配置文件

- 创建目录 
   - 日志 /usr/local/redis/log
   - 数据 /usr/local/redis/data
   - 配置文件 /usr/local/redis/conf
- redis.conf官网下载地址：[http://download.redis.io/redis-stable/redis.conf](http://download.redis.io/redis-stable/redis.conf)
- redis.conf配置讲解参考如下：[https://mp.csdn.net/console/editor/html/112244632](https://mp.csdn.net/console/editor/html/112244632)
- docker映射redis.conf命令 
```
//docker映射redis.conf命令：
docker run -p 6379:6379 --name redis -v /usr/local/redis/redis.conf:/etc/redis/redis.conf -v /usr/local/redis/data:/data -d redis redis-server /etc/redis/redis.conf --appendonly yes
docker run -p 6379:6379 --name redis -v /usr/local/redis/conf/redis.conf:/etc/redis/redis.conf -v /usr/local/redis/data:/data -d redis redis-server /etc/redis/redis.conf --appendonly yes

http://download.redis.io/redis-stable/redis.conf

https://github.com/redis/redis/blob/4930d19e70c391750479951022e207e19111eb55/redis.conf
```
### 命令解释 
```
-p 6379:6379 端口映射：前表示主机部分，：后表示容器部分。
--name redis 指定该容器名称，查看和进行操作都比较方便。
-v 挂载目录，规则与端口映射相同。
为什么需要挂载目录：个人认为docker是个沙箱隔离级别的容器，这个是它的特点及安全机制，不能随便访问外部（主机）资源目录，所以需要这个挂载目录机制。
-d redis 表示后台启动redis
redis-server /etc/redis/redis.conf ?以配置文件启动redis，加载容器内的conf文件，最终找到的是挂载的目录/usr/local/redis/redis.conf
docker启动redis
```
### 配置 
```
#任何ip可以访问
bind 0.0.0.0

#守护进程
daemonize yes

#密码
requirepass 123456

#日志文件
logfile "/usr/local/redis/log/redis.log"

#持久化文件名称
dbfilename xdclass.rdb

#持久化文件存储路径
dir /usr/local/redis/data

#持久化策略, 10秒内有个1个key改动，执行快照
save 10 1
```
### docker——启动redis
```
docker exec -it [redis_id] /bin/bash

bind 0.0.0.0
port 6379
daemonize yes
requirepass "123456"
logfile "/usr/local/redis/log/redis1.log"
dbfilename "redis1.rdb"
dir "/usr/local/redis/data"
databases 16
appendonly yes
appendfilename "appendonly1.aof"
masterauth "123456"
```
### docker安装RabbitMQ
```
docker search rabbitmq  #搜索rabbitmq镜像
docker pull rabbitmq  #拉取mq镜像

docker run -d --name rabbit -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=admin -p 15672:15672 -p 5672:5672 -p 25672:25672 -p 61613:61613 -p 1883:1883 rabbitmq:management
```
```
#1.拉取最新版本的镜像
   docker pull rabbitmq 
 #2.启动服务
   docker run -d --name rabbitmq -p 15672:15672 -p 5672:5672 rabbitmq 
 #3.启动管理插件
   docker exec -it rabbitmq rabbitmq-plugins enable rabbitmq_management 
 #4.重启rabbitmq服务
 	docker restart rabbitmq
#5.进入rabbit命令面板
docker exec -it rabbit /bin/bash
#6.查看用户列表
rabbitmqctl list_users
```

- 安装MQ延迟队列插件
```
下载插件： wget https://github.com/rabbitmq/rabbitmq-delayed-message-exchange/releases/download/3.11.1/rabbitmq_delayed_message_exchange-3.11.1.ez
docker cp /opt/soft-ware/rabbitmq_delayed_message_exchange-3.9.0.ez  rabbitmq:/opt/rabbitmq/plugins/
```
## DockerCompose安装

- 下载地址：[https://docs.docker.com/compose/install/other/](https://docs.docker.com/compose/install/other/)
```bash
#使用镜像安装
sudo curl -L "https://get.daocloud.io/docker/compose/releases/download/v2.16.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
#读写权限
sudo chmod +x /usr/local/bin/docker-compose

```
