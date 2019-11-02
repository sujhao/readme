
## 下载jdk

## 解压
tar -xf /data/software/mysql-8.0.18-linux-glibc2.12-x86_64.tar

## 移动安装包
mv jdk1.8.0_152/ /usr/local/java/

## 设置所有者
chown -R root:root /usr/local/java/

## 配置系统环境变量
```
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$JAVA_HOME/bin:$PATH
```

