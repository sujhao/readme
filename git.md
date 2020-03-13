## git 常用命令
git rev-list HEAD --count //查看commit 次数

git checkout -b branchlocal //新建本地分支

git branch //查看本地分支

git checkout V2538 //切换到tag V2538

git tag //显示tag

git tag V2538 //加入本地tag

git push origin --tags; //推送本地tag到服务器

git push origin -d skin2 //删除远程分支

git checkout —-theirs filename //采用传人版本

git checkout --ours filename //采用当前更改

git status //查看当前状态

git checkout . //放弃当前更改

git add . //暂存更改

git remote set-url origin http://192.168.0.6:3000/haolong/ClientCore.git //修改远程仓库地址

git submodule add -f http://192.168.0.6:3000/haolong/ClientCore.git;//增加git子模块
git submodule add https://github.com/chaconinc/DbConnector //增加子模块

git branch -d branchname //删除本地分支

git branch -D branchname //强制删除本地分支

git push origin -d branchname //删除远程分支

git remote show origin //显示远程分支
git remote update origin -–prune //获取远程最新分支

git submodule add git@github.com:test/test.git //增加子模块
git submodule foreach git pull //获取所有模块
克隆一个包含子仓库的仓库目录，并不会clone下子仓库的文件，只是会克隆下.gitmodule描述文件，需要进一步克隆子仓库文件。
// 初始化本地配置文件
$ git submodule init

// 检出父仓库列出的commit
$ git submodule update
或者使用组合指令。

$ git submodule update --init --recursive


git submodule foreach git checkout master 
$ git rm --cached <本地路径>  //删除子仓库

git config --system core.longpaths true //设置windows档名太长
git submodule update --init

//回退版本
git reset --hard 3a8261ad30bd9d86882880453a48abb524354317
git push -f -u origin master

//递归克隆子仓库
git clone --recursive git@192.168.1.6：222、asn

//删除远程分支后同步本地分支
git remote prune origin

//查看当前git配置
git config --list

//合并master分支a.txt文件
git checkout -p master a.txt

//设置快捷键
git config --global alias.co checkout

git config --global alias.br branch

git config --global alias.ci commit

git config --global alias.st status


git config --global user.name jhao

git config --global user.email jhao123456@abc.com

## git多个remote，假如你想把一个仓库又备份到gitee又备份到github咋搞，这时候就要到多个remote
```
git remote add gitee https://gitee .com/project.git

git remote add github https://github .com/project.git

git push github master

git push gitee master

```


## mac 生成ssh key

```

 - 输入指令：ssh-keygen -t rsa -C “test@qq.com"，提示输入保存密钥路径，直接回车即可（三次默认回车）。
 - cd ~/.ssh，文件夹内会存在2个文件：id_rsa和id_rsa.pub。
 - 将公钥内容添加到GitHub，即id_rsa.pub文件拷贝到git服务器配置上
```





