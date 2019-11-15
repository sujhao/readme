
利用git工具打开 Git Bash Here利用git工具打开 Git Bash Here

执行如下命令 ssh-keygen -t rsa -C "email@email.com" 其中邮箱为GitHub的邮箱

再执行eval  "ssh-agent -s"命令

输入ssh-add ~/.ssh/id_rsa 命令时候报错

ssh-agent bash

用vim复制key的内容：vim ~/.ssh/id_rsa.pub 到GitHub中

