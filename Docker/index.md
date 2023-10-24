# 什么是docker

>  Build, Ship and Run Any App,Anywhere

docker将软件需要的运行环境一起打包，并生成一个镜像文件。镜像文件可以在任何docker中运行。

docker需要依赖Linux内核运行。

docker类似于VMware，docker中的每个容器都是一个精简版的Linux系统，只有最基本的Linux系统功能。

# 安装docker

docker需要运行在linux环境中

卸载docker

```Bash
yum remove docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine
```

Linux需要存在yum-utils

```Bash
yum install -y yum-utils device-mapper-persistent-data lvm2
```

添加docker阿里云镜像仓库

```Bash
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

安装docker

```Bash
yum install docker-ce
```

测试docker

```Bash
docker -v
```

运行成功将显示docker版本

启动/关闭docker

```Bash
systemctl start |stop docker
```

查看docker状态

```Bash
systemctl status docker
```

设置自启动

```Bash
systemctl enable docker
```

阿里云镜像加速服务：https://cr.console.aliyun.com/cn-chengdu/instances/mirrors

# 快速部署

以Mysql为例

拉取Mysql镜像文件

```Bash
docker pull mysql:latest 
```
创建并运行一个Mysql容器
```Bash
docker run -d --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql
```