# learnGit
Git鼓励大量使用分支：

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>
  
  
  
1.创建分支dev，修改readme.txt，切换到master，可以看到该文件。
2.在dev，加到暂存区，切换到master，可以看到。
3.在dev，将文件释放到工作区，stash，切换到master，没有看到。
4.切换到dev，把stash pop，文件回到工作区。
5.在dev，将文件加到暂存区，stash，切换到master，没有看到。
6.切换到dev，把stash pop，文件回到工作区。
7.在dev，修改文件test.txt,并且加到暂存区，此时，readme.txt还在   工作区，切换到master,可以看到这两个文件，状态和在dev一致，切   换回dev，stash，然后pop，两个文件都出现在工作区。

结论：1.工作区和暂存区是共用的，在各个分支里都可以看到没被stash       的文件。
    2.在工作区和暂存区的文件都可以stash，pop之后都会出现在工作       区。

8.在dev，新增文件temp.txt，切换到master，可以看到该文件
9.切换在dev，把temp.txt加到暂存区，切换到master，可以看到
10.切换在dev，stash，切换到master，没有看到
11.切换到dev，stash pop，temp.txt回到原来的暂存区，而不是工作区！（这里发现stash pop后，新增文件跟修改文件不一样的）
结论：对于新增文件，stash pop后会出现在原有的地方


暂存区  工作区  提交历史 
这三块  暂存区切换分支可能数据丢失
工作区 和 有提交历史的部分  git保存
所以切换分支  要么将暂存区内容 git add  + git commit提交,有提交历史
要么 git stash 提交到工作区

github上已经有master分支 和dev分支

在本地

git checkout -b dev 新建并切换到本地dev分支

git pull origin dev 本地分支与远程分支相关联

在本地新建分支并推送到远程

git checkout -b test

git push origin test   这样远程仓库中也就创建了一个test分支

1. 克隆代码
git clone https://github.com/master-dev.git  
# 这个git路径是无效的，示例而已

2. 查看所有分支
git branch --all  
# 默认只有master分支，所以会看到如下两个分支
# master[本地主分支] origin/master[远程主分支]
# 新克隆下来的代码默认master和origin/master是关联的，也就是他们的代码保持同步

3. 创建本地新的dev分支
git branch dev  # 创建本地分支
git branch  # 查看分支
# 这是会看到master和dev，而且master上会有一个星号
# 这个时候dev是一个本地分支，远程仓库不知道它的存在
# 本地分支可以不同步到远程仓库，我们可以在dev开发，然后merge到master，使用master同步代码，当然也可以同步

4. 发布dev分支
发布dev分支指的是同步dev分支的代码到远程服务器
git push origin dev:dev  # 这样远程仓库也有一个dev分支了

5. 在dev分支开发代码
git checkout dev  # 切换到dev分支进行开发
# 开发代码之后，我们有两个选择
# 第一个：如果功能开发完成了，可以合并主分支
git checkout master  # 切换到主分支
git merge dev  # 把dev分支的更改和master合并
git push  # 提交主分支代码远程
git checkout dev  # 切换到dev远程分支
git push  # 提交dev分支到远程
# 第二个：如果功能没有完成，可以直接推送
git push  # 提交到dev远程分支
# 注意：在分支切换之前最好先commit全部的改变，除非你真的知道自己在做什么

6. 删除分支
git push origin :dev  # 删除远程dev分支，危险命令哦
# 下面两条是删除本地分支
git checkout master  # 切换到master分支
git branch -d dev  # 删除本地dev分
