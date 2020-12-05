
## MAVEN 安装

参考链接：
https://linuxize.com/post/how-to-install-apache-maven-on-debian-10/

方法一：

通过 apt 安装
```
sudo apt update
sudo apt install maven
```

<br>

方法二：

下载安装
```
wget https://www-us.apache.org/dist/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz -P /tmp
sudo tar xf /tmp/apache-maven-*.tar.gz -C /opt
sudo ln -s /opt/apache-maven-3.6.3 /opt/maven
```

修改环境变量
```
sudo nano /etc/profile.d/maven.sh

# 插入
export JAVA_HOME=/usr/lib/jvm/default-java
export M2_HOME=/opt/maven
export MAVEN_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}
```

<br>

查看版本
```
mvn -version
```

