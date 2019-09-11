
cd ~
 vim ~/.bashrc
PS1='>>> \w\012\$ '

PS1='\u>>> \w\012\$'


export SVN_EDITOR=vim

export LS_OPTIONS='--color=auto'

export CLICOLOR=1

export LSCOLORS=gxfxaxdxcxegedabagacad

alias ll='ls -al'

alias rm="rm -i"

#alias .svnignore="svn propedit svn:ignore "

"~/.bashrc" 15L, 298C

清除 Xcode 编译产生的缓存
```
open ~/Library/Developer/Xcode/DerivedData
```
删除 Xcode 中的 profile 证书
```

open ~/Library/MobileDevice
```

```
source .bashrc
```