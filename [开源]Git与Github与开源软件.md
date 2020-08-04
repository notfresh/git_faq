# Git知识

59

场景：今天想到之前的一个仓库，想好好的整理一下. 比如清空过去的提交记录？

哦.. 这个完全可以通过删库来解决的。

我想起来了一个常用的办法

git有很多的子命令，不懂的时候，输入 git 子命令 --help 就可以看手册了。

当然，目前也有很多问题，比如仅仅知道git的命令，却不知道其背后的原理，我很焦虑

想法：我想把一个刚刚push过的本地仓库合并几个commit, 然后看能不能推送上去？

知识：rebase的用法啊，git rebase master, 当前在dev上面，那么意思就是把dev的commits应用到master上面去。当前的分支放到前面。

511

场景： 今天在一个项目里开始git管理，使用git add -A,  把一些不想加进去的东西添加到暂存区里去了。 想到了git reset 命令， 就恢复了，然后再在 .gitignore里加上

比如 *.pyc  .idea

一

我在想 git 对一个改名的文件该如何处理呢 ？

如果为了简洁处理，那么绝对不会把文件作为唯一标识符，而是会起一个文件的ID，保存着当前的路径。



521

Git status -s

git.diff [--cached] 

Git log -p -2。p表示patch

git log --since --before 

525

在a上Merge b，意思是把b合并到a里面去

a的指针移动

$ git log --no-merges issue54..origin/master

issue54..origin/master 语法是一个日志过滤器，要求 Git 只显示所有在后面分支（在本例中是origin/master）但不在前面分支（在本例中是 issue54）的提交的列表

你可能会想要使用 rebase -i 来将工作压缩成一个单独的提交，或者重排提交中的工作使补丁更容易被维护者审核 - 查看 重写历史 了解关于交互式变基的更多信息。

$ git log contrib --not master

528

场景：

如果某次提交忘了加上某个文件或者忘记漏了某一行，该怎么办？

如果重新再补一个commit, 那么会非常的丑陋，两个commit只做了一件事，因为自己的疏忽多提交了一个commit。

解决： 使用git commit --ammend

书签：

如何写一个标准的 .gitignore文件呢？

参见p25

场景：如何查看某次commit 做了哪些修改呢？

解决： 使用 show命令 + commitID

场景：每次使用的流程都是 git add xxx, git commit， 可以缩短步骤吗？

解决： 使用 git commit -a -m 'commit'。

理解： git reset --hard 和 git reset 到底有什么区别？

答： git reset --hard 用提交区（或者说待提交区）覆盖工作区，但是 git rest 不修改工作区。

理解： git reflog到底是干什么的？

答： git reflog是用来记录每一次 HEAD指针变化的。可以用来方便的进行时空穿梭。

书籍补充：

状态简览： 

AM表示加入待提交区，又修改了。

UU 双方都修改了文件

在网上看到一个消息， 双字母的，再无冲突的时候，第一个表示待提交区，第二个表示工作区。

有冲突的时候，XY 表示两个版本

530

git show CommitID， 可以查看某次提交的详细信息，修改了哪些东西。

git log -p -1 可以查看上次提交的详细信息， -2 可以查看两次信息。

git log --stat 可以查看统计信息。

git log是一个非常非常非常重要的命令，我今天，现在终于知道了。这个命令，简直是重要的不能重要了。但是，我反思了一下，其实我对这个命令了解的并不多。

问题：提交者和作者是什么区别？TODO

git log的筛选

根据日期筛选 git log --before --after=2018-01-01, 如果跟的有时分秒，用引号引起来

根据作者筛选

git log显示日志的顺序， 是先显示最近的，再显示最早的， 如果想从头查询， 跟上 --reverse

书签：p37页，有关log的自定义特殊用法。 

重置暂存区， 用提交区去覆盖暂存区， git reset

git checkout -- file ，会用提交区覆盖工作区。

rebase

最难的环节

打标签 git tag

标签的作用是别名，我觉得意义非常重要。

p47

推送标签

git push origin tagname

git push origin --tags

git tag -d 

62

章节：Git分支

查看各个分支指向的位置，使用 --decorate命令 

--all 会显示所有分支的位置

git branch --merged 查看合并到当前分支的其他分支

git branch --no-merged则相反

分支的工作模式

p71

pu分支 proposed-updates

dev分支

master分支

分支命名规范 issNUMBR, issNUMBERv2

远程分支默认只有一个不可移动的 remote/branchX, 不会自动新建一个本地的branchX和它关联，这需要手动建立。

git checkout -b branchX origin/branchX 

等同于

git checkout --track origin/branchX

git branch -vv 只会显示绑定的本地分支和没联网的 origin/分支之间差几个，想要查看实时的，需要先 fetch, git fetch --all

git pull == git fetch + git merge

git rebase 最常用的作用是 向别人的仓库贡献代码的时候

打个比方， HEAD在branchX上面

git rebase branchY, 那么意思是，以branchY为基底，把branchX上面独有的提交在branchY上面重新应用一遍，同时把branchX的指针位置，移动到rebase过程中最后一次提交上面。

git rebase --onto branchX branchY branchZ

把branchZ上有而branchY没有的应用到branchX上面

git rebase branchX branchY

rebase变基之后，可能需要使用-f推送

问题： 对提交进行sha1校验和计算包含哪些东西？

默认配置 pull 使用rebase : git config --global pull.rebase true

书签：在p90页，因为rebase已经推送的提交， 导致和其他同事尴尬的事。

在p91页提出了解决办法

Git分支这一章节结束！！

章节：分布式Git

git工作模式：

集中式工作流

集成管理者工作流

63

继续看分布式Git这一章

书签： p116, 提交的信息格式，不只是git commit -m 'XXX', 还可以写的更详细一点

\-

问题：git fetch origin 会抓取 origin所有的新提交吗？包括所有的分支？

知识：引用规格是什么？

答：关于refs的，是关于remote某个仓库的配置，应用在fetch中。 用于指定每次 运行

git fetch origin时拉取哪些分支，默认拉取所有分支。

git remote add remoteX，会在 仓库里的 .git/config下面写入详细信息

远程引用的全称是 refs/remotes/origin/mater, 简写为 origin/master

知识：--amend可以删除或加入在暂存区的文件，而git add和git rm都是修改暂存区的文件，但是这会修改commit的Sha1，如果推送了就不要这么做了，会造成麻烦！！

知识：关于如何命名想贡献代码的仓库呢？可以起名为origin,但是你没有推送代码的权利，你可以在fork一个，并且命名为myfork.

知识：关于两个分支如何关联的相关命令，有以下：

\- git push -u

\- git checkout -b branchX origin/branchX

\- [branchX]: git branch -u origin/branchX

\- git branch -u origin/branchX branchX

知识：如果想向一个仓库remoteX贡献代码，fork了一个仓库MyFork, 并且拉取到本地，基于master的C1开创一个本地功能分支FeatureA, 如果remoteX/master往前移动到了C2，如何申请pr呢？答案是基于remoteX/master变基，那么就可以解决冲突问题了。

知识：向一个公开的项目做贡献，在自己的特性分支上提交。

知识：如果有两个已经分叉的分支branchX和branchY, 如何查看branchX有而branchY没有的分支？写出用到的命令

git log branchY..branchX
note: 两个点不是三个点。

等同于 git log branchX --not branchY

知识： git diff master...iss1 比较iss1新加入的东西，找到和master分叉的祖先节开始计算。

比较两个commit之间的区别，使用 git diff commit1 commit10



维护项目

-在 特性分支中工作

分支命名规范 贡献者ID/分支名

其他:创建分支而不立即切换 git branch newbranch basedbranch(local or origin/branchX)

-应用来自邮件的补丁，跳过

-检出远程分支 没东西

-确定引入了哪些东西 

知识:git log branchx..branchY 很好理解，从branchx到branchY,字面理解是，branchx了落后，branchY靠前

替代语法， git log branchY --not branchX

git merge-base branchX branchY 查看这两个分支的交点

替代语法 git diff branchX…branchY

-将贡献的工作整合进来

--合并工作流:merge就完了

-大项目合并工作流:没东西

-变基与拣选工作流: git cherry-pick commitid

-rerere:没看懂

-为发布打标签:没看懂

-生成一个构建号:无用

-准备一次发布:不看

-制作提交简报:有点意思，下来细看

-总结:本章完结



\#Github

Tmp GITHUB学习

-:章节介绍:看完

-账号创建:看完

-SSH访问:学会

-头像:看完

-邮件地址: 看完

-两步验证:看完

-对项目做出贡献:正在看

-fork 项目:看完

-Github 流程:看完

-创建合并请求: 看完: 可以创建一个新的有含义名字的分支,然后在这个分支上创建 pr申请拉取, 基于github 的可视化网页是非常方便的.

-利用合并请求:看完

-合并请求进阶:有子项

-将合并做成补丁:翻译的抠脚,没看懂.

-与上游保持同步:没看懂

-markdown:

\```Python

\```

-维护项目:

-创建新的版本库:没东西

-添加合作者:添加 collaborator

-管理合并请求:

-邮件通知:

-在合并请求上通知:

-合并请求引用:看不懂

-合并请求之上的合并请求:看不懂,翻译的狗屎一样

-提醒和通知:没东西

-通知页面: 没啥东西

notification-center

-网页通知: 没东西

-邮件通知: 无聊

-特殊文件:无聊

-README: 有点提示

可以是任何格式,只要可读,就会渲染

-CONTRIBUTING: 有点帮助

在提 PR 的时候有用

-项目管理:没卵用

—改变默认分支:没卵用

—移交项目:没卵用

-组织管理:没卵用

—组织的基本知识:

可以把项目挂在组织下

—团队

可以对不同仓库有不同的权限

—审计日志:没卵用

-脚本 Github:完全不感兴趣

 

 

 

Git 工具

*选择修订版本

**单个修订版本

**剪短的 sha1:没意思

**分支引用:无用

探测分支的 头 rev-pare branchX

**引用日志:

只在本地

**祖先引用:

~和^

**提交区间

***三点:

只存在一个分支的

*交互式暂存

**暂存于取消暂存: 垃圾玩意

**暂存补丁: -p

*贮藏

**贮藏工作:

贮藏可以在 branchX 上储藏,在 branchY 上应用..但是 stash list 上有,最好不要整这些幺蛾子

git stash 默认会把暂存区里的东西也主藏起来.

而如果—keep-index的话, 会保留待提交区里的东西, 并且切换分支也会继续带到下一个分支.

git checkout 是不管工作区干不干净的.

git stash -u 会把未跟踪的也暂存起来.

***从贮藏的创建一个分支.

git stash branch branchx

这会自动 pop,并且创建一个分支

***清理工作目录

git clean -n -d 会显示模拟删除的东西

-d 表示目录

默认会过滤符合

这没卵用

*签署工作:暂时搁置

*搜索: 作用不大,搁置

*git日志搜索:

git log -S”你要找的东西”

**行日志搜索:实用价值不大.

*重写历史

**修改多个提交历史

git rebase -i HEAD~X

*核武器即应用: git filter-branch:暂时不想看了.

 

Git 暂时学到这里, 后面的工具不用了, 感觉暂时够用.

 

 67

到此为止,我感觉已经基本够用了.

我将暂停 Git 的学习.

 

一.  在一台新电脑上用git应该干哪些事?

答: 应该配置自己的user.name, user.email, 

配置一些命令缩写, 方便自己使用. 比如 git config --global alias.l "log --color --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

<br>

二. How to view the git user.name?

<br>

三. git log 是做什么用的?

答: 不知道, 不过当一个仓库没有提交的时候,  输入 git log 命令会提示如下:

\```

$ git log

fatal: your current branch 'master' does not have any commits yet

\```

<br>

四. 问:git branch 命令是干嘛的?

答: 查看当前版本的. 详细的解释参见 https://git-scm.com/docs/git-branch#_description

<br>

五. 如何获取帮助?

答: git 子命令 --help, 在windows下使用 git bash for windows, 会自动打开默认浏览器并且加载html文档, 可读性很高.

还可以参看官方文档  https://git-scm.com/docs, 还可以看廖雪峰的git教程,  https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000

<br>

六. 如何把本地写了很久的仓库推送到github上面去?

答:https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000 可以找到答案, 步骤是在github上新创建一个仓库, 关键是不要在远程初始化, 否则需要处理冲突. 然后在本地 git remote add origin XXXX, 然后git push -u origin master, 就会把本地仓库完全推送到远程去.

<br>

七. git diff的格式是咋样的？

答: 应该是和linux下的diff格式一致的.

<br>

八. 版本回退是什么命令？（2）git log和git reflog有什么区别？

答: git reset --hard 版本号或者 head∧  （2）todo

<br>

九. 从暂存区撤销一个文件的命令是什么？

答： git checkout -- filename

\# git查看

看历史

\- git log pretty=oneline

\- git reflog

ref log 详细log

\### 查看当前状态

git status

\# 版本控制

\### 版本号

\- HEAD：当前版本， HEAD^: 前一个版本， HEAD^^ 前两个版本

\### 版本选择

git reset --hard 版本号

[从版本库删除]

\# 针对已经加入版本库的文件, 

git rm filepath # 删除动作处于缓存区

git rm --cache filepath # 从缓存区里删除, 但是保存文件.

\# 参考 https://blog.csdn.net/GW569453350game/article/details/50956059

[从stage区回退]

\# git add 回退

git reset HEAD filepath # 保存源文件, 但是从暂存区删掉

[查看某一个文件的提交历史]

git log -- filepath





 





@git读物

https://gist.github.com/yisibl/8281454 





[[ 廖雪峰的git教程 ]]



[ 时光机穿梭 ]



@难点

diff命令和git diff

diff命令的格式和标记是什么意思？



@提示

git log可以查看提交历史



@疑点

git log和git reflog有什么区别？



@重点

git reset 

git reset HEAD^可以回退一个版本

HEAD必须大写



@提示

版本号最短需要4位



@？

git checkout -- readme.txt

git reset HEAD <file>

git rm

git commit







[ 远程仓库 ]

ssh-keygen -t rsa -C “youremail@example.com"

git remote add origin git@github.com:michaelliao/learngit.git

 git push -u origin master

使用https除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用ssh协议而只能用https。

Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。



















Commit管理

\# 改 BUG 流程

cherry-pick 介绍 https://www.jianshu.com/p/08c3f1804b36 

修复流程完整描述 https://blog.csdn.net/treesky/article/details/50126387 



\# undo git pull

git reset --keep HEAD@{1}

https://stackoverflow.com/questions/5815448/how-to-undo-a-git-pull/5815626



\# 文件代码含义

https://blog.csdn.net/u011623532/article/details/46692937



git add filename ；

git add -A 会把所有修改添加到缓存区

git add -p, git checkout -p 添加到缓存区与删除修改

-p 是--patch， 批，块的意思





git reset HEAD filename， 

git reset HEAD 会清空缓存区，



git commit -m’注释内容’

git commit --amend 修改最后一次没有推送的提交的注释



git checkout -- filename 恢复到最近一次commit 或者add状态



git rm --cache .idea/workspace.xml 从缓存区里删除, 但是保存文件.

如果git rm filname后，想反悔， git checkout -- filename 撤销删除

\### 撤销修改

！QUESTION 如果一个文件既加入了缓存区， 又修改了工作区？如何恢复到最初的版本？

ANSWER： 先丢弃缓存区的东西，git reset HEAD filename， 再 git checkout -- filename， 顺序不能反。

git checkout(add) -p filename

git log --pretty=oneline filename





reset 是 commit 的反义词, 

commit 使指针向前移动一次,  reset 则相反

reset --soft 只移动版本库的指针, 不移动待提交区和工作区

reset --mixed 移动版本库的指针和修改待提交区, 不改变工作区

reset --hard 则会修改所有.



其他

\# 查看一个文件的作者

https://www.cnblogs.com/flyme/archive/2011/11/28/2265899.html



git diff HEAD -- read.txt



\# display unicode

git config --global core.quotePath false





Stash命令



git stash--> git stack push 把当前工作区压栈

git stash list--> 查看工作栈

git stash apply--> 把工作栈的内容和当前的分支合并，可能会起冲突，冲突的话手动修复。

git stash apply stash@{0}

另一种方式是用git stash pop，恢复的同时把stash内容也删了：







git 快捷键



git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"



git config --global alias.l "log --color --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"



理解提示：alias是config的自命令

git config alias.lg



superlog = log --color --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cd) %C(bold blue)<%an>%Creset %ae ' --abbrev-commit --date  ='format:%Y-%m-%d %H:%M:%S'





分支管理

git branch -va 远程查看 https://www.barretlee.com/blog/2014/04/30/switch-branch-in-git/ 



git checkout -b 本地分支名x origin/远程分支名x  创建本地的远程分支  https://blog.csdn.net/tterminator/article/details/52225720



\# 分支关联

git branch --set-upstream-to[简写 -u]  remote/<remote_branch> local_branch 



 另外, 在推送的时候 加上 -u 也可以建立关联

git push remote localbranch:remotebranch 推送,如果远程分支不存在,创建





git checkout -b 分支名 某个版本号, 为某个历史版本建立一个分支

git branch -d dev

git merge <name>



git branch -vva可以查看远程分支，本地分支， 远程分支和本地分支的关联，本地分支落后了远程分支几个版本等等。





rebase



git pull --rebase origin dev



都相差了几百个commit了还去做rebase的是傻逼！rebase只适合相差不大提交的合并。



有时候采用分支开发的模式，一个feature开一个分支，开发完毕之后合并了，这个branch就可以删了，这个时候用rebase还是不错的



刚维护完一个1年的分支 我的过程是 经常rebase 时刻保持你的代码是基于最新代码修改。解决冲突也是一个挑战，合并上线用merge 提交历史会很清晰。





推送管理

git push remote --delete remotebranch = git push remote :remotebranch 删除远程分支

命令详解 https://blog.csdn.net/sky1203850702/article/details/41344131 



\# git push 回退

https://blog.csdn.net/jeffasd/article/details/51736569

远程关联

git remote -v

删除 git remote rm remote_name

添加远程 git remote add origin git@github.com:notfresh/wechat_miniapp_mytododemo

\# git 从本地分支推送

现在本地创库, 开发,然后推送到远端

当出现这种错误: 

git无法pull仓库refusing to merge unrelated histories

解决办法是: git pull origin master --allow-unrelated-histories



 

\# 我在本地建了一个仓库



我在本地建立了一个仓库, 不停的提交代码, 写着写着我觉得有必要提交到线上去了. 



\1. 于是, 此时, 我在github上面建了一个仓库. abc



\2. 我把github仓库和本地仓库关联, 第一步, 初始化远程仓库, 提交一次(必须的, 否则没有分支, 就没法建立关联)



\3. 我在本地仓库使用命令 git remote add origin git@github.com:GITHUB_USERNAME/abc.git ( 这种地址表明使用git协议, 推送不必使用密码, http协议推送需要使用密码, 使用git协议需要使用ssh配置, 这里就不多讲了)



\4. 我从本地拉取远程仓库 git pull --rebase origin master --allow-unrelated-histories



\5. 我把本地的master分支和远程的master分支关联起来. 使用以下命令: 



git branch --set-upstream-to[简写 -u]  remote_name/<remote_branch> local_branch , (提示, 远程仓库在前, 本地仓在后, 顺序是固定的)



在这里, 我写 git branch -u origin/master master, 于是就建立了关联.



\6. 我向远程推送代码. git push.







打标签



git tag v1 创建标签 git tag -d v1 删除标签



git tag v1 commitid(5位或者7位)

\## 查看标签 



git show tagname

git tag 查看所有标签

git show commitid



# Github知识

## 如何提一个PR？

进入pr，new pr

 

# 为什么阅读软件是可行的？

因为软件遵循一定的体系结构和设计模式，采用模块化思路，采用面向对象的思路，所以相对独立的功能是可以被理解的。

但是也不能着急，因为一个开源软件的创作是非常辛苦的，所以不要以为可以凭借自己的摸索在短期时间内搞懂全部知识。



# CJson学习笔记



# 给力仓库

github的给力仓库

https://mp.weixin.qq.com/s/OD0AxM1j41M04bOM3k20Og





# 参考

[1]如何使用 GitHub？ - 腾讯技术工程的回答 - 知乎 

https://www.zhihu.com/question/20070065/answer/1174997617

[3]和逛知乎、刷微博一样高效使用 GitHub - 程序猿杂货铺的文章 - 知乎

 https://zhuanlan.zhihu.com/p/61172248

[7]程序员宝库,开源社区GitHub到底该怎么玩 |如何玩转Github 

https://www.bilibili.com/video/BV1d4411L7Jk/

关键词：使用GitHub，compare、project、wiki、insight、 

感受：0基础人的人看的

[8]视频演示如何玩转一个开源项目 |如何运行+如何读代码 |顺便讲讲IDE

https://www.bilibili.com/video/BV1y4411p74E

关键词：跑起来、idea、拆分、阅读源码调试、halo、修改自定义、springboot、gradle(json)、Import、auto-import、src-main-java-application、调试



**[9] HelloGithub**

**https://hellogithub.com/**



[10]如何轻松阅读 GitHub 上的项目源码?

https://mp.weixin.qq.com/s/suBaNVG6S18mv06owccRPw









[11]最值得学习阅读的10个C语言开源项目代码

https://blog.csdn.net/hackerwin7/article/details/40864551



[12]有哪些轻量级适合阅读的优秀 C++ 开源项目？ - Flyer的回答 - 知乎 

https://www.zhihu.com/question/40131963/answer/90966253



[13]有哪些轻量级适合阅读的优秀 C++ 开源项目？ - 码云 Gitee的回答 - 知乎
https://www.zhihu.com/question/40131963/answer/249330962



[14]写给初学者的C语言源代码阅读指南--书籍介绍

https://book.douban.com/review/6512809/



[15]如何高效有效的阅读源码？

https://mp.weixin.qq.com/s/Tt-SQR6NCEtLAgzviopiLA



[16] Tinyhttpd的中文文档

https://github.com/EZLippi/Tinyhttpd



[17]**Tinyhttpd**官网

https://sourceforge.net/projects/tinyhttpd/



[18]sqlite 源码解读

https://huili.github.io/sqlite/architecture.html



[19]Java开源项目推荐

https://www.bilibili.com/video/BV1rb41157Rk



[20]Flask语言阅读

https://jiajunhuang.com/articles/2016_09_15-flask_source_code.rst.html

[22]Git 同步fork 拉取远程仓库代码

https://blog.csdn.net/wzy4072/article/details/79628659

[23]使用 git upstream 从其他远程仓库同步分支

http://jalan.space/2019/05/28/2019/git-upstream/





[2]给自己点时间再记记这200条Git命令 - 爱前端不爱恋爱的文章 - 知乎 

https://zhuanlan.zhihu.com/p/137194960

[4]如果你觉得学习 Git 很枯燥，**那是因为你还没玩过这款游戏**！ - GitHub Daily的文章 - 知乎 

https://zhuanlan.zhihu.com/p/134346782

[5]这才是真正的Git——Git内部原理揭秘！ - 腾讯技术工程的文章 - 知乎 

https://zhuanlan.zhihu.com/p/96631135

[6]工作流一目了然，看小姐姐用动图展示10大Git命令 - 机器之心的文章 - 知乎 

https://zhuanlan.zhihu.com/p/132573100

[11] cherry pick的用法

http://www.ruanyifeng.com/blog/2020/04/git-cherry-pick.html

[21]我用四个命令，总结了 Git 的所有套路

https://mp.weixin.qq.com/s/VdeQpFCL3GGsfOKrIRW6Hw

[24]图解git git diff的用法

http://marklodato.github.io/visual-git-guide/index-zh-cn.html

