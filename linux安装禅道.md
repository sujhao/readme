# linux安装禅道

## 上传下载的压缩包到服务器
下载地址:https://www.zentao.net/download/
```
scp /Users/jhao/Downloads/ZenTaoPMS.11.6.1.zbox_64.tar.gz root@182.61.108.196:/opt
```
## 解压
```
tar -zxvf ZenTaoPMS.11.6.1.zbox_64.tar.gz
```

## 启动Apache与mysql
执行/opt/zbox/zbox start 命令开启Apache和Mysql。
执行/opt/zbox/zbox stop 命令停止Apache和Mysql。
执行/opt/zbox/zbox restart 命令重启Apache和Mysql。
注：如果需要开机自动启动，可以把 /opt/zbox/zbox restart 加到操作系统的自启目录。
禅道默认管理员帐号是 admin，密码 123456。

## 其他
可以使用/opt/zbox/zbox -h命令来获取关于zbox命令的帮助。
其中 -ap参数 可以修改Apache的端口，-mp参数 可以修改Mysql的端口。
例如（apache端口改为36550，mysql端口改为3307）：
/opt/zbox/zbox stop
/opt/zbox/zbox -ap 36550 -mp 36560
/opt/zbox/zbox start

## 登录
http://ip:apache端口

http://182.61.108.196:36550

admin Aa11223344

