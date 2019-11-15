## linux安装mysql

--创建MySQL专属文件夹 
```
mkdir mysql            
cd mysql                                                               
```
--安装MySQL5.7版本
```
wget https://dev.mysql.com/get/mysql80-community-release-el8-1.noarch.rpm
wget http://dev.mysql.com/get/mysql57-community-release-el7-7.noarch.rpm           
```

--查看安装包内容
```
rpm -qpl mysql57-community-release-el7-7.noarch.rpm 
```
 --安装rpm包
```
rpm -ivh mysql57-community-release-el7-7.noarch.rpm  
```
--生成MySQL安装包
```
yum list Mysql*      
```
--安装社区版MySQL
```
yum install mysql-community-server 
```
--启动MySQL
```
service mysqld start 
```
--查看MySQL初始密码
```
grep "password" /var/log/mysqld.log   
```
--用初始密码登录MySQL
```
mysql -u root -p 
注：在默认密码的长度最小值为 4 ，由 大/小写字母各一个 + 阿拉伯数字一个 + 特殊字符一个，
set password for root@localhost = password('Abc@666666');
```


## 卸载Mysql

#### rpm包安装方式卸载
```
查包名：rpm -qa|grep -i mysql
删除命令：rpm -e –nodeps 包名
```

#### yum安装方式下载
```
1.查看已安装的mysql
命令：rpm -qa | grep -i mysql

2.卸载mysql
命令：yum remove mysql-community-server-5.7.28-1.el7.x86_64
查看mysql的其它依赖：rpm -qa | grep -i mysql

//卸载依赖
 yum remove mysql57-community-release-el7-7.noarch
```