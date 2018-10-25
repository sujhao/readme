
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

