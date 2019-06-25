## tar命令

- *.tar 用 tar -xvf 解压
- *.gz 用 gzip -d或者gunzip 解压
- *.tar.gz和*.tgz 用 tar -xzf 解压   tar.xz  用 tar -Jxvf 解压
- *.tar.gz和*.tgz 用 tar -xzf 解压   tar.xz  用 tar -Jxvf 解压
- *.tar.bz2用tar -xjf 解压
- *.Z 用 uncompress 解压
- *.tar.Z 用tar -xZf 解压
- *.rar 用 unrar e解压
- *.zip 用 unzip 解压

## Mac kill 进程

- sudo lsof -i:9527
- sudo kill 2193




# ubantu14.04安装图形化界面并使用VNCViewer连接

1.安全组和防火墙需要放行5901端口（vncserver端口）
2.下载VNC viewer客户端连接软件https://www.realvnc.com/en/connect/download/viewer/


1.首先远程连接登录服务器。
2.执行命令：apt-get -y update更新源
3.执行命令 apt-get -y install x-window-system-core gnome-core gdm 安装环境。
4.执行命令 startx 启动图形化桌面 效果如下：

安装VNCserver服务。
1.执行命令 apt-get -y install vnc4server 安装vncserver
2.运行vnc4server 命令开启VNC服务并按界面提示设置连接密码。
3.运行命令 ps -ef | grep vnc 确认服务是否已经启动。如果返回以下类似结果，说明服务已经启动。
4.运行 cp -p ~/.vnc/xstartup ~/.vnc/xstartup.bak 命令备份原有xstartup文件。
5.按以下步骤修改vnc4server启动文件。
（1）运行 vim ~/.vnc/xstartup 命令打开文件。
（2）按i键进入编辑模式。
（3）将文件内容替换为以下内容。
#!/bin/sh
# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &
gnome-terminal &

5.依次运行以下命令生成新的会话

vncserver -kill :1 # 杀掉原来的桌面进程（假设桌面号为:1）
 vncserver :1 #生成新的会话

