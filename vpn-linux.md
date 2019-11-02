## IPsec VPN 服务器一键安装脚本

使用以下命令快速搭建 IPsec VPN 服务器：
```
sh vpnsetup-cenos.sh (在本仓库下的文件)
```
android 问题
```
/etc/ipsec.conf在VPN服务器上编辑。
查找sha2-truncbug=yes并替换它sha2-tr‘uncbug=no。
保存文件并运行service ipsec restart（Ref）。
```

windows问题
```
下载Fix_VPN_Error_809_Windows_Vista_7_8_10_Reboot_Required.reg文件安装进注册表，双击打开即可，在我的这个git项目下可以找到，重启电脑

返回网络和共享中心。在左侧，单击“ 更改适配器设置”。
右键单击新VPN条目，然后选择“ 属性”。
单击“ 安全”选项卡。为VPN类型选择“具有IPsec的第2层隧道协议（L2TP / IPSec）” 。
单击允许这些协议。选中“质询握手身份验证协议（CHAP）”和“Microsoft CHAP版本2（MS-CHAP v2）”复选框。
单击“ 高级设置”按钮。
选择使用预共享密钥进行验证，并输入Your VPN IPsec PSK的关键。
```