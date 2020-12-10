
## MAVEN 安装(DEBIAN)

参考链接：
https://linuxize.com/post/how-to-install-apache-maven-on-debian-10/

<br>

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

## mysql 安装(DEBIAN)

参考链接: 
https://www.jianshu.com/p/40b770d86a7b

<br>

1. 下载文件: [mysql-apt-config_0.8.16-1_all.deb](https://dev.mysql.com/downloads/repo/apt/)
或
```
wget https://dev.mysql.com/get/mysql-apt-config_0.8.16-1_all.deb
```

2. 使用dpkg指令添加该文件进apt-get的源
```
sudo dpkg -i ./mysql-apt-config_0.8.16-1_all.deb
```

3. 更新源
```
sudo apt-get update
```

4. 安装MySQL
```
sudo apt-get install mysql-server
```

<br>

**其他**
```
# 开启MySQL服务
sudo service mysql start

# 关闭服务
sudo service mysql stop

# 重启服务
sudo service mysql restart

# 登录
mysql -u root -p

# 创建数据库用户
CREATE USER 'username'@'%' IDENTIFIED BY 'password';

# 分配权限
GRANT ALL PRIVILEGES ON *.* TO 'username'@'%';

# 刷新权限
FLUSH PRIVILEGES;

# 无法登录
sudo vim /etc/mysql/mysql.conf.d/mysqlld.cnf
- bind-address    = 127.0.0.1
+ bind-address    = 0.0.0.0
```


## REDIS 安装(DEBIAN)

参考链接:
https://www.jianshu.com/p/c10a080875a7

<br>

安装
```
sudo apt-get install redis-server
```

校验Redis服务是否正常运行
```
sudo systemctl status redis-server
```

配置远程访问
```
sudo vi /etc/redis/redis.conf
```

重新启动
```
sudo systemctl restart redis-server
```

验证正在监听的端口
```
ss -an | grep 6379

netstat -lntp|grep 6379
```

允许子网访问(ufw管理防火墙)
```
sudo ufw allow proto tcp from 192.168.121.0/24 to any port 6379
```

测试链接
```
redis-cli -h <REDIS_IP_ADDRESS> ping
```
