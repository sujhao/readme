# 设置Linux用户连续N次登陆失败时，自动锁定X分钟(pam_tally)
1、如果想在所有登陆方式上，限制所有用户，可以在 /etc/pam.d/system-auth 中增加2行

```
auth  required  pam_tally.so  onerr=fail  no_magic_root
account  required  pam_tally.so   deny=5 unlock_time=3600   root_unlock_time=3600  no_magic_root  even_deny_root_account  per_user  reset

```
deny  设置普通用户和root用户连续错误登陆的最大次数，超过最大次数，则锁定该用户；
no_magic_root  连root用户也在限制范围，不给root特殊权限。
unlock_time: 锁定用户时间，单位为秒；

2.手动解除锁定
```
#查看某一用户错误登陆次数：
pam_tally –user username
#例如，查看work用户的错误登陆次数：
pam_tally –user work

#清空某一用户错误登陆次数：
pam_tally –user username –reset
#例如，清空 work 用户的错误登陆次数，
pam_tally –user work –reset

faillog -r 命令亦可
```

3.pam_tally没有自动解锁功能
```

因为pam_tally没有自动解锁的功能，所以，在设置限制时，要多加注意，万一全做了限制，而 root用户又被锁定了，就只能够进单用户模式解锁了，当然，也可以添加crontab任务，达到定时自动解锁的功能，但需要注意的是，如果在/etc /pam.d/system-auth 文件中添加了pam_tally的话，当root被锁定后，crontab任务会失效，所以，最好不要在system-auth 文件中添加pam_tally。
```