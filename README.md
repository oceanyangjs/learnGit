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
