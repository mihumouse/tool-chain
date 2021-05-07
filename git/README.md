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
- git reset：回退版本，把add的内容回退
- git diff：查看差异，注意比对的是工作区与缓存区的差异
```
git diff git/test/text
```