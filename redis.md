# Redis使用

- 下载解压redis $tar xzf redis-5.0.4.tar.gz 
- cd redis-5.0.4/
- make
- cd src
- ./redis-server ../redis.conf                 //redis.conf 是一个默认的配置文件。我们可以根据需要使用自己的配置文件。

- 启动成功

- 启动redis服务进程后，就可以使用测试客户端程序redis-cli和redis服务交互了。 比如：
- $ cd src
- $ ./redis-cli
- redis> set foo bar
- OK
- redis> get foo
- "bar"


 
