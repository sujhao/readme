1.查找要屏蔽的ip
awk '{print $1}' nginx.access.log |sort |uniq -c|sort -n

2.在nginx的安装目录下面,新建屏蔽ip文件，命名为blockip.conf，以后新增加屏蔽ip只需编辑这个文件即可。 加入如下内容
deny 165.91.122.67; 
deny 123.45.6.0/24;   #屏蔽IP段即从123.45.6.0到123.45.6.24访问的命令

## 3.在nginx的配置文件nginx.conf中加入如下配置，可以放到http, server, location, limit_except语句块，需要注意相对路径，本例当中nginx.conf，blocksip.conf在同一个目录中。
include blockip.conf; 
