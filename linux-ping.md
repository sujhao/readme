# Linux禁止ping以及允许ping的方法
[toc]

![](./assets/1.jpg)

Ping是Windows、Unix和Linux系统下的一个命令。ping也属于一个通信协议，是TCP/IP协议的一部分。利用“ping”命令可以检查网络是否连通，可以很好地帮助我们分析和判定网络故障。

ping虽然可以帮助我们分析网络故障， 但是某些病毒木马会强行大量远程执行ping命令抢占你的网络资源，导致系统变慢，网速变慢。严禁ping入侵作为大多数防火墙的一个基本功能提供给用户进行选择。通常的情况下如果你没有什么特殊的要求，就禁止他吧，来保护系统的安全。

系统是否允许Ping由两个因素决定的：内核参数和防火墙。只要两个因素都允许才允许被ping,如果其中一个因素不允许就会禁止被ping。

下面就说一说，在Liunx系统下如何开启被ping和禁止被ping

## 内核参数设置

### 允许ping设置
1.临时允许PING操作的命令为：
```
#echo 0 >/proc/sys/net/ipv4/icmp_echo_ignore_all
```
2.永久允许PING配置方法。
/etc/sysctl.conf中增加一行
```
net.ipv4.icmp_echo_ignore_all=0
```
如果已经有net.ipv4.icmp_echo_ignore_all这一行了，直接修改=号后面的值即可的（0表示允许，1表示禁止）。
修改完成后执行sysctl -p使新配置生效。

### 禁止ping设置
1.临时禁止PING的命令为：
```
#echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all
```
2.永久允许PING配置方法。
/etc/sysctl.conf中增加一行
```
net.ipv4.icmp_echo_ignore_all=1
```
如果已经有net.ipv4.icmp_echo_ignore_all这一行了，直接修改=号后面的值即可的（0表示允许，1表示禁止）。
修改完成后执行sysctl -p使新配置生效。

## 防火墙设置
注：此处的方法的前提是内核配置是默认值，也就是没有禁止Ping
这里以Iptables防火墙为例，其他防火墙操作方法可参考防火墙的官方文档。
1、允许PING设置
```
iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT
```
或者也可以临时停止防火墙操作的。
```
service iptables stop
```
2、禁止PING设置
```
iptables -A INPUT -p icmp --icmp-type 8 -s 0/0 -j DROP
```

