首先，推荐跑下面的脚本：

https://github.com/BoizZ/PPTP-L2TP-IPSec-VPN-auto-installation-script-for-CentOS-7

这个脚本将pptp l2tp  ipsec都按照，并且配置好，当然很多配置不准确

跑脚本的时候配置好ip规划，PPsk共享秘钥（这个后面客户端连接需要用到） 用户名 ，密码 （后面连接都需要用到）  

PSK共享秘钥在/etc/ipsec.secrets可以找到和配置

用户名密码在/etc/ppp/chap-secrets 可以找到配置


参考：https://www.cnblogs.com/mikeluwen/p/10402631.html