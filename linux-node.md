
## linux安装nodejs
拷贝nodejs上去
```
scp /Users/sujiehao/work/projects/linux-publish/node-v12.11.1-linux-x64.tar.xz  haolong@18.163.10.56:/home/haolong
```
```
tar xf node-v12.11.1-linux-x64.tar.xz       // 解压
```
加入环境变量
```
export NODE_HOME=/home/haolong/node-v12.11.1-linux-x64
export PATH=$NODE_HOME/bin:$PATH
source .bashrc
```

安装pm2
```
npm install pm2@latest -g
pm2 start app.js
pm2 list
pm2 show 0
pm2 restart 0
```