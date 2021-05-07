# git
## 配置相关
- git config --global --list：查全局配置
- git config --list：查当前库配置
- git config user.name：查某个属性
- git config -e：编辑当前库配置
- git config -e --global：编辑全局库配置

## 仓库初始化
- git init：初始化仓库，默认当前目录
```
git init
```
也可以指定目录
```
git init fileName
```

- git clone：远程克隆，将远程库拉取至当前目录
```
git clone https://github.com/mihumouse/tool-chain.git
```
也可指定目标目录
```
git clone https://github.com/mihumouse/tool-chain.git path
```

## 文件提交
- git add：文件add到缓存区
- git status：查看文件状态，显示有变更的文件
- git diff：查看差异，注意比对的是工作区与缓存区的差异
```
git diff git/test/text
```
- git commit：提交到本地仓库
```
git commit -m "commit test"
```

## reset
reset需要先理解，工作区——暂存区——本地库这三个位置含义   
- git reset：回退版本，语法 git reset [--soft | --mixed | --hard] [HEAD]
- HEAD   
HEAD 表示当前版本   
HEAD^ 上一个版本   
HEAD^^ 上上一个版本（也可HEAD^2）   
HEAD^^^ 上上上一个版本（也可HEAD^3）   
- --soft 仅仅是把本地库的指针移动了，而暂存区和你本地的代码是没有做任何改变的
```
git reset --soft HEAD
```

- --mixed 为默认，移动本地库指针、重置暂存区
```
$ git reset HEAD^            # 回退所有内容到上一个版本  
$ git reset HEAD^ hello.php  # 回退 hello.php 文件的版本到上一个版本  
$ git  reset  052e           # 回退到指定版本
```

- --hard 移动本地库指针、重置暂存区、重置工作区
```
$ git reset –hard HEAD~3  # 回退上上上一个版本  
$ git reset –hard bae128  # 回退到某个版本回退点之前的所有信息。 
$ git reset --hard origin/master    # 将本地的状态回退到和远程的一样
```
