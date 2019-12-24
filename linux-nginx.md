# linux下使用nignx

## 安装依赖包
```
//一键安装上面四个依赖
yum -y install gcc zlib zlib-devel pcre-devel openssl openssl-devel
```

## 下载安装包
```
wget http://nginx.org/download/nginx-1.16.1.tar.gz
# 解压缩
tar -zxvf nginx-1.16.1.tar.gz
cd nginx-1.12.2/
# 执行配置
./configure --with-http_ssl_module  //添加ssl模块以后会用到如果使用https
# 编译安装(默认安装在/usr/local/nginx)
make
make install

```

