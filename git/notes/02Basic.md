# 基础
## 获取git仓库
### 本地初始化仓库
- git init：初始化仓库，默认当前目录
```
git init
```
也可以指定目录
```
git init fileName
```

### 元辰克隆仓库
- git clone：远程克隆，将远程库拉取至当前目录
```
git clone https://github.com/mihumouse/tool-chain.git
```
也可指定目标目录
```
git clone https://github.com/mihumouse/tool-chain.git path
```

## 状态
### 文件状态
文件分为未被跟踪、未修改、已修改、已缓存等状态，变化规律如下   
![](pic/fileStatuspng.png)

### 查询状态
git status，可查看是否有文件在以上的文件状态下，以便于开发者了解状态和处理   
-s参数能够简化status的冗长描述
```
$ git status -s
 M README.md
AM notes/01Start.md
AM notes/02Basic.md
A  test.md
?? notes/pic/
```
- 执行后M为修改，A为新增   
- AM代表即在缓存区add了，后又进行了修改   
- ??代表新增为被跟踪

## 跟踪
新建文件后，文件默认状态是untracked，需要通过git add，开始对该文件跟踪
```
git add test.md
```



