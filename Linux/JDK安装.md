查看Linux是否安装 JDK

```
java -version
```

创建JDK所在目录

```sh
mkdir /usr/local/java
```

解压jdk.tar.gz

```sh
tar -zxvf jdk-8u241-linux-x64.tar.gz  -C /usr/local/java
```

在*/etc/profile*中添加如下内容：

```
export JAVA_HOME=/usr/local/java/jdk1.8.0_351

export JRE_HOME=${JAVA_HOME}/jre

export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib

export PATH=${JAVA_HOME}/bin:$PATH
```

配置文件立即生效：

```
source /etc/profile
```

在Docker中 需要在*/root/.bashrc*中配置

```sh
export JAVA_HOME=/usr/local/java/jdk1.8.0_351
export PATH=$PATH:$JAVA_HOME/bin
```

因为重启容器后*/etc/profile*的配置将失效，具体原因未知？

# PING

```
#Ubuntu
apt install iputils-ping
```

