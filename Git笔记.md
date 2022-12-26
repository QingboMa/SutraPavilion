

## 规范

### 分支命名规约

| 前缀       | 含义                             |
| ---------- | -------------------------------- |
| **-test    | 测试分支，验证后可直接发布的版本 |
| **-beta    | 用于发布beta版本分支             |
| **-release | 用于发布正式稳定版分支           |
| develop    | 开发主分支，最新的代码分支       |
| feature-** | 功能开发分支                     |
| bugfix-**  | 未发布bug修复分支                |
| hotfix-**  | 已发布bug修复分支                |

> 核心原则：
> 1、版本发布是一个递进的过程
> 2、每个发布的特性或bug修需要进行测试再进行发布
> 3、小版本仅仅修复bug或仅改版本号进行透明升级的特性

### 提交命名规约

除了分支的名称需要规范，提交的命名也同样如此。猪齿鱼并没有把这个规则固化到系统中，需要团队共同遵守。

格式为：[操作类型]操作对象名称，如[ADD]readme，代表增加了readme描述文件。

常见的操作类型有：

- [IMP] 提升改善正在开发或者已经实现的功能
- [FIX] 修正BUG
- [REF] 重构一个功能，对功能重写
- [ADD] 添加实现新功能
- [REM] 删除不需要的文件



## git发版的分支流程

先从远程master新建一个本地master分支。

![image-20220609175644166](D:/dev/Typora/image/image-20220609175644166.png)

之后再从本地master分支切出一个新分支，如新建uat_mqb_37684分支，并切换到uat_mqb_37684分支

![image-20220609175744442](D:/dev/Typora/image/image-20220609175744442.png)



在uat_mqb_37684分支上编写代码之后 

```bash
git add .
```

```bash
git commit -m 'message'
```

```bash
git push origin uat_mqb_37684
```

之后切换到远程uat分支

![image-20220609175906233](D:/dev/Typora/image/image-20220609175906233.png)

首先要获取远程的最新代码

```bash
 git pull origin uat
```

或者

![image-20220609180257420](D:/dev/Typora/image/image-20220609180257420.png)

之后将自己写的uat_mqb_37684分支上的代码合并到本地uat分支

![image-20220609180407436](D:/dev/Typora/image/image-20220609180407436.png)

之后将本地uat分支提交到远程uat分支

![image-20220609180459651](D:/dev/Typora/image/image-20220609180459651.png)

### 版本回退

若想要回退到该节点

![image-20220609180639497](D:/dev/Typora/image/image-20220609180639497.png)

#### 复制版本号 

![image-20220609180702043](D:/dev/Typora/image/image-20220609180702043.png)

#### Reset HEAD

![image-20220609180753949](D:/dev/Typora/image/image-20220609180753949.png)

将复制的版本号粘贴到 `To Commit`

Reset Type 选择 `Hard`,之后点击Reset就成功回退

![image-20220609180828656](D:/dev/Typora/image/image-20220609180828656.png)

## git命令

### 先`add`后`commit`

```bash
git commit -am '注释'
```

### 更改上次提交的注释

```   bash
git commit --anend  '注释'
```

### 回退版本

#### 回退前一次提交

```bash
git reset --hard HEAD^
```

#### 回退前n次提交

```bash
git reset --hard HEAD^n
```

#### 回退到ce1f0a488a9a121a7e79c0c5f6681677aa63947e版本

`ce1f0a488a9a121a7e79c0c5f6681677aa63947e`可以简写 `ce1f0a`

```bash
git reset --hard ce1f0a488a9a121a7e79c0c5f6681677aa63947e
```

### 查看所有的日志

`git reflog`

### 放弃工作区的修改

```bash
git checkout .
```



## 将指定分支的某次提交合并到另一分支

首先，切换到develop分支，敲 git log 命令，查找需要合并的commit记录，比如commitID：7fcb3defff；

然后，切换到master分支，使用 git cherry-pick 7fcb3defff  命令，就把该条commit记录合并到了master分支，这只是在本地合并到了master分支；

最后，git push 提交到master远程，至此，就把develop分支的这条commit所涉及的更改合并到了master分支。





## 撤销某次提交

git revert 撤销中间的提交记录

[_forwardMyLife的博客-CSDN博客_git撤销某次提交](https://blog.csdn.net/lucky_ly/article/details/101394171)



## 撤销未添加到暂存区的文件（工作区的文件(未add的文件)）



git restore [file_path]





## 撤销已经add但是没有commit的代码

git rm --cached D:\job\dev\hcmcc_fssc\src\main\resources\rebel.xml

