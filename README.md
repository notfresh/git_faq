# Git FAQ

![git-faq](https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/git-faq-2450018.jpg)

[![standard-readme compliant](https://img.shields.io/badge/standard--readme-OK-green.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

先吐个槽：

git的命令很难记.  
这么多命令要记死人啊!!  
**尼玛, 一会这个参数在前, 一会那个参数在后, 根本记不住啊, 现在记住, 过一会又忘了...**   
真的不好理解, 就不能使用统一的格式和参数吗.  
文档也说不清楚啊.  
或者看不懂啊.  
怪我菜喽.  
git的入门是真的难.  
命令多的一匹, 又不好找识记规律.  

毫无疑问, Git是有它坑爹之处，但是Git 又很强大, 可以多人合作和版本管理，让人又爱又恨！！  


所以！！我写了这篇教程来帮助看到的同学学习 Git 命令。

 本教程 开始书写于 2019-06-07 17:28:19. 历经多次修改和整理

**还有一部分没有完成，持续更新优化中。**



## 目录

- [学 Git 的误区和正确姿势](#学-Git-的误区和正确姿势)
- [优秀的教程和文档](#优秀的教程和文档)
- [快问快答](#快问快答)
- [Git 的关键概念](#Git-的关键概念)
- [Git 高频命令](#Git-高频命令)
- [Git 低频命令](#Git-低频命令)
- [存疑知识](#存疑知识)
- [维护者](#维护者)
- [如何贡献](#如何贡献)
- [参考文献](#参考文献)
- [如何规范你的commit](#如何规范你的commit)
- [tricks](#tricks)
- [Licence](#licence)
- [github国内加速方法](#github国内加速方法)


## 学 git 的误区和正确姿势 

我犯过很多错误，现在就来盘点一下自己踩过的坑和总结的经验。

### 误区

1 妄图成为 Git 专家，初心只是学会使用 Git

2 死记硬背命令，转头就忘

3 盲目复制网上的命令，不知道其原理，不知道正确的自学方法



### 正确姿势

1 首先要明白，Git 只是一个工具。真正能把工作做好的基础是内容，没有 Git，每个版本复制一份也可以。  

2 先学个大概，细节和原理再慢慢了解

3 学会去查**官方文档**和**自带命令行帮助**（使用 git --help）

    使用帮助系统, 如果你对 git add 或者 git log 命令不熟悉, 你可以使用 git log --help, 或者 man git 命令. 这是 Linux 的本地文档帮助系统.  
    
    使用官方在线文档系统. 网址是 https://git-scm.com, 点击去打开 documentation, 里面有详细的内容, 文档分为三个部分, reference, book( ProGit book), videos.  
    分别指的是 经典的文档系统, 这里面全部用英文写的, 里面有对于各个子命令的解读和各种参数的详细说明, 关于 Git 的一本在线书籍, 阅读起来更友好, 还有就是对于 Git的介绍视频. 可能视频暂时无法观看, 估计是用 Youtube 播放的(需要翻墙). 
    
    我重点推荐那本 Git 的书（待会给出来链接） . 里面有各个语言版本的, 其中中文的链接在这里, https://git-scm.com/book/zh/v2 , 需要提的一点的是, 中文的翻译质量稍微低了一点, 如果英语好的同学自己去看英文.

4 使用命令行的时候注意命令的输出信息, 在 shell 里面, 输出的信息是非常重要的的, 出了问题或者有疑问, 提示信息都写的比较清楚, 当然要英语好一点. 在使用 Git 的时候, 每个命令, 都会有相关的操作提示和说明,要好好利用 Git 的提示信息.



5 去优秀的学习网站查找资料

在 Github 上的一些仓库里有的 Git 学习资料.

去博客园 https://cnblogs.com 里查看好一点的文章.

最后还有去 stackoverflow.com 或者知乎等问答网站找自己想要的答案.

引用别人说的句话，**对于工具的学习，我认为应该多做减法，只捡最有用的学，那些奇技淫巧不学也罢，应该把时间投入更有价值的事情中**。



## 优秀的教程和文档

我写的文档并不如一些前辈们和其他优秀博客主写的好，所以我建议优先去看这些文档。



[1]  ProGit, 一本Git官网推荐的书籍。

传送门：[Git官方推荐书籍](https://git-scm.com/book/zh/v2), 本仓库也保存着

推荐理由：这本书是中文的，也有对应英文的, 这本书是我见过**最好的Git学习资料**，我学习Git走了很多弯路，但

是我希望后面的同学们可以在入门之后去阅读这本书，但不推荐直接阅读这本书，因为内容有点多。  



[2] 高频使用的 Git 清单
http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html  
推荐理由：阮一峰出品，必属精品



[3] 廖雪峰的 Git 教程.

传送门：[廖雪峰的Git教程](https://www.liaoxuefeng.com/wiki/896043488029600/896202815778784)  

推荐理由：

网上的教程很多, 但是写的少的却不多. 就我个人而言, 如何形象的感受 Git 在工作中的应用, 我推荐去看廖雪峰的 Git 教程.  

因为我在学习 Git 的时候, 刚开始看了一些别的网站的教程, 都是一些支离破碎的命令和比较浅的没有系统讲述 Git 使用的, 而且很多教程是互相抄袭的, 你抄我, 我抄你, 特别是 CSDN 上, 批评一下 CSDN 对于创作者的版权保护不够, 现在乌烟瘴气的, 到处是抄袭的文章.  

 **这个教程内容丰富, 生动形象, 白话为主, 学起来相对 Easy, 我觉得三天或者一周左右可以吃透这个教程**.  

**但是， 看廖雪峰的教程够吗?**

我认为是不够的. 原因是: 廖雪峰的教程只说了具体的操作, 却并没有说透里面的原理或者工作模型. 也许本身原理比较难说透, 但是, 我认为这个东西是非常重要的, 理解了才能更好地记忆. 知其然而不知其所以然, 特别是对于 Git 这个常用的工具, 是极其不利于工作的.

廖雪峰的教程不能完全满足其他高级需求, 有的东西, 我认为没有讲清楚, 需要阅读别的材料补充和提升.



[4] 四个命令总结 Git 的套路

传送门：https://mp.weixin.qq.com/s/VdeQpFCL3GGsfOKrIRW6Hw  

推荐理由：labuladong的博客, 简单粗暴，魅力自成体系。



## 快问快答

### 问: 这个教程是写给谁看的?
 答: 写个对 Git 了解不多的人看的, 或者 Git 的新手.

  

### 问: 这个教程我能学到什么?  
 答: 可以学到关于 Git 的基础入门知识和工作实用技巧，以及一些其他教程没有说透的知识点。所以，本教程可以是上文章节“优秀的教程和文档”的补充，你可以先去阅读那些教材，等你有需要更多的文章或者补充细节，或者查漏补缺，再回过头来阅读本文。

  

### 问: 需要知道 Git 和其他版本控制工具的区别吗?  
答: 不是必须知道的, 你至少需要了解 Git 就好了, 我认为做比较这种事需要了解或者熟悉比较对象. 如果你熟悉 Git或者 SVN, 或者 CVS, 还有很多别的版本管理工具, 你心里大概有数。

我认为“比较”这件事本身是需要对被比较的事物都有一个了解，帮助用户从旧的迁移到新的，如果你不了解被比较的对象，就不需要知道区别，反而省去了历史包袱。

  

### 问: Git 应该是用命令行还是界面工具?
  答: 我认为各有优势. 命令行工具是程序员的传统工具, 面对黑乎乎的界面, 你需要从头开始记得很多命令, 需要有一个适应的过程.  
  但是命令行因为不需要构建 GUI(用户界面), 开发工作量小, 可以接受的参数多, 使用灵活, 所以功能非常的强大. 缺点刚刚也说了, 就是要记住很多命令.   
  命令行还有一个缺点, 就是阅读体验不好, 尤其是比较两个文件差异的时候, 可读性比较差.   
  而 GUI 则操作简单, 非常的人性化, 上手很快, 阅读体验好.  但是实现的功能是命令行的子集.  
  用哪一种, 看自己的与需要, **我本人是两者结合着用**, 我喜欢的 GUI 是 Github出品 的 Git 本地客户端 [GitHub Desktop](https://desktop.github.com/).



## git 的关键概念

### git 的工作模式

 git 有三个区, 历史版本区(或者已经提交区), 待提交区(暂存区), 工作区. 还有其他的名字, 英文名分别叫 repository, index 或者 staging area, working directory. 无论他们叫什么名字, 他们的本质都一样的。

我们通过图文详细说明一下：

Git 主要的目的是通过操纵这三棵树来以更加连续的状态记录项目的快照。

<div><img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618092908203.png" alt="image-20200618092908203" style="width:50%;margin:0" /></div>



让我们来可视化这个过程：假设我们进入到一个新目录，其中有一个文件。 我们称其为该文件的 v1 版本，将它
标记为蓝色。 

1 现在运行 git init，这会创建一个 Git 仓库，其中的 HEAD 引用指向未创建的分支（master 还
不存在）。我们创建一个 file1.txt，那么现在仓库的情况是这样的：



<div>
	<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618093126098.png" alt="image-20200618093126098" style="width:50%;margin:0" />
</div>



此时，只有工作目录有内容。



2 **现在我们想要提交这个文件，所以用 git add 来获取工作目录中的内容，并将其复制到索引区中**。

<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618093242914.png" alt="image-20200618093242914" style="zoom:50%;margin:0" />



3 **接着运行 git commit**，它会取得索引中的内容并将它保存为一个永久的快照，然后创建一个指向该快照的提交对象，最后更新 master 来指向本次提交。

<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618093605400.png" alt="image-20200618093605400" style="zoom:50%;margin:0" />



**4** 现在我们想要对文件进行修改然后提交它。 我们将会经历同样的过程；首先在工作目录中修改文件。 我们称其
为该文件的 v2 版本，并将它标记为红色。
<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618093724948.png" alt="image-20200618093724948" style="zoom:50%;margin:0" />

如果现在运行 **git status**，我们会看到文件显示在 “Changes not staged for commit,” 下面并被标记为红
色，因为该条目在索引与工作目录之间存在不同。 接着我们运行 **git add** 来将它暂存到索引中。

<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618093847326.png" alt="image-20200618093847326" style="zoom:50%;margin:0" />

此时，由于索引和 HEAD 不同，若运行 git status 的话就会看到 “Changes to be committed” 下的该文件
变为绿色 ——也就是说，现在预期的下一次提交与上一次提交不同。 



5 最后，我们运行 **git commit** 来完成提交。

<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618094027488.png" alt="image-20200618094027488" style="zoom:50%;margin:0" />



现在运行 git status 会没有输出，因为三棵树又变得相同了。
切换分支或克隆的过程也类似。 当**检出(checkout命令)**一个分支时，它会修改 HEAD 指向新的分支引用，**将索引 填充为该次提交的快照**，然后将 索引 的内容复制到 工作目录 中。



为什么要有三个区呢（工作目录、暂存区、提交历史区）？

工作目录和提交历史我们可以理解，提交历史也可以理解，但是为什么要有暂存区？直接从工作目录到提交历史不可以吗？如果没有暂存区，我们工作目录的所有修改应该都要一次全部的放入提交历史了。所以说，暂存区的存在允许了指定一部分修改作为一次提交。



最后，使用工作场景回忆一下开始使用 Git 的命令, 然后下面挑几个常用的命令来重点介绍一下.  

    1. 下载别人的仓库: git clone 仓库地址  
    2. 创建自己的仓库: mkdir directory_name(名字自取) ; cd directory_name; git init
    3. 配置自己的 ID 和邮箱, 方便在开发中协作
       git config --global user.name notfresh  
       git config --global user.email notfresh@foxmail.com
    4. 查看项目的历史: git log, 这个命令, 我认为是我使用频率最高, 最重要的命令之一, 我认为必须熟悉使用这个命令.
    5. 根据任务或者自己的想法, 创建一个文本文件, 然后准备再本地提交, git add new_file.  
       git add 也是个高频命令.
    6. 我想看一下仓库的情况, 我决定使用 git status, 根据提示, 我清楚的知道了哪些文件修改了.
    7. 写好了自己的任务或者想法, 我提交一下, 使用 git commit -m '提交说明'.
    8. 我觉得应该看一下当前的历史, 我使用 git log 再次查看.
    9. 我觉得我应该把我写的东西拿给别人看了, 我使用 git push 命令. 关于上传代码, 还有多处细节, 我就大致一提.
    10. 有别的同事也提交了代码, 我赶紧去看看他写的啥, 我使用 git pull origin, 下载了他写的代码.
    11. 循环 步骤5-10 
    12. 当然, 还有很多意外和惊喜, 在工作中, 所以我必须使用别的命令来处理代码版本控制问题和别的同事的协作问题.



### git 中的提交  



在 git 中, 提交是最核心的概念, 提交涉及到很多的底层概念, 我知道的也不多, 因为我也不是专门研究 git的, 如果我专门去研究, 平时又用不到, 那么很快就会忘记。
一次 git commit 就是一次提交, 会生成一个 40 位长的 16 进制 sha1编号, 根据文件大小, 时间,等多方因素生成的可保证唯一的一哈希字符. 

一次提交记录了提交时间,提交人, 提交的标题, 详细的消息, 等等等等...    



### git 中的分支

使用 git branch BRANCH_NAME [commit_hash | branch name | tag name] 来创建分支。如果不填写 commit_hash | branch name | tag name，就会以当前的指针为参考建一个分支。

git checkout -b NEW_BRANCH_NAME  [commit_hash | branch_name | tag_name]   也会创建一个分支，并且理解切换到该分支上去。



### 提交和分支的关系
假设有 10 个提交, 按时间从早到晚, C1, C2,.., C10. 
有一个分支 master.  master 现在指向 C5,起点是 C1.  
在C2 的时候, 创建了branchX, 然后 branchX 目前指向 C5, 包含了 4 个分支, 那么如果删掉分支 branchX, C2~C5会被删除吗? 
不会. 因为 master 还有一段指向 C2~C5。  
再假设, 在C2 的时候, 创建了branchX, 然后 branchX 目前指向 C10, 包含了 9 个提交, 那么如果删掉分支 branchX, 哪些提交被删除?   
自然是 C6-C10, 因为包含他们的分支 branchX 已经被删除了.  
而 C2-C5 不能被删除, 因为还有 master 分支包含着它们.  



总结一下, **分支就是一段提交的区间的名称，或者说同义词**,  分支的起点呢, 是创建它的那个提交。



### git 的HEAD指针

TODO



## git 高频命令

我们经常使用到几个命令，而其他的命令相对较少，因此我们需要对这些常用的命令多多掌握和学习。

git add、git status、git log、git commit，git checkout, git push等命令是比较常见的。



### git add命令和 git status 命令

git管理下的文件有几个状态，如下图所示，

- 没有跟踪的状态
- 未修改状态
- 修改状态
- 暂存待提交状态



![image-20200618092039831](https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618092039831.png)

图 来自 ProGit



我们最常用的几个命令之一，第一个就是 git add命令了。

git add 实现了 untracked->staged 和 modified->staged 的阶段。

**补充一个实用小技巧，**如果一次修改太多，想在暂存的时候查看修改了哪里，可以使用 `git add --patch [FILE_NAME]` 或者 `git add -p [FILE_NAME] `  命令一块一块的暂存。



### git commit 命令

正如我们前面关键概念所讲到的，一次 git commit 形成了一次提交历史，使用一个非常长的哈希码表示，形式是一串字母加数字，这个哈希码根据文件的大小，创建提交的时间，提交者信息等等综合生成，几乎不会有哈希冲突。即便是不同的人在不同的电脑上提交，生成的哈希码也是不同的，所以可以保证多人开发的时候的全局唯一性。

git commit -m COMMIT_MASSAGE

其中，COMMIT_MASSAGE 应该尽量使用动宾短语，简练而清晰。

如下，一个 commit 的详细信息

```
commit b8b2b4985abf4c132abbfea3c5ffcf23e97db9ef (HEAD -> master)
Author: notfreshmbp <1195056983@qq.com>
Date:   Fri Jun 26 19:35:51 2020 +0800

    add 5.txt

    This is a test message to show people that this is the detailed message.

diff --git a/5.txt b/5.txt
index e69de29..58c9bdf 100644
--- a/5.txt
+++ b/5.txt
@@ -0,0 +1 @@
+111
```



如果使用 git commit 而不带 -m 参数，那么会进入详细提交信息的编辑页面，默认的编辑器在 MacOS 和 Linux 下是 Vim 编辑器，第一行是提交信息，第二行是空行，（包含）第三行往下是详细说明信息，如果本次提交需要附加的信息特别多，应该在编辑器里详细写明。

![image-20200626193807855](https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200626193807855.png)

![image-20200626193636486](https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200626193636486.png)

`#`开头表示的注释信息会被自动忽略掉。

如图所示, 使用 `git show  HEAD`命令或者 git show COMMIT_ID， 即可查看一次提交的详细信息。

> git show COMMIT_ID 命令可以查看一次提交的详细信息。

![image-20200626193849481](https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200626193849481.png)



哈希码字符串太长了，非常的不好记，**实际上一般最少只需要前4个字符即可表示**（如果本次提交前4个字符和其他提交哈希码相同，再加字符直到不重复为止，也即是最短不重复前缀原则）。

例如 我可以使用 `git show b8b2` 来代替 `git show HEAD `



###  git log 命令 

git log 查看一个文件的提交历史, 也可以查看整个仓库的的提交历史。

毫不夸张的说， git log 的命令是我们使用最高频的命令之一。然而 git log 本身输出的格式不是我们想要的，如图所示：

```
commit b8b2b4985abf4c132abbfea3c5ffcf23e97db9ef (HEAD -> master)
Author: notfreshmbp <1195056983@qq.com>
Date:   Fri Jun 26 19:35:51 2020 +0800

    add 5.txt

    This is a test message to show people that this is the detailed message.

commit 4e7f6e354179c19e5adfff6515a2982f732c02e2
Author: notfreshmbp <1195056983@qq.com>
Date:   Thu Jun 18 10:42:32 2020 +0800

    update 1.txt
```



展示了太多没用的信息，当我们想要查看更加详细的、可视化的信息的时候，我们可以在终端执行如下操作：

```shell
git config --global alias.l "log --color --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s%Creset %Cgreen(%cd) %C(bold blue)<%an>%Creset' --abbrev-commit --date='format:%Y-%m-%d %H:%M:%S'"
```

这条命令为 git log 配置了一个别名，附带了很多的参数，我们可以使用 git l 查看效果：

```
 ➜  git-test git:(master) git l
 
* b8b2b49 - (HEAD -> master) add 5.txt (2020-06-26 19:35:51) <notfreshmbp>
* 4e7f6e3 - update 1.txt (2020-06-18 10:42:32) <notfreshmbp>
* 6bee770 - (newb) branch split (2020-06-18 10:33:23) <notfreshmbp>
* 0222aca - create 5.txt (2020-06-18 09:59:57) <notfreshmbp>
* 95e0daf - (b4) create 3.txt (2020-06-18 08:54:08) <notfreshmbp>
* ec694fd - (b3, b2) create 2.txt (2020-06-18 08:43:01) <notfreshmbp>
* c1a68d9 - create 1.txt (2020-06-18 08:42:29) <notfreshmbp>
```

具体的参数可以去官方该网站或者 ProGit 上查找对应配置信息，方便个性化设置。

我们还可以给 git log  增加一个参数， git log FILE_PATH, 以此查看某个文件的提交信息。

此外，git log 还支持 grep 命令查询提交信息（只支持提交信息查询），使用 `git log * --all --grep=KEY_WORD` 可以搜索某些提交

此外，git log 还支持 其他特定字段的查询，比如根据作者查询`git log --author=AUTHOR_NAME`。



### git branch 命令

branch命令如下：

git branch NewBranch  [FromBranch] (或者commitID), 

什么是分支, 有人说,分支, 就是 这个命令创建的. 我们需要深入的理解一下, 不能光知其然而不知其所以然. 分支, 就是一个区域, 有起点, 有终点, 起点一个 CommitA, 终点 CommitB. 



- 问: 远程分支怎么用? 如何查看远程分支? 
  TODO  
  使用命令 `git branch -v`和 `git branch -vv`, 当然这看的都是离线版的, 如果想拉取远程最新的, 使用`git fetch REMOTE`, 然后再执行.    
- 问: fetch 命令是什么?   
  拉取远程提交.  
- 什么是 cherry-pick 命令?  
- 什么是 git clean 命令?  
  使用场景: 如果不小心给工作区加了很多垃圾, 想要批量删除这些还没暂存的垃圾, 就应该使用git clean命令.  







### git checkout 命令是什么? 

答: 想要搞懂 checkout 命令,首先要理解分支的概念.  

大名鼎鼎的 master 分支, 我们都熟悉, 自然起点是最早的那个提交, 而终点, 我们可以使用 git show master 查看master的终点.  
我们先搁置这个问题, 继续往下看.

$ git checkout 1a 

> 1a 表示一个分支，或者一个 commit上面的打的标签

如下：这就是 checkout 命令的工作原理

<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618095257616.png" alt="image-20200618095257616" style="zoom:50%;margin:0" />

#### 新增的文件和修改的文件的区别对待

新增的文件，没有被保存到历史区，无论怎么切换分支，都是可以的，但是如果修改了一个文件A，在切换分支前，应该提交或者暂存（stash命令）修改的内容。

否则出现两种情况，如果切换到的那个分支没有修改文件A，那么可以顺利切换过去，否则就会提示，切换分支会导致修改被覆盖，从而切换失败。



### git reflog 命令

可以查看HEAD指针的移动情况。



### git reset 命令

git reset 命令是一个非常复杂、让人迷惑、危险的命令，下面来详细解释一下。

在以下情景中观察 reset 命令会更有意义。

继续上面演示 Git 工作流程的例子，假设我们再次修改了 file.txt 文件并第三次提交它。 

现在的历史看起来是这样的：

<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618100418746.png" alt="image-20200618100418746" style="zoom:67%;margin:0" />

我们看到有3个提交，从早到晚分别是 eb43, 9e5e, 38db， 现在指针指向 38db。

**第 1 步：移动 HEAD**
reset 做的第一件事是移动 HEAD 的指向。reset 命令移动HEAD 指向的提交。 这意味着如果 HEAD 在 master 分支上，运行 git reset 9e5e 将会使 HEAD指针指向 9e5e。

无论你调用了何种形式的带有一个提交的 reset，它首先都会尝试这样做。 

> 使用reset的时候，如果存在回退的行为，提交历史会被擦除！这个时候，需要使用 git reflog 命令找到丢失的提交。

**使用 reset --soft，它将仅仅停在那儿。**
现在看一眼上图，理解一下发生的事情：**它本质上是撤销了上一次 git commit 命令**。 

当你在运行 git commit 时，Git 会创建一个新的提交，并移动 HEAD 所指向的分支来使其指向该提交。 当你将它 reset 回HEAD~（HEAD 的父结点）时，其实就是把该分支移动回原来的位置，而不会改变索引和工作目录。 现在你可以更新索引并再次运行 git commit 来完成 git commit --amend 所要做的事情了（见 修改最后一次提交）。

<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618101407284.png" alt="image-20200618101407284" style="zoom:67%;" />



**第 2 步：更新索引（--mixe）**默认的，不带参数的。

注意，如果你现在运行 git status 的话，就会看到新的 HEAD 和以绿色标出的它和索引之间的区别。
接下来，reset 会用 HEAD 指向的当前快照的内容来更新索引。

<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618101649341.png" alt="image-20200618101649341" style="zoom:67%;margin:0" />

如果指定 --mixed 选项，reset 将会在这时停止。 **这也是默认行为**，所以如果没有指定任何选项（在本例中只是 git reset HEAD~），这就是命令将会停止的地方。

现在再看一眼上图，理解一下发生的事情：它不仅会撤销一上次提交，还会取消暂存区的所有的东西，也就是说，**Git会用历史区的HEAD指针指向的版本内容覆盖暂存区**。 于是，我们回滚到了所有 git add 和 git commit 的命令执行之前。

第 3 步：更新工作目录（--hard）

reset 要做的的第三件事情就是让工作目录看起来像索引。 如果使用 --hard 选项，它将会继续这一步。

<img src="https://typora-1256991781.cos.ap-beijing.myqcloud.com/uPic/image-20200618102225932.png" alt="image-20200618102225932" style="zoom:67%;" />

现在让我们回想一下刚才发生的事情。 

你撤销了最后的提交、git add 和 git commit 命令以及工作目录中的所有工作。
必须注意，**--hard 标记是 reset 命令唯一的危险用法**，它也是 Git 会真正地销毁数据的仅有的几个操作之一。其他任何形式的 reset 调用都可以轻松撤消，但是 --hard 选项不能，因为它强制覆盖了工作目录中的文件。在这种特殊情况下，我们的 Git 数据库中的一个提交内还留有该文件的 v3 版本，我们可以通过 reflog 来找回它。**但是若该文件还未提交，Git 仍会覆盖它从而导致无法恢复**。

通过这一个详细的了解，我们就可以对 Git reset 命令有一个清晰的认识。



### git merge

举个例子，分支 master 含有 c1, c2, c3,共3个提交， 分支 dev 含有 c1, c2,c3, c4 共4个提交，即 dev完全包含 master，如果使用 git merge dev master, 意思就是让 master 合并 dev 分支了里的内容。merge 完成后，master也有了 c1，c2, c3,c4 共4个分支，而dev没有任何变化。这种合并叫做 fast forward, 可以理解为“快速追上”的策略。

再举个例子，分支 master 含有 c1, c2, c3,共3个提交， 分支 dev 含有 c1, c2, c4 共4个提交，即 dev 分支有包含 master 分支没有的内容，如果使用 git merge dev master, 意思就是让 master 合并 dev 分支了里的内容。merge 完成后，master也有了 c1，c2, c3, c5, 共4个分支，c5里包含着 c4 提交的内容，而dev没有任何变化。这种合并为合并了分叉内容，会自动创建一个提交，例如c5分支。

### git pull 

git pull = git fetch + git merge

git pull --rebase = git fetch + git rebase origin 



##  git 低频命令

我会就 rebase、cherry-pick、rm、



### git rebase 

 rebase 变基, 打个比方, 分支 master 包含 C1,C2,C3, 分支 branchX 包含 C2, C4, C5.  
  采用普通的merge策略, 会新建一个提交C6, 让C3, C5都指向C6. C6的内容包含master和branchX都有的内容.  
  采用rebase, 命令格式为  git rebase BASE_BRANCH TO_MERGE_BRANCH  
  在这里使用 `git rebase master branchX`就是把 C4-C5在C3后续上, 然后branchX指针指向C5, master位置不变, 也就是说分支的指向位置都没变, 只不过提交历史的形状变了.  
   如果没有冲突顺利合并, 如果有冲突解决冲突.  
  如果 只写git rebase BASE_BRANCH, 那么git就会假定当前分支就是TO_MERGE_BRANCH.  
  <br>
  总结: 什么是rebase? 变基, 变谁的基? 就拿刚才一个具体的命令来说吧, 当前分支是branchX, 执行`git rebase master branchX`, 或者`git rebase master`, 我们这么理解, 变得就是branchX的基, 基, 英语base, 我们不妨理解为起点. 重新修改branchX的起点, 之前branchX的起点是C2, 现在我们让它的起点改为C3.  



#### 什么情况下应该用 rebase?

  第一种场景:  
  如果我想手动的自己处理分支, 比如远程仓库已经更新, 我执行如下操作:
  step1: git fetch origin  
  step2: git rebase origin/master master :这句话的意思是以origin/master 为base, 把master放到origin/master的末端
  这样就可以把提交历史捋直了, 否则就会出现一次merge操作. 
  上面两句等同于 git pull --rebase: 把本地的放到远程的上面, 让本地的提交包括远程的提交.  

  > 有一种错误的rebase, 在step2, 执行 git rebase master origin/master, 因为origin/master是不可以移动的, git会自动拷贝一个提交历史放到master的前面, 这样一来, 尽管内容是相同的, 可是本地的分支包含了远程分支没有的提交历史, 中间夹了几个本地提交的分支, 就会导致无法推送. 感兴趣的不妨试一下. 



#### git rebase 合并提交

如果提交历史存在多个提交，但是感觉没必要拆解成多个，可以使用合并提交的功能进行重写历史。

重写历史的命令是 git rebase -i 截止历史hash

```
* d2c68c0 - (HEAD -> master) try randomNumber (2023-02-02 16:50:59) <notfreshmbp>
* e3895eb - rename csv (2022-09-21 14:52:32) <notfreshmbp>
* 31c85ac - (tag: v0.0.14, origin/master) update csvfile (2022-09-19 12:13:00) <notfreshmbp>
* b43d8f8 - (tag: v0.0.13) add new csv reader fix bug (2022-09-14 16:43:05) <notfreshmbp>
* 8c7135d - (tag: v0.0.12) add new csv reader (2022-09-14 16:41:06) <notfreshmbp>
* cb486e4 - (tag: v0.0.11) add csv reader (2022-09-14 16:37:54) <notfreshmbp>
```

举个例子，> git rebase 31c85ac, 命令行就会出现以下窗口，我们可以选择其中一个提交，指定特定命令，进行历史的重写。

```
  1 pick e3895eb rename csv
  2 pick d2c68c0 try randomNumber
  3
  4 # Rebase 31c85ac..d2c68c0 onto 31c85ac (2 commands)
  5 #
  6 # Commands:
  7 # p, pick <commit> = use commit
  8 # r, reword <commit> = use commit, but edit the commit message
  9 # e, edit <commit> = use commit, but stop for amending
 10 # s, squash <commit> = use commit, but meld into previous commit
 11 # f, fixup <commit> = like "squash", but discard this commit's log message
 12 # x, exec <command> = run command (the rest of the line) using shell
 13 # d, drop <commit> = remove commit
 14 # l, label <label> = label current HEAD with a name
 15 # t, reset <label> = reset HEAD to a label
```

### git fetch 命令

git fetch 命令 表示把远程仓库拉下来，但是不合并到当前分支，仅仅用作后序操作或者查看内容之用。



### git tag

git tag -m "打个标签" TagName   ===》这是轻量级的标签
git show TagName  ===>查看标签代表的提交

## 

### git diff 



另一个有用的操作是查看程序两个版本之间的区别， 以便了解改动详情。在命令行中，你
可以使用 git diff 命令进行查看。例如，执行下述命令可以查看 2a 和 2b 两个修订版本之
间的区别：
$ git diff 2a 2b

接下来, 我们看一个全能的diff示意图.

![image](https://user-images.githubusercontent.com/12556509/128114726-5ea256ba-a9bb-437d-9acf-fba1d4f3dcaa.png)

可以这么理解, git diff 的出发点是当前工作目录, 也就是你实时修改的, git diff 比较工作目录和暂存区, git diff HEAD 比较工作目录和最后提交的, git diff --cached 比较暂存区和最后提交的,
git diff branch1 branch2 比较branch2和branch1的区别, git diff commit1 commit2 比较commit2和commit1相比的变化.

### git stash

如图所示，假设如下场景，我在b4分支的编辑的时候，接到一个临时任务，那么我需要把当前的工作临时保存起来，但不提交，那么我使用 git stash命令即可。然后我切换到其他分支去工作，那我我现在的提交历史如下：

> 想要看到这种效果，配置如下：
> git config --global alias.l "log --color --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s%Creset %Cgreen(%cd) %C(bold blue)<%an>%Creset' --abbrev-commit --date='format:%Y-%m-%d %H:%M:%S'"
>
> 然后使用 git l 即可查看。 

我们可以看到 新增了两个“提交”，d341: index on b4 和 1c03 - (refs/stash) WIP

```
* b8b2b49 - (HEAD -> master) add 5.txt (2020-06-26 19:35:51) <notfreshmbp>
* 4e7f6e3 - update 1.txt (2020-06-18 10:42:32) <notfreshmbp>
* 6bee770 - (newb) branch split (2020-06-18 10:33:23) <notfreshmbp>
* 0222aca - create 5.txt (2020-06-18 09:59:57) <notfreshmbp>
| *   1c03cfd - (refs/stash) WIP on b4: 95e0daf... (2020-06-18 10:44:33) <notfreshmbp>
| |\
|/ /
| * d34156e - index on b4: 95e0daf create 3.txt (2020-06-18 10:44:33) <notfreshmbp>
|/
* 95e0daf - (b4) create 3.txt (2020-06-18 08:54:08) <notfreshmbp>
* ec694fd - (b3, b2) create 2.txt (2020-06-18 08:43:01) <notfreshmbp>
* c1a68d9 - create 1.txt (2020-06-18 08:42:29) <notfreshmbp>
```

当我其他事情工作完毕，我切换到 b4 分支，我再使用 **git stash pop**，可以把临时工作再恢复到工作区。

```
➜  git-test git:(b4) git stash pop
On branch b4
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   1.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (1c03cfd8d607a723be6d8afd270fba4d734e3b29)

➜  git-test git:(b4) ✗ git l

* b8b2b49 - (master) add 5.txt (2020-06-26 19:35:51) <notfreshmbp>
* 4e7f6e3 - update 1.txt (2020-06-18 10:42:32) <notfreshmbp>
* 6bee770 - (newb) branch split (2020-06-18 10:33:23) <notfreshmbp>
* 0222aca - create 5.txt (2020-06-18 09:59:57) <notfreshmbp>
* 95e0daf - (HEAD -> b4) create 3.txt (2020-06-18 08:54:08) <notfreshmbp>
* ec694fd - (b3, b2) create 2.txt (2020-06-18 08:43:01) <notfreshmbp>
* c1a68d9 - create 1.txt (2020-06-18 08:42:29) <notfreshmbp>

```

现在提交历史又恢复了，我们可以继续编辑了。




## 存疑知识

**1 Git 是如何保存文件的?**  

我有一个疑惑是Git 如何保存数据的, 为什么可以快速的在各个版本之间快速移动. ProGit 里面提到, Git 保存的是文件的快照, 而不是每次的修改, 所以 Git 可以实现在各个版本和分支(稍后我会解释)之间来回切换, 凭借这一点, Git 在所有版本控制系统之间独领风骚. 确实厉害, 但是直到现在为止, 我还是没有弄明白, 快照是什么, 如果一个 2M 大小的文本被修改了, 

那么它的快照有多大呢? 快照是重新拷贝一份吗, 我曾经试过, 修改一个 特定大小的文件, 然后提交, 快照非常的小, 并不是修改后的文件的再次复制.  

我并不知道快照在底层文件系统中是如何保存的, 曾经我有几个想法, 会不会是保存一份文件指针, 然后保存几个修改对象指针, 而所谓的快照就是初始文件和快照的集合, 在切换版本和分支的时候, 快速利用指针的集合拼凑成一个文件.  

快照是什么, 我如今仍然不得而知.  



## 如何规范你的commit

从公司多人角度考虑, 如何规范你的 Git Commit message

如何规范你的Git commit？ - 阿里技术的文章 - 知乎
https://zhuanlan.zhihu.com/p/182553920

## Tricks

--name-only 在 git diff 和 git show 等命令中，如果指向看文件维度的，就可以加上这个配置


## github国内加速方法

参见这个网址，非常的好用。  
https://www.cnblogs.com/july-sunny/p/13697156.html



## 维护者

[@notfresh](https://github.com/notfresh)

## 如何贡献

PRs accepted.

Small note: If editing the README, please conform to the [standard-readme](https://github.com/RichardLitt/standard-readme) specification.




## 参考文献

不错的ppt，准备下载，改造

https://www.slideshare.net/bcbbslides/introduction-to-git-and-github-72514916?from_action=save#

下载网站

https://slidesharedownloader.ngelmat.net/ 

5@ibm 

https://developer.ibm.com/zh/articles/os-cn-git-and-github-1/

5@ [4]如果你觉得学习 Git 很枯燥，**那是因为你还没玩过这款游戏**！ - GitHub Daily的文章 - 知乎 

https://zhuanlan.zhihu.com/p/134346782

5@ [6]工作流一目了然，看小姐姐用动图展示10大Git命令 - 机器之心的文章 - 知乎 

https://zhuanlan.zhihu.com/p/132573100

3@[5]Git内部原理揭秘！ - 腾讯大佬的分享

https://zhuanlan.zhihu.com/p/96631135

3@腾讯大佬的配套讲解

https://www.bilibili.com/video/av77252063

3@ [2] 高频使用的 Git 清单
http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html  

3@ [2]给自己点时间再记记这200条Git命令 - 爱前端不爱恋爱的文章 - 知乎 

https://zhuanlan.zhihu.com/p/137194960

3@ [24]图解git git diff的用法

http://marklodato.github.io/visual-git-guide/index-zh-cn.html

3@git diff的格式

https://www.jianshu.com/p/98829d4e996f

3@ [1]git - 简明指南

https://rogerdudler.github.io/git-guide/index.zh.html

3@ [2]用动图展示10大Git命令 https://mp.weixin.qq.com/s/PUUL913fig6cFfqy4OKcGA

2@ [4]Git 的 4 个阶段的撤销更改 https://mp.weixin.qq.com/s/S33W_L9-taAC-aEuHvZYPQ

2 @[6] -- 的理解

https://stackoverflow.com/a/22750480/9561380

1@ [5]Git 高级用法 https://mp.weixin.qq.com/s/LTHLKrle5mOczHKsK2k30A

1@ [3]Git使用教程：最详细、最傻瓜、最浅显、真正手把手教 https://mp.weixin.qq.com/s/g0jgzZZ0RG_-dNoBwEs16Q

3@[1] ebooks for git

https://github.com/EbookFoundation/free-programming-books/blob/master/free-programming-books.md#git

1@[21]我用四个命令，总结了 Git 的所有套路

https://mp.weixin.qq.com/s/VdeQpFCL3GGsfOKrIRW6Hw

1@[11] cherry pick的用法

http://www.ruanyifeng.com/blog/2020/04/git-cherry-pick.html

1@详解 Git 大文件存储（Git LFS） - 腾讯技术工程的文章 - 知乎 https://zhuanlan.zhihu.com/p/146683392

1@过来人告诉你，去工作前最好还是学学Git - Java3y的文章 - 知乎 https://zhuanlan.zhihu.com/p/149169595

1@给女朋友讲解什么是Git - Java3y的文章 - 知乎 https://zhuanlan.zhihu.com/p/147161045

ppt

https://www.yupengsir.com/topic/content?i=52

submodule
https://zhuanlan.zhihu.com/p/87053283

github加速
https://zhuanlan.zhihu.com/p/248356236


## 特别感谢

本文大量插图来自于 [ProGit](https://git-scm.com/book/zh/v2)， 感谢作者的辛勤创作。由于本仓库作者一个人精力有限，不能一一标注图片来源。



## License

CC4.0 自由转载-保持署名  © 2020 notfresh





