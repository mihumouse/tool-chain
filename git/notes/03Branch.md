# 分支
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

## 相关说明
- master并不特殊，只是git提供的默认分支的名称
- HEAD代表当前分支
- git中通过对象记录文件、结构、版本变化：blob保存文件快照、Tree对象保存目录结果和索引、提交对象包括提交的信息（提交人等）和文件快照及树对象（快照和树是该对象的属性）
