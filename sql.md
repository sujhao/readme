## Mysql 重置密码
- 如果忘记密码,强行修改:
- 停止Mysql服务 sudo /usr/local/mysql/support-files/mysql.server stop
- 进入终端输入：cd /usr/local/mysql/bin/回车后;
- 登录管理员权限 sudo su回车后;
- 输入以下命令来禁止mysql验证功能 ./mysqld_safe --skip-grant-tables & 回车后mysql会自动重启（偏好设置中mysql的状态会变成running）
- 输入命令 ./mysql回车后，
- 输入命令 FLUSH PRIVILEGES;
- 回车后，输入命令 ALTER USER 'root'@'localhost' IDENTIFIED BY '你的新密码';

