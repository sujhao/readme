## IPsec VPN 服务器一键安装脚本

使用以下命令快速搭建 IPsec VPN 服务器：
```

wget https://git.io/vpnsetup -O vpnsetup.sh && sudo sh vpnsetup.sh
如果使用 CentOS，请将上面的地址换成 https://git.io/vpnsetup-centos。
```
android 问题
```
/etc/ipsec.conf在VPN服务器上编辑。查找sha2-truncbug=yes并替换它sha2-truncbug=no。保存文件并运行service ipsec restart（Ref）。
```