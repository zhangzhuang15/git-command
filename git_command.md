# git 命令

## 前言
git分为本地仓库和远程仓库。 

git本地仓库的核心分为三部分，工作区、缓存区（或暂存区）、仓库本身，依次对应
Working Directory、index、HEAD，详情[戳这里](https://git-scm.com/book/zh/v2/Git-工具-重置揭密#_git_reset)👈。

在文档中总会使用`<url>`这样的标记，<>中表示某种对象，整体表示的是对象值。
比如url表示的是网址，`<url>`表示的就是具体的那个网址，也就是那一长条的字符串。
如果英文可以直接体现含义，将不再单独解释。

推荐一个[git可视化网页游戏](https://learngitbranching.js.org)  

&nbsp;

&nbsp;


<a id="0"></a>

## 目录

<a id="01"></a>
#### [本地项目推到github](#1)

<a id="02"></a>
#### [拷取远程项目到本地](#2)

<a id="03"></a>
#### [设置 git用户名、邮箱、密码](#3)

<a id="04"></a>
#### [初始化本地仓库](#4)

<a id="05"></a>
#### [添加远程仓库地址别名](#5)

<a id="06"></a>
#### [修改远程仓库地址别名](#6)

<a id="07"></a>
#### [修改别名对应的远程仓库地址](#7)

<a id="08"></a>
#### [查看别名对应的远程仓库地址](#8)

<a id="09"></a>
#### [查看远程仓库别名及其地址的列表](#9)

<a id="010"></a>
#### [拷贝远程仓库](#10)

<a id="011"></a>
#### [新建本地分支](#11)

<a id="012"></a>
#### [切换本地分支](#12)

<a id="013"></a>
#### [新建本地分支并切换到这个分支](#13)

<a id="014"></a>
#### [新建关联远程分支的本地分支](#14)

<a id="015"></a>
#### [删除本地分支](#15)

<a id="016"></a>
#### [删除远程分支](#16)

<a id="017"></a>
#### [重命名本地分支](#17)

<a id="018"></a>
#### [查看本地分支名单](#18)

<a id="019"></a>
#### [查看远程分支名单](#19)

<a id="020"></a>
#### [查看所有分支名单](#20)

<a id="021"></a>
#### [查看本地分支详细信息](#21)

<a id="022"></a>
#### [将本地分支和远程分支关联](#22)

<a id="023"></a>
#### [取消本地分支和远程分支的关联](#23)

<a id="024"></a>
#### [拉取远程分支的分支信息到本地](#24)

<a id="025"></a>
#### [添加文件到本地仓库的缓存区](#25)

<a id="026"></a>
#### [撤销git add](#26)

<a id="027"></a>
#### [把缓存区的信息提交到本地仓库](#27)

<a id="028"></a>
#### [文件恢复到上次commit时的样子](#28)

<a id="029"></a>
#### [取消git对文件的版本追踪](#29)

<a id="030"></a>
#### [重命名文件并更新到缓存区](#30)

<a id="031"></a>
#### [比较缓存区和工作区的差异](#31)

<a id="032"></a>
#### [比较缓存区和本地仓库中文件的差异](#32)

<a id="033"></a>
#### [比较本地两个分支本地仓库的差异](#33)

<a id="034"></a>
#### [比较本地两个分支本地仓库某文件的差异](#34)

<a id="035"></a>
#### [查看本地两个分支有哪些文件存在差异](#35)

<a id="036"></a>
#### [本地分支推送到远程仓库](#36)

<a id="037"></a>
#### [远程分支和本地分支合并](#37)

<a id="038"></a>
#### [设置本地分支默认推送到哪个远程分支](#38)

<a id="039"></a>
#### [打标签](#39)

<a id="040"></a>
#### [查看本地仓库都创建了哪些标签](#40)

<a id="041"></a>
#### [查看远程仓库都有哪些标签](#41)

<a id="042"></a>
#### [删除本地分支的标签](#42)

<a id="043"></a>
#### [删除远程仓库的标签](#43)

<a id="044"></a>
#### [基于标签创建一个本地分支](#44)

<a id="045"></a>
#### [查看本地分支提交历史](#45)

<a id="046"></a>
#### [本地分支回滚到某一个版本](#46)

<a id="047"></a>
#### [状态暂存并切换分支](#47)

<a id="048"></a>
#### [终端无法正常显示中文字符](#48)

&nbsp;

&nbsp;


<a id="1"></a>

## 本地项目推到github

1. 在github上创建远程仓库，自动生成`main`分支，拷贝仓库地址 `url`， 拷贝`authenticate token`;
2. 进入本地项目目录下执行`git init`, 自动生成`master`分支;
3. 新建分支`git branch dev`;
4. 切换到新分支`git checkout dev`;
5. 提交项目所有文件到本地缓存`git add --all`;
6. 把本地缓存提交到本地仓库`git commit -m <message>`;
7. 添加远程仓库名称 `git remote add origin <url>`;
8. 执行`git push --set-upstream origin`;
9. 输入github账户名和`<authenticate token>`;
10. 推送到远程仓库`git push origin dev`;
11. 远程仓库将出现dev分支，包含项目中的所有代码；

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#01)

<a id="2"></a>

## 拷取远程项目到本地

1. 在github上拷贝仓库地址`url`;
2. 进入本地存储该项目的文件夹下，执行`git clone <url>`;
3. 拉取远程仓库分支的信息`git fetch origin`;
4. 在本地新建一个远程仓库的同名分支develop，并和该分支关联  
   `git checkout develop`
   > 也可以执行   
   `git checkout --track origin/develop`  
   > 还可以给本地分支换个名字  
   `git checkout -b mydevelop origin/develop`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#02)

<a id="3"></a>

## 设置 git用户名、邮箱、密码

`git config --global user.name <your_name>`  
`git config --global user.email <your_email>`  

`git config --global credential.helper store` 执行后，第一次调用git pull 或者 git push，输入密码，之后就不需要输入密码了

> 对于github，已经改为`authenticate_token`验证方式,不再使用密码。

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#03)

<a id="4"></a>

## 初始化本地仓库

假设你位于project文件夹下，且该文件夹就是你的项目根目录  

此时project仅仅是文件系统的文件夹而已，并不是git本地仓库  

执行 `git init`  

结果：  
* 将project初始化为本地仓库
* 建立一个默认分支master
  
&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#04)

<a id="5"></a>

## 添加远程仓库地址别名

> 假设你知道远程仓库地址 `url`  
在后续 push 或者 pull 操作中，总会使用这个`url`  
因为`url`本身是很长的字符串，非常不方便记忆和命令行输入  
所以，类似`ip地址`和`域名`的做法，给远程仓库地址取个别名使用  

执行  

`git remote add origin <url>`  

`origin`就是别名，你可以取一个你喜欢的名字  

后续使用远程仓库地址的地方，就可以使用 `origin` 代替

> 对于支持用户名和密码方式访问的git服务端，可以在url中加入用户名和
> 密码信息，可避免git push 或者 git pull 时再输入用户名、密码。  
>  
> 假设url是"https://bbhub.com/bbb.git",用户名为xiao,密码为ak47,  
> 则加入用户名和密码的url为"https://xiao:ak47@bbub.com/bbb.git".  
>
> 最后执行`git remote add origin <url>`即可  
> 后续执行和origin相关的push和pull操作，就不会再用输入用户名、密码

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#05)


<a id="6"></a>

## 修改远程仓库地址别名

假设当前远程仓库地址别名是 origin，但出于某种原因，必须要改为 own  

执行  

`git remote rename origin own`
> 很好理解，把某个名字重命名为另一个名字，旧名字当然在前，新名字在后啦  
 
&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#06)


<a id="7"></a>

## 修改别名对应的远程仓库地址

假设当前仓库地址别名是 origin, 但是远程仓库地址由`<url>` 改成了 `<new_url>`  

考虑到兼容性，你想继续使用 origin作为远程仓库新地址的别名  

执行  

`git remote set-url origin <new_url>`  

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#07)


<a id="8"></a>

## 查看别名对应的远程仓库地址

假设当前仓库地址别名是 origin，但你想不起来origin对应的远程仓库地址是什么了  

执行  

`git remote get-url origin`  

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#08)


<a id="9"></a>

## 查看远程仓库别名及其地址的列表

`git remote -v`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#09)


<a id="10"></a>

## 拷贝远程仓库

`git clone <url>`

url是远程仓库地址.

假设远程仓库的默认分支是main，在上述指令执行完毕后

* 你将拥有一个本地仓库
* 本地仓库会有一个main本地分支, 该分支会与远程main分支关联
* 你将得到一个自动创建的远程仓库的别名origin
* 你将获取远程仓库所有分支的分支信息，用`git branch -r`可查看

如果你想更进一步，在拷贝完远程仓库后，不留在main分支，而是新建
一个和远程分支同名且关联的本地分支，然后留在这个新的本地分支

可执行
`git clone -b <branch-name> <url>`
> 分支名一定要和远程仓库众多分支中的一个保持一致！

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#010)


<a id="11"></a>

## 新建本地分支

`git branch <branch-name>`
  
将从当前分支拉出一个新分支，名字为`<branch-name>`  

> 你也可以基于tag创建分支：`git branch <branch-name> <tag-name>`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#011)


<a id="12"></a>

## 切换本地分支

假设你处于分支master，想切换到分支dev  

执行  `git checkout dev` 

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#012)


<a id="13"></a>

## 新建本地分支并切换到这个分支

假设你处于分支master，想创建一个新分支dev，并切换到dev分支  

执行 `git checkout -b dev`  

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#013)


<a id="14"></a>

## 新建关联远程分支的本地分支

假设你处于分支dev, 并知道远程仓库的一个分支名dev_remote_1  

你发现本地没有一个分支关联这个远程分支  

你想创建一个新的本地分支关联这个远程分支  

* 执行
    `git checkout --track origin/dev_remote_1`
    > 在本地创建一个dev_remote_1分支，并切换到该分支，且
    > 该分支和远程的dev_remote_1分支关联  

* 执行
    `git checkout dev_remote_1`
    > 效果同上, 但本地不能有叫做 dev_remote_1的分支，否则
    > 会直接切换到该分支，不会创建新分支

* 执行
    `git checkout -b dev_1 origin/dev_remote_1`
    > 本地创建一个叫 dev_1的分支，该分支与远程分支dev_remote_1
    > 关联，并切换到dev_1分支

> 如果上述执行失败，请执行 `git fetch origin -a`, 再重试

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#014)


<a id="15"></a>

## 删除本地分支

`git branch -d <branch-name>` 
> 分支`<branch-name>`必须和远程分支完成充分的合并，或者根本
> 没有关联到远程分支。

或者

`git branch -D <branch-name>`
> 强制删除。
  
&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#015)


<a id="16"></a>

## 删除远程分支
假设你位于 dev 分支，要删除的是远程 dev33分支。  

方法一：  
`git push origin : <remote-branch-name>`
> 即 `git push origin  :dev33`；  
> 这一步还会删除 origin/dev33 分支；

方法二：
`git push origin -d <remote-branch-name>`
> 即 `git push origin -d dev33`；  
> 这一步同样后删除 origin/dev33 分支；

***注意***  
`git branch -d -r origin/dev33`
> 只会删除 origin/dev33 分支，不会影响到远程分支；  
> 如果省略 `-r` ，只能删除本地分支，无法删除 origin/dev33分支。


&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#016)


<a id="17"></a>

## 重命名本地分支

`git branch -m <old-branch-name> <new-branch-name>`
> 很好理解，把某个分支移动为另一个分支，因此旧的分支名在前，
> 新的分支名在后

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#017)


<a id="18"></a>

## 查看本地分支名单

`git branch`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#018)


<a id="19"></a>

## 查看远程分支名单

`git branch -r`
> r 就是 remote

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#019)


<a id="20"></a>

## 查看所有分支名单

`git branch -a`
> a 就是 all

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#020)


<a id="21"></a>

## 查看本地分支详细信息

`git branch -vv`
> 可获取 本地分支名、本地分支关联的远程分支名、本地分支版本是否领先远程分支；

`For example:`

``` 
      iss53     7e424c3    [origin/iss53: ahead 2] forgot the brackets
     master     1ae2a45    [origin/master] deploying index fix
 *serverfix     f8674d9    [teamone/server-fix-good: ahead 3,
                            behind 1] this should do it
    testing     5ea463a    trying something new
``` 
> `head 2` 表示本地分支有2个提交没有同步到远程分支  
> `behind 1` 表示远程分支有1个提交还没有合并到本地分支  
> `*`号表示当前分支

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#021)


<a id="22"></a>

##  将本地分支和远程分支关联

假设：
* 你处于分支dev
* 远程仓库名你已经设定为origin
* 你想将分支dev和远程分支develop关联  
  
执行 `git branch -u origin/develop`  
> -u 是 --set-upstream-to 的缩写  

设置关联的好处：  
当你想push或者pull的时候，只需执行`git push origin` 或 `git pull origin`，
关于远程分支的信息可省略

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#022)


<a id="23"></a>

## 取消本地分支和远程分支的关联

假设你处于分支dev，该分支已经和远程分支develop关联，你想取消关联  

执行 `git branch --unset-upstream`  

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#023)


<a id="24"></a>

## 拉取远程分支的分支信息到本地  

* 执行  

    `git fetch origin dev`
    > 拉取远程分支dev的分支信息到本地，执行 `git branch -a`
    > 将会看见`remotes/origin/dev`

* 执行
    `git fetch origin -a`
    > 拉取远程仓库origin所有分支的分支信息到本地

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#024)


<a id="25"></a>

## 添加文件到本地仓库的缓存区

项目中的文件在最开始只是停留在文件系统中，git没有对它进行版本跟踪

需要将文件添加到本地仓库缓存区后，git才会对它进行版本跟踪

执行
`git add <文件存储路径>`
> 第一次执行时，文件会被git跟踪  
> 之后执行时，文件的改动信息会被存储到本地仓库缓存区

对于所有已被追踪的文件，可以一步到位
`git add --all`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#025)


<a id="26"></a>

## 撤销git add

你执行完 git add指令，将一些文件的修改加入到本地仓库的缓存区后，觉得  
不妥，想撤销刚才的 git add操作，  

执行  
`git reset HEAD <filename>`
> 指定的文件就会被取消已发生的 git add操作


&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#026)


<a id="27"></a>

## 把缓存区的信息提交到本地仓库

`git commit -m <message>`

message 是本次提交的一些说明，方便以后查看提交记录排查问题、锁定重要版本代码

还有另一种情况极为常见
* 你执行了一次git commit操作
* 之后，你发现提交的message有问题，或者代码修改仍存在问题

你很可能按照 git add、git commit的流程再来一遍，这样你会提交了
两次，但是你也可以只提交一次

你要做的就是
* 继续修改文件，改完后 git add
* 提交的时候执行 `git commit --amend`

这样，你不会重新提交一次，而是将上一次和本次的提交合并为一个来处理

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#027)


<a id="28"></a>

## 文件恢复到上次commit时的样子

在开发过程中，固然可以借助编辑器的撤销指令回退，但你无法确定回退到哪一步
刚好是上次提交后的情形。如果你想将文件的内容恢复到上次提交后的样子，执行 
`git checkout -- <filename>`
> 注意，这将改变本地文件系统中的文件，而文件在本地仓库缓存区中的记录不会受到
> 影响

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#028)


<a id="29"></a>

## 取消git对文件的版本追踪

`git rm --cached <filename>`
> 文件将会从本地仓库的缓存区中移除，不再接收git的版本追踪，但不会从文件系统中删除

如果想更进一步，把文件也删除掉，执行 `git rm <filename>`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#029)


<a id="30"></a>

## 重命名文件并更新到缓存区

当你修改文件名称后，缓存区的信息将和文件不一致，此时你还要重新git add，
当然，有一种更简单的方法，执行   
`git mv <filename> <file_newname>` 

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#030)


<a id="31"></a>

## 比较缓存区和工作区的差异

`git diff`

返回本分支文件在缓存区和工作区的差异

你修改一个文件，执行git add，之后你继续修改这个文件，你在某个
时间点想知道手头上的文件，和上次git add时有什么差异，就可以用此命令

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#031)


<a id="32"></a>

## 比较缓存区和本地仓库中文件的差异

`git diff --cached` 

你使用git commit 完成了一次提交，此时所有文件的状态记作A，
你又开始工作，修改了一些文件，之后执行git add将改动加入缓存
区，此时缓存区中所有文件的状态记作B，这时你想看看A和B之间有什么
差异，就可以用该命令

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#032)


<a id="33"></a>

## 比较本地两个分支本地仓库中的差异

`git diff <branchname1> <branchname2>`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#033)


<a id="34"></a>

## 比较本地两个分支本地仓库某文件的差异

`git diff <branchname1> <branchname2> <filename>`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#034)


<a id="35"></a>

## 查看本地两个分支有哪些文件存在差异

`git diff <branchname1> <branchname2> --stat`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#035)


<a id="36"></a>

## 本地分支推送到远程仓库

在完成了 git commit后，就可以将本地分支推送到远程仓库

假设你位于本地分支main, 并准备推送到远程分支develop

`git push origin main:develop`

> * `git push` 默认会选择推送给`origin`；
> * 把某个分支推送到另一个分支，本地分支名当然在前，远程分支名当然在后啦
> * 如果省略`:develop`，会将main分支推送到它所关联的远程分支，
> 没有关联的远程分支的话，就会在远程仓库创建一个新的同名分支，并推给这个分支。本地会生成 `origin/main`虚拟分支。
> * 如果省略`main`,相当于删除远程分支develop
> * 如果本地分支已经关联到远程分支develop且二者同名，  
> 可简写为`git push origin`    
>   * 尽管本地分支和远程分支关联, 但他们的分支名字不同，git会考虑安全问题选择拒绝执行push。


&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#036)


<a id="37"></a>

## 远程分支和本地分支合并

当远程分支有更新，你需要让本地分支与远程分支同步一下

假设你位于本地分支main，要去同步的远程分支为develop

`git pull origin develop:main`

> * 把某个分支拉到另一个分支上合并，远程分支名当然在前，本地分支名当然在后啦
> * 如果省略`:main`，会将远程分支develop拉取到当前本地分支
> * 如果当前本地分支已经关联远程分支develop且二者同名，可简写为  
> `git pull origin`

> 如果想让两个本地分支合并，可以使用git merge 命令：
> 1. `git merge jack` 将jack分支合并到当前分支
> 2. `git cherry-pick <commit-id>` 将某次提交所做的改动合并到当前分支上，也可以是多次提交，提交ID号用空格隔开即可。

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#037)


<a id="38"></a>

## 设置本地分支默认推送到哪个远程分支

假设你位于本地分支main，想让该分支每次git push操作推送给远程分支develop

`git push --set-upstream origin develop`

对于git pull的情形，同理有   
`git pull --set-upstream origin develop`

*设置本地分支和远程分支相关联，其实就是同时完成了上边的两个设置*

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#038)


<a id="39"></a>

##  打标签

* 执行`git tag <tagname>`, 会根据当前本地分支上一次的git commit结果创建一个标签

    或者，更进一步，你可以为标签添加一些解释信息  
    `git tag -a <tagname> -m <message>`
  
    你也可以根据某一次的commitID创建标签  
    `git tag <tagname> <commitID>`

    实际上`git tag <tagname>`是`git tag <tagname> HEAD`的缩写


* 推送到远程仓库  
`git push origin <tagname>`

在github上的tags列表就能看到你新创建的标签  

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#039)


<a id="40"></a>

## 查看本地仓库都创建了哪些标签

`git tag -l` or `git tag`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#040)

<a id="41"></a>

## 查看远程仓库都有哪些标签

`git ls-remote --tags origin`

[返回目录](#0)
[返回条目](#041)

<a id="42"></a>

##  删除本地分支的标签

`git tag -d <tagname>`  

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#042)


<a id="43"></a>

## 删除远程仓库的标签

`git push origin --delete <tagname>`

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#043)


<a id="44"></a>

## 基于标签创建一个本地分支

`git checkout -b <branchname> <tagname>`

你开发完v1.0.0的代码，打好一个标签v1.0.0

你要接着v1.0.0的代码开发v2.0.0的代码 

你就可以使用上述指令创建一个新的分支，在该分支上继续你的开发

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#044)


<a id="45"></a>

## 查看本地分支提交历史

`git log`

你可以从输出看到每一次提交信息，最重要的是`commitID`;

该指令还有一些拓展用法

* `git log -2`               只显示最近两次的提交记录

* `git log --since=2.weeks`  只显示最近两周内的提交记录
  
* `git log --util=2.weeks`   只显示两周之前的提交记录

* `git log --author=jack`    只显示提交记录中作者是jack的所有记录

* `git log --committer=jack` 只显示提交记录中提交者是jack的所有记录

* `git log  --grep=mm`       只显示提交记录message中包含 mm的所有记录

* `git log -S straw`         只显示添加或者删除内容匹配straw的提交记录

* `git log --stat`           额外列出修改的文件名

* `git log --shortstat`      额外显示--stat中修改的行数信息

* `git log -p`               额外列出被修改的文件，改前和改后的差异

* `git log --pretty=oneline` 每一个提交的记录单行输出，除了oneline还可以有 `full` `short` `fuller` `format`

* `git log --pretty=format:"%h  %an %ar %s"`  
    采用format，自定义输出信息格式  
    %h      提交的简写hash码  
    %H      提交的完整hash码  
    %an     作者名字  
    %ae     作者邮箱  
    %ad     作者修订的日期  
    %ar     作者多久前修订的  
    %cn     提交者名字  
    %ce     提交者邮箱  
    %cd     提交者修订的日期   
    %cr     提交者多久前修订的   
    %s      提交的信息

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#045)


<a id="46"></a>

## 本地分支回滚到某一个版本

使用`git log`找到某一版本的`commitID`  

* 执行   
    `git reset <commitID>`
    > 缓存区和本地仓库数据会回滚到该版本，工作区不受影响

* 执行  
    `git reset --sort <commitID>`
    > 本地仓库数据会回滚到该版本，工作区和缓存区不受影响

* 执行  
    `git reset --hard <commitID>`
    > 本地仓库、缓存区、工作区数据回滚到该版本


在此基础上，执行一步git push操作即可完成远程分支版本回滚

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#046)


<a id="47"></a>

## 状态暂存并切换分支

假设你在dev_1分支上编写代码，出于某种原因，你要切换到dev_2分支  
修改一些代码，可是，你没有git add和git commit,无法完成分支切换，  
这种情况下，你可以  
1. `git stash`
2. `git checkout dev_2`
3. 解决dev_2的代码问题，在commit后，切换回dev_1分支
4. `git stash apply` or `git stash pop`
5. 继续修改dev_1分支上未完成的编码工作

&nbsp;

&nbsp;

[返回目录](#0)
[返回条目](#047)


<a id="48"></a>

## 终端无法正常显示中文字符
当你执行 `git status` 后，如果发现终端无法显示正常的中文字符，你可以
这样解决：  
执行 `git config --global core.quotepath false`  

[返回目录](#0)
[返回条目](#047)