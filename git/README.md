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

## rm
git rm ：将文件从暂存区和工作区中删除
```
git rm -f file
```
删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f，目录递归 -r，如果只删除暂存区，不删除工作区则--cached
```
git rm --cached file
```   

## 分支管理
- git branch：列出现有分支
- git branch newBranch：创建新的分支，分支名为newBranch，注：创建分支时，不用新增目录
- git checkout targetBranch：切换到目标分支，增加-b则创建新分支并立即切换到该分支下
- git merge secondBranch：secondBranch分支合并到master
- git branch -d secondBranch：合并后，方可将分支删除
- 冲突处理：当两个分支存在冲突时，merger会Automatic merge failed，并列出冲突文件，冲突文件中会展示冲突内容和差异，需要人工完成冲突处理，然后重新add，完成merge，如下：
```
$ git merge newBranch
Auto-merging git/test/text
CONFLICT (content): Merge conflict in git/test/text
Automatic merge failed; fix conflicts and then commit the result.

手工处理冲突 

lenovo@LAPTOP-4CLVVOF3 MINGW64 /e/IdeaProjects/tool-chain/git/test (master|MERGING)
$ git add text

lenovo@LAPTOP-4CLVVOF3 MINGW64 /e/IdeaProjects/tool-chain/git/test (master|MERGING)
$ git commit -m 'deal confict'
[master 82380e5] deal confict

lenovo@LAPTOP-4CLVVOF3 MINGW64 /e/IdeaProjects/tool-chain/git/test (master)
$ git merge newBranch
Already up to date.

lenovo@LAPTOP-4CLVVOF3 MINGW64 /e/IdeaProjects/tool-chain/git/test (master)
$ git branch -d newBranch
Deleted branch newBranch (was 9775552).
```