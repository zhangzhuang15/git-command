# Git从零体验
## 跟着步骤做

1. 打开终端，切换到exercise目录下
2. 执行`git init`
3. 执行`git status`, 会看到
   ``` 
   On branch master
   
   No commits yet

   Untracked files:
    (use "git add <file>..." to include in what will be committed)
        README.md

   nothing added to commit but untracked files present (use "git add" to track)
   ``` 
4. 恭喜你🎉，完成了本地仓库初始化！
5. 恭喜你🎉，会使用`git status`查看本地仓库信息啦！
6. 执行 `git branch`, 没有输出
7. 创建一个`test.txt`文件
8. 执行 `git branch`, 会看到
   ``` 
   On branch master

   No commits yet

   Untracked files:
     (use "git add <file>..." to include in what will be committed)
        README.md
        test.txt

   nothing added to commit but untracked files present (use "git add" to track)  
   ```
9. 执行`git branch develop`,会看到
   ``` 
   fatal: Not a valid object name: 'master'.
   ```
10. 执行 `git add test.txt`
11. 恭喜你🎉，将工作区文件加入到暂存区，test.txt开始被git版本追踪！
12. 执行`git branch`, 没有输出
13. 执行`git commit -m "create test.txt"`, 会看到
    ``` 
    // 省略一部分内容....
    your configuration file:

        git config --global --edit

    After doing this, you may fix the identity used for this commit with:

        git commit --amend --reset-author

    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test.txt
    ```
14. 恭喜你🎉，完成了一次本地提交
15. 执行`git branch develop`, 没有输出
16. 恭喜你🎉，基于master分支成功创建了一个develop分支！
17. 不信？继续操作，验证一下！
18. 执行`git branch`, 会看到
    ``` 
      develop
    * master
    ```
19. 恭喜你🎉，已经知道使用`git branch`查看本地分支名列表啦！  
    *号表示你当前位于master分支哦🤣
20. 执行`git log`, 会看到类似的信息
    ``` 
    commit a1026cf770c39a8c8ab5fe56597daa2213708fb1 (HEAD -> master, develop)
    Author: **<______@##############>
    Date:   Mon Jan 10 23:40:12 2022 +0800

          create test.txt
    ```
21. 恭喜你🎉，你学会了使用`git log`查看本地历史提交信息啦
    > 你会发现自己在master分支提交的，develop分支也继承了这次
    > 提交的记录
22. 执行 `git ls-files`，会看出输出`test.txt`
23. 恭喜你🎉，会使用`git ls-files`查看本地有哪些文件被git版本跟踪啦
24. 执行`git checkout develop`, 会看到
    ``` 
    Switched to branch 'develop'
    ``` 
25. 恭喜你🎉，已经学会如何切换当前分支啦
26. 执行`git diff`，没有输出 
27. 向`test.txt`输入一些内容吧, 比如
    ``` 
    it's sunny today, I am going to walk my stupid dog!
    ```
28. 执行`git diff`, 会看到类似的信息
    ``` 
    diff --git a/test.txt b/test.txt
    index e69de29..4b7c9f1 100644
    --- a/test.txt
    +++ b/test.txt
    @@ -0,0 +1 @@
    +it's sunny today, I am going to walk my stupid dog!
    \ No newline at end of file
    ```
    > a代表暂存区，b代表工作区
29. 恭喜你🎉，知道如何查看暂存区和工作区文件的差异啦
30. 执行`git diff master develop`, 没有输出，为什么呢？向下看
31. 执行`git add test.txt`
32. 此时你的修改已经加入到了暂存区
33. 执行`git diff master develop`, 还是没有输出
34. 执行`git commit -m "add two line"`
35. 哎呀，信息提交错啦，应该是一行！哈哈，我们是故意做错的
36. 执行`git commit --amend`
37. 你会进入一个类似vim的编辑窗口，如果你懂得vim，上手改成"add one line
38. 如果你不懂vim，别慌，切至英文输入，按下"i"键, 按下➡️键把光标移动到"o"后边，按下删除键，删除“two”，再输入"one"，按下“esc”键，按下冒号键，光标会移动到左下角，输入“wq”，按下回车即可
39. 执行`git diff master develop`, 终于看到结果啦
    > a表示master分支，b表示develop分支
    > 看来它们比较的不是工作区，也不是暂存区，而是提交的结果
40. 恭喜你🎉，学会如何比对两个分支最近一次提交结果的差异啦！
41. 执行`git diff master develop test.txt`，你会看到同样的结果
    > 区别在于指定要比较的文件
    > 因为两个分支被跟踪的文件只有test.txt，所以两次结果一样
42. 算算我们git commit了几次？总共应该是3次，那么提交记录中是不是会有3次记录呢？
43. 执行`git log`, 发现记录里只有两次！
    > `git commit --amend`不会增加提交记录，而是覆盖之前`git commit `的记录
44. 执行`git log -1`, 发现只有最近的1次记录！
45. 往test.txt中再写一行
    ``` 
    it's sunny today, I am going to walk my stupid dog!
    however, it's at 5 o'clock, I can't get up!
    ```
46. 现在，我们打算会master分支看看
47. 执行`git checkout master`, 会看到
    ``` 
    error: Your local changes to the following files would be overwritten by checkout:
        test.txt
    Please commit your changes or stash them before you switch branches.
    Aborting
    ``` 
48. 提示我们去提交改动或者.....stash, WTF!这是什么鬼？
49. 别担心，执行`git status`，看看会给我们什么建议
    ``` 
    On branch develop
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   test.txt

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        README.md

    no changes added to commit (use "git add" and/or "git commit -a")
    ```
50. 建议我们继续走提交，或者使用 git restore
51. 来，试试`git restore test.txt`
52. 不！test.txt的第二行不见啦！
53. 恭喜你🎉，知道如果撤销文件区文件的修改啦
54. 不过，还是手动把第二行加回来吧，加好了，奔下走
55. 执行`git stash`
56. 执行`git checkout master`
57. yes!成功啦！
58. 恭喜你🎉，知道如何暂时保存分支现场后，切换分支啦
59. 在test.txt中写一行 
    ``` 
    I am fans of Harry Potter
    ```
60. 执行`git stash list`， 会看到
    ``` 
    stash@{0}: WIP on develop: e994869 add one line
    ``` 
    > 这是在develop分支执行 git stash形成的
61. 执行`git stash`、`git stash list`, 会看到
    ```
    stash@{0}: WIP on master: a1026cf create test.txt
    stash@{1}: WIP on develop: e994869 add one line
    ```
62. 切换回develop分支
63. 发现test.txt的第二行又不见啦，没关系，我们使用git stash已经记录它了，它跑不了！
64. 执行`git stash list`，输出的又是上边的结果，回忆一下，哪个是对应develop分支的？很明显，是 `stash@{1}`
65. 执行`git stash apply stash@{1}`
66. 第二行回来啦
67. 恭喜你🎉，会用git stash在分支间一来一会啦！🎆
68. 执行`git stash list`，发现依旧是那两行输出,请记住这点，后边要考哒！
69. 执行`git add test.txt`
70. 哎呀，怎么取消呢？问问 `git status`吧
    ``` 
    On branch develop
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        modified:   test.txt

    Untracked files:
     (use "git add <file>..." to include in what will be committed)
        README.md
    ```
71. 执行`git restore --staged test.txt`
72. okey,改回来啦，不信？`git status`查看一下啊
    > `git status` 祝您一路平安
73. 恭喜你🎉，会撤销git add，而且知道 git status的威力啦！
74. 现在，我们想让test.txt恢复到上一次提交后的状态，手动删除第二行？不存在的！按照git status的建议执行git restore？NO！
75. 执行`git checkout -- test.txt`
76. 第二行不见啦，恭喜你🎉，又学会一个小技能！
77. 我们突发奇想，想让develop分支回滚到第一次提交后的状态
78. 执行`git log`查看第一次提交时的ID号
    ``` 
    commit e994869e21e667fae923fb3b58be49f6308c7cd8 (HEAD -> develop)
    Author: yy <yy@ppt>
    Date:   Tue Jan 11 00:24:50 2022 +0800

    add one line

    commit a1026cf770c39a8c8ab5fe56597daa2213708fb1 (master)
    Author: yy <yy@ppt>
    Date:   Mon Jan 10 23:40:12 2022 +0800

    create test.txt

    ``` 
    > HEAD->develop 表示当前你位于develop分支，并且所处的提交
    版本号为e994869e21e667fae923fb3b58be49f6308c7cd8
79. 我的是a1026cf770c39a8c8ab5fe56597daa2213708fb1
80. 执行`git reset a1026cf770c39a8c8ab5fe56597daa2213708fb1`
81. 执行`git log`只剩下一个记录啦
82. 执行`git diff`，发现有差异，不是分支都回到第一次提交后了嘛？
    > git reset 只是将 本地仓库和暂存区滚回到了第一次提交时的样子，工作区没有回滚哦  
    > 如果想要工作区也回滚，git reset后边要加上 --hard
83. 恭喜你🎉，学会本地分支回滚啦
84. 接下来，我们想取消对test.txt的版本跟踪
85. 执行`git rm --cached test.txt`
86. `git status`查看一下 
    ``` 
    On branch develop
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
        deleted:    test.txt

    Untracked files:
      (use "git add <file>..." to include in what will be committed)
        README.md
        test.txt

    ```
87. test.txt位于Untracked files下，确实取消啦
88. 还记得上边留的关于git stash的坑吗？
89. 切换回master分支
90. `git stash list`，会看到
    ``` 
    stash@{0}: WIP on master: a1026cf create test.txt
    stash@{1}: WIP on develop: e994869 add one line
    ``` 
91. 选择哪一个呢？显而易见，是 stash@{0}
92. 执行`git stash pop stash@{0}`, 会看到
    ``` 
    CONFLICT (modify/delete): test.txt deleted in Updated upstream and modified in Stashed changes. Version Stashed changes of test.txt left in tree at test.txt~Stashed changes.
    The stash entry is kept in case you need it again.
    ``` 
93. * 我们在develop分支放弃了对test.txt的跟踪，于是test.txt回到了工作区，但是master分支的test.txt依旧被跟踪，发生了冲突。  
    * 所以git创建了一个新文件test.txt~Stashed，里边的内容正是我们在master分支中添加的内容，而test.txt文件中的内容则是我们在develop分支中添加的内容。  
    * 最重要的信息是 The stash entry is kept in case you need it again.这表明发生特殊情况下stash@{0}被保存下来，反之，可推出正常情况下会被删除掉。  
    * 所以， git stash apply 和 git stash pop有相同的效果，但是后者会删除stash@{}的记录，前者不会。
94. 恭喜你🎉，完成了所有的探索内容，自己多加练习再熟悉下吧
    

PS：关于`git push` `git pull`以及上述命令的详细使用，可参考git_command.md继续探索！

Thanks a lot !