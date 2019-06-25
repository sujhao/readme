# linux下配置vpn环境

## Linux架设PPTP VPN

PPTP使用TCP（传输控制协议）连接的创建，维护，与终止隧道，并使用GRE(通用路由封装)将PPP帧封装成隧道数据。

我现在配置的是在Centos 6.4 x86_64下进行的，centos 6.4内核版本在2.6.15以上，都默认集成了MPPE和PPP，因此下面检查可以忽略，如果是2.6.15以下的需要检测如下：
#rpm -q  ppp      //查询当前系统的ppp是否默认集成了，以及ppp的版本

安装ppp

yum –y install ppp 或者
yum install pptpd ppp 

安装pptpd 　　pptpd 经常用来穿墙，或者是进行机房服务器管理

wget http://poptop.sourceforge.net/yum/stable/rhel6Server/pptp-release-current.noarch.rpm
rpm -ivh pptp-release-current.noarch.rpm

## 修改配置

$ vi /etc/ppp/options.pptpd
name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
proxyarp
lock
nobsdcomp 
novj
novjccomp
nologfd
ms-dns 114.114.114.114
ms-dns 114.114.115.115

ms-dns配置的是VPN client连接上VPN服务器之后获得的DNS，需要配置自己所在地的运营商的DNS也可以是第三方的DNS

$ vi /etc/pptpd.conf
option /etc/ppp/options.pptpd   ##配置文件路径

logwtmp                            ##日志 

localip 192.168.12.57        ## 填写vpn主机的外网地址。（我的是在内网，做了nat映射。所以本机ip就等于公网地址）

remoteip 192.168.80.1-50  ## 自己给一个VPN远程主机的IP地址范围。


$ vi /etc/ppp/chap-secrets
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
dog          pptpd  sujiehao9527        172.16.7.31

设置linux内核，支持ip转发
配置 /etc/sysctl.conf 文件
net.ipv4.ip_forward = 1将值改为1，即为启用
保存退出，执行sysctl -p 使之生效



六、iptables！！！！ （注意）
检查是否安装了iptables 
service iptables status 
安装iptables 
yum install -y iptables 
升级iptables 
yum update iptables 
安装iptables-services 
yum install iptables-services


需要开启1723端口 同时要做一条snat。（我曾天真的以为关掉防火墙就好了，结果连上vpn之后却不能上网！！纠结！！）

iptables -A INPUT -p tcp -m tcp --dport 1723 -j ACCEPT  （开启1723端口）

iptables -t nat -A POSTROUTING -s 192.168.80.0/24 -o eth0 -j MASQUERADE  ## 192.168.80.0/24  vpn远程服务器地址范围 etho 网卡设备名

iptables -A FORWARD -s 192.168.80.0/24 -o eth0 -j ACCEPT 

iptables -A FORWARD -d 192.168.80.0/24 -i eth0 -j ACCEPT
