# 基于CentOS搭建 FTP 文件服务

[toc]

## 安装并启动 FTP 服务：安装 VSFTPD，使用 yum 安装 vsftpd，安装命令如下
```
yum install vsftpd -y
```

## 启动 VSFTPD：安装完成后，启动 FTP 服务，启动命令如下：
```
service vsftpd start
```

## FTP 协议默认使用 21 端口作为服务端口，启动后，可以看到系统已经 监听了 21 端口
```
netstat -nltp | grep 21
```
此时，访问 ftp://你的服务器IP地址， 可浏览机器上的 /var/ftp 目录了。

## 配置 FTP 权限：
vsftpd 的配置目录为 /etc/vsftpd，包含下列的配置文件：
vsftpd.conf 为主要配置文件
ftpusers 配置禁止访问 FTP 服务器的用户列表
user_list 配置用户访问控制

编辑 /etc/vsftpd/vsftpd.conf，
```
# 禁用匿名用户
anonymous_enable=NO
# 禁止切换根目录
chroot_local_user=YES
```
重新启动 FTP 服务，重启命令如下：
```
service vsftpd restart
```

## 创建FTP用户，创建一个用户 ftpuser，命令如下：
```
useradd ftphao
```
为用户 ftpuser 设置密码，命令如下：
```
echo "sujiehao" | passwd ftphao --stdin
```

## 限制该用户仅能通过 FTP 访问：
```
usermod -s /sbin/nologin ftphao
```

## 为用户分配主目录

## 设置访问权限，让用户对他的主目录有可读写权限，执行如下命令：
```
 chmod a-w /root/haoupload/ 
 chmod 777 -R /root/haoupload/

```
## 把该目录设置为用户的主目录，执行如下命令：
```
usermod -d /root/haoupload ftphao
```

## 测试





