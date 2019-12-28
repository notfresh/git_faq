# 切换分支
$ git checkout 1a 
> 1a 表示一个分支，或者一个 commit上面的打的标签

# git fetch 系列

$ git fetch --all
$ git fetch --tags
$ git reset --hard origin/master

# git tag
git tag -m "打个标签" TagName   ===》这是轻量级的标签
git show TagName  ===>查看标签代表的提交

# 查看程序两个版本之间的区别
另一个有用的操作是查看程序两个版本之间的区别， 以便了解改动详情。在命令行中，你
可以使用 git diff 命令进行查看。例如，执行下述命令可以查看 2a 和 2b 两个修订版本之
间的区别：
$ git diff 2a 2b

# git 查看一个文件的变化
git log fileName

# git 放弃新增缓存区
git reset --mixed

# 误删恢复
Step 1： git status
Step 2：git reset HEAD [ 被删除的文件或文件夹 ]
Step 3：git checkout  [ 被删除的文件或文件夹 ]
