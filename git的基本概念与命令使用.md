# 什么是Git
### Git是目前世界上最先进的分布式版本控制系统，且没有之一。
### 那么什么又是版本控制系统

**版本控制是指对软件开发过程中各种程序代码、[配置文件](https://baike.baidu.com/item/配置文件/286550)及说明文档等文件变更的管理，是[软件配置管理](https://baike.baidu.com/item/软件配置管理/3765602)的核心思想之一。**

举个栗子：大家都会经历编写修改毕业论文，emmmm…回想起来就很痛苦。先建立名为毕业论文.doc的Word文档，然后毕业论文1.doc，然后论文初稿123.doc、论文终稿、终终稿、终终定稿打死都不修改版……只想保留最新的，又不敢删其他的。而且当指导老师帮你修改拷到U盘中的论文后如果没有批注你想知道做了哪些修改是非常困难的。

但如果是这样：

文件名 | 修改人| 修改内容 | 修改时间 | 修改说明
-|-|-|-|-|
毕业论文.doc | Zander | 第一段第三行 | 2019/7/8 15:30 | 修改摘要关键字
毕业论文.doc | john | 第五段 | 2019/7/9 9:00 | 修改背景意义部分
毕业论文.doc | 指导老师 | 最后一段 | 2019/7/10 19:45 | 修改英文摘要
毕业论文.doc | …… | ……	| ……	| ……
真巧，分布式版本管理系统Git正好能做到
               ——**有效、高速地处理从很小到非常大的项目版本管理**。
  项目中的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

# Git命令使用
## 新增版本库
- $mkdir a 创建一个目录
- $ cd a 转换路径
- $ pwd 显示当前所在的位置
- $git init 初始化git仓库
    - 在git bash里，转换路径： cd e:/ belstar20190214
    - 输入 git init。就会在e:/ belstar20190214下产生目录 .git(隐藏目录)，表示e:\ web20170210里的项目代码（即所有的文件）会使用git进行版本管理。

## 增删文件
- 增加：
    - $git add index.html
    - $git commit -m “本次提交说明”
- 删除：
    - $git rm index.html
    - $git commit -m ”删除说明”
- 理解：add和commit
    - Add:添加；相当于打了标记（实际上是存储在了暂存区stage里）,告诉git，下次提交时把该文件进行提交。
    - Commit：提交。把打过标记的（即用add进行添加的文件），一次性进行提交。即可以一次性把暂存区里的文件全部进行提交，
提交了master分支（主分支）。提交完成后，暂存区里就没有文件了。

## 工作区与暂存区的概念
![img](https://img-blog.csdnimg.cn/20181207164931216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ppYW5nNzcwMTAzNw==,size_16,color_FFFFFF,t_70)

## 提交撤回
 - 文件在工作区的修改，没到暂存区
    - git checkout index.html 用暂存区中的内容或者版本库中的内容覆盖掉工作区
- commit 前修改
    - git reset HEAD index.html 撤销修改的暂存
- git status 查看本地仓库的状态
- git diff HEAD --  查看工作区和版本库里面最新版本的区别
- git checkout --  可以丢弃工作区的修改：
- 版本回退
    - Git log 查看所有的版本的命令 查看历史提交记录
    - Git reset -—hard HEAD^ 要恢复到上一个版本
    - git reset -—hard 版本序列号 恢复到指定版本

## 分支
- 查看分支：git branch
- 创建分支：git branch name
- 切换分支：git checkout name
- 创建+切换分支：git checkout -b name
- 合并某分支到当前分支：git merge name
- 删除分支：git branch -d name

## tag的概念及使用
- git tag tagname 新建一个标签
- git tag -a tagname -m “标签说明” 指定标签信息
- git tag 可以查看所有标签。
- git show tagname 查看某一标签
- git tag –d tagname 删除某一标签

## 克隆clone
- GitHub 登陆新建一个远程库
- Git clone 远程库地址
- Git push 提交更新
- Git pull 拉取更新 抓取远程仓库所有分支更新并合并到本地

## 每天做的git相关工作
- git add . 将所有修改过的工作文件提交暂存区
- git commit –m “版本描述”
- git push -u origin master 将本地主分支推到远程(如无远程主分支则创建，用于初始化远程仓库)
![img](https://img-blog.csdnimg.cn/20181207165305316.png)

 ## git提交GitHub
- 第一步：进入本地项目文件，cmd进入命令框，输入
    - git init
会在本地项目文件中，生成一个.git的文件

- 第二步：添加文件到仓库
    - git add .
- 第三步：提交的文件注释说明，最好说明一下，否则有时候会出错

    - git commit -m '注释说明'
- 第四步：将本地仓库关联到GitHub上的仓库里去

    - git remote add origin 仓库链接地址
- 第五步：首次提交要git pull 一下

    - git pull origin master
- 第六步：将代码提交到GitHub上

    - git push -u origin master

## git提交GitLab
- 打开git bash 然后输入如下命令：
    - git config --global  user.name “xxxx”
    - git config --global  user.email   "xxx@xxx"
![img](https://img-blog.csdn.net/20180522225203944?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzIwNjYzMjI5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

- 通过git config  --list可以列出配置信息
![img](https://img-blog.csdn.net/20180522225221249?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzIwNjYzMjI5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

- 将gitlab上面的空版本库克隆到本地
    - git clone   +“第一步获得的ssh地址"
![img](https://img-blog.csdn.net/20180522225303911?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzIwNjYzMjI5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

- 将需要提交的代码复制到上一步得到的空仓库中，然后在仓库所在的目录打开git bash，输入如下三条命令提交代码：
    - git add .
    - git  commit -m "提交信息"
    - git  push-u  origin master
![img](https://img-blog.csdn.net/20180522225419374?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzIwNjYzMjI5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
![img](https://img-blog.csdn.net/20180522225427971?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzIwNjYzMjI5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
![img](https://img-blog.csdn.net/20180522225435560?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzIwNjYzMjI5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

- 以后如果本地仓库的代码有更改，重复执行一次步骤4即可


